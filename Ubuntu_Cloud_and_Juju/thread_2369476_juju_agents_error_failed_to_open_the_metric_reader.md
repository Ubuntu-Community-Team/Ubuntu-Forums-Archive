---
title: "juju agents error: failed to open the metric reader: EOF, than: too many open files"
date: 2017-08-23
forum: Ubuntu Cloud and Juju
---

### Post by radw on 2017-08-23
I have installed Canonical Kubernetes Distribution on three nodes, one master and two workers. There is a problem on master node with juju agents, they transition to failed state after some time. First they log a lot of the following error messages:

```

2017-08-23 11:58:07 ERROR juju.worker.dependency engine.go:546 "metric-sender" manifold worker returned unexpected error: failed to open the metric reader: EOF
2017-08-23 11:58:10 ERROR juju.worker.dependency engine.go:546 "metric-sender" manifold worker returned unexpected error: failed to open the metric reader: EOF
2017-08-23 11:58:13 ERROR juju.worker.dependency engine.go:546 "metric-sender" manifold worker returned unexpected error: failed to open the metric reader: EOF
...

```

then the following errors messages are logged (example for etcd agent):

```

2017-08-23 12:23:16 ERROR juju.juju.sockets sockets_nix.go:50 failed to listen on unix:/var/lib/juju/agents/unit-etcd-0/872806956/s: listen unix /var/lib/juju/agents/unit-etcd-0/872806956/s: socket: too many open files
2017-08-23 12:23:16 ERROR juju.worker.dependency engine.go:546 "metric-sender" manifold worker returned unexpected error: listen unix /var/lib/juju/agents/unit-etcd-0/872806956/s: socket: too many open files
2017-08-23 12:23:19 ERROR juju.juju.sockets sockets_nix.go:50 failed to listen on unix:/var/lib/juju/agents/unit-etcd-0/964729755/s: listen unix /var/lib/juju/agents/unit-etcd-0/964729755/s: socket: too many open files
2017-08-23 12:23:19 ERROR juju.worker.dependency engine.go:546 "metric-sender" manifold worker returned unexpected error: listen unix /var/lib/juju/agents/unit-etcd-0/964729755/s: socket: too many open files
2017-08-23 12:23:22 ERROR juju.juju.sockets sockets_nix.go:50 failed to listen on unix:/var/lib/juju/agents/unit-etcd-0/925849150/s: listen unix /var/lib/juju/agents/unit-etcd-0/925849150/s: socket: too many open files
2017-08-23 12:23:22 ERROR juju.worker.dependency engine.go:546 "metric-sender" manifold worker returned unexpected error: listen unix /var/lib/juju/agents/unit-etcd-0/925849150/s: socket: too many open files
...

```

juju version used is 2.2.1, machines are manually provided, behind proxy. Agents on worker nodes doesn't have the problem. I have also another installation of CDK, exactly the same version on different machines, and that installation doesn't have this problem. The difference is the first environment has some custom kubernetes applications installed while the second one is almost empty. I tried to figure out what differences are between environments but couldn't notify any significant diffrence, particularly network configuration and proxy/no_proxy settings are analogous.

Maybe somebody has an idea how to resolve this ?

---

### Post by radw on 2017-08-25
After some more investigation I stopped all unit agents, removed all files from /var/lib/juju/metricspool/ directory and started agents again and the problem has gone away ! Only 4 files has been created in the directory, previously there were above 600 files. What's interesting some .meta files contained reference to old version of charm: "charmurl":"cs:~containers/kubeapi-load-balancer-11", while current version is: "charmurl":"cs:~containers/kubeapi-load-balancer-16". The kubernetes bundle was upgraded before, maybe some files with old url left in the metricspool directory and coused the erroneous behavior ?

---

