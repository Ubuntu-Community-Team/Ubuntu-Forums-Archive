---
title: "LXC/LXD containers questions"
date: 2018-10-24
forum: Server Platforms
---

### Post by patrickman2 on 2018-10-24
Hi Guys.

Im currently running Ubuntu 18.04 server and have lxc/lxd installed.

I want to install a minimal version of the Centos 7 container? How do I go about doing it?

My worry is if I just run the following:

lxc launch images:centos/7 

It will not install the minimal version of centos I want?

---

### Post by patrickman2 on 2018-10-24
I went ahead and tried this:

lxc launch images:centos/7/default/amd64 lxc-centos-test

seems okay but I run into issues when a try to untar an application in the container:

"Cannot mknod: Operation not permitted"

I know the tar file is fine as it has no issues untar in a standard centos 7 installation, so it appear it's only happening on a LXC/LXD environment.

Im the root user on centos 7

Im just bewildered what's causing this

---

### Post by Dragonbite on 2018-10-26
Could it be different filesystems between the two systems (one successful, LXD version failing)?

---

