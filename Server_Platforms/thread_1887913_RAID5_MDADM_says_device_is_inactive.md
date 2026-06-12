---
title: "RAID5 MDADM says device is inactive"
date: 2011-11-28
forum: Server Platforms
---

### Post by Crumbs744 on 2011-11-28
When i run mdadm -D /dev/md2:
> mdadm: md device /dev/md2 does not appear to be active.

and cat /proc/mdstat shows:

> Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdf1[1] sde1[0]
      3709312 blocks [2/2] [UU]

md1 : active raid1 sdf2[1] sde2[0]
      200704 blocks [2/2] [UU]

md2 : inactive sdb[0](S) sdc[2](S) sdd[3](S) sda[1](S)
      5860553984 blocks

unused devices: <none>


This happened after a powerout, not really sure where to start.

I realise this is probably vague, but any pointers would be appreciated. Google searching didnt seem to find anything that worked for me...

Thanks :)

---

### Post by rubylaser on 2011-11-28
Have you tried to stop md2, and re-assemble it?  All of your devices are showing as spares.

```
sudo -i
mdadm --stop /dev/md2
mdadm --assemble --force /dev/md2 /dev/sd[abcd]
```

If that doesn't re-assemble the array, could you paste the output of this?
```
mdadm -E /dev/sd[abcd]
```

---

### Post by Crumbs744 on 2011-11-28
Thanks for the reply.

When I try to reassmeble, i get this:

> mdadm: failed to RUN_ARRAY /dev/md2: Input/output error


mdadm -E output is:

