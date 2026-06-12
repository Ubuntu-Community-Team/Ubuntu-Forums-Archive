---
title: "Software Raid Recovery Assistance"
date: 2010-11-27
forum: Server Platforms
---

### Post by mitchd123 on 2010-11-27
Need some help, my software raid no longer mounts, all disks show they are in standby?   The actual hardware is fine, I think it may be a UUID issue?  I've tried to force this but no luck?  Any hints would be **greatly** appreciated!

**Raid state: **
root@virtual:/tmp# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdd1[2](S) sde1[3](S) sdc1[1](S) sdb1[0](S)
      1953182208 blocks
       
unused devices: <none>


**Attempt to start the array:**

root@virtual:/tmp# mdadm --assemble --scan --verbose /dev/md0
mdadm: looking for devices for /dev/md0
mdadm: no RAID superblock on /dev/sde
mdadm: /dev/sde has wrong uuid.
mdadm: cannot open device /dev/sdd2: Device or resource busy
mdadm: /dev/sdd2 has wrong uuid.
mdadm: cannot open device /dev/sdd: Device or resource busy
mdadm: /dev/sdd has wrong uuid.
mdadm: no RAID superblock on /dev/sdc
mdadm: /dev/sdc has wrong uuid.
mdadm: no RAID superblock on /dev/sdb
mdadm: /dev/sdb has wrong uuid.
mdadm: cannot open device /dev/sda5: Device or resource busy
mdadm: /dev/sda5 has wrong uuid.
mdadm: no RAID superblock on /dev/sda3
mdadm: /dev/sda3 has wrong uuid.
mdadm: cannot open device /dev/sda2: Device or resource busy
mdadm: /dev/sda2 has wrong uuid.
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: /dev/sda1 has wrong uuid.
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: /dev/sda has wrong uuid.
mdadm: /dev/sde1 is identified as a member of /dev/md0, slot 3.
mdadm: /dev/sdd1 is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sdc1 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 0.
mdadm: added /dev/sdb1 to /dev/md0 as 0
mdadm: added /dev/sdc1 to /dev/md0 as 1
mdadm: added /dev/sde1 to /dev/md0 as 3
mdadm: added /dev/sdd1 to /dev/md0 as 2
mdadm: /dev/md0 assembled from 2 drives - not enough to start the array.

**mdadm.conf **

root@virtual:/tmp# cat /etc/mdadm/mdadm.conf |grep md0
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=f5a6ec06:b292289b:1fd984af:668516de



**Hardware all checks out OK: **


root@virtual:/tmp# hdparm -tT /dev/sd[b-e]

/dev/sdb:
 Timing cached reads:   1956 MB in  2.00 seconds = 978.09 MB/sec
 Timing buffered disk reads:  212 MB in  3.02 seconds =  70.25 MB/sec

/dev/sdc:
 Timing cached reads:   1922 MB in  2.00 seconds = 961.53 MB/sec
 Timing buffered disk reads:  212 MB in  3.01 seconds =  70.33 MB/sec

/dev/sdd:
 Timing cached reads:   1920 MB in  2.00 seconds = 960.32 MB/sec
 Timing buffered disk reads:  372 MB in  3.00 seconds = 123.87 MB/sec

/dev/sde:
 Timing cached reads:   1892 MB in  2.00 seconds = 946.09 MB/sec
 Timing buffered disk reads:  210 MB in  3.01 seconds =  69.82 MB/sec

**Array detail / UUID:** 

root@virtual:/tmp# cat /etc/mdadm/mdadm.conf |grep md0
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=f5a6ec06:b292289b:1fd984af:668516de
root@virtual:/tmp# blkid |grep member
/dev/sdb1: UUID="f5a6ec06-b292-289b-1fd9-84af668516de" TYPE="linux_raid_member" 
/dev/sdc1: UUID="f5a6ec06-b292-289b-1fd9-84af668516de" TYPE="linux_raid_member" 
/dev/sdd1: UUID="f5a6ec06-b292-289b-1fd9-84af668516de" TYPE="linux_raid_member" 
/dev/sde1: UUID="f5a6ec06-b292-289b-1fd9-84af668516de" TYPE="linux_raid_member"


**Partition list:**

root@virtual:/tmp# fdisk -l /dev/sd[b-e] |grep raid
/dev/sdb1               1       60790   488295643+  fd  Linux raid autodetect
/dev/sdc1               1       60790   488295643+  fd  Linux raid autodetect
/dev/sdd1               1       60790   488295643+  fd  Linux raid autodetect
/dev/sde1               1       60790   488295643+  fd  Linux raid autodetect

**Partition list verbose:**




root@virtual:/tmp# fdisk -l /dev/sd[b-e]

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x917da1bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60790   488295643+  fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xed96d8e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60790   488295643+  fd  Linux raid autodetect

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc50392d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60790   488295643+  fd  Linux raid autodetect
/dev/sdd2           60791      243201  1465216357+  83  Linux

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5c831555

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       60790   488295643+  fd  Linux raid autodetect


Solved with the command:

mdadm -A --force /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1

What was key here I think is matching the order of the devices to assemble them as they were listed in cat /proc/mdstat  


root@virtual:/tmp# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdd1[2](S) sde1[3](S) sdc1[1](S) sdb1[0](S)
      1953182208 blocks
       
unused devices: <none>
root@virtual:/tmp# mdadm -A --force /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
mdadm: forcing event count in /dev/sdb1(0) from 94022 upto 94026
mdadm: forcing event count in /dev/sdc1(1) from 94022 upto 94026
mdadm: /dev/md0 has been started with 4 drives.

---

### Post by SaturnusDJ on 2010-12-16
Can someone comment on this? Might be usefull to others to know whether or not the order matters.

---

### Post by rubylaser on 2010-12-16
mdadm uses the UUID of the array, which is in the superblock of each drive of the array to assemble, not the specific device order. What made that command work was the --force option.  The previous attempts show no mention of forcing the array to re-assemble.

---

