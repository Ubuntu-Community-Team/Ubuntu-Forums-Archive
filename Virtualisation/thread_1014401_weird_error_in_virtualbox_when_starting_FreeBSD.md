---
title: "weird error in virtualbox when starting FreeBSD"
date: 2008-12-17
forum: Virtualisation
---

### Post by jimi_hendrix on 2008-12-17
i get error:

 p, li { white-space: pre-wrap; }     Virtual machine [COLOR=#0000CC]'FreeBSD'[/COLOR] has terminated unexpectedly during startup.
 
    Result Code: 
  [FONT= ]NS_ERROR_FAILURE (0x80004005)[/FONT]
   Component: 
  Machine
   Interface: 
  IMachine {1e509de4-d96c-4f44-8b94-860194f710ac}

and:

 p, li { white-space: pre-wrap; }  VERR_VM_DRIVER_NOT_INSTALLED (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

[COLOR=#0000FF]'/etc/init.d/vboxdrv setup'[/COLOR]

as root. Users of Ubuntu or Fedora should install the DKMS package at first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary

but i DO have DKMS installed...so whats up?

---

### Post by Mr-Biscuit on 2009-03-14
First things first. Best to download a preconfigured image of freebsd for virtualbox.
Second thing. Use qemu for freebsd virtualization or xen.


Do as it said. Build and load the driver.

---

