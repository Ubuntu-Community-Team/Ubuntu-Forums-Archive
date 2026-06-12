---
title: "RAID problems after upgrading from 10.04 server to 12.04"
date: 2015-03-25
forum: Server Platforms
---

### Post by al_paun on 2015-03-25
There is something strange when using command mdadm --examine /dev/sda1 I receive this:

```
mdadm --examine /dev/sdb3
/dev/sdb3:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 58b3f336:3dd1f89d:776c2c25:004bd7b2 (local to host rescue)
  Creation Time : Fri Jun 24 08:21:59 2011
     Raid Level : raid1
  Used Dev Size : 730202368 (696.38 GiB 747.73 GB)
     Array Size : 730202368 (696.38 GiB 747.73 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 2

    Update Time : Wed Apr 17 01:54:57 2013
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 82615909 - correct
         Events : 870


      Number   Major   Minor   RaidDevice State
this     1       8       19        1      active sync   /dev/sdb3

   0     0       8        3        0      active sync   /dev/sda3
   1     1       8       19        1      active sync   /dev/sdb3
```

but when trying the same for /dev/sda3 I receive like this:

```
/dev/sda3:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 58b3f336:3dd1f89d:776c2c25:004bd7b2 (local to host rescue)
  Creation Time : Fri Jun 24 08:21:59 2011
     Raid Level : raid1
  Used Dev Size : 730202368 (696.38 GiB 747.73 GB)
     Array Size : 730202368 (696.38 GiB 747.73 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 2

    Update Time : Thu Mar 26 00:04:23 2015
          State : clean
 Active Devices : 1
Working Devices : 1
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 8970f993 - correct
         Events : 28649134


      Number   Major   Minor   RaidDevice State
this     0       8        3        0      active sync   /dev/sda3

   0     0       8        3        0      active sync   /dev/sda3
   1     1       0        0        1      faulty removed

/dev/md2:
        Version : 0.90
  Creation Time : Fri Jun 24 08:21:59 2011
     Raid Level : raid1
     Array Size : 730202368 (696.38 GiB 747.73 GB)
  Used Dev Size : 730202368 (696.38 GiB 747.73 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Thu Mar 26 00:04:23 2015
          State : clean, degraded 
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 58b3f336:3dd1f89d:776c2c25:004bd7b2 (local to host rescue)
         Events : 0.28649134

    Number   Major   Minor   RaidDevice State
       0       8        3        0      active sync   /dev/sda3
       1       0        0        1      removed
```

That's why when booting I get a message in dmesg:

```
md: bind<sda3>
[    3.445141] bio: create slab <bio-1> at 1
[    3.445344] md/raid1:md2: active with 1 out of 2 mirrors
[    3.445408] md2: detected capacity change from 0 to 747727224832
[    3.446445] md: bind<sda2>
[    3.446636]  md2: unknown partition table
```

---

### Post by al_paun on 2015-03-25
Please help. This is a very important server for me and it needs to be started ASAP. 

Thanks, 
Alex

---

### Post by al_paun on 2015-03-25
I don't know why but I cannot reassembly the array correctly 

```
mdadm --assemble --force /dev/md2 /dev/sd[a,b]3
mdadm: /dev/md2 has been started with 1 drive (out of 2).
root@rescue ~ # mdadm --detail /dev/md2
/dev/md2:
        Version : 0.90
  Creation Time : Fri Jun 24 08:21:59 2011
     Raid Level : raid1
     Array Size : 730202368 (696.38 GiB 747.73 GB)
  Used Dev Size : 730202368 (696.38 GiB 747.73 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Thu Mar 26 00:44:47 2015
          State : clean, degraded 
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 58b3f336:3dd1f89d:776c2c25:004bd7b2 (local to host rescue)
         Events : 0.28649226

    Number   Major   Minor   RaidDevice State
       0       8        3        0      active sync   /dev/sda3
       1       0        0        1      removed

mdadm --assemble --force /dev/md2 /dev/sdb3
mdadm: /dev/md2 has been started with 1 drive (out of 2).
root@rescue ~ # mdadm --detail /dev/md2
/dev/md2:
        Version : 0.90
  Creation Time : Fri Jun 24 08:21:59 2011
     Raid Level : raid1
     Array Size : 730202368 (696.38 GiB 747.73 GB)
  Used Dev Size : 730202368 (696.38 GiB 747.73 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Wed Apr 17 01:54:57 2013
          State : clean, degraded 
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 58b3f336:3dd1f89d:776c2c25:004bd7b2 (local to host rescue)
         Events : 0.870

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       19        1      active sync   /dev/sdb3
```

