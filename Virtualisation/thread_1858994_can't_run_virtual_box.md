---
title: "can't run virtual box"
date: 2011-10-13
forum: Virtualisation
---

### Post by cmcanulty on 2011-10-13
Launchpad had me fix my sources file and now I can't run virtual box I tried the fixes here
[https://forums.virtualbox.org/viewtopic.php?f=7&t=41228](https://forums.virtualbox.org/viewtopic.php?f=7&t=41228)
but I still get
```
Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.
```
I am afraid I have messed up grub by trying to fix this. I do have dkms installed but it seems like virtualbox doesn't see it.

---

### Post by CharlesA on 2011-10-13
VirtualBox won't mess with grub.

How did you install Virtualbox?

---

