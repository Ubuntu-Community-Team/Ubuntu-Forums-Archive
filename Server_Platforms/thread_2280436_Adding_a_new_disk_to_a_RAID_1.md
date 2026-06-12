---
title: "Adding a new disk to a RAID 1"
date: 2015-05-30
forum: Server Platforms
---

### Post by Windowsxpnomore on 2015-05-30
server has 4 disks
80G boot
3T, 3T RAID1 md0
3T backup Disk.

one of the 3T failed in md0. I have physically removed it and replaced it with a new hd that I have used GTPart to format in Ext4 format.
From the below sda is part of md0, sdb is the backup disk, sbc is no where and sdd is the 80G boot disk
Have I got this right?

To add sdc to the raid is all I need to do
**sudo mdadm --add /dev/md0 /dev/sdc1**
and wait for a very long time?

do I need to do 
**sudo grub-install /dev/md0**
? and why?

yes the data is backup, should the mirror go wrong.


```
sudo lshw -C disk

  *-disk:0                
       description: ATA Disk
       product: ST3000DM001-9YN1
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: CC4B
       serial: Z1F1AXRA
       size: 2794GiB (3TB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=953d2281-dce4-41cd-aafb-1124edfbf4d4
  *-disk:1
       description: ATA Disk
       product: WDC WD30EFRX-68E
       vendor: Western Digital
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: 80.0
       serial: WD-WMC4N2361912
       size: 2794GiB (3TB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=527de0f2-af58-482a-bc2c-779762e1ed10
  *-disk
       description: ATA Disk
       product: WDC WD30EFRX-68E
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sdc
       version: 82.0
       serial: WD-WCC4N7VXZ1ST
       size: 2794GiB (3TB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=9eb746d1-7f34-48bb-ad06-e17867cc72d7
  *-cdrom
       description: DVD writer
       product: DVD+-RW TS-H653A
       vendor: TSSTcorp
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: D300
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: ATA Disk
       product: SAMSUNG HD080HJ/
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdd
       version: ZH10
       serial: S0DEJ1KLC01353
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0000b407
```



```
df -h

Filesystem                    Size  Used Avail Use% Mounted on
/dev/mapper/MediaServer-root   58G  3.5G   52G   7% /
udev                          3.9G  4.0K  3.9G   1% /dev
tmpfs                         1.6G  588K  1.6G   1% /run
none                          5.0M     0  5.0M   0% /run/lock
none                          3.9G     0  3.9G   0% /run/shm
/dev/sdd1                     228M   52M  165M  24% /boot
/dev/md0                      2.7T  2.6T   47G  99% /mnt/data
/dev/sdb1                     2.7T  2.6T   49G  99% /mnt/BackupDisk
```

```
sudo mdadm -D /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Sat May 11 11:52:01 2013
     Raid Level : raid1
     Array Size : 2930133824 (2794.39 GiB 3000.46 GB)
  Used Dev Size : 2930133824 (2794.39 GiB 3000.46 GB)
   Raid Devices : 2
  Total Devices : 1
    Persistence : Superblock is persistent

    Update Time : Sat May 30 19:26:56 2015
          State : clean, degraded 
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           Name : MediaServer:0  (local to host MediaServer)
           UUID : 94c8b9dd:8a6c9061:83d1dd29:2bbeef2b
         Events : 158056

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       2       8        1        1      active sync   /dev/sda1
```


many thanks

---

### Post by sandyd on 2015-05-30
Assuming that you removed the failed disk from mdadm properly (mdadm -D /dev/md0 should show as removed), use
```

mdadm --manage /dev/md0 -a /dev/sdc1
```
The following command should show you the added disk and the state of the resyncing```
cat /proc/mdstat
```

---

### Post by Windowsxpnomore on 2015-05-30
> Assuming that you removed the failed disk from mdadm properly (mdadm -D /dev/md0 should show as removed), use


Er no - just powered down and removed the failed disk and added in a new disk.

sudo mdadm -D /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Sat May 11 11:52:01 2013
     Raid Level : raid1
     Array Size : 2930133824 (2794.39 GiB 3000.46 GB)
  Used Dev Size : 2930133824 (2794.39 GiB 3000.46 GB)
   Raid Devices : 2
  Total Devices : 1
    Persistence : Superblock is persistent

    Update Time : Sat May 30 19:26:56 2015
          State : clean, degraded 
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           Name : MediaServer:0  (local to host MediaServer)
           UUID : 94c8b9dd:8a6c9061:83d1dd29:2bbeef2b
         Events : 158056

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       2       8        1        1      active sync   /dev/sda1

---

### Post by SeijiSensei on 2015-05-30
Does /proc/mdstat show the drive being rsynced?

If not, try removing  the drive using mdadm then add it again.
```

sudo mdadm --manage /dev/md0 -r /dev/sdc1
sudo mdadm --manage /dev/md0 -a /dev/sdc1

```

Resyncing a 3 terabyte drive will take hours; patience is a virtue in this case.

I'd read through these as well: [https://raid.wiki.kernel.org/index.php/Detecting,_querying_and_testing](https://raid.wiki.kernel.org/index.php/Detecting,_querying_and_testing) and [https://raid.wiki.kernel.org/index.php/Reconstruction](https://raid.wiki.kernel.org/index.php/Reconstruction)

---

### Post by darkod on 2015-05-31
First, you didn't need to format the new partition as ext4. In SW raid, the filesystem sits on top of the /dev/mdX devices, not the partitions. The arrays get formatted. But in this case I think it shouldn't matter. Just in the future, create partition(s) on the disks you want for raid, but do not format those partitions.

Second, if you simply physically replaced the disk, it's not automatically included in md0. As the -D md0 shows, sda1 is currently the only member of md0. As already mentioned above, and since it looks you never tried to add sdc1 to md0, all you need to do is:
```
sudo mdadm /dev/md0 --add /dev/sdc1
```

After that do the -D /dev/md0 again to check the details of md0. sdc1 should show as member and syncing. It will take some time for 3TB to sync but as soon as you see sdc1 as member, it means it was added correctly.

---

### Post by Windowsxpnomore on 2015-05-31
many thanks

 after 9 hours - 

cat /proc/mdstat

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdc1[3] sda1[2]
      2930133824 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>

df -H
Filesystem                    Size  Used Avail Use% Mounted on
/dev/mapper/MediaServer-root   62G  3.8G   55G   7% /
udev                          4.2G  4.1k  4.2G   1% /dev
tmpfs                         1.7G  1.1M  1.7G   1% /run
none                          5.3M     0  5.3M   0% /run/lock
none                          4.2G     0  4.2G   0% /run/shm
/dev/sdd1                     239M   54M  173M  24% /boot
/dev/md0                      3.0T  2.8T   51G  99% /mnt/data
/dev/sdb1                     3.0T  2.8T   36G  99% /mnt/BackupDisk

---

