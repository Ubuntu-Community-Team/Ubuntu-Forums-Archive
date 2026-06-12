---
title: "Installing vmware on ubuntu 8.10"
date: 2009-09-19
forum: Virtualisation
---

### Post by exww on 2009-09-19
Hello , first of all i have OVH server running ubuntu 8.10.
OVH uses their custom kernels in ubuntu installations: 

[ftp://ftp.ovh.net/made-in-ovh/bzImage/](ftp://ftp.ovh.net/made-in-ovh/bzImage/)

The problem is that when i try to install vmware it asks me for the location of c headers.
I cant install c headers because:

```
 :sudo apt-get install linux-headers-`uname -r` build-essential xinetd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-2.6.27.10-grsec-xxxx-grs-ipv4-64
```Also the ovh kernels dont have module support . So i guess i need to recompile the kernel to a different version with the module support but the problem is i dont know what or how to do it... If anyone can help it would be nice , thanks

---

