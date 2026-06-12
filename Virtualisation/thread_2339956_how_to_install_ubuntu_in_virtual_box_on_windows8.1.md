---
title: "how to install ubuntu in virtual box on windows8.1 system with uefi boot"
date: 2016-10-14
forum: Virtualisation
---

### Post by vignoble on 2016-10-14
my desktop PC only boots throug uefi in windows 8.1, no matter wat configuration in BIOS. I have a bootable disk with ubuntu 14.04.3 and an image downloaded of ubuntu 16.04.1 . I also installed virtual box but windows does not recognise the virtual drive. is there a possibillity to install ubuntu any other way on the virtual drive?

---

### Post by ajgreeny on 2016-10-14
The easiest way to install Ubuntu is to make a new VM, give it the name and description you want and create a vdi virtual disk.
I always give mine up to half of my physycal RAM, 20GB, and of a fixed size, not dynamic, but that is your choice.

Once you have created the new virtual disk click on Start and in the dialogue that appears click on the little icon to the right of the drop-down box, navigate to the ubuntu-16.04.1.iso file you have for Ubuntu on your hard disk and run it as a normal live OS from which you can install in the usual way, just choosing the default of "Use whole disk" which will, of course, be the 20GB virtual disk you just created, not your hard disk.  You can ignore the UEFI/BIOS problem installing this way as it is of no concern in a VM.

It will install very quickly and tell you to reboot.

Job done!

---

