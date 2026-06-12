---
title: "how do i mount and use a raid please?"
date: 2010-12-23
forum: Server Platforms
---

### Post by zander1013 on 2010-12-23
hi,

using ubuntu 10.10 alternate install disk on a netbook with a pair of 4gb usb sticks on a dongle.

i have what i believe to be a working raid 1 setup following instructions here...
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

here is the output of mdadm --querry ...

> af@jayne:~$ sudo mdadm --query --detail /dev/md*
/dev/md0:
        Version : 00.90
  Creation Time : Thu Dec 23 11:32:19 2010
     Raid Level : raid1
     Array Size : 3687360 (3.52 GiB 3.78 GB)
  Used Dev Size : 3687360 (3.52 GiB 3.78 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Dec 23 16:42:59 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 74380809:d00ffa12:ef32bd85:f9dc5bba
         Events : 0.58

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
af@jayne:~$

and the output of fdisk -l...

> af@jayne:~$ sudo fdisk -l

Disk /dev/sda: 30.8 GB, 30816608256 bytes
255 heads, 63 sectors/track, 3746 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00057406

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3587    28806144   83  Linux
/dev/sda2            3587        3747     1285121    5  Extended
/dev/sda5            3587        3747     1285120   82  Linux swap / Solaris

Disk /dev/mmcblk0: 2032 MB, 2032664576 bytes
41 heads, 40 sectors/track, 2420 cylinders
Units = cylinders of 1640 * 512 = 839680 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   *           1        2421     1984910+   6  FAT16

Disk /dev/sdb: 4012 MB, 4012900352 bytes
124 heads, 62 sectors/track, 1019 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00069dd8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         960     3687424   fd  Linux raid autodetect
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 32, 33) logical=(0, 33, 3)
Partition 1 has different physical/logical endings:
     phys=(459, 48, 37) logical=(959, 66, 12)
Partition 1 does not end on cylinder boundary.
/dev/sdb2             960        1020      228353    5  Extended
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(459, 81, 5) logical=(959, 99, 13)
Partition 2 has different physical/logical endings:
     phys=(487, 190, 23) logical=(1019, 25, 26)
Partition 2 does not end on cylinder boundary.
/dev/sdb5             960        1020      228352   82  Linux swap / Solaris

Disk /dev/md0: 3775 MB, 3775856640 bytes
2 heads, 4 sectors/track, 921840 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/sdc: 4012 MB, 4012900352 bytes
124 heads, 62 sectors/track, 1019 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a26a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         960     3687424   fd  Linux raid autodetect
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 32, 33) logical=(0, 33, 3)
Partition 1 has different physical/logical endings:
     phys=(459, 48, 37) logical=(959, 66, 12)
Partition 1 does not end on cylinder boundary.
/dev/sdc2             960        1020      228353    5  Extended
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(459, 81, 5) logical=(959, 99, 13)
Partition 2 has different physical/logical endings:
     phys=(487, 190, 23) logical=(1019, 25, 26)
Partition 2 does not end on cylinder boundary.
/dev/sdc5             960        1020      228352   82  Linux swap / Solaris
af@jayne:~$ 



how do i mount and use the raid?

do i need to add a mount point and edit /etc/fstab or /etc/mtab?

perhaps the raid is not configured correctly as i believe?

please advise.

thank you.

thank you.

---

### Post by psusi on 2010-12-23
First it needs to have a filesystem put on it for you to mount.  You can format it with sudo mke2fs -t ext4 /dev/md0.  Then if you want to permanently mount it, yes, you need to add a line to /etc/fstab.

---

### Post by zander1013 on 2010-12-24
hi,

(using the 10.10 alternate installer iso from a usb stick)

i have removed the first md0 device using the installer and re-made the raid 1 array from scratch before i got your reply to use mke2f. :(

here is the out put from mdadm --query now...

> af@jayne:~$ sudo mdadm --query --detail /dev/md*
[sudo] password for af: 
mdadm: cannot open /dev/md*: No such file or directory
af@jayne:~$

and the current output from fdisk -l...

> af@jayne:~$  sudo fdisk -l

Disk /dev/sda: 30.8 GB, 30816608256 bytes
255 heads, 63 sectors/track, 3746 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00057406

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3587    28806144   83  Linux
/dev/sda2            3587        3747     1285121    5  Extended
/dev/sda5            3587        3747     1285120   82  Linux swap / Solaris

Disk /dev/mmcblk0: 2032 MB, 2032664576 bytes
41 heads, 40 sectors/track, 2420 cylinders
Units = cylinders of 1640 * 512 = 839680 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   *           1        2421     1984910+   6  FAT16

Disk /dev/sdb: 4012 MB, 4012900352 bytes
124 heads, 62 sectors/track, 1019 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000235b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         960     3687424   fd  Linux raid autodetect
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 32, 33) logical=(0, 33, 3)
Partition 1 has different physical/logical endings:
     phys=(459, 48, 37) logical=(959, 66, 12)
