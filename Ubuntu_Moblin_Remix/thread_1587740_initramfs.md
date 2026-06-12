---
title: "initramfs"
date: 2010-10-04
forum: Ubuntu Moblin Remix
---

### Post by anjanesh on 2010-10-04
I recently got a [Dell Inspiron Mini 1010]("http://www.dell.com/us/en/home/notebooks/laptop-inspiron-10/pd.aspx?refid=laptop-inspiron-10&s=dhs&cs=19&%7Eoid=us%7Een%7E29%7Elinux_4%7E%7E") with Moblin Remix pre-installed.
I did a sudo apt-get update and then a sudo apt-get upgrade and after a 400MB upgrade & a reboot I got this after grub loaded :

```
udevadm trigger is not permitted while udev is unconfigured
udevadm settle is not permitted while udev is unconfigured
svgalib: Cannot open /dev/mem.
Gave up waiting for root device. Common Problems:
- Boot args (cat /proc/cmdline)
 - Check rootdelay= (did the system wait long enough?)
 - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/8385aead-85ae-48cc-8920-a3b2ed362115 does not exist. Dropping to shell!

BusyBox v1.33.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in-commands

(initramfs)
```

---

### Post by viralmeme on 2010-10-04
> **anjanesh said:**
> I did a sudo apt-get update and then a sudo apt-get upgrade and after a 400MB upgrade & a reboot I got this after grub loaded

[Re: udevadm trigger is not permitted while udev is unconfigured]("http://ubuntuforums.org/showthread.php?t=1285172")

---

### Post by DSK on 2011-01-27
Fixed my problem by booting to "System Rescue CD" then running a check with gparted on the drive.

[http://sourceforge.net/projects/systemrescuecd/files/sysresccd-x86/2.0.0/systemrescuecd-x86-2.0.0.iso/download](http://sourceforge.net/projects/systemrescuecd/files/sysresccd-x86/2.0.0/systemrescuecd-x86-2.0.0.iso/download)

Gparted fixed a bunch of "orphaned inodes" then everything booted fine again.

---

