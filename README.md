# Wisecow – Containerization & Kubernetes Deployment

A DevOps project demonstrating the containerization, deployment, and continuous integration of the **Wisecow** application using **Docker**, **Kubernetes**, **GitHub Actions**, and **TLS**.

## Project Overview

This project containerizes the Wisecow application and deploys it on a Kubernetes cluster (Minikube) with secure HTTPS communication. A GitHub Actions workflow automates Docker image builds and pushes to Docker Hub whenever changes are committed.

## Features

- Dockerized the Wisecow application
- Kubernetes deployment using Minikube
- Kubernetes Service and Ingress configuration
- TLS enabled using cert-manager and self-signed certificates
- Automated CI/CD pipeline using GitHub Actions
- Docker image automatically built and pushed to Docker Hub

## Tech Stack

- Docker
- Kubernetes (Minikube)
- NGINX Ingress Controller
- cert-manager
- GitHub Actions
- Docker Hub
- Bash
- Git

## Project Structure

```
.
├── .github/
│   └── workflows/
│       └── ci-cd.yml
├── k8s/
│   ├── namespace.yaml
│   ├── deployment.yaml
│   ├── service.yaml
│   ├── ingress.yaml
│   ├── issuer.yaml
│   └── certificate.yaml
├── Dockerfile
├── README.md
├── wisecow.sh
└── LICENSE
```

## Kubernetes Resources

The project deploys the following Kubernetes resources:

- Namespace
- Deployment
- Service
- Ingress
- TLS Certificate
- Issuer (cert-manager)

## CI/CD Pipeline

The GitHub Actions workflow automatically:

1. Checks out the repository
2. Builds the Docker image
3. Logs in to Docker Hub
4. Pushes the latest Docker image

Workflow Location:

```
.github/workflows/ci-cd.yml
```

## Docker Image

Docker Hub Repository

```
https://hub.docker.com/r/vivek65666/wisecow
```

Pull the latest image

```bash
docker pull vivek65666/wisecow:latest
```

Run locally

```bash
docker run -p 4499:4499 vivek65666/wisecow:latest
```

## Deployment

Deploy the application

```bash
kubectl apply -f k8s/
```

Verify resources

```bash
kubectl get all -n wisecow
```

## TLS Verification

The application supports HTTPS using a self-signed certificate issued through cert-manager.

Example:

```bash
curl -k -H "Host: wisecow.local" https://127.0.0.1
```

## Screenshots / Verification

Successfully verified:

- Docker image build
- Docker image pushed to Docker Hub
- Kubernetes deployment
- Service exposure
- Ingress routing
- HTTPS/TLS communication
- GitHub Actions workflow execution

## Future Improvements

- Automatic Continuous Deployment to Kubernetes
- Production-ready TLS using Let's Encrypt
- Helm chart support
- Monitoring with Prometheus and Grafana
- Kubernetes Horizontal Pod Autoscaler
- Multi-stage Docker builds

## Repository

GitHub

```
https://github.com/vivek65666/wisecow
```

Docker Hub

```
https://hub.docker.com/r/vivek65666/wisecow
```

## Acknowledgements

Original Wisecow application:

https://github.com/nyrahul/wisecow

This repository extends the original project by implementing containerization, Kubernetes deployment, TLS, and CI/CD automation.
