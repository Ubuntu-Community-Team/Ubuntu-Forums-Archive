---
title: "Help interpreting mdadm RAID1 status"
date: 2011-02-07
forum: Server Platforms
---

### Post by R.Bucky on 2011-02-07
I have a RAID1 array, where mdadm states that one of the disks is "removed." Naturally, I assume one of the drives has failed. The mdadm --detail command tells me that the sda drive has failed. However, further inspection from the mdadm -E /dev/sdb1 command says that sdb1 disk has been removed. I am a bit confused. Can someone clarify which drive is failed? Am I misreading the command outputs?

```
sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00011388

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60194   483500032   fd  Linux raid autodetect
/dev/sda2           60194       60802     4885504   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00034632

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60194   483500032   fd  Linux raid autodetect
/dev/sdb2           60194       60802     4885504   82  Linux swap / Solaris
```


```
sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Tue Jul  6 21:54:06 2010
     Raid Level : raid1
     Array Size : 483499968 (461.10 GiB 495.10 GB)
  Used Dev Size : 483499968 (461.10 GiB 495.10 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Feb  7 06:02:14 2011
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 25cf598f:38082643:b43d2f2e:d818a49f
         Events : 0.3752558

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       17        1      active sync   /dev/sdb1
```

```
sudo mdadm -E /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 25cf598f:38082643:b43d2f2e:d818a49f
  Creation Time : Tue Jul  6 21:54:06 2010
     Raid Level : raid1
  Used Dev Size : 483499968 (461.10 GiB 495.10 GB)
     Array Size : 483499968 (461.10 GiB 495.10 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Sun Feb  6 18:11:49 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 4a1f9554 - correct
         Events : 3734096


      Number   Major   Minor   RaidDevice State
this     0       8       33        0      active sync   /dev/sdc1

   0     0       8       33        0      active sync   /dev/sdc1
   1     1       8       49        1      active sync   /dev/sdd1

```

```
sudo mdadm -E /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 25cf598f:38082643:b43d2f2e:d818a49f
  Creation Time : Tue Jul  6 21:54:06 2010
     Raid Level : raid1
  Used Dev Size : 483499968 (461.10 GiB 495.10 GB)
     Array Size : 483499968 (461.10 GiB 495.10 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0

    Update Time : Mon Feb  7 06:05:07 2011
          State : clean
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 4a20ccf6 - correct
         Events : 3752630


      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       0        0        0      removed
   1     1       8       17        1      active sync   /dev/sdb1

```

---

### Post by SeijiSensei on 2011-02-07
Use "cat /proc/mdstat" to get a report like this:
```

Personalities : [raid1] 
md0 : active raid1 hdg2[0] hdf2[1]
      139829696 blocks [2/2] [UU]
      
unused devices: <none>

```

The [UU] entry indicates both drives are up.  If the first drive (/dev/hdg2) were not working, it would report [_U].  If /dev/hdf2 were down, it would report [U_].

---

### Post by R.Bucky on 2011-02-07
It is the first drive then. If sda is no longer functioning, wondering why the **sudo mdadm -E /dev/sdb1** command shows removed.
```
sudo cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb1[1]
      483499968 blocks [2/1] [_U]
      
unused devices: <none>
```

---

### Post by R.Bucky on 2011-02-07
Come to find out that my array did not have a hardware fault after all. What had happened is that the power connector on the back of the drive had broken off and was not supplying power the last time I booted up. I knew that it had broke off and it has power now. But, I thought that it shorted or something when the power connector broke. Long story short, I added the drive back into the array with the following command.

```
sudo mdadm /dev/md0 -a /dev/sda1
```

The array is rebuilding now. 

[IMG]http://nwlinux.com/uploads/array_rebuilding-500x402.png[/IMG]

---

