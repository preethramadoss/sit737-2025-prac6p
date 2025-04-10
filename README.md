# SIT737 – Task 6.1P: Kubernetes Deployment of a Containerized Application

## Overview

This repository documents the process of deploying a Dockerized Node.js application (LOOPII) on a local Kubernetes cluster using Docker Desktop. The project includes configuring Kubernetes, deploying the application using YAML manifests, exposing it through a NodePort service, and enabling Kubernetes Dashboard access with administrative privileges.

## Tools and Technologies

1. Docker Desktop (with Kubernetes enabled)

2. Kubernetes CLI (`kubectl`)

3. Visual Studio Code

4. GitHub

5. Docker Hub

## Implementation Steps

### 1. Enable Kubernetes in Docker Desktop

--> Enabled Kubernetes from Docker Desktop settings.

--> Verified setup using:

kubectl version

kubectl get nodes

### 2. Configure Kubernetes Dashboard Access

**dashboard-adminuser.yaml**

**cluster_role_binding.yaml**

Applied using:

kubectl apply -f dashboard-adminuser.yaml

kubectl apply -f cluster_role_binding.yaml

### 3. Deploy the Web Application

**deployment.yaml**

Deploy using:

kubectl apply -f deployment.yaml

### 4. Create a ReplicaSet

**replicaset.yaml**

### 5. Expose the App with NodePort

**service.yaml**

Apply the service:

kubectl apply -f service.yaml

Access the application:

http://localhost:30080

### 6. Access Kubernetes Dashboard

Start the proxy:

kubectl proxy

Visit Dashboard:

http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/

Generate login token:

kubectl -n kubernetes-dashboard create token admin-user

Login with the token.

## Screenshots and Verifications

--> Output of `kubectl get pods`

--> Output of `kubectl get services`

App accessible at `http://localhost:30080`

Kubernetes Dashboard interface

--> Output of `kubectl get pods --show-labels`

--> Output of `kubectl describe service loopii-service`

All screenshots are stored in the `/screenshots` directory.

## Conclusion

This repository demonstrates the deployment of a containerized web application on Kubernetes. It includes replication management using Deployment and ReplicaSet, service exposure via NodePort, and secure access to the Kubernetes Dashboard. The project successfully achieves all specified task outcomes.
