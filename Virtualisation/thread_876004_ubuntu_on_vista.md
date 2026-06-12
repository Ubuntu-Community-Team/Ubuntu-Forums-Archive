---
title: "ubuntu on vista"
date: 2008-07-31
forum: Virtualisation
---

### Post by crysis on 2008-07-31
is there any way to run ubuntu on top of vista (or other windows) with 2d and 3d acceleration for compiz fusion and other moderate 3d support, and better videos??

any graphics acceleration supported virtualization software out there???

i'hv heard vmware workstation 6.5 have 3d support for xp guest os. is there any improvement for linux guest os??

---

### Post by LinuxRocks713 on 2008-08-04
VMWare/Vbox/QEMU/Parallels/VPC all do not support 3D.

---

### Post by cjm5229 on 2008-08-05
Use Wubi [http://wubi-installer.org/](http://wubi-installer.org/) The Ubuntu Live CD has a Wubi installer built in. While in Windows just insert the live CD and install it. The wubi installer from the Wubi website will Download the Ubuntu ISO and install it if you don't have a Ubuntu cd. It is not a Virtual Machine it is an actual install in a folder in Windows. It uses all your actual hardware, including your Graphics card. You do have to reboot to access it just like a Dual boot, but if you don't want to keep it you can just uninstall it from Add?Remove in Windows just like any other program and you don't have to repartition your HD.

---

