---
title: "Changing Boot drives to 3Tb RAID1 problems"
date: 2014-06-29
forum: Server Platforms
---

### Post by James074 on 2014-06-29
Hi,
I have an HP Proliant DL-140 G2 that is running in a RAID1 80Gb multi disk software Raid. Recently I bought 2x 3Tb Seagate Barracuda drives to RAID them as my old 80Gig ones. I just can't get the system to boot after the installation. I get a grub rescue :mad: I am using the Ubuntu ISO 12.04 server x64 in expert mode, i format the drives as GPT, make 256mb Partition for grub bootloader, a 32Gb Raid md1 device for Swap( as i have 16Gb Ram ) , and the rest md2 device as 2.7Tb Raid, system loads perfectly but grub just cannot boot off a GPT 3Tb drive. I did not declare any bootable flags.

I am stuck.. Any help appreciated..

---

### Post by oldfred on 2014-06-29
I do not know RAID, but with gpt partitioned drives and I assume even in RAID it still applies you need either an efi partition for UEFI boot on newer systems and/or a bios_grub partition to boot in BIOS mode.
The efi partition is FAT32 formatted and has boot flag or with gdisk a code of ef00. 300MB is a good size.
The bios_grub partition is only 1 or 2MB unformatted (unless using something other than ext type formats, then may need to be large as grub2's core.img becomes much bigger). It has to have bios_grub flag or with gdisk a code of ef02.

       GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

This user created both bios_grub and efi partitions:
      
 How to install Ubuntu 14.04 in software RAID 1 with Intel Z87 chipset mobo controller
[http://ubuntuforums.org/showthread.php?t=2229126](http://ubuntuforums.org/showthread.php?t=2229126)

---

### Post by houstonbofh on 2014-06-29
I am betting the proliant can not boot to the 3TB drives or to GPT.  You may need a very small boot drive.  It can even be on a USB drive.

---

### Post by James074 on 2014-06-30
I was thinking too that the Proliant has a very old BIOS and a non UEFI Bios as Oldfred suggested does not read GPT. When I changed the drives from GPT to MBR they still did not work. It installs everything but does not boot. Grub fails with a Grub Rescue prompt.

Would a small USB Drive slow down the Server performance ? Or it is used only during boot time and that's it !

The Pen drive would hold only the BIOS Grub info and would be used only whenever a server reboot is required.

Many thanks for your help guys..

---

### Post by houstonbofh on 2014-07-05
You can make a /boot drive with your MBR on the USB to boot the system.  It is only used during boots and updates.  It will last a LONG time.

---

