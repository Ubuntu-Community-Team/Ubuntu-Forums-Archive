---
title: "VirtualBox kernel driver problems"
date: 2008-08-12
forum: Virtualisation
---

### Post by masterbrumm on 2008-08-12
Hi i am trying to get win xp up and running through virtual box
when i am tring to execure the iso file i get this message 

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

im trying to figure out what to do here any ideas?

---

### Post by Perpetual on 2008-08-12
> **masterbrumm said:**
> Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.

Try...

```

sudo /etc/init.d/vboxdrv setup

```

---

