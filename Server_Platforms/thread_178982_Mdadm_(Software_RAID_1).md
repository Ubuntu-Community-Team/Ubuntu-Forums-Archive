---
title: "Mdadm (Software RAID 1)"
date: 2006-05-18
forum: Server Platforms
---

### Post by Sniffer on 2006-05-18
Hi ubuntu fellows,

Here it's my problem :confused: 

I have a configured a Ubuntu server with Raid 1 following this tutorial:

[http://www.howtoforge.com/linux_software_raid](http://www.howtoforge.com/linux_software_raid)

Tough now 1 of the HDD just went off (the 1st one), when i disconnect this hard drive and plug only the second.... i tought it was just like Win32...just start up the system...but no.... on the boot it mdadm misses the other HDD (1ST one)...continues to boot...but on the end just black screen....

YES THE RAID 1 WAS CONFIGURED 100% WORKING.

So my questions?

1st - How the hell if one of my drives fail, can i boot only with the other one?

2nd - And after booting only with this HDD, how can i add a new HDD, pass alll the information to this new HDD and have a 100% functional RAID 1?

Thanks for all the help.... I'm needing it :-D

---

### Post by Glut on 2006-05-18
You need to setup grub on both drives. The first disk will already boot grub correctly. You then need to use the grub console (from the command line) to setup on the second disk:

root@foo: grub
grub> root (hd1,0)
 Filesystem type is ext2fs, partition type 0xfd

grub> setup (hd1) 
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are
embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p
(hd1,0)/boot/grub/stage2 /boot/grub/grub.conf"... succeeded
Done.

grub> quit

--
After doing this you should be able to boot off both disks (assuming no errors).

---

### Post by Sniffer on 2006-05-19
[QUOTE=Glut]You need to setup grub on both drives. The first disk will already boot grub correctly. You then need to use the grub console (from the command line) to setup on the second disk:

root@foo: grub
grub> root (hd1,0)
 Filesystem type is ext2fs, partition type 0xfd

grub> setup (hd1) 
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are
embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p
(hd1,0)/boot/grub/stage2 /boot/grub/grub.conf"... succeeded
Done.

grub> quit

--
After doing this you should be able to boot off both disks (assuming no errors).[/QUOTE]


Then i should have done that when the Raid1 was configured..before the 1st disk went off... :( 

Thanks for all the help mate.

---

