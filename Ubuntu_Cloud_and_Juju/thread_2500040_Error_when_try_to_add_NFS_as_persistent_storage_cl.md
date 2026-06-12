---
title: "Error when try to add NFS as persistent storage class for charmed kubernetes"
date: 2024-08-20
forum: Ubuntu Cloud and Juju
---

### Post by dimitrion4a on 2024-08-20
I'm trying to add NFS server as persistent storage class for a charmed kubernetes cluster. I deployed NFS provisioner with helm using:


helm install -n nfs-provisioning --create-namespace nfs-subdir-external-provisioner nfs-subdir-external-provisioner/nfs-subdir-external-provisioner --set nfs.server=192.168.0.112 --set nfs.path=/data/kubedata

I inspected status of deployment but I notice that the NFS folder is not mounting - missing nfs helper program:

kubectl -n nfs-provisioning describe pods
Name:             nfs-subdir-external-provisioner-58bf6cf97f-8zw59
Namespace:        nfs-provisioning
Priority:         0
Service Account:  nfs-subdir-external-provisioner
Node:             juju-dd5591-8/10.240.211.105
Start Time:       Tue, 20 Aug 2024 10:34:57 +0300
Labels:           app=nfs-subdir-external-provisioner
                  pod-template-hash=58bf6cf97f
                  release=nfs-subdir-external-provisioner
Annotations:      <none>
Status:           Pending
IP:               
IPs:              <none>
Controlled By:    ReplicaSet/nfs-subdir-external-provisioner-58bf6cf97f
Containers:
  nfs-subdir-external-provisioner:
    Container ID:   
    Image:          registry.k8s.io/sig-storage/nfs-subdir-external-provisioner:v4.0.2
    Image ID:       
    Port:           <none>
    Host Port:      <none>
    State:          Waiting
      Reason:       ContainerCreating
    Ready:          False
    Restart Count:  0
    Environment:
      PROVISIONER_NAME:  cluster.local/nfs-subdir-external-provisioner
      NFS_SERVER:        192.168.0.112
      NFS_PATH:          /data/kubedata
    Mounts:
      /persistentvolumes from nfs-subdir-external-provisioner-root (rw)
      /var/run/secrets/kubernetes.io/serviceaccount from kube-api-access-sfbbr (ro)
Conditions:
  Type                        Status
  PodReadyToStartContainers   False 
  Initialized                 True 
  Ready                       False 
  ContainersReady             False 
  PodScheduled                True 
Volumes:
  nfs-subdir-external-provisioner-root:
    Type:      NFS (an NFS mount that lasts the lifetime of a pod)
    Server:    192.168.0.112
    Path:      /data/kubedata
    ReadOnly:  false
  kube-api-access-sfbbr:
    Type:                    Projected (a volume that contains injected data from multiple sources)
    TokenExpirationSeconds:  3607
    ConfigMapName:           kube-root-ca.crt
    ConfigMapOptional:       <nil>
    DownwardAPI:             true
QoS Class:                   BestEffort
Node-Selectors:              <none>
Tolerations:                 node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                             node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
Events:
  Type     Reason       Age                  From     Message
  ----     ------       ----                 ----     -------
  Warning  FailedMount  90s (x85 over 158m)  kubelet  MountVolume.SetUp failed for volume "nfs-subdir-external-provisioner-root" : mount failed: exit status 32
Mounting command: mount
Mounting arguments: -t nfs 192.168.0.112:/data/kubedata /var/lib/kubelet/pods/e6f2d9a2-c9ac-4b1a-a872-b1aa2e251efe/volumes/kubernetes.io~nfs/nfs-subdir-external-provisioner-root
Output: mount: /var/lib/kubelet/pods/e6f2d9a2-c9ac-4b1a-a872-b1aa2e251efe/volumes/kubernetes.io~nfs/nfs-subdir-external-provisioner-root: bad option; for several filesystems (e.g. nfs, cifs) you might need a /sbin/mount.<type> helper program.



The nfs-common package is not installed on  juju-dd5591-8 (kubernetes-worker/1) vm.

Ane ideea how to solve?

Thank you.

---

