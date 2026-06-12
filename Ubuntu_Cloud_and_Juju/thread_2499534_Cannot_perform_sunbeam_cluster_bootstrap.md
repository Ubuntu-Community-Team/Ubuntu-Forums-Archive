---
title: "Cannot perform sunbeam cluster bootstrap"
date: 2024-07-30
forum: Ubuntu Cloud and Juju
---

### Post by madscientist813 on 2024-07-30
I always receive the following error:

Deploying OpenStack Control Plane to Kubernetes (this may take a while) ... waiting for services to come online (5/32)Timed out while waiting for model 'openstack' to be ready
Error: Timed out while waiting for model 'openstack' to be ready

Any assistance will be greatly appreciated.

---

### Post by merten2000 on 2024-07-30
Hey, can you share the steps you have done? and at what step it fails? (and also share the HW + OS you are using?)
I followed these: 
[https://ubuntu.com/blog/openstack-with-sunbeam-for-small-scale-private-cloud-infrastructure](https://ubuntu.com/blog/openstack-with-sunbeam-for-small-scale-private-cloud-infrastructure)

running on a GCP compute engine (n1-standard-8; ubuntu 22.04 with nested virtualization enabled)  (I had a smaller box before and it failed ...) 
I have a fully running Openstack (inc. Magnum) but it fails when creating a cluster as it is pulling an image version that is not in the repo ... (and / or using the wrong repo....) 
See errors below - that version does not exist in the repo - it starts at v1.24.6 
Happy the share the detailed steps I have done 

Events:
  Type     Reason     Age                    From               Message
  ----     ------     ----                   ----               -------
  Normal   Scheduled  28m                    default-scheduler  Succetssfully assigned kube-system/openstack-cloud-controller-manager-n2jvt to kubernetes-cluster-01-i5rcyua7ia24-master-0
  Warning  Failed     27m (x6 over 28m)      kubelet            Error: ImagePullBackOff
  Normal   Pulling    26m (x4 over 28m)      kubelet            Pulling image "registry.k8s.io/provider-os/openstack-cloud-controller-manager:v1.23.1"
  Warning  Failed     26m (x4 over 28m)      kubelet            Failed to pull image "registry.k8s.io/provider-os/openstack-cloud-controller-manager:v1.23.1": rpc error: code = Unknown desc = Error response from daemon: manifest for registry.k8s.io/provider-os/openstack-cloud-controller-manager:v1.23.1 not found: manifest unknown: Failed to fetch "v1.23.1"
  Warning  Failed     26m (x4 over 28m)      kubelet            Error: ErrImagePull
  Normal   BackOff    3m32s (x109 over 28m)  kubelet            Back-off pulling image "registry.k8s.io/provider-os/openstack-cloud-controller-manager:v1.23.1"

---

### Post by merten2000 on 2024-07-31
issue with image versions resolved:
[https://ubuntuforums.org/showthread.php?t=2499537](https://ubuntuforums.org/showthread.php?t=2499537)

---

