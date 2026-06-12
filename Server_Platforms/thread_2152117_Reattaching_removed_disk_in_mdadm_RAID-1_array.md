---
title: "Reattaching removed disk in mdadm RAID-1 array"
date: 2013-06-06
forum: Server Platforms
---

### Post by RyanBiggs on 2013-06-06
Hello all,

I'm new to Ubuntu and server administration in general, but have been having good times with several Ubuntu 12.04 servers I've set up at my company.

I had believed I had properly set up a software RAID-1 array during Ubuntu installation on one server, but when I learned more about the mdadm tool, I discovered the RAID is degraded and one of the disks is "removed"

```
 sudo mdadm --detail /dev/md1
/dev/md1:
        Version : 1.2
  Creation Time : Fri Mar 29 23:20:08 2013
     Raid Level : raid1
     Array Size : 8112064 (7.74 GiB 8.31 GB)
  Used Dev Size : 8112064 (7.74 GiB 8.31 GB)
   Raid Devices : 2
  Total Devices : 1
    Persistence : Superblock is persistent


    Update Time : Thu Jun  6 16:17:36 2013
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0


           Name : subversion:1  (local to host subversion)
           UUID : efd38d7e:b49b368f:698e813f:b83574bc
         Events : 72


    Number   Major   Minor   RaidDevice State
       0     252        3        0      active sync   /dev/dm-3
       1       0        0        1      removed

```
(md0 is a similar RAID for the swap partition and has the same issue.)

I've read about adding the drive back to the array with the mdadm --add command, but can't figure out how to get this to work properly. What are the correct steps to get things working correctly?

Thanks!

---

### Post by RyanBiggs on 2013-06-07
> (md0 is a similar RAID for the swap partition and has the same issue.)


Oops, got those backwards -- as you can see from the array size, md1 is the swap partition while md0 is the main (923GB) partition.

Seems some of my confusion stems from using the RAID array with LVM (/dev/dm-3, etc), which I'm studying but which is still mostly over my head...

---

### Post by SaturnusDJ on 2013-06-07
Try:
```

mdadm --manage /dev/md1 --re-add /dev/diskxx

```

---

### Post by RyanBiggs on 2013-06-07
Thanks for the help!

> **SaturnusDJ said:**
> Try:
```

mdadm --manage /dev/md1 --re-add /dev/diskxx

```

I don't have diskxx entries in /dev, but when I try

 sudo mdadm --manage /dev/md0 --re-add /dev/dm-0

or

 sudo mdadm --manage /dev/md0 --re-add /dev/disk/by-id/dm-name-pdc_egddehgi

(which I'm guessing based on: 

```
 ls /dev/mapper -l
total 0
crw------- 1 root root 10, 236 Jun  3 17:26 control
lrwxrwxrwx 1 root root       1 Jun  3 17:26 pdc_egddehgi -> ../dm-0
lrwxrwxrwx 1 root root       1 Jun  3 17:26 pdc_egddehgi1 -> ../dm-1
lrwxrwxrwx 1 root root       1 Jun  3 17:26 pdc_egddehgi2 -> ../dm-2
lrwxrwxrwx 1 root root       1 Jun  3 17:26 pdc_egddehgi5 -> ../dm-3

```


I get, for example:

```
mdadm: Cannot open /dev/dm-0: Device or resource busy
```

(Looking over the tutorial you linked, I'm wondering if I need to boot from a live CD and have the RAID stopped in order to do this, so maybe I'll try that next...)

---

### Post by darkod on 2013-06-07
To use raid and lvm you usually do it the other way. First the raid devices are created from the physical partitions/disks, and then the lvm is created from one or more md devices. You seem to have it the other way around.

I would back up the data on external hdd and redo the system if it's not too much trouble for you.

The md devices have to be created from something like /dev/sda1, /dev/sdb1, /dev/sda2, /dev/sdb2, etc, not from /dev/dm-X.

On top of the above, your ls /dev/mapper seems to show fakeraid devices (or not). I was under the impression pdc_..... is a fakeraid device. If that is true you seem to have fakeraid devices, then LVM created from them, and then md devices created from the LVM which makes no sense.

---

### Post by RyanBiggs on 2013-06-07
Thanks Darko, great info. I was thinking things seemed goofy regarding the relationship between LVM and RAID. I'm not sure how things got so garbled since I let the installer set up the RAID. But I had first attempted to set things up with a fakeraid instead of software raid before I realized what junk the fake raid controller was, so perhaps I poisoned the well or left something configured incorrectly in BIOS.

> **darkod said:**
> 
I would back up the data on external hdd and redo the system if it's not too much trouble for you.


Yeah I'm coming to the conclusion that this is the easiest way out too...

> **darkod said:**
> The md devices have to be created from something like /dev/sda1, /dev/sdb1, /dev/sda2, /dev/sdb2, etc, not from /dev/dm-X.

Makes sense; that's the way the other server I've set up with a (correctly functioning) RAID looks.

---

