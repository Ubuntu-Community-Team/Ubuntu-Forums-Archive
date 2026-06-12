---
title: "Problem building new RAID on Server 10.04"
date: 2011-10-19
forum: Server Platforms
---

### Post by netwidget on 2011-10-19
I am trying to build an NAS using Ubuntu Server 10.04.  I am using the following system:

Intel/Pentium 4 2.6GHz
1GB Ram
Silicon Image 4 port SATA/RAID controller (fakeRAID)
4 - 1TB HDD 

The HDD's are drives I have used in the past to test and build different RAID configs using mdadm.  I am trying to build a RAID 1 with 4 disks using the following:

```
mdadm -Cv -l1 -n4 /dev/md0 /dev/sd{b,c,d,e}1
```
When I try this I get a "Device or resource busy" error.  When I catalog the /proc/mdstat I get the following:

> Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md3 : active raid10 sdd1[3] sdb1[1] sdc1[0] sda1[2]
      1953519872 blocks 64K chunks 2 near-copies [4/4] [UUUU]
      
unused devices: <none>

And When I examine the partitions with mdadm:
```
mdadm --examine /dev/sd{a,b,c,d}1
```
 I get:
> /dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 61f714b5:fe18b25f:adc23f65:cc5a51de
  Creation Time : Sun Jul 10 02:59:45 2011
     Raid Level : raid10
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 1953519872 (1863.02 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 3

    Update Time : Mon Oct 17 11:33:19 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 5a46c420 - correct
         Events : 98

         Layout : near=2, far=1
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       17        2      active sync   /dev/sdb1

   0     0       8       49        0      active sync   /dev/sdd1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       8       65        3      active sync   /dev/sde1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 61f714b5:fe18b25f:adc23f65:cc5a51de
  Creation Time : Sun Jul 10 02:59:45 2011
     Raid Level : raid10
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 1953519872 (1863.02 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 3

    Update Time : Mon Oct 17 11:33:19 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 5a46c42e - correct
         Events : 98

         Layout : near=2, far=1
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   /dev/sdc1

   0     0       8       49        0      active sync   /dev/sdd1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       8       65        3      active sync   /dev/sde1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 61f714b5:fe18b25f:adc23f65:cc5a51de
  Creation Time : Sun Jul 10 02:59:45 2011
     Raid Level : raid10
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 1953519872 (1863.02 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 3

    Update Time : Mon Oct 17 11:33:19 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 5a46c43c - correct
         Events : 98

         Layout : near=2, far=1
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       49        0      active sync   /dev/sdd1

   0     0       8       49        0      active sync   /dev/sdd1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       8       65        3      active sync   /dev/sde1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 61f714b5:fe18b25f:adc23f65:cc5a51de
  Creation Time : Sun Jul 10 02:59:45 2011
     Raid Level : raid10
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 1953519872 (1863.02 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 3

    Update Time : Mon Oct 17 11:33:19 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 5a46c452 - correct
         Events : 98

         Layout : near=2, far=1
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       65        3      active sync   /dev/sde1

   0     0       8       49        0      active sync   /dev/sdd1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3       8       65        3      active sync   /dev/sde1

It is indicating that there is a RAID 10 device md3 in existance and active.  However I have tried to stop the device with -S command and even tried to zero out the superblock for /dev/sd{a,b,c,d}1 and I get a device busy error again.

I have reformatted the disks and even zeroed them out using dd however it still comes back.  I went into the FAKEraid settup just before the BIOS posts and checked the status of the card.  It indicates that "No RAID device to delete" when trying to delete any possible configurations in the card.  fdisk -l gives the following:

> isk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00011e81

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5482f9cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2d6b9798

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   83  Linux

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3d04945c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001   83  Linux

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000997d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sde2              32       60802   488134657    5  Extended
/dev/sde5              32       60802   488134656   8e  Linux LVM

Disk /dev/md3: 2000.4 GB, 2000404348928 bytes
2 heads, 4 sectors/track, 488379968 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

    Device Boot      Start         End      Blocks   Id  System

Notice the md3 device at the bottom of the fdisk print out.  

Any help with this would be greatly appreciated.

Thanks

---

### Post by netwidget on 2011-10-19
Also I forgot to post the results of the detail of the md3 RAID device.  See below:

> /dev/md3:
        Version : 00.90
  Creation Time : Sun Jul 10 02:59:45 2011
     Raid Level : raid10
     Array Size : 1953519872 (1863.02 GiB 2000.40 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 3
    Persistence : Superblock is persistent

    Update Time : Wed Oct 19 02:14:15 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : near=2, far=1
     Chunk Size : 64K

           UUID : 61f714b5:fe18b25f:adc23f65:cc5a51de
         Events : 0.98

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8       17        1      active sync   /dev/sdb1
       2       8        1        2      active sync   /dev/sda1
       3       8       49        3      active sync   /dev/sdd1

Thanks again - any help.

---

### Post by rubylaser on 2011-10-19
What do you have in your /etc/mdadm/mdadm.conf file?  You should be able to clear that out and then reboot.  After the reboot, mdadm won't auto assemble the array.  At that point, you can zero the superblocks on your disks, and then create your new array.

Can, I ask why you're trying to create a 4 disk RAID1? Do you really need 4 copies of that data?  You could consider a RAID10, or if you want the possibility to add more disks in the future, a RAID6 works well too.

---

### Post by a2j on 2011-10-19
I'd stay with raid10 or do raid6. but if you really want raid1 with 4 drives, first delete existing raid10 setup and then configure a new raid1 array.

---

### Post by netwidget on 2011-10-19
@rubylaser - The mdadm.conf file did have the definition for the ARRAY for the raid10 in it.  I commented it out so that it would not autoload.  I also renamed the file so currently the system is booting without a mdadm.conf file.

It still shows up.  I have seen that dmraid can automatically load raid drives from the kernel at boot but I do not have dmraid installed on this server.  And the new partitions that I setup are type 83 not fd (raid autodetect).  I am even concerned that the SATA/RAID 4 channel card is somehow configuring the array.  I unfortunately have no way of shutting this down in the BIOS (Old mobo old BIOS).

@a2j - If you had read my first post carefully you would have understood that I have tried several ways to delete the existing raid10 and remove the md3 device.  I have even tried to zero the drives using dd.  I am hoping someone will spend the time to read the information provided and give me insights into additional possible ways to delete and remove the device.

Thank you in advance anyone who may be able to help.

---

### Post by a2j on 2011-10-20
I see mdadm and BIOS in your posts. so, are we talking about software or hardware/faike raid?

did you try *umount /dev/md3*?
what *df -hT* says?
what is in */etc/fstab* ?

---

### Post by netwidget on 2011-10-20
@aj2 - The intent is software RAID, I want to avoid the fakeraid option.  md3 is not mounted I thought of the same idea and the umount command just returns /dev/md3: not mounted.  Therefore df only shows use of the bootable drive which is not apart of the this raid set, and is working fine.

---

### Post by rubylaser on 2011-10-20
What is the output of
```
mount
```

Also, if you're sharing the folder out via SMB or NFS, you'll want to stop the service or at a minimum comment out the file share.  Then umount, then stop the array, and zero the superblocks.  Luckily, it's not magic, something is using / accessing your array, so we'll figure it out :)

---

### Post by netwidget on 2011-10-22
I believe I have fixed it.  Here were the steps (as I remember them) that worked (also I didn't have NFS or SMB services running or configured yet):

1. Removed partitions from the physical drives in the array using fdisk. Without partitions any active raid that uses partitions (mine did) will not be able to build itself, after a reboot without the partitions being placed back on the drives.

2. Renamed mdadm.conf to mdadm.conf.backup
```
cp /etc/mdadm/mdadm.conf /etc/mdadm/mdadm.conf.backup
rm /etc/mdadm/mdadm.conf
```
This is to ensure that the ARRAY device commands in the conf file are not executed.

3. Rebooted computer
```
reboot
```
Once rebooted I ran:
```
cat /proc/mdstat
```
I did this to check that the array was not active. Since this is the only array device on this system it listed no active arrays.

4. Zeroed physical drives in array (my OS does not reside on these drives).
```
dd if=/dev/zero of=/dev/sda bs=1M seek=1013760
```

5. rebooted computer again.
6. Partitioned the drives using fdisk.
7. rebuilt raid10.
```
mdadm -Cv -l10 -n4 /dev/md4 /dev/sd{a..d}1
```
And finally the new raid device built itself.

8.  After build I ran:
```
mdadm -details /dev/md4
```
And the array was re-syncing.

9.  Once the array was active I copied the mdadm.conf.backup back to mdadm.conf and added the new array into it:
```
vi /etc/mdadm/mdadm.conf
and added the following at the end of the file:

ARRAY /dev/md4 level=raid10 num-devices=4 UUID=<my device's UUID here>
```

10.  Once the array finished syncing I rebooted the computer to ensure all was working.

Now its on to creating the file system and creating a mount point in /etc/fstab.

Thanks all for your thoughts.

---

