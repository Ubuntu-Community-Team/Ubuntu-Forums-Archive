---
title: "Kubernetes installation problem"
date: 2019-08-19
forum: Ubuntu Cloud and Juju
---

### Post by lukemiller on 2019-08-19
[FONT=Ubuntu][SIZE=3][COLOR=#111111]I just installed [/COLOR][/SIZE][/FONT][COLOR=#111111][FONT=Ubuntu]Charmed Kubernetes using the quick start on a single systems using lxd. I have some services which are sitting in waiting status.

# juju status
Model     Controller           Cloud/Region         Version  SLA          Timestamp
k8s-test  my-cloud-controller  localhost/localhost  2.6.6    unsupported  23:05:36Z


App                    Version  Status   Scale  Charm                  Store       Rev  OS      Notes
containerd                      active       5  containerd             jujucharms   20  ubuntu
easyrsa                3.0.1    active       1  easyrsa                jujucharms  270  ubuntu
etcd                   3.2.10   active       3  etcd                   jujucharms  449  ubuntu
flannel                0.10.0   active       5  flannel                jujucharms  438  ubuntu
kubeapi-load-balancer  1.14.0   active       1  kubeapi-load-balancer  jujucharms  664  ubuntu  exposed
kubernetes-master      1.15.2   waiting      2  kubernetes-master      jujucharms  724  ubuntu
kubernetes-worker      1.15.2   active       3  kubernetes-worker      jujucharms  571  ubuntu  exposed


Unit                      Workload  Agent  Machine  Public address  Ports           Message
easyrsa/0*                active    idle   0        10.15.77.181                    Certificate Authority connected.
etcd/0                    active    idle   1        10.15.77.37     2379/tcp        Healthy with 3 known peers
etcd/1*                   active    idle   2        10.15.77.32     2379/tcp        Healthy with 3 known peers
etcd/2                    active    idle   3        10.15.77.251    2379/tcp        Healthy with 3 known peers
kubeapi-load-balancer/0*  active    idle   4        10.15.77.178    443/tcp         Loadbalancer ready.
kubernetes-master/0       waiting   idle   5        10.15.77.52     6443/tcp        Waiting for 6 kube-system pods to start
  containerd/4            active    idle            10.15.77.52                     Container runtime available.
  flannel/4               active    idle            10.15.77.52                     Flannel subnet 10.1.92.1/24
kubernetes-master/1*      waiting   idle   6        10.15.77.76     6443/tcp        Waiting for 6 kube-system pods to start
  containerd/1            active    idle            10.15.77.76                     Container runtime available.
  flannel/1               active    idle            10.15.77.76                     Flannel subnet 10.1.4.1/24
kubernetes-worker/0       active    idle   7        10.15.77.70     80/tcp,443/tcp  Kubernetes worker running.
  containerd/2            active    idle            10.15.77.70                     Container runtime available.
  flannel/2               active    idle            10.15.77.70                     Flannel subnet 10.1.35.1/24
kubernetes-worker/1*      active    idle   8        10.15.77.219    80/tcp,443/tcp  Kubernetes worker running.
  containerd/0*           active    idle            10.15.77.219                    Container runtime available.
  flannel/0*              active    idle            10.15.77.219                    Flannel subnet 10.1.69.1/24
kubernetes-worker/2       active    idle   9        10.15.77.119    80/tcp,443/tcp  Kubernetes worker running.
  containerd/3            active    idle            10.15.77.119                    Container runtime available.
  flannel/3               active    idle            10.15.77.119                    Flannel subnet 10.1.50.1/24


Machine  State    DNS           Inst id        Series  AZ  Message
0        started  10.15.77.181  juju-59942b-0  bionic      Running
1        started  10.15.77.37   juju-59942b-1  bionic      Running
2        started  10.15.77.32   juju-59942b-2  bionic      Running
3        started  10.15.77.251  juju-59942b-3  bionic      Running
4        started  10.15.77.178  juju-59942b-4  bionic      Running
5        started  10.15.77.52   juju-59942b-5  bionic      Running
6        started  10.15.77.76   juju-59942b-6  bionic      Running
7        started  10.15.77.70   juju-59942b-7  bionic      Running
8        started  10.15.77.219  juju-59942b-8  bionic      Running
9        started  10.15.77.119  juju-59942b-9  bionic      Running

I am seeing these messages in the logs:

# juju debug-log -m k8s-test -n 20

unit-kubernetes-worker-2: 23:24:33 INFO unit.kubernetes-worker/2.juju-log Failed to apply label juju-application=kubernetes-worker. Will retry.
unit-kubernetes-worker-1: 23:24:33 DEBUG unit.kubernetes-worker/1.update-status Error from server (NotFound): nodes "juju-59942b-8" not found
unit-kubernetes-worker-1: 23:24:33 INFO unit.kubernetes-worker/1.juju-log Failed to apply label juju-application=kubernetes-worker. Will retry.
unit-kubernetes-worker-0: 23:24:33 DEBUG unit.kubernetes-worker/0.update-status Error from server (NotFound): nodes "juju-59942b-7" not found
unit-kubernetes-worker-0: 23:24:33 INFO unit.kubernetes-worker/0.juju-log Failed to apply label juju-application=kubernetes-worker. Will retry.
unit-kubernetes-worker-2: 23:24:34 DEBUG unit.kubernetes-worker/2.update-status Error from server (NotFound): nodes "juju-59942b-9" not found
unit-kubernetes-worker-2: 23:24:34 INFO unit.kubernetes-worker/2.juju-log Failed to apply label juju-application=kubernetes-worker. Will retry.

Any ideas of what is going on here?
Thanks,
Luke






[/FONT][/COLOR]

---

### Post by digikin on 2020-01-19
What is your storage setup as on lxc?
I went through the entire process to find nodes sitting on a waiting status until I changed the storage pool to a dir format. 

There is an issue: 
Currently, **Charmed Kubernetes** only supports dir as a storage option and does not support ipv6, which should be set to none from the init script. Additional profiles will be added automatically to LXD to support the requirements of **Charmed Kubernetes**. [URL="https://ubuntu.com/kubernetes/docs/install-local"]https://ubuntu.com/kubernetes/docs/install-local


[/URL]

---

