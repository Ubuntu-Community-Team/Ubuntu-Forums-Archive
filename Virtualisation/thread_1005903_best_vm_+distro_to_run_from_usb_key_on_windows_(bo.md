---
title: "best vm +distro to run from usb key on windows (bootable as well"
date: 2008-12-08
forum: Virtualisation
---

### Post by teddmeister2 on 2008-12-08
What is the best distro + vm software to use on a pen drive such that linux will run relatively smoothly from a virtual machine on a middle aged (not extremely old but old nonetheless) windows computer?... Also, does anyone know where I can find a howto for installing this (whichever distro+vm that you choose)?  I've been searching around, and I figure out what would work the best.

Thanks so much.

---

### Post by M4rotku on 2008-12-08
For a distro I would advise to use Puppy linux.  I have fit the minumum installation on a 265 mb drive and a version with java and firefox on a 512 mb.

However, I don't think you will be able to get any virtualization software to fit on a flashdrive.  Maybe if you got one of the new 16 Gb flash drives, then you could fit a small distro of linux, and then run VirtualBox with a windows installation (I'm assuming that's what u want).  However, you would need a decent amount of ram to run both the lightweight linux system and the virtual system.  I would advise at least 512 mb at the very minimum.

---

### Post by aurelieng on 2008-12-09
An alternative could be to install a minimal ubuntu with debootstrap (see for instance [http://howtoforge.com/minimal-ubuntu-8.04-server-install](http://howtoforge.com/minimal-ubuntu-8.04-server-install) ) on an ext3 partition of your key, then use qemu (stored on the first FAT32 partition of the key) to virtualize it.

---

