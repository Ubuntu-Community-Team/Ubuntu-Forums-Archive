---
title: "First time Virtualbox user"
date: 2009-05-21
forum: Virtualisation
---

### Post by MedianMajik on 2009-05-21
So I recently setup a virtual 2gb partition for Puppy 4.2 in Virtualbox.  I used the recommended kernel 2.6 and mounted the iso image.  When I attemped to start I got two errors.  

```
Failed to open a session for the virtual machine Puppy 4.2.
Virtual machine 'Puppy 4.2' has terminated unexpectedly during startup.
Result Code: 

Details-
NS_ERROR_FAILURE (0x80004005)
Component: 
Machine
Interface: 
IMachine {13420cbb-175a-4456-85d0-301126dfdec7}

```

**and**
```

Kernel Driver not installed (rc=-1908)
The Virtualbox Linux Kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv.  Re-setup the kernel module by executing
'/etc/init.d/vboxdrv setup'
as root.  User of Ubuntu should installed the DKMS package first.  This package keeps track of Linux kernel changes and recompiles the xboxdrv kernel module if necessary.
```

I check and I have the DKMS package installed on Ubuntu 8.10 32-bit.  I have no idea what the error is stemming from.  Any suggestions are greatly appreciated!

---

### Post by bodhi.zazen on 2009-05-21
First try running :

```
sudo /etc/init.d/vboxdrv setup
``` in a terminal and restart virtualbox.

If that fails I would assume you are runing the OSE and advise you install the PEUL.

[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

---

### Post by MedianMajik on 2009-05-21
Thanks!  Puppy is now good to go (I'm using the closed source edition of virtualbox).  If I install virtual machines on a virtual drive (1.6gb) will I have to worry about any alterations being made the the grub on my primary o/s or actual partition changes via gparted?

Thanks

---

### Post by kpkeerthi on 2009-05-22
No. Your GRUB on the host machine will not be touched.

---