Partition 1 does not end on cylinder boundary.
/dev/sdb2             960        1020      228353    5  Extended
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(459, 81, 5) logical=(959, 99, 13)
Partition 2 has different physical/logical endings:
     phys=(487, 190, 23) logical=(1019, 25, 26)
Partition 2 does not end on cylinder boundary.
/dev/sdb5             960        1020      228352   82  Linux swap / Solaris

Disk /dev/sdc: 4012 MB, 4012900352 bytes
124 heads, 62 sectors/track, 1019 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00019f81

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         960     3687424   fd  Linux raid autodetect
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 32, 33) logical=(0, 33, 3)
Partition 1 has different physical/logical endings:
     phys=(459, 48, 37) logical=(959, 66, 12)
Partition 1 does not end on cylinder boundary.
/dev/sdc2             960        1020      228353    5  Extended
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(459, 81, 5) logical=(959, 99, 13)
Partition 2 has different physical/logical endings:
     phys=(487, 190, 23) logical=(1019, 25, 26)
Partition 2 does not end on cylinder boundary.
/dev/sdc5             960        1020      228352   82  Linux swap / Solaris
af@jayne:~$

for completeness here is the result of mke2fs ...

> af@jayne:~$ sudo mke2fs -t ext4 /dev/md0
[sudo] password for af: 
mke2fs 1.41.12 (17-May-2010)
Could not stat /dev/md0 --- No such file or directory

The device apparently does not exist; did you specify it correctly?
af@jayne:~$ 


please advise on how to proceed.

thank you.;)

---

### Post by psusi on 2010-12-24
If you are doing this in the installer then the very same or next screen lets you choose what filesystem to format the array with and where to mount it.

---

### Post by zander1013 on 2010-12-24
> **psusi said:**
> If you are doing this in the installer then the very same or next screen lets you choose what filesystem to format the array with and where to mount it.

i am doing it with the 10.10 alternate installer.

in the software RAID configuration menu i have removed the raid i ran the commands for in my previous post. then in the same menu chosen "Create MD Device" to create the device and get the screen you have spoken of. (i don't seem to be able to find the screen you have mentioned)

next, i am asked to choose the type and i select... RAID1

next, i select 2 as number of active devices for the RAID1

next, i set 0 for number of spare devices.

next, i choose which partitions are active devices. i must select exactly 2. i choose /dev/sdc1 and /dev/sdd1

this returns me to the software RAID configuration menu where i select Finish.

the partitioner starts, runs for < 10 seconds, then i am back at the "Partition disks" menu.

the options on the Partition disks menu are Guided partitioning, Configure software RAID, Configure the Logical Volume Manager, Configure encrypted volumes.

under these 4 options the the RAID1 device i just created is displayed first followed by the main hdd for the netbook displayed 2nd, 3rd and 4th are the 4gb usb sticks i am using for the RAID.

after the partitions the options "Undo changes to partitions" and "Finish partitioning and write changes to disk" are listed.

i select the last option "Finish partitioning and write changes to disk" press continue and i get a red screen that says "No root file system" "No root file system is defined." "Please correct this from the partitioning menu." next i select "Continue"

i am taken back to the partitioning menu that i described where i am presented with those same options.

the raid disk is shown as this...
> RAID1 device #0 - 3.8 GB Software RAID device
     #1           3.8 GB
                983.0 KB     unuseable


if i select the row with >     #1           3.8 GB

i am presented with the options "do not use", "Copy data from another partition", "Erase data on this partition" and Done setting up the partition"

perhaps i should choose "Copy data from another partition"?

and if this is the case what partition should i copy the data from?

thank you.

---

### Post by zander1013 on 2010-12-25
hi,

i have now been through both paths offered by "Copy data from another partition", "Erase data on this partition" in an attempt to setup an ext4 file system and mount point using the 10.10 alternate installer. "do not use" seems unlikely to offer the opportunity to setup the file system under RAID1 device #0.

there are other reports that only the 9.04 alternate installer works for this purpose.

i will try that next.:|

---

### Post by furlabs on 2010-12-25
From memory you go into "Do not use" and change it to filesystem: ext4, mount point: /. Don't forget, you will also need a partition to act as swap space. This can be RAID as well if you choose. In this case you will need to create two RAID partitions on each drive, and then create two RAID1 multidisks instead of one.

---

### Post by psusi on 2010-12-25
> **furlabs said:**
> from memory you go into "do not use" and change it to filesystem: Ext4, mount point: /. Don't forget, you will also need a partition to act as swap space. This can be raid as well if you choose. In this case you will need to create two raid partitions on each drive, and then create two raid1 multidisks instead of one.

+1

---

### Post by zander1013 on 2010-12-26
the thread is solved. (using 10.10 desktop alternate .iso)

thank you for your assistance. :popcorn:

---

