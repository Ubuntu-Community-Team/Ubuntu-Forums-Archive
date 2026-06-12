---
title: "grub dualboot is broken after bios update"
date: 2022-09-10
forum: Ubuntu/Debian BASED
---

### Post by kiyohimewah on 2022-09-10
i have a windows 10 and ubuntu 22.04 dual boot system. on both systems ive been having (power-related?) issues. when under heavy load from both cpu and gpu monitor, os, and keyboard completely freeze and fans ramp up as soon as it happens) so i updated bios as a last resort before buying a new psu (z370p d3 F12>F15 version, non-reversable) after bios update grub bootloader shows command line and linux is completely gone from my bios boot loader and efibootmgr, i tried using ls to fix the grub boot loader but i think the grub folder got removed, it's nowhere to be found. boot-repair gives me nv-ram locked error, someone else fixed it by resetting CMOS, i tried and it didn't fix it. I don't have any backups, ive been looking for a fix on the internet for a few days and nothing seems to work when I try

---

### Post by yancek on 2022-09-10
To get more detailed information for members here to help, post the output of sudo efibootmgr and also of boot repair link after selecting the Create BootInfo Summary option.

---

### Post by kiyohimewah on 2022-09-10
sudo efibootmgr :
BootCurrent: 0007
Timeout: 1 seconds
BootOrder: 0000,0002,0005,0006,0007
Boot0000* Windows Boot Manager
Boot0002* UEFI OS
Boot0005* Windows Boot Manager
Boot0006* UEFI: KingstonDataTraveler 3.01100
Boot0007* UEFI: KingstonDataTraveler 3.01100, Partition 1

bootinfo summary : [http://*******.us/yMA2bp](http://*******.us/yMA2bp)

---

### Post by yancek on 2022-09-10
The boot repair link is broken, repost it please.

---

### Post by kiyohimewah on 2022-09-10
hopefully this works? [https://pastebin.com/twBTuALw](https://pastebin.com/twBTuALw)

---

### Post by tea for one on 2022-09-10
> **kiyohimewah said:**
> hopefully this works? [https://pastebin.com/twBTuALw](https://pastebin.com/twBTuALw)
I cannot see the boot-repair report via this link.
The only thing visible is another link to an insecure site (i.e.http rather than https)

Any reason to avoid [https://paste.ubuntu.com?](https://paste.ubuntu.com?)

---

### Post by kiyohimewah on 2022-09-10
that was the original link provided by boot-repair, but here [https://paste.ubuntu.com/p/qzkj975RNh/](https://paste.ubuntu.com/p/qzkj975RNh/) i copied it

---

### Post by tea for one on 2022-09-10
> **kiyohimewah said:**
> I don't have any backups, 
Line 76 - Live-session OS is Pop 64-bit (Pop!_OS 22.04 LTS, jammy, x86_64)
As you have booted into a live session, backup your personal data before you do anything else.

---

### Post by kiyohimewah on 2022-09-10
mhm i backed up my files

---

### Post by tea for one on 2022-09-10
Now that you have backups and a new power supply, run a live session for a few hours to see if your power-related issues are resolved.
As there are no boot files in your EFI System Partitions (nvme0n1p1 and nvme0n1p5), I imagine that you cannot even boot into Windows via the one-time boot menu?

---

### Post by howefield on 2022-09-10
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

