---
title: "Clone SSD Win10 partition still boots old HDD partition"
date: 2019-06-23
forum: Windows
---

### Post by johnzbesko on 2019-06-23
I installed a larger SSD to replace the smaller Win10 HDD partition on my dual boot Kubuntu system. I used GParted to clone the Win10 HDD partition to the SSD. I ran grub-update and both OS's were found. When I reboot, both choices boot the HDD version.

When I use the Disk Management tool in Win10, both drive partitions have the same GUID. (Both disks have, I believe, an MBR partition table. The HDD is old- the Win10 is an upgrade from Win7. Thus, I used MBR for the new SSD.) So, using the Win10 bcdedit command line utility doesn't work because I can't distinguish between the two drives.

Grub is on a GPT partitioned SSD. (Yes, there are now two SSD's) When booted into linux, blkid shows two different GUID's for each drive, each different from the GUID listed under Win10. (Some confusion with UUID.)

How do I boot Win10 from the SSD? I tried physically disconnecting the HDD (also contains my /home partition.) The Win10 boot fails with an error message to use a repair disk. I don't want to mess with the original HDD Win10 partition until I'm convinced the SSD version is working properly.

Thank you for any help.

---

### Post by oldfred on 2019-06-23
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Generally you cannot keep a cloned drive plugged in on reboot as duplicate UUIDs (and GUIDs) are not allowed. You either unplug drive, or once you know new works correctly reformat/repartition old drive.

---

