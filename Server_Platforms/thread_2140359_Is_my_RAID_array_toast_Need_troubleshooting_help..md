---
title: "Is my RAID array toast? Need troubleshooting help."
date: 2013-04-29
forum: Server Platforms
---

### Post by abion on 2013-04-29
Hey there,

Last night I received an e-mail from mdadm about the possible failure of two drives on my array. The raid array was set up as a 4 2TB drive raid5 with one hot spare. Is this system truly fried? Did the hot spare pick up anything at all, or did the two drives fail at once? Did one drive fail, start to rebuild onto the spare, and then cause another drive failure? I'm fairly new to working with raids, and this system is one I inherited from a previous employee, so I'm unsure of what the proper troubleshooting steps are here. Any help would be much appreciated. 

Output of cat /proc/mdstat:
```


[FONT=arial]sudo cat /proc/mdstat[/FONT]
[FONT=arial]Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10] [/FONT]
[FONT=arial]md0 : active raid5 sdc[4](F) sdd[5](F) sda[6](S) sdb[0] sde[3][/FONT]
[FONT=arial]      5860543488 blocks level 5, 64k chunk, algorithm 2 [4/2] [U__U]
[/FONT]

```

Output of mdadm --detail:
```


[FONT=arial]#sudo mdadm --detail /dev/md0
[/FONT]
[FONT=arial]/dev/md0:[/FONT]
[FONT=arial]        Version : 0.90[/FONT]
[FONT=arial]  Creation Time : Mon Jun 21 13:54:13 2010[/FONT]
[FONT=arial]     Raid Level : raid5[/FONT]
[FONT=arial]     Array Size : 5860543488 (5589.05 GiB 6001.20 GB)[/FONT]
[FONT=arial]  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)[/FONT]
[FONT=arial]   Raid Devices : 4[/FONT]
[FONT=arial]  Total Devices : 5[/FONT]
[FONT=arial]Preferred Minor : 0[/FONT]
[FONT=arial]    Persistence : Superblock is persistent[/FONT]

[FONT=arial]    Update Time : Mon Apr 29 10:52:27 2013[/FONT]
[FONT=arial]          State : clean, FAILED[/FONT]
[FONT=arial] Active Devices : 2[/FONT]
[FONT=arial]Working Devices : 3[/FONT]
[FONT=arial] Failed Devices : 2[/FONT]
[FONT=arial]  Spare Devices : 1[/FONT]

[FONT=arial]         Layout : left-symmetric[/FONT]
[FONT=arial]     Chunk Size : 64K[/FONT]

[FONT=arial]           UUID : 2874db80:a0f02d66:999df3c7:[/FONT][FONT=arial]ff8f8e6e (local to host bigkahuna)[/FONT]
[FONT=arial]         Events : 0.10984[/FONT]

[FONT=arial]    Number   Major   Minor   RaidDevice State[/FONT]
[FONT=arial]       0       8       16        0      active sync   /dev/sdb[/FONT]
[FONT=arial]       1       0        0        1      removed[/FONT]
[FONT=arial]       2       0        0        2      removed[/FONT]
[FONT=arial]       3       8       64        3      active sync   /dev/sde[/FONT]

[FONT=arial]       4       8       32        -      faulty spare   /dev/sdc[/FONT]
[FONT=arial]       5       8       48        -      faulty spare   /dev/sdd[/FONT]
[FONT=arial]       6       8        0        -      spare   /dev/sda

[/FONT]
```

---

### Post by darkod on 2013-04-29
First, for future reference, it's better to use partitions as mdadm members instead of whole disks like you did. If one disk was a hot spare, the array should still work. Do you know which disk was the spare? It would help if you know and tell us. PS: I jusr reread your post, is /dev/sde the hot spare?

Also, post the --examine output:
```
sudo mdadm --examine /dev/sd[abcde]
```

---

### Post by abion on 2013-04-29
Thanks, it seems like I'll need to read some guides to get a better understanding of working with RAIDs. If you have any advice in that regard, I'd appreciate it. What is the advantage of partition members? I believe /dev/sde was the spare that was installed.

output of sudo mdadm -- examine /dev/sd[abcde]:

