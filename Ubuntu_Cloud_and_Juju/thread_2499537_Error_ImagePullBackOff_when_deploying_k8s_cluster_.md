---
title: "Error: ImagePullBackOff when deploying k8s cluster in sunbeam"
date: 2024-07-30
forum: Ubuntu Cloud and Juju
---

### Post by merten2000 on 2024-07-30
Followed steps from this blog:
[https://ubuntu.com/blog/openstack-with-sunbeam-for-small-scale-private-cloud-infrastructure](https://ubuntu.com/blog/openstack-with-sunbeam-for-small-scale-private-cloud-infrastructure)

Openstack is installed and the k8s cluster is created (status completed and healthy)
However when inspecting the newly created cluster there is a few pods in error, as it is pulling a non-existing image version from the registry.k8s.io (pulling image 1.23 where the first version in the repo is 1.24 due to the migration from docker.io)

As I have no clue(yet) on where the image URL + version are set for the failing PODs any support in fixing this is greatly appreciated :) either a quick fix or permanently 

(see config + errors below)


NAMESPACE     NAME                                         READY   STATUS             RESTARTS   AGE
kube-system   coredns-56448757b9-ltx5d                     1/1     Running            0          127m
kube-system   coredns-56448757b9-rkd8w                     1/1     Running            0          127m
kube-system   dashboard-metrics-scraper-67f57ff746-8hxbk   0/1     Pending            0          126m
kube-system   k8s-keystone-auth-mcrms                      0/1     ImagePullBackOff   0          126m
kube-system   kube-dns-autoscaler-6d5b5dc777-whgzn         0/1     Pending            0          127m
kube-system   kube-flannel-ds-5z9mg                        1/1     Running            0          126m
kube-system   kube-flannel-ds-jcwn9                        1/1     Running            0          121m
kube-system   kubernetes-dashboard-7b88d986b4-vnvj7        0/1     Pending            0          126m
kube-system   magnum-metrics-server-6c4c77844b-kcf77       0/1     Pending            0          126m
kube-system   openstack-cloud-controller-manager-8rskf     0/1     ImagePullBackOff   0          69m

Specific events for the faliing POD:
Events:
  Type     Reason     Age                    From               Message
  ----     ------     ----                   ----               -------
  Normal   Scheduled  28m                    default-scheduler  Successfully assigned kube-system/openstack-cloud-controller-manager-n2jvt to kubernetes-cluster-01-i5rcyua7ia24-master-0
  Warning  Failed     27m (x6 over 28m)      kubelet            Error: ImagePullBackOff
  Normal   Pulling    26m (x4 over 28m)      kubelet            Pulling image "registry.k8s.io/provider-os/openstack-cloud-controller-manager:v1.23.1"
  Warning  Failed     26m (x4 over 28m)      kubelet            Failed to pull image "registry.k8s.io/provider-os/openstack-cloud-controller-manager:v1.23.1": rpc error: code = Unknown desc = Error response from daemon: manifest for registry.k8s.io/provider-os/openstack-cloud-controller-manager:v1.23.1 not found: manifest unknown: Failed to fetch "v1.23.1"
  Warning  Failed     26m (x4 over 28m)      kubelet            Error: ErrImagePull
  Normal   BackOff    3m32s (x109 over 28m)  kubelet            Back-off pulling image "registry.k8s.io/provider-os/openstack-cloud-controller-manager:v1.23.1"


UPDATE
seems to  be possible to set a specific version in the "labels" section - once tried I will put an update

k8s_keystone_auth_tagThis label allows users to override the default k8s-keystone-auth container image tag. Refer to [k8s-keystone-auth page for available tags]("https://hub.docker.com/r/k8scloudprovider/k8s-keystone-auth/tags"). Stein default: v1.13.0 Train default: v1.14.0 Ussuri default: v1.18.0
cloud_provider_tagThis label allows users to override the default openstack-cloud-controller-manager container image tag. Refer to [openstack-cloud-controller-manager page for available tags]("https://hub.docker.com/r/k8scloudprovider/openstack-cloud-controller-manager/tags"). Stein default: v0.2.0 Train default: v1.15.0 Ussuri default: v1.18.

---

