---
title: "Issues with installing Kubernetes"
date: 2017-11-20
forum: Server Platforms
---

### Post by espressobeanmachine on 2017-11-20
So I have Ubuntu Server LTS version and I am using this tutorial to install Kubernetes on Ubuntu:

[https://tutorials.ubuntu.com/tutorial/install-kubernetes-with-conjure-up?backURL=%2F#0](https://tutorials.ubuntu.com/tutorial/install-kubernetes-with-conjure-up?backURL=%2F#0)

But I am running into issues, here are the commands and responses I obtain:

```

coffee@serverone:~$ sudo snap install conjure-up --classicsnap "conjure-up" is already installed, see "snap refresh --help"
coffee@serverone:~$ sudo conjure-up
usage: conjure-up [-h] [-d] [-s] [--version] spell
conjure-up: error: the following arguments are required: spell
coffee@serverone:~$ conjure-up kubernetes
Reading package lists...
Building dependency tree...
Reading state information...
E: Unable to locate package kubernetes


```

What am I missing/doing wrong?

---

### Post by #&amp;thj^% on 2017-11-20
If my memory serves me right.. after installing "sudo snap install conjure-up --classic"
```
**# re-login may be required at that point if you just installed snap utility**
conjure-up kubernetes
```

---

### Post by espressobeanmachine on 2017-11-20
> **1fallen said:**
> If my memory serves me right..
# re-login may be required at that point if you just installed snap utility
conjure-up kubernetes
Already did that but still same message, cannot locate package.

---

### Post by #&amp;thj^% on 2017-11-20
Did you ever see a list of recommended spells.
With:
```
conjure-up
```

---

### Post by howefield on 2017-11-20
Try..

```
conjure-up
```

on its own, no sudo and no kubernetes...

---

### Post by deadflowr on 2017-11-20
Right on.
No such package itself as kubernetes.
Following the guide simply run the conjure-up command and scroll down to *The Canonical distribution of Kubernetes* and press enter.

The kubernetes that's listed is the sub-category, like the bigdata category is above it. and openstack category below it.

---

### Post by espressobeanmachine on 2017-11-20
I tried it but here is the result:

```

coffee@serverone:~$ conjure-up
usage: conjure-up [-h] [-d] [-s] [--version] spell
conjure-up: error: the following arguments are required: spell

```

---

### Post by espressobeanmachine on 2017-11-21
I have no idea what the issue was. Anyways, even after rebooting the entire server the issue remained.

What I done was the following:

uninstalling snap using the purge flag along with conjure-up and then autoremoving everything. rebooting the server. install snap, reboot the server, install conjure-up, reboot the server and the problem was resolved then.

---

