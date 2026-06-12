---
title: "Gparted fails to load"
date: 2012-02-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by dino99 on 2012-02-05
Its the first time i try to use gparted since we got 0.11 version on Precise i386. Loading it from the menu (gnome-classic) fails with this error:

- the first time, a greyed parted dialogbox start to scan to find hdds (have 2 pata + 1 sata) but found nothing, then get the error.
- the next times i even does not get the dialogbox, it silently exit and give again:

error: libhal_acquire_global_interface_lock: org.freedesktop.Hal.Device.InterfaceAlreadyLocked: The interface org.freedesktop.Hal.Device.Storage is already exclusively locked either by someone else or it's already locked by yourself

then lot of messages like:

libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sdc7 is a logical partition but no extended partition exists


Of course there is other process that could lock it, except that libgdu is also used by other apps.

Are you getting such issue on your system ?

---

### Post by cap10devnull on 2012-02-05
today I used gparted to shrink my partition, no problem 
I downloaded the daily build AMD64 yesterday

---

### Post by BC59 on 2012-02-05
> **dino99 said:**
> Its the first time i try to use gparted since we got 0.11 version on Precise i386. Loading it from the menu (gnome-classic) fails with this error:

- the first time, a greyed parted dialogbox start to scan to find hdds (have 2 pata + 1 sata) but found nothing, then get the error.
- the next times i even does not get the dialogbox, it silently exit and give again:

error: libhal_acquire_global_interface_lock: org.freedesktop.Hal.Device.InterfaceAlreadyLocked: The interface org.freedesktop.Hal.Device.Storage is already exclusively locked either by someone else or it's already locked by yourself

then lot of messages like:

libgdu-WARNING **: Partition /org/freedesktop/UDisks/devices/sdc7 is a logical partition but no extended partition exists


Of course there is other process that could lock it, except that libgdu is also used by other apps.

Are you getting such issue on your system ?

Well, no. I burned a CD with version 11 a week ago and I use it without problem.

---

### Post by dino99 on 2012-02-05
hm strange, previous gparted was not complaining at all if it was ran from the active running OS (hard install, not from cd)

Googling around it easy to find recent similar issue, like:
[http://www.mombu.com/gnu_linux/mandriva/t-gparted-on-20100-powerpack-32-bit-3777003.html](http://www.mombu.com/gnu_linux/mandriva/t-gparted-on-20100-powerpack-32-bit-3777003.html)

---

### Post by keithpeter on 2012-02-05
Hello dino99 and all

12.04 64bit installed on hard drive from 28th Jan daily then updated daily. 

Gparted installed today, seems to work fine, wiped a 4Gb stick and added a Fat32 partition no errors.

Checked by logging into Gnome Classic, works fine from there as well.

---

### Post by dino99 on 2012-02-05
Finally found the reason: the floppy ghost was activated into the silly bios, damn :( That bios propose to boot on something not existing in that box.

Effectively now gparted works, but its stupid too: it should not fail to detect the real hardware, it's his first job :(

---

### Post by larrypg on 2012-02-05
Hello,

Well this conversation made me check gparted and found it was not installed.  I do not remember having to install it in the past. Maybe because it is a VirtualBox install?

---

### Post by cariboo on 2012-02-05
Gparted isn't installed by default, it is on the Live CD though.

---

