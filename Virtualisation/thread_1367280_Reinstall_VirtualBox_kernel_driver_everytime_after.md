---
title: "Reinstall VirtualBox kernel driver everytime after reboot"
date: 2009-12-29
forum: Virtualisation
---

### Post by 0x414141 on 2009-12-29
Hello, i  have ubunutu (2.6.31-16-generic) and virtualBox 3.1. Every time i load a Virtual Machine, i have this error:

>   p, li { white-space: pre-wrap; }  The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

[COLOR=#0000ff]'/etc/init.d/vboxdrv setup'[/COLOR]

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.
I run the command, as root and i am able to work with my VM until the next reboot. After the reboot, i have to reinstall it.

Is there a way to fix it?

---

### Post by SamD42 on 2009-12-29
Adding "vboxdrv" (without quotes) to /etc/modules should do it. I've had this problem on each machine i've installed Karmic on so far.

---

### Post by 0x414141 on 2009-12-30
Awesome!

Thank you so much!

---

