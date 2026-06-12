---
title: "Virtualbox Help"
date: 2008-08-27
forum: Virtualisation
---

### Post by Landscapeman on 2008-08-27
I keep getting this message on both of my computers(Kubuntu & Ubuntu) I have installed several packages for the kernels and yet nothing works. Any Ideas? Thanks


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by Jose Catre-Vandis on 2008-08-27
You need to do as suggested and install the virtualbox-ose-modules-generic found in synaptic and /or the ones for your version of the kernel. plus make sure you have added yourself to the vboxusers group. if all else fails, uninstall and go for the Sun binaries found via [www.virtualbox.org](www.virtualbox.org)

---

