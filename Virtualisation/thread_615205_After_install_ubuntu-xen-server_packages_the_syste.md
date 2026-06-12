---
title: "After install ubuntu-xen-server packages the system don't boot"
date: 2007-11-16
forum: Virtualisation
---

### Post by frankabel on 2007-11-16
Hi all,

I'm using gusty server and after install ubuntu-xen-server meta package the system don't boot, I mean Dom0 don't boot well, the last message that I can see is "Setting system clock", after that, the boot process not continue. I can ping the machine, but neither sshd or other services are started.

Anybody have the same problem? Can someone report that he/she install this packages successfully? I'm testing over VMware, but expect that the error isn't related with that, because VMware emulate very well i386 hardware. 

Thanks in advance.

Salute
Frank Abel

---

### Post by Kango_V on 2007-11-19
We're having this same problem.  I'm sure it's something to do with GDM starting with an NVidia or ATI driver.  Anyone else having any luck?

---

### Post by frankabel on 2007-11-19
I already fill a bug, add your experience there so they know that I'm not crazy at all, lol

[https://bugs.launchpad.net/ubuntu/+source/xen-meta/+bug/163605](https://bugs.launchpad.net/ubuntu/+source/xen-meta/+bug/163605)

---

