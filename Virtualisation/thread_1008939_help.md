---
title: "help"
date: 2008-12-12
forum: Virtualisation
---

### Post by Hari sankar on 2008-12-12
i get the following error message when i try to create a virtual machine


tell me what to do ..



VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by Peter09 on 2008-12-12
Go to 

System->Admin->Synaptic Package Manager

Search for the Virtual-box-ose package for your kernel, tick the box and apply. This will install the modules that you need.

---

