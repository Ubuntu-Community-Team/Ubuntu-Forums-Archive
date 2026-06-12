---
title: "RAID 5 Failure while increasing size - No data now!"
date: 2010-09-06
forum: Server Platforms
---

### Post by bond00 on 2010-09-06
Based on the reading I've done over the past 48 hours I think I'm in serious trouble here with my RAID 5 array. I got another 1 TB drive and added to my other 3 to increase my space to 3 TB...no problem. 

While the array was resyncing...it got to about 40%, I had a power failure. So I'm pretty sure it failed while it was growing the array...not the partition. Next time I booted mdadm didn't even detect the array. I fiddled around trying to get mdadm to recognize my array, but no luck. 

I finally got desperate enough to just create the array again...I knew the settings of my and had seen some people have success with this method. When creating it, it asked me if I was sure because the disks appeared to belong to an array already, but I said yes. The problem is when I created it, it created a clean array and this is what I'm left with.

```
/dev/md0:
        Version : 00.90
  Creation Time : Sun Sep  5 20:01:08 2010
     Raid Level : raid5
     Array Size : 2930279808 (2794.53 GiB 3000.61 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Sep  6 00:33:38 2010
          State : clean, degraded
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 128K

           UUID : f70f06af:82f788ae:6c6e2548:fb1d9613
         Events : 0.10

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       0        0        3      removed

```

I then tried to mount it, but I get the following error from mount.

```

mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I tried looking for backup superblock locations using e2fsck and every other tool I could find, but nothing worked. I tried testdisk which says it found my partition on /dev/md0, so I let it create the partition. Now I have a /dev/md0p1, which won't let me mount it either. What's interesting is gparted reports /dev/md0p1 as the old partition size (1.82 TB)...the data has to still be there, right?!

Does anyone please have any ideas? My wife's gonna kill me. :???:

---

### Post by ian dobson on 2010-09-06
Hi,

If mdadm creates a device /dev/md0p1 then mdadm hasn't got the correct information in the /etc/mdadm/mdadm.conf.

Recreate the mdadm.conf file and if your lucky your partition will reappear on the next reboot.

Maybe recreate your inital ramdisk after correcting mdadm.conf with update-initramfs -u 

Regards
Ian Dobson

---

### Post by bond00 on 2010-09-06
I erased (and backed up) the mdadm.conf and rebooted...but I think you're right...mdadm is detecting my array wrongly. Probably because when I grew the array, it updated all the discs, but because the sync never finished, it's now in limbo. The newly created mdadm.conf is the same as the replaced one.

Maybe I don't fully understand RAID 5 with mdadm...but I only grew the array...not the partition. So shouldn't my partition/data still be intact? Is there a way to force mdadm to read the old size?

---

### Post by ian dobson on 2010-09-07
Hi,

Can you recreate the mdadm conf file, using:-

echo 'DEVICE partitions' > mdadm.conf
mdadm  --examine  --scan --config=mdadm.conf >> mdadm.conf
update-initramfs -u

Then reboot.

Sorry I should have said block device, rather than partition. Yesterday was a long day and it't now 6am and on my way back to work. Also how many drives do you actually have in your array? The mdadm dump you've provided shows 4 (3 active and a removed drive).


Regards
Ian Dobson

---