### Post by merten2000 on 2024-07-31
[h=3]Supported labels[/h][COLOR=#333333][FONT=-apple-system]The tested labels for each release is as follow[/FONT][/COLOR]

[LIST]
[*]Caracal
kube_tag=v1.27.8-rancher2,container_runtime=containerd,containerd_version=1.6.28,containerd_tarball_sha256=f70736e52d61e5ad225f4fd21643b5ca1220013ab8b6c380434caeefb572da9b,cloud_provider_tag=v1.27.3,cinder_csi_plugin_tag=v1.27.3,k8s_keystone_auth_tag=v1.27.3,magnum_auto_healer_tag=v1.27.3,octavia_ingress_controller_tag=v1.27.3,calico_tag=v3.26.4

[*]Bobcat
kube_tag=v1.25.9-rancher1,flannel_tag=v0.21.5,master_lb_floating_ip_enabled=true,cinder_csi_enabled=true,ingress_controller=octavia,container_runtime=containerd,containerd_version=1.6.20,containerd_tarball_sha256=1d86b534c7bba51b78a7eeb1b67dd2ac6c0edeb01c034cc5f590d5ccd824b416,cloud_provider_tag=v1.25.5,cinder_csi_plugin_tag=v1.25.5,k8s_keystone_auth_tag=v1.25.5,octavia_ingress_controller_tag=v1.25.5,coredns_tag=1.10.1,csi_snapshotter_tag=v6.2.1,csi_attacher_tag=v4.2.0,csi_resizer_tag=v1.7.0,csi_provisioner_tag=v3.4.1,csi_node_driver_registrar_tag=v2.8.0
kube_tag=v1.26.8-rancher1,flannel_tag=v0.21.5,master_lb_floating_ip_enabled=true,cinder_csi_enabled=true,ingress_controller=octavia,container_runtime=containerd,containerd_version=1.6.20,containerd_tarball_sha256=1d86b534c7bba51b78a7eeb1b67dd2ac6c0edeb01c034cc5f590d5ccd824b416,cloud_provider_tag=v1.26.3,cinder_csi_plugin_tag=v1.26.3,k8s_keystone_auth_tag=v1.26.3,octavia_ingress_controller_tag=v1.26.3,coredns_tag=1.10.1,csi_snapshotter_tag=v6.2.1,csi_attacher_tag=v4.2.0,csi_resizer_tag=v1.7.0,csi_provisioner_tag=v3.4.1,csi_node_driver_registrar_tag=v2.8.0

[*]Antelope
kube_tag=v1.23.8-rancher1,flannel_tag=v0.18.1,master_lb_floating_ip_enabled=true,cinder_csi_enabled=true,ingress_controller=octavia,container_runtime=containerd,containerd_version=1.6.6,containerd_tarball_sha256=a64568c8ce792dd73859ce5f336d5485fcbceab15dc3e06d5d1bc1c3353fa20f,cloud_provider_tag=v1.23.4,cinder_csi_plugin_tag=v1.23.4,k8s_keystone_auth_tag=v1.23.4,magnum_auto_healer_tag=v1.23.4,octavia_ingress_controller_tag=v1.23.4,autoscaler_tag=v1.23.0,coredns_tag=1.9.3,csi_snapshotter_tag=v4.2.1,csi_attacher_tag=v3.3.0,csi_resizer_tag=v1.3.0,csi_provisioner_tag=v3.0.0,csi_node_driver_registrar_tag=v2.4.0
[/LIST]

---

### Post by merten2000 on 2024-07-31
fixed when using the proper labels + tags:

mertenvgastel@test-sunbeam-02:~$ kubectl --kubeconfig=config get pods -A
cat: /var/snap/microk8s/6829/args/kubectl: Permission denied
NAMESPACE     NAME                                         READY   STATUS    RESTARTS   AGE
default       nginx-77b4fdf86c-8ckr7                       1/1     Running   0          20s
default       nginx-77b4fdf86c-k4447                       1/1     Running   0          20s
default       nginx-77b4fdf86c-t8xvm                       1/1     Running   0          20s
kube-system   coredns-5ff97bd88-8j4zm                      1/1     Running   0          8m7s
kube-system   coredns-5ff97bd88-98pd4                      1/1     Running   0          8m7s
kube-system   dashboard-metrics-scraper-5b9cf67c69-btdf9   1/1     Running   0          7m59s
kube-system   k8s-keystone-auth-r6slv                      1/1     Running   0          7m56s
kube-system   kube-dns-autoscaler-6c8ccf9bb4-jpdc8         1/1     Running   0          8m6s
kube-system   kube-flannel-ds-b8kq9                        1/1     Running   0          8m3s
kube-system   kube-flannel-ds-p8rh9                        1/1     Running   0          3m16s
kube-system   kubernetes-dashboard-dd5c86b8f-kltc7         1/1     Running   0          8m
kube-system   magnum-metrics-server-8457b5867c-hm7gg       1/1     Running   0          7m36s
kube-system   npd-7cl97                                    1/1     Running   0          3m1s
kube-system   openstack-cloud-controller-manager-bvldr     1/1     Running   0          8m8s

---

