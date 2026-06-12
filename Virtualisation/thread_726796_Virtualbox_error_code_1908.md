---
title: "Virtualbox error code 1908"
date: 2008-03-17
forum: Virtualisation
---

### Post by omidomid on 2008-03-17
Hello,
I installed virtualbox, and when I try to create a windows xp virtual machine, and then run it, I get the error:
---------------------

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 --------------------

Can anyone help?

---

### Post by omidomid on 2008-03-19
Fixed it by installing the OSE version via debian. now it won't let me set my cd drive, so it doesn't show up in windows (it doesn't show up in virtualbox's dropdown menu)

---

