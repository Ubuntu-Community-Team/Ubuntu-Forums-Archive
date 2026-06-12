---
title: "Samba Software Raid Server. Raid Issue"
date: 2013-09-16
forum: Server Platforms
---

### Post by lingpanda on 2013-09-16
Created a new Samba server using two 2 terabyte drives. Ubuntu 12.04.3 LTSx64. On system reboot files appear to be missing. On system shutdown and start everything appears normal. Or so I think. However mdadm I believe shows errors. First time attempting a raid server. This is what I get on shutdown and start.

```
/dev/md0:
        Version : 1.2
  Creation Time : Fri Sep 13 14:00:33 2013
     Raid Level : raid1
     Array Size : 97608576 (93.09 GiB 99.95 GB)
  Used Dev Size : 97608576 (93.09 GiB 99.95 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Mon Sep 16 13:25:54 2013
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : smbserver:0
           UUID : 98fc156b:196f47f9:e9a15bcd:3bb0b1d2
         Events : 34

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
```

```
/dev/md1:
        Version : 1.2
  Creation Time : Fri Sep 13 14:00:39 2013
     Raid Level : raid1
     Array Size : 1855707968 (1769.74 GiB 1900.24 GB)
  Used Dev Size : 1855707968 (1769.74 GiB 1900.24 GB)
   Raid Devices : 2
  Total Devices : 1
    Persistence : Superblock is persistent

    Update Time : Mon Sep 16 13:26:54 2013
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           Name : smbserver:1
           UUID : fd0ad888:eb039bd8:169291b1:b4d4b720
         Events : 23697

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       18        1      active sync   /dev/sdb2
```

I get this on reboot 99% of the time

```
/dev/md0:
        Version : 1.2
  Creation Time : Fri Sep 13 14:00:33 2013
     Raid Level : raid1
     Array Size : 97608576 (93.09 GiB 99.95 GB)
  Used Dev Size : 97608576 (93.09 GiB 99.95 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Mon Sep 16 13:37:44 2013
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : smbserver:0
           UUID : 98fc156b:196f47f9:e9a15bcd:3bb0b1d2
         Events : 34

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
```

```

/dev/md1:
        Version : 1.2
  Creation Time : Fri Sep 13 14:00:39 2013
     Raid Level : raid1
     Array Size : 1855707968 (1769.74 GiB 1900.24 GB)
  Used Dev Size : 1855707968 (1769.74 GiB 1900.24 GB)
   Raid Devices : 2
  Total Devices : 1
    Persistence : Superblock is persistent

    Update Time : Mon Sep 16 13:37:47 2013
          State : active, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           Name : smbserver:1
           UUID : fd0ad888:eb039bd8:169291b1:b4d4b720
         Events : 3542

    Number   Major   Minor   RaidDevice State
       0       8        2        0      active sync   /dev/sda2
       1       0        0        1      removed
```

Followed the urbanpenguin guide from youtube to create the array. Thanks for any help.

---

### Post by rubylaser on 2013-09-23
Can you show us what is in /etc/mdadm/mdadm.conf?

```
cat /etc/mdadm/mdadm.conf
```

Also, how are you repairing this after a reboot?

---

### Post by lingpanda on 2013-09-23
> **rubylaser said:**
> Can you show us what is in /etc/mdadm/mdadm.conf?

```
cat /etc/mdadm/mdadm.conf
```

Also, how are you repairing this after a reboot?

I decided to mark sdb as bad and attempt resync. During the resync process I had power failure which resulted in total HD Failure. In the end I started over on a new raid and all is well. I did decided the second time to let the Drives Sync before installing software on the server.

---

### Post by tehtide on 2013-09-25
You might also want to just double check the SMART data for the drives. I've had intermittent failures on my MDADM RAID 5 that were tough to diagnose until I took at look at the hardware. With both the SMART data at the vendor specific drive checking utilities I was able to determine that one of the drives had bad blocks causing intermittent read failures on my RAID. Just something to think about.

---

