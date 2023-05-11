# Nextcloud_Apache-Kubernetes
Deploy Nextcloud Apache Version on Kubernetes

![logo](/Images/Nextcloud_Logo.png )

This repository contains YAML files for deploying Nextcloud on a Kubernetes cluster using kubectl.

## Installation :

1. Clone this repository:

       git clone https://github.com/uruzFR/module-sim800c.git
2. Edit the YAML files according to your requirements.

3. Apply the YAML files using kubectl apply -f command:

       kubectl apply -f [file-name].yaml
You can apply all the YAML files at once using the following command:

       kubectl apply -f .
This command applies all the YAML files in the current directory in the order they appear in the directory.

## Usage :

You can use kubectl commands to manage your deployment, services, and pods.

For example, to view the status of your pods, use the following command:

       kubectl get pods
To view the logs of a pod, use the following command:
       
       kubectl logs [pod-name]
For more information on using kubectl, see the Kubernetes documentation.

## Info :

If you do not have root access on the cluster, you may need to recompile the Docker image with a different UID and GID. To do so, use the following Dockerfile:
       
    FROM nextcloud:apache
    RUN apk --no-cache add shadow && \
       groupmod --gid 1001 www-data && \
       usermod --uid 1001 www-data
After that, call this file to build your image:

       app:
    build:
        context: ./
        dockerfile: Dockerfile
    restart: always


## Authors

- [@uruzFR](https://github.com/uruzFR)