```

[FONT=arial]sudo mdadm --examine /dev/sd[abcde][/FONT]

[FONT=arial]/dev/sda:[/FONT]
[FONT=arial]          Magic : a92b4efc[/FONT]
[FONT=arial]        Version : 0.90.00
           UUID : 2874db80:a0f02d66:999df3c7:ff8f8e6e (local to host bigkahuna)
[/FONT]
[FONT=arial]  Creation Time : Mon Jun 21 13:54:13 2010
     Raid Level : raid5
[/FONT]
[FONT=arial]  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 5860543488 (5589.05 GiB 6001.20 GB)
   Raid Devices : 4
  Total Devices : 5
Preferred Minor : 0

[/FONT]
[FONT=arial]    Update Time : Mon Apr 29 11:33:25 2013[/FONT]
[FONT=arial]          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 2
  Spare Devices : 1
[/FONT]
[FONT=arial]       Checksum : 1dcdcbb6 - correct[/FONT]
[FONT=arial]         Events : 10988

         Layout : left-symmetric
     Chunk Size : 64K

[/FONT]
[FONT=arial]      Number   Major   Minor   RaidDevice State
[/FONT]
[FONT=arial]this     6       8        0        6      spare   /dev/sda[/FONT]

[FONT=arial]   0     0       8       16        0      active sync   /dev/sdb[/FONT]
[FONT=arial]   1     1       0        0        1      faulty removed[/FONT]
[FONT=arial]   2     2       0        0        2      faulty removed[/FONT]
[FONT=arial]   3     3       8       64        3      active sync   /dev/sde[/FONT]
[FONT=arial]   4     4       8       32        4      faulty   /dev/sdc[/FONT]
[FONT=arial]/dev/sdb:[/FONT]
[FONT=arial]          Magic : a92b4efc[/FONT]
[FONT=arial]        Version : 0.90.00
           UUID : 2874db80:a0f02d66:999df3c7:ff8f8e6e (local to host bigkahuna)
[/FONT]
[FONT=arial]  Creation Time : Mon Jun 21 13:54:13 2010
     Raid Level : raid5
[/FONT]
[FONT=arial]  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 5860543488 (5589.05 GiB 6001.20 GB)
   Raid Devices : 4
  Total Devices : 5
Preferred Minor : 0

[/FONT]
[FONT=arial]    Update Time : Mon Apr 29 11:33:25 2013[/FONT]
[FONT=arial]          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 2
  Spare Devices : 1
[/FONT]
[FONT=arial]       Checksum : 1dcdcbc0 - correct[/FONT]
[FONT=arial]         Events : 10988

         Layout : left-symmetric
     Chunk Size : 64K

[/FONT]
[FONT=arial]      Number   Major   Minor   RaidDevice State
[/FONT]
[FONT=arial]this     0       8       16        0      active sync   /dev/sdb[/FONT]

[FONT=arial]   0     0       8       16        0      active sync   /dev/sdb[/FONT]
[FONT=arial]   1     1       0        0        1      faulty removed[/FONT]
[FONT=arial]   2     2       0        0        2      faulty removed[/FONT]
[FONT=arial]   3     3       8       64        3      active sync   /dev/sde[/FONT]
[FONT=arial]   4     4       8       32        4      faulty   /dev/sdc[/FONT]
[FONT=arial]mdadm: No md superblock detected on /dev/sdc.[/FONT]
[FONT=arial]mdadm: No md superblock detected on /dev/sdd.[/FONT]
[FONT=arial]/dev/sde:[/FONT]
[FONT=arial]          Magic : a92b4efc[/FONT]
[FONT=arial]        Version : 0.90.00
           UUID : 2874db80:a0f02d66:999df3c7:ff8f8e6e (local to host bigkahuna)
[/FONT]
[FONT=arial]  Creation Time : Mon Jun 21 13:54:13 2010
     Raid Level : raid5
[/FONT]
[FONT=arial]  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
     Array Size : 5860543488 (5589.05 GiB 6001.20 GB)
   Raid Devices : 4
  Total Devices : 5
Preferred Minor : 0

[/FONT]
[FONT=arial]    Update Time : Mon Apr 29 11:33:25 2013[/FONT]
[FONT=arial]          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 2
  Spare Devices : 1
[/FONT]
[FONT=arial]       Checksum : 1dcdcbf6 - correct[/FONT]
[FONT=arial]         Events : 10988

         Layout : left-symmetric
     Chunk Size : 64K

[/FONT]
[FONT=arial]      Number   Major   Minor   RaidDevice State
[/FONT]
[FONT=arial]this     3       8       64        3      active sync   /dev/sde[/FONT]

[FONT=arial]   0     0       8       16        0      active sync   /dev/sdb[/FONT]
[FONT=arial]   1     1       0        0        1      faulty removed[/FONT]
[FONT=arial]   2     2       0        0        2      faulty removed[/FONT]
[FONT=arial]   3     3       8       64        3      active sync   /dev/sde[/FONT]
[FONT=arial]   4     4       8       32        4      faulty   /dev/sdc[/FONT]


``` 

