# k8s-ansible-ubuntu

----

Setup Kubernetes cluster on ubuntu.20 machine by ansible

This repo tells you how to setup Kubernetes cluster with kubeadm on ubuntu machine by ansible.

----

## Preparation

- Checkout this repository
- download mitogen-0.2.9 into the root folder of this repository. Please refer to the location specified in ansible.cfg
- create k8s-inventory file with k8s-inventory.template. Configure k8s-inventory with your own master and worker node IP.
- Assuming you will run ansible playbook from a specified machine(e.g. machine1) with user1. You could use ssh-keygen to generate SSH Key Pair and then use ssh-copy-id to install public key into master and work nodes
```
ssh-keygen

ssh-copy-id <user1>@<master or worker node ip>

``` 
- Install Ansible 2.9.4 in the specifid machine(e.g. machine1)
- Configure your own registry server IP for insecure_docker_registries in all.yml. You could use docker command below to setup registry.
```
docker run -d -p 5000:5000 --restart=always --name registry registry:2
```

## Start Installation

Use the command below to start installation

```
ansible-playbook site.yml

```

## Reset cluster

Use the command below to reset cluster. This will destroy the current Kubernetes cluster

```
ansible-playbook reset-site.yml

```
