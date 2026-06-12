---
title: "mdadm raid recovery when things go really south"
date: 2012-05-13
forum: Server Platforms
---

### Post by MakOwner on 2012-05-13
I have an external 8 disk esata enclosure.
I have been having what appeared to be link issues and I have been trying to determine if it's the controller, the port multipliers or the cables between.  (I think I have it isolated to the port multipliers and I have a ticket open with the vendor)

In the mean time as a method of testing reliability of the enclosure/array, I built an 8 disk raid 5 array and filled it with data.  Then I started doing shutdown and power cycle and warm reboots as that's where the issue with hardware were always exhibited.  No problem after it was up and running, you just never know if it's coming back...


So, anyway... 

I have this 8 disk array that during one of the boot ups, the port multiplier never became stable enough to maintain a link to 4 of the drives.  I powered it off from the initramfs shell prompt you get to after a failed boot.


So, I have the enclosure and stablized enough right now that the disks can come online with a consistent link, but the array will no longer function.  After the boot it's "inactive".

```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : inactive sdc1[1](S) sdb1[0](S) sdi1[8](S) sdh1[6](S) sdg1[5](S) sdf1[4](S) sde1[3](S)
      5128001536 blocks super 1.2

```

Every partition that was once in the array is now spare - this is an example of the first volume and every volume looks like this:
```

# mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 6ebecaf9:27fd6848:619e5291:e2ef3b44
           Name : pe850-fs01:2  (local to host pe850-fs01)
  Creation Time : Fri May  4 14:21:10 2012
     Raid Level : -unknown-
   Raid Devices : 0

 Avail Dev Size : 1465143296 (698.63 GiB 750.15 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 154f3aa5:d1cbf9a3:5790ad5e:3c34baf8

    Update Time : Sun May 13 16:19:29 2012
       Checksum : 8992f43b - correct
         Events : 2


   Device Role : spare
   Array State :  ('A' == active, '.' == missing)

```


Is there a chance that an mdadm --stop and then a forced assembly assuming a clean state will bring this back?

---

### Post by rubylaser on 2012-05-13
If you haven't written anything to the array during this process, you should be able to stop the array, and then force assemble it.

```
mdadm --stop /dev/md2
mdadm --assemble --force /dev/md2 /dev/sd[bcdefghi]1
```

---

### Post by MakOwner on 2012-05-13
I must have had the parameters backwards or something. I couldn't get the assemble to work.  Create with assume clean worked - it's survived a fsck and a couple of reboots so far.

I need to run an array verify.

This worked:
```

mdadm --create --assume-clean /dev/md2 --verbose --level=5 --raid-devices=8 /dev/sd[bcdefghi]1

```

And this didn't -- I didn't use the correct syntax...

```

 mdadm --assemble --assume-clean /dev/md2 --verbose --level=5 --raid-devices=8 /dev/sd[bcdefghi]1

```

Should have used --force instead of --assume-clean

---

### Post by rubylaser on 2012-05-13
Good, glad you got it working. Let me know if you have any further problems.

---