Running smartctl returned the following error for sdc and sdd:

```

[FONT=arial]sudo smartctl -a -T permissive /dev/sdc[/FONT]
[FONT=arial]smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.0.0-14-[/FONT][FONT=arial]generic] (local build)[/FONT]
[FONT=arial]Copyright (C) 2002-11 by Bruce Allen, [/FONT][http://smartmontools.sourceforge.net]("http://smartmontools.sourceforge.net/")

[FONT=arial]Vendor:               /1:0:0:0[/FONT]
[FONT=arial]Product:              [/FONT]
[FONT=arial]User Capacity:        600,332,565,813,390,450 bytes [600 PB][/FONT]
[FONT=arial]Logical block size:   774843950 bytes[/FONT]
[FONT=arial]>> Terminate command early due to bad response to IEC mode page[/FONT]

[FONT=arial]Error Counter logging not supported[/FONT]
[FONT=arial]Device does not support Self Test logging[/FONT]

```

---

### Post by darkod on 2013-04-29
Well, sdc and sdd have no superblock on them, don't know how it was lost. But even in this situation the other three disks have equal event counters which means you should be able to assemble the array as degraded. It was a 4 disk raid5 array and it should work with 3 disks.

Try something like:
```
sudo mdadm --stop /dev/md0 #(stop the array first)
sudo mdadm --assemble /dev/md0 /dev/sda /dev/sdb /dev/sde
```

Tell us whether it says something like device started with 3 disks, or it fails.

---

### Post by abion on 2013-04-29
I tried doing so, and got the message:

```

/dev/md0 assembled from 2 drives and one spare - not enough to start the array.

```
Which I assume means that the process did not work? 

I tried the same after rebooting the system, to the same effect. But oddly, sdc and sdd both had superblocks again when I checked them. Using the advice of another poster in another forum I asked for advice:

```
sudo mdadm --assemble /dev/md0 --scan --force
```

Which then resulted in this:

```

[FONT=arial]mdadm: forcing event count in /dev/sdc(1) from 10977 upto 10988[/FONT]
[FONT=arial]mdadm: forcing event count in /dev/sdd(2) from 10977 upto 10988[/FONT]
[FONT=arial]mdadm: clearing FAULTY flag for device 3 in /dev/md0 for /dev/sdc[/FONT]
[FONT=arial]mdadm: clearing FAULTY flag for device 1 in /dev/md0 for /dev/sdd[/FONT]
[FONT=arial]mdadm: /dev/md0 has been started with 4 drives and 1 spare.

 sudo cat /proc/mdstat[/FONT][COLOR=#500050][FONT=arial]
[/FONT][/COLOR]
[FONT=arial]Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] [/FONT]
[FONT=arial]md0 : active raid5 sdb[0] sda[6](S) sde[3] sdd[2] sdc[1][/FONT]
[FONT=arial]      5860543488 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU][/FONT]

[FONT=arial]unused devices: <none>[/FONT]

```

I then mounted the array and have had no trouble accessing files so far...what happened here? Is this truly reassembled, or just a ticking time bomb or something? Checking SMART errors on ALL 5 drives shows Pre-Fail on attributes #1, #3, #5 (read error rate, spin-up time, reallocated sectors count) and old-age on the rest of the attribute #s. I'm assuming this means it's time to back up and replace these drives sooner rather than later? How many bad sectors are too many? Are these HD's just on their last legs? Knowing the next step here before a disaster would be great.

---

### Post by rubylaser on 2013-04-29
Could we see the full smart output for each disk?  
```
smartctl -a /dev/sda
smartctl -a /dev/sdb
smartctl -a /dev/sdc
smartctl -a /dev/sdd
smartctl -a /dev/sde
```
Also, how are these disks connected to the computer (via SATA to the motherboard or through a PCIe card)?

It would be nice to see the dmesg output grepped for md0.

---

