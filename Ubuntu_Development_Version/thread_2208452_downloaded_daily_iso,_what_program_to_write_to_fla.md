---
title: "downloaded daily iso, what program to write to flash drive?"
date: 2014-02-28
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2014-02-28
what will work in 14.04?

---

### Post by sdowney717 on 2014-02-28
startup disk creator errors.
does not work

In fact it never works for me, There is some other program that works.I used it but dont recall the name.

ahh it is 
sudo apt-get install unetbootin

---

### Post by grahammechanical on 2014-02-28
I have a SanDisk Cruzer Edge that came pre-installed with a Windows backup utility. I had to format it with a Microsoft format - FAT (32 bit version); partition type = W95 FAT 32 (LBA). I formatted it in Ubuntu.

I have used Startup Disk Creator to put Edubuntu on it with persistence.

Regards

---

### Post by sdowney717 on 2014-02-28
unetbootin finished  with no error and booted flash drive ok.

---

### Post by mc4man on 2014-02-28
In general Sdc always seems to have some issue during dev & sometimes beyond
Right now it works here as long as the flash drive does not need formating 
(as in format to fat32 first in Disks or gparted if anything is on the drive

---

### Post by QDR06VV9 on 2014-02-28
> **sdowney717 said:**
> unetbootin finished  with no error and booted flash drive ok. +1 unetbootin ALWAYS works for me also. It just always works for me. :) As mc4man mentioned sometimes during the Develoment cycles somethings might not be there as needed to get er done.

---

