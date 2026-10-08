# Cargill Kubernetes Manifests & GitOps Repository (CD)

This repository contains all **Kubernetes deployment manifests, Helm charts, and Harness CD pipeline definitions** for Cargill's microservices and observability components.

## Structure:
- `order-service/`: Kubernetes manifests (`deployment.yaml`, `service.yaml`, `configmap.yaml`, `hpa.yaml`).
- `.harness/pipeline.yaml`: Harness Continuous Delivery pipeline YAML configuring:
  - Rolling deployment to Amazon EKS (`supplychain-dev` namespace).
  - Dynamic image tag injection from GitHub Actions CI payload (`<+input.DOCKER_IMAGE_TAG>`).
  - Automated Health Check verification against `/health` endpoint.
  - Automated Rollback execution if pod readiness or health checks fail.
