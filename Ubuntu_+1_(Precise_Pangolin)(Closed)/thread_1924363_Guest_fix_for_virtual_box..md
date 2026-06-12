---
title: "Guest fix for virtual box."
date: 2012-02-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by philinux on 2012-02-12
[http://www.webupd8.org/2012/02/virtualbox-ubuntu-1204-guest-fixes.html](http://www.webupd8.org/2012/02/virtualbox-ubuntu-1204-guest-fixes.html)

---

### Post by jerrrys on 2012-02-12
nice find, thanks

---

### Post by larrypg on 2012-02-12
Hello,

Not sure if I should ask it here or start a new thread but...I tried the suggestion on webupd8.  So I did apt-get remove virtualbox-* (which I am thinking was a mistake).  I then installed oracle's virtual box and get the following:


The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

I can install virtualbox-ose and it works but oracle 4.1.8 does not because of what was removed.

Thanks for any suggestions.

---

