---
title: "XP Setup Hangs After Installing Ibex"
date: 2008-11-23
forum: Windows
---

### Post by f1lter on 2008-11-23
So.... I've got two internal hard drives, a 120GB PATA and a 160GB SATA. The SATA drive holds all my data on a big ext3 partition. The PATA drive has a 255mb /boot, a 100GB /, a 4GB swap, and the remaining space is an ntfs partition for XP. The problem is, XP setup doesn't want to start with those Linux partitions in place. It hangs after the "examining your hardware configuration" screen. Before you tell me to install Windows first: I'm trying to avoid that. I'm a big boy, I can reinstall GRUB. I've also tried blanking out the MBR (first 446 bytes of hda). This didn't work, so I restored from backup and went back into Ibex. Then, just for experimentation's sake, I backed up the first 512 bytes of hda (MBR + partition table) to sda, and overwrote them with zeroes. Windows setup started without a hitch (and showed 120GB of unpartitioned space).

My question: is there ANY way I can get Windows to install without re-installing Ubuntu? I put a lot of work into the Ubuntu install before I tried installing XP. I have also heard of someone using fdisk to re-do the partition table (down to the exact sector) and having that work for some reason. Does anyone have any ideas?

---

### Post by caljohnsmith on 2008-11-23
I've seen more than a few cases in the forums where the person's HDD partition table turned out to be slightly corrupt, so even though the person could boot into Ubuntu OK, the Windows Install CD choked and refused to see the existing partitions. I would recommend checking your HDD's partition table to see if that's the cause of your problems; how about posting:
```
sudo fdisk -l
```
Next make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen.

---

### Post by f1lter on 2008-11-23
fdisk -l:

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a7b0a7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          31      248976   83  Linux
/dev/sdb2              32       11702    93747307+  83  Linux
/dev/sdb3           11703       12224     4192965   82  Linux swap / Solaris
/dev/sdb4           12225       14593    19028992+   7  HPFS/NTFS

testdisk (no errors):

Disk /dev/sdb - 120 GB / 111 GiB - CHS 14593 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * Linux                    0   1  1    30 254 63     497952
 2 P Linux                   31   0  1 11701 254 63  187494615
 3 P Linux Swap           11702   0  1 12223 254 63    8385930
 4 P HPFS - NTFS          12224   0  1 14592 254 63   38057985

---

### Post by caljohnsmith on 2008-11-23
Your 120 GB drive partition table looks fine. I notice though that your 120 GB drive is listed as "sdb" and not "sda"; do you have it set up as a slave drive maybe? Windows needs to install to a master drive, or if you want to install Windows on a slave drive, Windows will put its boot files in a primary NTFS/FAT partition on the master drive. I think that might be your issue.

---

### Post by f1lter on 2008-11-23
It's not, the new IDE driver just likes to do things strangely. I liked the old one that called things by their proper names. My drives actually alternate between sda and sdb, so I have to do everything with UUID's or labels. The 120GB drive is set up as the primary PATA master, my two CD drives are the secondary master and slave, and the 160GB drive is in the 1st SATA port.

---

