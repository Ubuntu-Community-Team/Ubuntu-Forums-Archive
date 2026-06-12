---
title: "[SOLVED] error when trying to run virtual box."
date: 2008-07-18
forum: Virtualisation
---

### Post by sneeks on 2008-07-18
installed all ok and set up drive ok,but when i get to start it i get this error .
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

i re-installed both modules but to no avail.

---

### Post by scragar on 2008-07-18
The problem, is that Vbox requires moddules for the kernel, but there was recently a kernel upgrade, so now the Vbox module is behind the kernel and won't let it run. there are a few solutions, the quickest of which is to rebuild the module yourself(full guides available, step by step, I'll help if you need help), but the easiest is to just wait for the module to be updated in a few days(it's usualy around 4 - 7 days behind)

---

### Post by sneeks on 2008-07-20
thanks but i managed to get it running by d/l it from sun

---

