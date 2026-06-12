---
title: "mdadm - adding new spare fails"
date: 2013-09-12
forum: Server Platforms
---

### Post by chris115 on 2013-09-12
I have an RAID0 Array of two 2TB USB drives which I would like to grow to 6TB. I've connected an identical 2TB drive, partitioned exactly the same.

Here's my drive setup (fdisk -l, skipping the irrelevant /dev/sda):

```
Disk /dev/sdb: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907024896 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  3907024895  1953512447+  ee  GPT


WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdc: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907024896 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  3907024895  1953512447+  ee  GPT


WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sdd: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907024896 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1  3907024895  1953512447+  ee  GPT


Disk /dev/md0: 4000.8 GB, 4000788250624 bytes
2 heads, 4 sectors/track, 976754944 cylinders, total 7814039552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disk identifier: 0x00000000


Disk /dev/md0 doesn't contain a valid partition table

```

Identical partition schemes. I should note that I don't really care about any data on the array; I'm just testing to ensure we can easily add drives in the future as needed. I'm also aware that what I'm doing isn't very safe/is stupid, but I dont care. This is a simple offsite backup of a backup, and I dont need redundancy.

Ok, so the drive is partitioned correctly. I'll try adding the new drive as a spare:

```
root@backupserver:~# mdadm --add /dev/md0 /dev/sdd1
mdadm: add new device failed for /dev/sdd1 as 2: Invalid argument
```

Fails every time. I've tried everything I can think of. Sometimes, it will come in as a spare after I reboot (despite the error message!) - it will go away again after a reboot. In this state, the array will not mount:

```
root@backupserver:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdb1[0] sdd1[2](S) sdc1[1]
      5860529664 blocks super 1.2
       
unused devices: <none>

```
```

root@backupserver:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Thu Sep 12 11:56:16 2013
     Raid Level : raid0
   Raid Devices : 2
  Total Devices : 3
    Persistence : Superblock is persistent


    Update Time : Thu Sep 12 11:56:16 2013
          State : active, Not Started 
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1


     Chunk Size : 512K


           Name : backupserver:0  (local to host backupserver)
           UUID : e8a426a3:0dd8026d:a9cb74b3:df873f3a
         Events : 0


    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1


       2       8       49        -      spare   /dev/sdd1

```
```

root@backupserver:~# mount -a
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I'm at my wits end. Anybody? I'm running 12.04.3/mdadm 3.2.5

---

### Post by chris115 on 2013-09-12
Here's my *--detail *for my array, in it's normal working state:

```
root@backupserver:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Thu Sep 12 11:56:16 2013
     Raid Level : raid0
     Array Size : 3907019776 (3726.02 GiB 4000.79 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent


    Update Time : Thu Sep 12 11:56:16 2013
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


     Chunk Size : 512K


           Name : backupserver:0  (local to host backupserver)
           UUID : e8a426a3:0dd8026d:a9cb74b3:df873f3a
         Events : 0


    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1

```

and the mdstat:

```
root@backupserver:~# cat /proc/mdstat Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid0 sdb1[0] sdc1[1]
      3907019776 blocks super 1.2 512k chunks
      
unused devices: <none>
```

---

### Post by SaturnusDJ on 2013-09-12
RAID0 doesn't use spares, because that's useless. If one active drive fails, there's no job to do for a spare.

Man page:
> If the --raid-disks option is being used to increase the number of devices in an array, then --add can be used to add some extra devices to be included in the array. In most cases this is not needed as the extra devices can be added as spares first, and then the number of raid-disks can be changed. However for RAID0, it is not possible to add spares. So to increase the number of devices in a RAID0, it is necessary to set the new number of devices, and to add the new devices, in the same command. 

So I think this should work:
```
mdadm --grow /dev/md0 --raid-devices=3 --add /dev/sdd1
```

Man page:
> From 2.6.35, the Linux Kernel is able to convert a RAID0 in to a RAID4 or RAID5. mdadm uses this functionality and the ability to add devices to a RAID4 to allow devices to be added to a RAID0. When requested to do this, mdadm will convert the RAID0 to a RAID4, add the necessary disks and make the reshape happen, and then convert the RAID4 back to RAID0. 

---

