---
title: "Kernel package"
date: 2005-05-02
forum: The Cafe
---

### Post by nobfu on 2005-05-02
Hi,

seems I have choosen the wrong distro. Xcuse me.

I need to build the Cisco VPN client. This is a kernel module and a userland utility. Hrmmm, ... there is nothing than an empty RPM !!!!!  8o|  tree in  /usr/src. The system is a 2.6.10-5-386. If I run synaptic there are only 2.4 kernels there.

I use the repository [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) with the sections universe main restricted multiverse.

Thanks for any hint

---

### Post by jdong on 2005-05-02
Patience :)


If you need to build a module against your current kernel, you can just install the appropriate linux-headers package.


Otherwise, grab the linux-source-2.6.10 package to fully rebuild a kernel. This package will make a linux-source.tar.bz2 file in /usr/src, which you then have to extract with tar xvjf

---

