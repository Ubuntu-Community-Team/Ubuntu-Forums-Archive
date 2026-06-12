---
title: "Virtual Box - can't install an OS"
date: 2008-06-29
forum: Virtualisation
---

### Post by MickSulley on 2008-06-29
Hi,
I have done a fresh install of Hardy and installed Virtual Box, but when I try to install an OS it gets to the part when it mounts the CD drive and gives an error - 

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

Any suggestions?

---

### Post by pytheas22 on 2008-06-29
This might fix it:
```

sudo /etc/init.d/vboxdrv setup
sudo /etc/init.d/vboxdrv start
```

Does it work now?

---

### Post by MickSulley on 2008-06-29
From a suggestion on another forum I removed it, downloaded from [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) and installed that one and that works fine.
Thanks anyway

---

