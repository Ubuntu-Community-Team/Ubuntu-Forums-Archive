---
title: "VirtualBox OSE -1908 (VERR_VM_DRIVER_NOT_INSTALLED)."
date: 2009-10-26
forum: Virtualisation
---

### Post by pricetech on 2009-10-26
First let me say that I don't want to change to the non free version from Sun.

My kernel was updated recently, within the last week as I recall.  Currently I am running 2.6.24-25-generic.  The latest Virtualbox-ose-modules listed in Synaptic is 2.6.24-24.

When I try to start a virtual machine I get:

```
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
```


I have DKMS installed.  When I run:

```
sudo /etc/init.d/vboxdrv setup
```
I get the response:

```
 * Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
```

The same thing happens if I substitute "virtualbox-ose" in the command and there are no other commands related to VirtualBox there.

All of the solutions I have found in the forums either don't work for me (as above) or refer to the non-free version from Sun.

Edit / Update:  Switching back to the 2.6.24-24 kernel IS a workaround.  However I'd rather have a solution that lets me stay with the latest kernel.

Any ideas ??

---

### Post by pricetech on 2009-11-02
Bump ??

---

### Post by pricetech on 2009-11-24
Solved when virtualbox-ose module for linux-image-2.6.24-25-generic was installed as part of a routine update.  I have switched back to the new kernel and everything is working just fine.

---

