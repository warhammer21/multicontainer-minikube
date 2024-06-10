# Multi-Container Minikube Project

This repository contains a multi-container setup for Minikube, including a Django Polls app, PostgreSQL database, and Kubernetes configurations.

## Project Structure

- `app-server/django-polls-app-replica-set.yml`: ReplicaSet configuration for the Django Polls app.
- `app-server/django-polls-app-service.yml`: Service configuration for the Django Polls app.
- `postgres/postgres-db-replica-set.yml`: ReplicaSet configuration for the PostgreSQL database.
- `postgres/postgres-db-service.yml`: Service configuration for the PostgreSQL database.
- `postgres/postgres-pvc.yml`: PersistentVolumeClaim for PostgreSQL storage.
- `db-secret.yml`: Kubernetes Secret for database credentials.
- `django-polls-ingress.yml`: Ingress configuration for the Django Polls app.
- `postgres-pv.yml`: PersistentVolume configuration for PostgreSQL storage.

## Deployment Steps

1. Deploy the ReplicaSets and Services:
    ```sh
    kubectl apply -f app-server/django-polls-app-replica-set.yml
    kubectl apply -f postgres/postgres-db-replica-set.yml
    kubectl apply -f postgres/postgres-pvc.yml
    kubectl apply -f db-secret.yml
    kubectl apply -f app-server/django-polls-app-service.yml
    kubectl apply -f postgres/postgres-db-service.yml
    ```

2. Deploy the Ingress:
    ```sh
    kubectl apply -f django-polls-ingress.yml
    ```

## Accessing the Application

Once everything is deployed, you can access the application through the IP provided by Minikube and the configured Ingress path.

```sh
minikube ip
