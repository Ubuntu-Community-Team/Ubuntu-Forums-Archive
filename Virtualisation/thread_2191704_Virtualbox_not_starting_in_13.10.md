---
title: "Virtualbox not starting in 13.10"
date: 2013-12-04
forum: Virtualisation
---

### Post by pshah.mumbai on 2013-12-04
Hi,

I am unable to start virtualbox since it gives me this error :

> 
Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.


I tried running the following

sudo /etc/init.d/vboxdrv setup
sudo: /etc/init.d/vboxdrv: command not found

I tried even reinstall virtualbox and dkms packages but still the same error.

---

### Post by QIII on 2013-12-04
Hello!

How did you initially install VBox?

---

