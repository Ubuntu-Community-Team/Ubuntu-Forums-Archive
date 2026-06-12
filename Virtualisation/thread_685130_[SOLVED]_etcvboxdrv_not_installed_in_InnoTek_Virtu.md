---
title: "[SOLVED] /etc/vboxdrv not installed in InnoTek VirtualBox 1.5.0"
date: 2008-02-01
forum: Virtualisation
---

### Post by yaknowwat on 2008-02-01
Everything was working fine until an update now InnoTek Virtual box does not install its file to '/etc/vboxdrv' thus causing this error even after a reinstall and removal.


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by yaknowwat on 2008-02-01
Solved after installing 1.5.2 deb package (one in the repo's is 1.5.0)

---

