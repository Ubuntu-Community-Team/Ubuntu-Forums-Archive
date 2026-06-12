---
title: "lvm2 pvmove gone bad, no dm_mirror"
date: 2010-05-05
forum: Server Platforms
---

### Post by pixelblender on 2010-05-05
Hi,

I have a fileserver running on ubuntu with following setup:
- Ubuntu Karmic 9.10 x64 (not clean install, upgraded from 9.04).
- 4 x 1TB Harddrives combined as one Logical Volume using lvm2. No RAID. Each drive has one 8e (Linux LVM) partition with 4MB Physical Extents. The Logical Volume is formatted as one 4TB Ext4 partition.

Initially what i had was 2 x 1TB. I built my LVM based on this guide: [http://www.howtoforge.com/linux_lvm](http://www.howtoforge.com/linux_lvm). Based on demand i added 1TB drive one at a time until it was 4TB. All i did was simply using pvcreate, pvextends and resize2fs to resize the ext4. I _never_ use pvmove.

Everything runs perfectly fine until 2 days ago i decided to upgrade one of the drive. I bought a new 2TB drive and was thinking of using it as a replacement for one of those 1TB.

I format the 2TB as 8e (Linux LVM), pvcreate on it with default 4MB PE, adding the drive to my VG (/dev/cyclopserver) using vgextends, then try to move data from one of the 1TB (/dev/sdb1) to the 2TB (/dev/sdf1) using pvmove /dev/sdb1 /dev/sdf1.

5-7 hours later, i can see that pvmove reached 100% but it says: ABORTING: Can't find mirror LV in cyclopserver for /dev/sdb1 ... (or was it /dev/sdf1, can't remember exactly). When i check on the new 2TB (/dev/sdf1) it has two almost identical PV. And instead of having 5TB capacity (3 x 1TB + 2TB), i only got 4.5TB :(.

I tried:
```

$ lvconvert -m0 /dev/cyclopserver/fileserver
Logical volume fileserver is already not mirrored.

```

Regarding the "Can't find mirror LV in ..", searching around the internet reveals that i need to install dmsetup and make sure that module dm_mirror is loaded .. the problem is, i can't find it :confused:

```

$ lsmod | grep -i dm
dm_raid45 78504 0
xor 5456 1 dm_raid45

```

and when i try to modprobe it says:

```

$ modprobe dm_mirror
FATAL: Module dm_mirror not found.

```

My questions are:
1. How do i get rid of the mirrored data on the 2TB drive? Is it safe to just force pvremove?
2. How do i make sure the dm_mirror module loaded?

Please help me. Many thanks in advance guys!

---

### Post by pixelblender on 2010-05-05
anyone? any insight? comments?

---

### Post by jwbaker on 2010-06-08
Did you find a solution to this?  I get the abort message but afterwards it seems to have worked anyway.  I also get the message even if I have dm_mirror loaded.  This is on Karmic 64.

```

  /dev/sde1: Moved: 99.6%
  ABORTING: Can't find mirror LV in homedirs for /dev/sde1
# pvs
  PV         VG       Fmt  Attr PSize    PFree  
  /dev/sdb1           lvm2 --    100.00G 100.00G
  /dev/sdc1           lvm2 --    100.00G 100.00G
  /dev/sdd1           lvm2 --    100.00G 100.00G
  /dev/sde1  homedirs lvm2 a-    100.00G 100.00G
  /dev/sdf1  homedirs lvm2 a-    100.00G      0 
  /dev/sdq1  homedirs lvm2 a-    499.99G 100.01G
# vgreduce -a homedirs
  Removed "/dev/sde1" from volume group "homedirs"
  Physical volume "/dev/sdf1" still in use
  Physical volume "/dev/sdq1" still in use

```

---

