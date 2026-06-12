---
title: "Dual Boot with LUKS partition"
date: 2018-09-05
forum: Ubuntu/Debian BASED
---

### Post by javes2 on 2018-09-05
Cross post from: [https://forums.puri.sm/t/support-dual-boot-on-librem13v2/](https://forums.puri.sm/t/support-dual-boot-on-librem13v2/)

Hello,

I purchased my Purism librem 13 with 500gb HDD (/sda) and a 500gb Samsung SSD (/sdb) addon.

I had PureOS installed on `sda` via normal configuration with LUKS encryption and I had not even mounted sdb until a few days ago.
To better use that space I thought to dual boot my laptop with kali linux on `sdb`

So I followed the usb installer instructions, nothing fancy - and I selected the entire `sdb` disk to host my kali OS.

Having got to the end, the installer asked me where it should install the grub payload stating the main disk was the standard, so I selected `sda` and finished installing...

Upon first boot of my machine I am immediately prompted to log in to kali, grub seems to have forsaken the `sda` PureOS LUKS partition and skips to kali `sdb` immediately.

I have attempted multiple times to enter SeaBIOS and play around with grub rescue but it simply does not recognize PureOS.
I suspect this is so because I had never used grub in the past, and upon inspection of my disks I find that disk1 (presumably sdb) has “MBR Grub2,” whereas disk2 has “MBR is FreeDOS eXtended FDisk” so even when I enter Grub rescue on startup and ls for bootable partitions it returns with errors.

Further info:
BIOS: Coreboot 4.6 from Purism 2
06/23/2017

The question is: how do I fix this? I have made backups but I’d rather not lose my PureOS sda partition.
All the tutorials online are for win+linux distr or for UEFI BIOS. I guess I need some specialized instructions for Coreboot…

PS: I am willing to fiddle around because I like the idea of having both kali and a debian distro on my computer. I have nothing of value in my kali `sdb` partition and I'm willing to reinstall that / delete anytime. I do dispose of live disks for both kali and pureos.

I’d appreciate any advice. Thank you

---

### Post by javes2 on 2018-09-05
This is an email I received in response:
> You basically need to reinstall grub.

First boot to Kali, and reinstall its grub to its disk (/dev/sdb). You can then boot to Kali when you press ESC when restarting and selecting that disk.
Then boot the PureOS live from USB drive, mount encrypted partitions and chroot into them, and reinstall grub to the /dev/sda. You can find a bunch of resources for this online, such as: [https://ubuntuforums.org/showthread.php?t=2311687](https://ubuntuforums.org/showthread.php?t=2311687)


This lingo was a bit too cryptic for me and I decided to ask for clarifications in regards of installing grub on sda (I did the chroot onto mounted pureos and grub-install etc but it doesn't seem to work and I didn't want to screw anything up by attempting to solve this issue with the solutions found on the linked thread pertaininf to a grub to single partition)

---

### Post by oldos2er on 2018-09-05
Moved to Other OS, Ubuntu/Debian BASED.

---

