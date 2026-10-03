# IBM Skills Network Guestbook Final Project

This repository is prepared for the IBM course **Introduction to Containers, Kubernetes and OpenShift**, Final Project: **Build and Deploy a Simple Guestbook App**.

## Source basis

The application files under `v1/guestbook` are reconstructed from the public IBM Developer Skills Network Guestbook repository and preserve its standard Go/HTML/JavaScript/CSS structure.

## Repository layout

- `v1/guestbook/main.go` — Guestbook Go HTTP application; listens on port 3000.
- `v1/guestbook/Dockerfile` — completed multi-stage Docker build for course Task 1.
- `v1/guestbook/public/index.html` — original v1 web page.
- `v1/guestbook/public/script.js` — Guestbook browser logic.
- `v1/guestbook/public/style.css` — Guestbook styling.
- `v1/guestbook/public/jquery.min.js` — bundled jQuery dependency used by the original app.
- `v1/guestbook/deployment.yml` — baseline Kubernetes Deployment named `guestbook`, container port 3000, image tag `guestbook:v1`, with 50m/20m CPU settings.
- `v1/guestbook/deployment-v2.yml` — prepared rolling-update manifest with 5m limit / 2m request CPU settings.
- `v1/guestbook/public/index-v2.html` — preserved v2 page artifact with both required strings exactly `Guestbook – v2`.
- `k8s/hpa.yml` — declarative equivalent of the course HPA settings: 1–10 replicas and 5% target CPU utilization.

## Runtime evidence

This repository contains source code and manifests only. Docker, IBM Cloud Container Registry, and Kubernetes were **not** executed by this repository preparation. No image digest, registry listing, HPA observation, rollout revision, ReplicaSet state, or screenshot is claimed here.

For IBM Cloud execution, replace the image reference in the Deployment with the actual registry-qualified image, for example:

`us.icr.io/$MY_NAMESPACE/guestbook:v1`

The course graded workflow uses `kubectl port-forward deployment.apps/guestbook 3000:3000`; a Kubernetes Service is not required for Tasks 1–10.