> /dev/sda:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : c8901512:2b1294da:dce694f6:20346b6f (local to host crumbs-server)
  Creation Time : Sun Mar 14 00:52:09 2010
     Raid Level : raid5
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB)
     Array Size : 4395415488 (4191.79 GiB 4500.91 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2

    Update Time : Fri Sep  2 06:37:43 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 8baca886 - correct
         Events : 3765655

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8        0        1      active sync   /dev/sda

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8        0        1      active sync   /dev/sda
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8       48        3      active sync   /dev/sdd
/dev/sdb:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : c8901512:2b1294da:dce694f6:20346b6f (local to host crumbs-server)
  Creation Time : Sun Mar 14 00:52:09 2010
     Raid Level : raid5
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB)
     Array Size : 4395415488 (4191.79 GiB 4500.91 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2

    Update Time : Sun Nov 27 11:10:33 2011
          State : active
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 8c15fa03 - correct
         Events : 6990257

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       16        0      active sync   /dev/sdb

   0     0       8       16        0      active sync   /dev/sdb
   1     1       0        0        1      faulty removed
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8       48        3      active sync   /dev/sdd
/dev/sdc:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : c8901512:2b1294da:dce694f6:20346b6f (local to host crumbs-server)
  Creation Time : Sun Mar 14 00:52:09 2010
     Raid Level : raid5
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB)
     Array Size : 4395415488 (4191.79 GiB 4500.91 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2

    Update Time : Sun Nov 27 11:10:33 2011
          State : active
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 8c15fa17 - correct
         Events : 6990257

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       32        2      active sync   /dev/sdc

   0     0       8       16        0      active sync   /dev/sdb
   1     1       0        0        1      faulty removed
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8       48        3      active sync   /dev/sdd
/dev/sdd:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : c8901512:2b1294da:dce694f6:20346b6f (local to host crumbs-server)
  Creation Time : Sun Mar 14 00:52:09 2010
     Raid Level : raid5
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB)
     Array Size : 4395415488 (4191.79 GiB 4500.91 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2

    Update Time : Sun Nov 27 11:10:33 2011
          State : active
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 8c15fa29 - correct
         Events : 6990257

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       48        3      active sync   /dev/sdd

   0     0       8       16        0      active sync   /dev/sdb
   1     1       0        0        1      faulty removed
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8       48        3      active sync   /dev/sdd


---

### Post by rubylaser on 2011-11-28
The first thing you'll want to do is run a SMART test on each of your disks;

```
sudo -i
apt-get install smartmontools
```

```
for i in a b c d; do
    smartctl -s on -t long /dev/sd$i
done

```

This takes a while to run (hours), but you can check how it's coming along like this...
```
smartctl -l selftest /dev/sda
```

If you have read errors on any of the disks, you will not want to include the disk when you put the array back together.

Based on the events counter, /dev/sda appears to be the disk had problems and as result, it is out of sync with the rest of the disks.  So, if the above SMART tests, look good, I would reassemble the array without /dev/sda like this.

```
mdadm --assemble --force /dev/md2 /dev/sd[bcd] 
```

That should reassemble the array in a degraded state.  You could then zero the superblock on /dev/sda, and finally add it back to the array.  Let me know first if the assembly above works before continuing.

---

### Post by Crumbs744 on 2011-11-28
When running, apt-get install smartmontools, i get this

> apt-get: error while loading shared libraries: libgcc_s.so.1: wrong ELF class: ELFCLASS32


I remember having to do something funny with files that look similar for a cod2 server...

---

### Post by rubylaser on 2011-11-28
You shouldn't have to do this, but can you try this?

```
sudo apt-get install ia32-libs
sudo apt-get install smartmontools
```

---

### Post by Crumbs744 on 2011-11-29
Same error. I have a feeling i may have pasted some custom somethings in the wrong place to get a cod2 server working... 

[here ]("http://games.on.net/file/2632/Call_of_Duty_2_Retail_dedicated_Linux_server_v1.3")is the guide i was more or less working off:

The part that i probably boned is this:
> IF YOU HAVE A PROBLEM WITH "LIBSTDC++.SO.5" ...
(This is a frequent-enough problem to merit discussion in the introduction.)

If you are reading this, it's probably because you tried to start your Linux
server and saw this message:

./cod2_lnxded: error while loading shared libraries: libstdc++.so.5:
cannot open shared object file: No such file or directory

COD2 is a C++ program built with gcc 3.3.4, which means it needs a
system library specific to gcc 3.3. Older Linux systems won't have
this installed, and we're starting to see newer Linux distributions that
don't have this either, since they are supplying an incompatible
gcc 3.4 version. The good news is that you can drop the needed library
into your system without breaking anything else.

Here is the library you need, if your Linux distribution doesn't supply it:
[http://icculus.org/updates/cod/gcc3-libs.tar.bz2](http://icculus.org/updates/cod/gcc3-libs.tar.bz2)

You want to unpack that somewhere that the dynamic linker will see it
(if you are sure it won't overwrite any files, you can even use /lib).

The brave can put it in the same directory as the game and run the server
like this:
LD_LIBRARY_PATH=$LD_LIBRARY_PATH:. ./cod2_lnxded

I remember trying to find the place to copy them... probably the wrong place, as nothing broke immediately i assumed it didnt matter.

*gulp*

---

### Post by rubylaser on 2011-11-29
You look like you pinpointed your problem.  Unfortunately, since I didn't set it up, I'm not sure what you did to break your gcc.  You could try to proceed with my directions, but I'd leave out drive sda as I mentioned earlier.

---

### Post by Crumbs744 on 2011-11-29
Thanks for your help. I'll try fix this other issue and get back to you with results.

---

### Post by Crumbs744 on 2011-12-01
Ok, i forgot the smartmontools and just reassembled for now. 

Looks ok so far, cat /proc/mdstat says:
> 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sde1[0] sdf1[1]
      3709312 blocks [2/2] [UU]

md1 : active raid1 sde2[0] sdf2[1]
      200704 blocks [2/2] [UU]

md2 : active raid5 sdd[3] sdb[0] sdc[2]
      4395415488 blocks level 5, 64k chunk, algorithm 2 [4/3] [U_UU]

unused devices: <none>


files dont show up on mount point, so i manually mount

> sudo mount /dev/md2 /srv
mount: /dev/md2 already mounted or /srv busy


I restarted a few times, same issue...

It should still mount when degraded right?

---

### Post by rubylaser on 2011-12-01
> **Crumbs744 said:**
> Ok, i forgot the smartmontools and just reassembled for now. 

Looks ok so far, cat /proc/mdstat says:


files dont show up on mount point, so i manually mount



I restarted a few times, same issue...

It should still mount when degraded right?

I'm not sure what you mean.  It should mount degraded because it's not your boot volume, but based on your post, the message is telling you that's already mounted.  What's the output of
```
mount
```

Also these two commands...
```
mdadm --detail --scan
```
```
cat /etc/mdadm/mdadm.conf
```

---

### Post by Crumbs744 on 2011-12-02
Everything decided to magically work by itself.

Looks like mdadm is re-adding the drive (taking a few hours to do it as well).

Also looked like it mounted now as well.

I just logged in to run those commands. :)

---

### Post by agentofcode on 2013-04-01
I came across this post and have something very similar. I started a new thread since it is different and this one is closed/solved. I was hoping you could help me...?
[http://ubuntuforums.org/showthread.php?t=2131134](http://ubuntuforums.org/showthread.php?t=2131134)

---

### Post by rubylaser on 2013-04-02
I have responded to your other thread.

---