Can anyone help me to fix this problem so I can start my server?

Thanks a lot in advance !!!

---

### Post by SeijiSensei on 2015-03-25
First, if one half of a RAID1 is still working you should be able to mount the device.  If you cannot do this, try redefining the device in /etc/fstab as /dev/sdb3 rather than /dev/md0.  I've found that a treating one drive from a RAID1 as if it were a single device works correctly.

The answer to why the array won't assemble is probably because you have a faulty drive that needs replacement.

---

### Post by cariboo on 2015-03-25
Please don't create multiple threads on the same subject. I have merged your two threads.

---

### Post by darkod on 2015-03-26
First, as Sensei says, a raid1 array with one member failed is still working and the data should be good at this point.

If the machine doesn't boot it might be if during initial raid setup you selected not to boot degraded. The process asks that at one point and if you say No it will not continue booting with any array degraded even if the data is readable.
Then, stop trying to force md2 to assemble. It is already assembled. Only one member is missing but the array is assembled and it seems working.
Also in the examine results take a good look at the events counts. It seems sdb3 dropped from the array at some point, maybe even long time ago. Because its counter is at 870 while sda3 and md2 have more than 28 million. That's a big difference in events so it looks normal the array doesn't want to accept sdb3.

What you can do....
1. To confirm data integrity try mounting md2 at its mount point or at a temp mount point and to read the data. That will show you if it's accessible.
2. Try to add sdb3 to md2 but that might not work because of events difference:
```
sudo mdadm /dev/md2 --add /dev/sdb3
```

3. If the above add doesn't work you can consider zeroing the superblock of sdb3 and then adding it as new member. It should start the rebuild (sync) automatically.
```
sudo mdadm --zero-superblock /dev/sdb3
sudo mdadm /dev/md2 --add /dev/sdb3
```

In any case if you suspect sdb hdd might be failing then buy a new replacement disk, create identical partitions and add them to corresponding arrays.
You never mentioned if other partitions from same disk are members of other arrays and if those arrays are degraded too or not. If other partitions work good maybe just sdb3 dropped at some point from what ever reason and the disk itself is good so you don't need to spend money buying a new one.

PS. What I wrote was based on the examine data in your first original post. If later you did something or the disk order has changed be very careful when running commands because you can zero the superblock on the wrong partition if disk order has changed for example.
Before you continue working I suggest you run the examine again and continue from there.

---

### Post by MAFoElffen on 2015-03-27
> **darkod said:**
> In any case if you suspect sdb hdd might be failing then buy a new replacement disk, create identical partitions and add them to corresponding arrays.
You never mentioned if other partitions from same disk are members of other arrays and if those arrays are degraded too or not. If other partitions work good maybe just sdb3 dropped at some point from what ever reason and the disk itself is good so you don't need to spend money buying a new one.
+1 

While I agree with both the previous posters... This is what was nagging me at the back of my mind while reading this thread. It may have failed for good reason. It may not be re-assembling for a valid reason. Before trying something that may change the filesystems on disks in the array... or putting high-stress on the good disk in the mirror (during a re-assembly), don't you think it may be a good idea to test the disks? Forcing an assembly on an array with a bad disk... not as much a concern where there is no striping, but still, why flirt with chaos?...

I always felt that advantage of doing a mirror was that you have 2 copies of something. If something has trouble... Test the troubled member. If okay, fail it and re-add it. If not, trash it and add new. The whole idea of having the mirror os to keep a good copy of good, right?

Disclaimer: Like Darkod noticed, a disk's partition #3, implies that there are other partitions on that disk and does not preclude that that is the sole partition on that disk... You did not post the "blkid" result of your system, so the recommendations we can give based on the info you supplied, may affect other parts of your system...

---

