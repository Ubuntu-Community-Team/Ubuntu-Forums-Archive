---
title: "INSTALLATION FAILED: chart requires kubeVersion"
date: 2023-03-14
forum: Server Platforms
---

### Post by dlf2023 on 2023-03-14
Hi!

I'm still a bit unused to Linux even if I used Linux on and off for 20y.. But I'm trying to learn a bit about Kubernetes and stuff like Rancher so i installed a VM with Ubuntu Pro Server and I got MicroK8s up and running after nuking around 10 VM's (Tried other Dists before Ubuntu) trying to set it all up and I'm almost done but when trying to install Rancher with:

```
microk8s helm3 repo add rancher-stable https://releases.rancher.com/server-charts/stable

microk8s helm3 repo update

microk8s kubectl create namespace cattle-system

microk8s helm3 install rancher rancher-stable/rancher \
   --namespace cattle-system \
   --set hostname=${HOSTNAME} \
   --set replicas=3 \
```

I get

```
Error: INSTALLATION FAILED: chart requires kubeVersion: < 1.25.0-0 which is incompatible with Kubernetes v1.26.1
```


What should I do? As I stated.. I'm still not used to Linux in at this level and still learning.

---

### Post by slickymaster on 2023-03-15
Thread moved to **Server Platforms** for a better fit

---

### Post by LHammonds on 2023-03-15
I have no experience with Kubernetes so take what I say with a grain of salt.

I did a quick search for articles and most of what I am seeing are steps to install Docker, then Ranger, then deploy Kubernetes clusters.

References:
[Install Kubernetes](https://ubuntu.com/kubernetes/install)
[Install Rancher on Ubuntu](https://phoenixnap.com/kb/install-rancher-on-ubuntu)
[How to install Rancher on Ubuntu 22.04](https://www.linuxtechi.com/how-to-install-rancher-on-ubuntu/)
[How to install Rancher in minutes on Ubuntu 20.04](https://ulrikchristensen.com/how-to-install-rancher-in-minutes/)

LHammonds

---

