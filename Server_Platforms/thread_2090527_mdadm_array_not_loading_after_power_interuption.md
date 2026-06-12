---
title: "mdadm array not loading after power interuption"
date: 2012-12-02
forum: Server Platforms
---

### Post by 5ilentj on 2012-12-02
Have a raid 5 mdadm array that dropped out after a power outage. When I rebooted the machine the fstab complained it could not mount /dev/md127.

Ran cat /proc/mdstat:
```

j@J-FileStore:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
unused devices: <none>

```

Ok so my array is not assembled, let just reassemble it and see what happens.

mdadm --assemble -scan -v
```

j@J-FileStore:~$ sudo mdadm --assemble --scan -v
mdadm: looking for devices for /dev/md0
mdadm: Cannot assemble mbr metadata on /dev/sda
mdadm: Cannot assemble mbr metadata on /dev/sdb
mdadm: Cannot assemble mbr metadata on /dev/sdc
mdadm: Cannot assemble mbr metadata on /dev/sdd
mdadm: Cannot assemble mbr metadata on /dev/sde

```
Well besides /dev/sda being my OS drive looks like it doesn't like the rest of my drives either.

And when I examine my drives:

mdadm --examine /dev/sd*
```

j@J-FileStore:~$ sudo mdadm --examine /dev/sd*
/dev/sda:
   MBR Magic : aa55
Partition[0] :    943847424 sectors at         2048 (type 83)
Partition[1] :     32917506 sectors at    943851518 (type 05)
mdadm: No md superblock detected on /dev/sda1.
/dev/sda2:
   MBR Magic : aa55
Partition[0] :     32917504 sectors at            2 (type 82)
mdadm: No md superblock detected on /dev/sda5.
/dev/sdb:
   MBR Magic : aa55
Partition[0] :   1953520002 sectors at           63 (type 07)
/dev/sdb1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : e3cb9187:060820ed:9722d719:3490b94d
  Creation Time : Mon May 23 17:10:39 2011
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 2930279808 (2794.53 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 127

    Update Time : Sun Dec  2 08:01:39 2012
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 378746f7 - correct
         Events : 166161

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8      97        1      active sync

   0     0       8      145        0      active sync
   1     1       8      113        1      active sync
   2     2       8      129        2      active sync
   3     3       8       97        3      active sync
mdadm: No md superblock detected on /dev/sdb1.
/dev/sdc:
   MBR Magic : aa55
Partition[0] :   1953520002 sectors at           63 (type 07)
/dev/sdc1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : e3cb9187:060820ed:9722d719:3490b94d
  Creation Time : Mon May 23 17:10:39 2011
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 2930279808 (2794.53 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 127

    Update Time : Sun Dec  2 08:01:39 2012
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 378746f7 - correct
         Events : 166161

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8      113        1      active sync

   0     0       8      145        0      active sync
   1     1       8      113        1      active sync
   2     2       8      129        2      active sync
   3     3       8       97        3      active sync
/dev/sdd:
   MBR Magic : aa55
Partition[0] :   1953520002 sectors at           63 (type 83)
/dev/sdd1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : e3cb9187:060820ed:9722d719:3490b94d
  Creation Time : Mon May 23 17:10:39 2011
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 2930279808 (2794.53 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 127

    Update Time : Sun Dec  2 08:01:39 2012
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 37874709 - correct
         Events : 166161

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8      129        2      active sync

   0     0       8      145        0      active sync
   1     1       8      113        1      active sync
   2     2       8      129        2      active sync
   3     3       8       97        3      active sync
/dev/sde:
   MBR Magic : aa55
Partition[0] :   1953520002 sectors at           63 (type 83)
/dev/sde1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : e3cb9187:060820ed:9722d719:3490b94d
  Creation Time : Mon May 23 17:10:39 2011
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 2930279808 (2794.53 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 127

    Update Time : Sun Dec  2 08:01:39 2012
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 37874715 - correct
         Events : 166161

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8      145        0      active sync

   0     0       8      145        0      active sync
   1     1       8      113        1      active sync
   2     2       8      129        2      active sync
   3     3       8       97        3      active sync

```

Try to assemble the raid manually

mdadm --assemble /dev/sdb1 /dev/sdc1 /dec/sdd1 /dev/sde1
```

j@J-FileStore:~$ sudo mdadm --assemble /dev/sdb1 /dev/sdc1 /dec/sdd1 /dev/sde1
mdadm: device /dev/sdb1 exists but is not an md array.

```

Thinking that maybe the superblock on /dev/sdb1 is corrupted I go on on to repair it. Reboot the machine and still isn't coming up right. Examine /dev/sdb1 with mdadm again and I get:
```

j@J-FileStore:~$ sudo mdadm --examine /dev/sdb1
mdadm: No md superblock detected on /dev/sdb1.

```

At that point I knew I've done something stupid, mdadm cannot read the raid information off /dev/sdb1 now. So I've hit on road block on what I should do next.

Anyone have any tips or suggestions on what to do? I figure if I can get the raid back and going with sdc1, sdd1, and sde1 I can always repair the array on sdb1.

Edit:
Decided to treat /dev/sdb1 as a degraded drive. Attempted to force a assemble with only /dev/sd[c-e]1, didn't work. Remembering that the array was mounted on /dev/md127 and prefered minor was 127, I tried that out. Array mounted! From there I was able to mount the array transfer files off. Though for some reason the server would freeze up when transferring the files over network, so just transferred files to a new array.

Not sure why the array just dropped out from the begging, though I guess anything can happen when the array just has its power cut.

---

