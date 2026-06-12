---
title: "Fail to boot Guest Windows 7 (64 bit) from Host Ubuntu 13.10"
date: 2014-01-17
forum: Virtualisation
---

### Post by jiapei100 on 2014-01-17
Hi, all:

It seems VirtualBox become harder (not as user-friendly as before). I failed to boot up my Windows 7 Guest from Ubuntu 13.10 Host.
Environment:
Host: Ubuntu 13.10 + VirtualBox 4.3.6 r91406 on /dev/sda (2T SATA)
Guest: Windows 7 (64 bit) + SP1  on /dev/sdb: 256Giga SSD
However, on **/dev/sda**, there are multiple partitions as follows:

> 
[email]jiapei@jiapei-pc:~/.Virtua[/email]lBox$ sudo fdisk -ls

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x32934804

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   586717183   293357568   83  Linux
/dev/sda2       586717184   617967615    15625216   82  Linux swap / Solaris
/dev/sda3   *   617967616   618172415      102400    7  HPFS/NTFS/exFAT
/dev/sda4       618172416  3907026943  1644427264    f  W95 Ext'd (LBA)
/dev/sda5       618174464  2268624895   825225216    7  HPFS/NTFS/exFAT
/dev/sda6      2268628992  3907026943   819198976    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 240.1 GB, 240057409536 bytes
255 heads, 63 sectors/track, 29185 cylinders, total 468862128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbada2531

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   468858879   234428416    7  HPFS/NTFS/exFAT

Disk /dev/mapper/cryptswap1: 16.0 GB, 16000221184 bytes
255 heads, 63 sectors/track, 1945 cylinders, total 31250432 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x47005c91

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table



I really have no idea why both /dev/sdb1 and /dev/sda3 are bootable? And, on GRUB, it shows:
Windows is booted from /dev/sda3, which is out of my mind (Sorry, the OS was not installed by myself, and I really don't want to install both systems again. )

I've already strictly followed the manual here [http://www.theunixtips.com/virtualbox-use-raw-disk-to-load-windows-under-linux](http://www.theunixtips.com/virtualbox-use-raw-disk-to-load-windows-under-linux), for both **/dev/sdb1** and **/dev/sda3**. Neither worked...

How I wish I can use VirtualBox as easy as before, when I was still able to select something like "boot from hard drive(disk)".

Please, can anybody give me some hints?

Thank you very much....


Best Regards
Pei

---

### Post by kansasnoob on 2014-01-17
I'm guessing this would receive better responses if posted here:

[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

If you click on "Report Post" in the bottom left hand corner one of the mods will be happy to transfer it :)

---

### Post by howefield on 2014-01-17
Moved to the "*Virtualisation*" forum.

---

