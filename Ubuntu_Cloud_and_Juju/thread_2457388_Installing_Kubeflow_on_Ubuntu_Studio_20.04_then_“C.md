---
title: "Installing Kubeflow on Ubuntu Studio 20.04 then “Couldn't contact api.jujucharms.com”"
date: 2021-02-01
forum: Ubuntu Cloud and Juju
---

### Post by skyemoor on 2021-02-01
I am following the install directions from both [https://microk8s.io/docs](https://microk8s.io/docs) and [https://ubuntu.com/ai/install-kubeflow](https://ubuntu.com/ai/install-kubeflow). All has been fine until;

```
microk8s enable kubeflow
```

Then the following happens;
> 
    Enabling dns...
    Enabling storage...
    Enabling dashboard...
    Enabling ingress...
    Enabling metallb:10.64.140.43-10.64.140.49...
    Waiting for DNS and storage plugins to finish setting up
    Couldn't contact api.jujucharms.com from within the Kubernetes cluster
    Please check your network connectivity before enabling Kubeflow.
    Failed to enable kubeflow

The network connection is fine and stable.I've tried rebooting and retrying.

I searched and found one recommendation to try;

```
sudo iptables -P FORWARD ACCEPT
```

That executed without issue, though did nothing to solve the problem.

Am I missing something simple?

---

