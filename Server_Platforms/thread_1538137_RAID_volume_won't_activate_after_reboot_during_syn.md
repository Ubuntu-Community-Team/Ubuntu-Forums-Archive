---
title: "RAID volume won't activate after reboot during sync"
date: 2010-07-24
forum: Server Platforms
---

### Post by taenus on 2010-07-24
I've got a file server with two RAID volumes.  The one in question is 6 1TB SATA drives in a RAID6 configuration.  I recently thought one drive was becoming faulty, so I removed it from the set.  After running some stress tests, I determined my underlying problem hadn't cleared up.  I added the disk back, which started the resync.  Later on, the underlying problem caused another lock up.  After a hard-reboot, the array will not start.  I'm out of ideas on how to kick this over.

```
$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdd1[1] sdc1[0]
      244139648 blocks [2/2] [UU]
      
md1 : inactive sda1[5](S) sdb1[6](S) sdh1[4](S) sdg1[0](S) sdf1[3](S) sde1[2](S)
      5860559616 blocks
       
unused devices: <none>
```

Most commands do not seem to pull back info on the array,
```
$ sudo mdadm -D /dev/md1
mdadm: md device /dev/md1 does not appear to be active.
```

And an attempt to force assembly meets with no success.
```
$ sudo mdadm -A -f /dev/md1 /dev/sd[abefgh]1
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: /dev/sda1 has no superblock - assembly aborted
```

The syslogs do not seem to have anything valuable.

The disks all have the same partion lay out,
```
$ sudo fdisk -l /dev/sda

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0ea526da

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001   fd  Linux raid autodetect
```

They all give about the same info on a mdadm --examine:
```
$ sudo mdadm -E /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : be6267fb:adfea5d0:c98f4fcf:6dfd4c27 (local to host XXXXX)
  Creation Time : Sat Apr 24 19:53:17 2010
     Raid Level : raid6
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 3907039744 (3726.04 GiB 4000.81 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 1

    Update Time : Sat Jul 24 06:42:16 2010
          State : active
 Active Devices : 5
Working Devices : 6
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 1f7e572f - correct
         Events : 904013

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     5       8        1        5      active sync   /dev/sda1

   0     0       8       97        0      active sync   /dev/sdg1
   1     1       0        0        1      faulty removed
   2     2       8       65        2      active sync   /dev/sde1
   3     3       8       81        3      active sync   /dev/sdf1
   4     4       8      113        4      active sync   /dev/sdh1
   5     5       8        1        5      active sync   /dev/sda1
   6     6       8       17        6      spare   /dev/sdb1
```

---

### Post by jbrown96 on 2010-07-24
You could try to stop the array first. It may also be a could idea to make the array readonly until you get this problem solved. 

--auto-assemble is worth a try, but probably won't do anything.

It looks like you know what you are doing, but checking the manpage may help you. You should look closely at the "Misc" mode section. The output from some of those commands may help you get a better idea what is happening.

---

### Post by taenus on 2010-07-24
The various detail commands didn't really pan out.

```
$ sudo mdadm --query /dev/md1
/dev/md1: is an md device which is not active
```
```
$ sudo mdadm --detail /dev/md1
mdadm: md device /dev/md1 does not appear to be active.
```
```
$ sudo mdadm --examine /dev/md1
mdadm: No md superblock detected on /dev/md1.
```

Your stop suggestion gave me an idea.  I forgot about the --verbose option and used it on an assemble with interesting results:
```
$ sudo mdadm --stop /dev/md1 
mdadm: stopped /dev/md1

$ sudo mdadm -A -f /dev/md1 /dev/sd[abefgh]1 --verbose
mdadm: looking for devices for /dev/md1
mdadm: /dev/sda1 is identified as a member of /dev/md1, slot 5.
mdadm: /dev/sdb1 is identified as a member of /dev/md1, slot 6.
mdadm: /dev/sde1 is identified as a member of /dev/md1, slot 2.
mdadm: /dev/sdf1 is identified as a member of /dev/md1, slot 3.
mdadm: /dev/sdg1 is identified as a member of /dev/md1, slot 0.
mdadm: /dev/sdh1 is identified as a member of /dev/md1, slot 4.
mdadm: no uptodate device for slot 1 of /dev/md1
mdadm: added /dev/sde1 to /dev/md1 as 2
mdadm: added /dev/sdf1 to /dev/md1 as 3
mdadm: added /dev/sdh1 to /dev/md1 as 4
mdadm: added /dev/sda1 to /dev/md1 as 5
mdadm: added /dev/sdb1 to /dev/md1 as 6
mdadm: added /dev/sdg1 to /dev/md1 as 0
mdadm: failed to RUN_ARRAY /dev/md1: Input/output error
```

I'm guessing my woes have something to do with the slot 1 thing.  I thought I'd post this before bowing to Google.

---

### Post by taenus on 2010-07-26
I found this thread on "that other forum":
[http://www.linuxquestions.org/questions/linux-general-1/raid5-with-mdadm-does-not-ron-or-rebuild-505361/]("http://www.linuxquestions.org/questions/linux-general-1/raid5-with-mdadm-does-not-ron-or-rebuild-505361/")

It would seam (quoting said thread) this *should* work:
```
[root@localhost ~]# cat /sys/block/md1/md/array_state
inactive
[root@localhost ~]# echo "clean" > /sys/block/md1/md/array_state
[root@localhost ~]# cat /sys/block/md1/md/array_state
clean
```

But I (even as root) do not seem to be able to write to that file.
```
root@localhost:/sys/block/md1# echo 'clean' > md/array_state 
-su: echo: write error: Invalid argument
```

---

### Post by rubylaser on 2010-07-26
Do you have an /etc/mdadm/mdadm.conf file, if so, can you post it here?  

Also, what does the events counter look like?
```
mdadm -E /dev/sd[a-h]1 | grep Event
```

That will tell you which drive(s) are stale.

Also, you could try to assemble the array without /dev/sda1 and then re-add it.  It will start degraded but you should be able to re-add it later...
```
sudo mdadm -A -f /dev/md1 /dev/sd[befgh]1
```
Then re-add /dev/sda
```
sudo mdadm --re-add /dev/md0 /dev/sdb1
```

---

