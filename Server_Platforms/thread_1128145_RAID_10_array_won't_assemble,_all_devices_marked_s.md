---
title: "RAID 10 array won't assemble, all devices marked spare, confusing mdadm metadata"
date: 2009-04-17
forum: Server Platforms
---

### Post by Nohthee8 on 2009-04-17
Please help me diagnose the following (catastrophic) problem.

I have two RAID arrays:

```

  $ sudo mdadm --examine --scan -v
  ARRAY /dev/md0 level=raid1 num-devices=2 UUID=e1023500:94537d05:cb667a5a:bd8e784b
     spares=1   devices=/dev/sde2,/dev/sdd2,/dev/sdc2,/dev/sdb2,/dev/sda2
  ARRAY /dev/md1 level=raid10 num-devices=4 UUID=f4ddbd55:206c7f81:b855f41b:37d33d37
     spares=1   devices=/dev/sde4,/dev/sdd4,/dev/sdc4,/dev/sdb4,/dev/sda4

```

/dev/md1 doesn't assemble on boot, and I can't assemble it manually (although that might be because I don't know how to):

```

  $ sudo mdadm --assemble /dev/md1 /dev/sda4 /dev/sdb4 /dev/sdc4 /dev/sdd4 /dev/sde4
  mdadm: /dev/md1 assembled from 1 drive and 1 spare - not enough to start the array.

```

As you can see from mdstat, the kernel appears to have marked all the partitions in /dev/md1 as spare (S):

```

  $ cat /proc/mdstat
  Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
  md1 : inactive sda4[0](S) sde4[4](S) sdd4[3](S) sdc4[2](S) sdb4[1](S)
        4829419520 blocks
         
  md0 : active raid1 sda2[0] sde2[2](S) sdb2[1]
        9767424 blocks [2/2] [UU]
        
  unused devices: <none>

```

This is clearly wrong.  The /dev/md1 arrray should have 4 members plus one spare. 

When I examine the partitions in /dev/md1, the messages are confusing, and seem contradictory: 

```

$ sudo mdadm -E /dev/sd{a,b,c,d,e}4
/dev/sda4:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : f4ddbd55:206c7f81:b855f41b:37d33d37
  Creation Time : Tue May  6 02:06:45 2008
     Raid Level : raid10
  Used Dev Size : 965883904 (921.14 GiB 989.07 GB)
     Array Size : 1931767808 (1842.28 GiB 1978.13 GB)
   Raid Devices : 4
  Total Devices : 5
Preferred Minor : 1

    Update Time : Tue Apr 14 00:45:27 2009
          State : active
 Active Devices : 3
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 7a3576c1 - correct
         Events : 221

         Layout : near=2, far=1
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       20        0      active sync   /dev/sdb4

   0     0       8       20        0      active sync   /dev/sdb4
   1     1       8       36        1      active sync   /dev/sdc4
   2     2       0        0        2      faulty removed
   3     3       8       68        3      active sync   /dev/sde4
   4     4       8       84        4      spare
/dev/sdb4:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : f4ddbd55:206c7f81:b855f41b:37d33d37
  Creation Time : Tue May  6 02:06:45 2008
     Raid Level : raid10
  Used Dev Size : 965883904 (921.14 GiB 989.07 GB)
     Array Size : 1931767808 (1842.28 GiB 1978.13 GB)
   Raid Devices : 4
  Total Devices : 5
Preferred Minor : 1

    Update Time : Tue Apr 14 00:44:13 2009
          State : active
 Active Devices : 4
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 1
       Checksum : 7a35767a - correct
         Events : 219

         Layout : near=2, far=1
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       36        1      active sync   /dev/sdc4

   0     0       8       20        0      active sync   /dev/sdb4
   1     1       8       36        1      active sync   /dev/sdc4
   2     2       8       52        2      active sync   /dev/sdd4
   3     3       8       68        3      active sync   /dev/sde4
   4     4       8       84        4      spare
/dev/sdc4:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : f4ddbd55:206c7f81:b855f41b:37d33d37
  Creation Time : Tue May  6 02:06:45 2008
     Raid Level : raid10
  Used Dev Size : 965883904 (921.14 GiB 989.07 GB)
     Array Size : 1931767808 (1842.28 GiB 1978.13 GB)
   Raid Devices : 4
  Total Devices : 5
Preferred Minor : 1

    Update Time : Tue Apr 14 00:44:13 2009
          State : active
 Active Devices : 4
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 1
       Checksum : 7a35768c - correct
         Events : 219

         Layout : near=2, far=1
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       52        2      active sync   /dev/sdd4

   0     0       8       20        0      active sync   /dev/sdb4
   1     1       8       36        1      active sync   /dev/sdc4
   2     2       8       52        2      active sync   /dev/sdd4
   3     3       8       68        3      active sync   /dev/sde4
   4     4       8       84        4      spare
/dev/sdd4:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : f4ddbd55:206c7f81:b855f41b:37d33d37
  Creation Time : Tue May  6 02:06:45 2008
     Raid Level : raid10
  Used Dev Size : 965883904 (921.14 GiB 989.07 GB)
     Array Size : 1931767808 (1842.28 GiB 1978.13 GB)
   Raid Devices : 4
  Total Devices : 5
Preferred Minor : 1

    Update Time : Tue Apr 14 00:44:13 2009
          State : active
 Active Devices : 4
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 1
       Checksum : 7a35769e - correct
         Events : 219

         Layout : near=2, far=1
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       68        3      active sync   /dev/sde4

   0     0       8       20        0      active sync   /dev/sdb4
   1     1       8       36        1      active sync   /dev/sdc4
   2     2       8       52        2      active sync   /dev/sdd4
   3     3       8       68        3      active sync   /dev/sde4
   4     4       8       84        4      spare
/dev/sde4:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : f4ddbd55:206c7f81:b855f41b:37d33d37
  Creation Time : Tue May  6 02:06:45 2008
     Raid Level : raid10
  Used Dev Size : 965883904 (921.14 GiB 989.07 GB)
     Array Size : 1931767808 (1842.28 GiB 1978.13 GB)
   Raid Devices : 4
  Total Devices : 5
Preferred Minor : 1

    Update Time : Fri Apr 10 16:43:47 2009
          State : clean
 Active Devices : 4
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 1
       Checksum : 7a31126a - correct
         Events : 218

         Layout : near=2, far=1
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8       84        4      spare

   0     0       8       20        0      active sync   /dev/sdb4
   1     1       8       36        1      active sync   /dev/sdc4
   2     2       8       52        2      active sync   /dev/sdd4
   3     3       8       68        3      active sync   /dev/sde4
   4     4       8       84        4      spare

```

As you can see, sda4 is not explicitly listed in any of the tables above.

I am guessing that this is because mdadm thinks that sda4 is the actual spare.  

I'm not sure that mdadm is correct.  Based on the fdisk readouts shown below,
and my (admittedly imperfect human) memory, I think that sde4 should be the
spare

Another confusing thing is that mdadm --examine for sda4 produces results that
appear to contradict the examinations of sdb4, sdc4, sdd4, and sde4.

The results for sda4 show one partition (apparently sdd4) to be "faulty
removed", but the other four examinations show sdd4 as "active sync".
Examining sda4 also shows 1 "Failed" device, whereas the remaining 4
examinations show no failures.

On the other hand, sda4, sdb4, sdc4, and sdd4 are shown as "State: active"
whereas sde4 is shown as "State: clean".  
 
The checksums look OK.

All the devices have the same UUID, which I presume, is the UUID for /dev/md1.

I haven't seen any obvious signs of hardware failure, although the following do
appear in my syslog:

```

  Apr 14 23:16:43 lonsdale mdadm[22524]: DeviceDisappeared event detected on md device /dev/md1
  Apr 14 23:23:21 lonsdale mdadm[10050]: DeviceDisappeared event detected on md device /dev/md1
  Apr 15 13:45:52 lonsdale mdadm[6780]: DeviceDisappeared event detected on md device /dev/md1

```

I cannot afford to mess around with /dev/md1 because it contains a small amount
of business-critical data for which no totally clean back-ups exist, i.e. I
don't want to do anything that could conceivably overwrite this data until I'm
certain that I've correctly diagnosed the problem.

So please suggest non-destructive diagnostic procedures that I can follow to
narrow down the problem.

A further complication is that /dev/md1 contains my /home, /var, and /tmp
filesystems, so I can't update my kernel, initrd or mdadm via a normal apt
install.


For what it's worth, here's my /etc/mdadm/mdam.conf, /etc/fstab, and fdisk outut:

mdadm.conf
```

  DEVICE partitions
  CREATE owner=root group=disk mode=0660 auto=yes
  HOMEHOST <system>
  MAILADDR root
  # definitions of existing MD arrays
  ARRAY /dev/md0 level=raid1 num-devices=2 UUID=e1023500:94537d05:cb667a5a:bd8e784b
  ARRAY /dev/md0 level=raid1 num-devices=2 UUID=8643e320:2d6a0e4d:49d52491:42504c27
  ARRAY /dev/md1 level=raid10 num-devices=4 UUID=f4ddbd55:206c7f81:b855f41b:37d33d37
     spares=1

```

fstab:
```

cat /etc/fstab 
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md0
UUID=5d494f0c-d723-4f15-90d6-b4d08e5fd059 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=2968bbbe-223f-490f-869e-1312dabdaf18 /boot           ext2    relatime        0       2
# /dev/mapper/vg--data1-lv--home on /dev/md1
UUID=8b824f93-e686-4f08-9ec2-76e754d8f06f /home           ext3    relatime        0       2
# /dev/mapper/vg--data1-lv--tmp on /dev/md1
UUID=dee6072f-ca1c-462f-9730-c277e3f8b8d9 /tmp            ext3    relatime        0       2
# /dev/mapper/vg--data1-lv--var on /dev/md1
UUID=03600db0-f72f-4021-9bb2-b8cb19f3a2a0 /var            ext3    relatime        0       2

```

fdisk
```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004b119

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          16      128488+  83  Linux
/dev/sda2              17        1232     9767520   fd  Linux RAID autodetect
/dev/sda3            1233        1354      979965   82  Linux swap / Solaris
/dev/sda4            1355      121601   965884027+  fd  Linux RAID autodetect


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000aca3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          16      128488+  83  Linux
/dev/sdb2              17        1232     9767520   fd  Linux RAID autodetect
/dev/sdb3            1233        1354      979965   82  Linux swap / Solaris
/dev/sdb4            1355      121601   965884027+  fd  Linux RAID autodetect

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00052d44


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          16      128488+  83  Linux
/dev/sdc2              17        1232     9767520   83  Linux
/dev/sdc3            1233        1354      979965   82  Linux swap / Solaris
/dev/sdc4            1355      121601   965884027+  fd  Linux RAID autodetect


Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00055ffb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1          16      128488+  83  Linux
/dev/sdd2              17        1232     9767520   83  Linux
/dev/sdd3            1233        1354      979965   82  Linux swap / Solaris
/dev/sdd4            1355      121601   965884027+  fd  Linux RAID autodetect


Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000249a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1          16      128488+  83  Linux
/dev/sde2              17        1232     9767520   83  Linux
/dev/sde3            1233        1354      979965   82  Linux swap / Solaris
/dev/sde4            1355      121601   965884027+  fd  Linux RAID autodetect

```

Finally, I should point out that some of the data on the dodgy /dev/md1 is absolutely vital and needs to be accessed urgently.

If the worst comes to the worst and I can't assemble, re-sync or re-build the array non-destructively, I'd appreciate any advice you could give on any possibilities that might exist for retrieving the data by reading the raw disks.

---

### Post by Nohthee8 on 2009-04-17
I've just rebooted the machine from an alternate install disc and got radically different results from "cat /proc/mdstat".

Now, mdadm thinks that /dev/md1 only consists of one partition (/dev/sda4), marking the other 3 unidentified members as removed.

Moreover, if I try to assemble with:

```

$ mdadm --assemble /dev/md1 /dev/sda4 /dev/sdb4 /dev/sdc4 /dev/sdd4 /dev/sde4

```

It says that it can't assemble because md1 is currently active ... whereas /proc/mstat says that it is inactive.

Any ideas?

N.B. I am having difficulty getting remote access to/from the machine concerned, so copy + paste code is currently unavailable.

---

### Post by fjgaude on 2009-04-17
I can't what has happened, gone wrong... My only suggestion is: re-name or delete your /etc/mdadm/**mdadm.conf** file, remove **mdadm**, re-boot. Then boot back up, install mdadm using **apt-get** and then run this command:

```
sudo mdadm --assemble --scan
```

A new mdadm.conf file will be auto generated and it will show just what mdadm thinks about the members of your array.

Show what this is:
```

sudo mdadm -D /dev/md0
sudo mdadm -D /dev/md1
```

Let us know what happens.

---

### Post by Nohthee8 on 2009-04-17
Hi Frank,

Thanks for the suggestion, but I can't follow it immediately.

I can remove the mdadm.conf file, use dpkg to remove mdadm, and reboot.

I can't re-install mdadm, because the failing array has my /var filesystem on it, e.g. all of /var/lib/apt.

Any ideas on how to work around that?

More importantly, since I last posted, I've made a bit of a breakthrough.

If I try:

```

$ mdadm --assemble /dev/md1 /dev/sdb4 /dev/sdc4 /dev/sdd4 /dev/sde4

```

I get:
```

mdadm: /dev/md1 assembled from 3 drives and 1 spare - need all 4 to start it 
(use --run to insist).

```

This is obviously promising, and reminds me of something I read somewhere about bad metadata on the first drive's superblock potentially screwing up mdadm.

Before I try using --run, I'd like a bit of re-assurance about it's effects, because the man page description is uncomfortably terse.

I guess that using --run will cause mdadm to use parity data from the other three drives to rebuild the fourth from the spare, overwriting blocks on the spare.

I'd be happy to try that, if:

1. There was a high degree of certainty that the rebuild would be completely successful, or;

2.  I could be certain that mdadm has now correctly identified the spare.

I don't want to go from the current situation (in which I seem to have 3 sound partitions + 1 bad + 1 spare) to a situation in which I end up with 2 good partitions + 2 bad + 1 spare.

Any thoughts?

---

### Post by fjgaude on 2009-04-17
I have never been in the situation you find yourself. The "run" mdadm command will likely not do anything, one way or the other.

The "force" command would be what I would use to assemble. But all this points out how important it is to have backups of all important data. RAID5 protects against one drive failure but that's it. When you think about how each drive has been getting exactly the same useage you can understand why when one fails the others are about to also. <sigh>

I don't have the knowledge or infomation to understand how to get out of the situation you are in. Sorry!

---

