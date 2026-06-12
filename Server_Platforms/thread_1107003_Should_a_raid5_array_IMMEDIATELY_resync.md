---
title: "Should a raid5 array IMMEDIATELY resync?"
date: 2009-03-26
forum: Server Platforms
---

### Post by TheKorn2 on 2009-03-26
I'm new to RAID, so apologies in advance if this question is all naff, but here goes.  I have four 1T hard drives.  I'm using the alternate setup disc for 9.0 alpha 6, i386.

I set up one 10G partition on each drive, and raided them together in a raid-1 array.  That's my boot (and root) partition.  2 active, 2 standby (or whatever the installer calls them).  That seems to have gone OK.  (ext3fs, in case anyone cares.)

I also set up a 1G swap partition on each drive.  These are NOT raided together, they're just single swap partitions on each drive that the kernel can figure out how it wants to use them.  :)

Finally, the remainder of the space on each drive I set up as four-way raid 5 partitions, and I'm using jfs for the file system.

That *seems* to have gone all right.  Jaunty Jackhole installed OK (despite the video corruption in the text mode installer), and I later added an entry to fstab to mount the 3TB raid-5 partition by UUID.

```

~$ mount
/dev/md0 on / type ext3 (rw,relatime,errors=remount-ro)
(snip)
/dev/md1 on /mythtv type jfs (rw)
(snip)

```

What I don't understand is that I now have two processes that come up whenever I start the system, and are consuming 30% of the CPU even when it's idle:

```

top - 09:12:52 up  2:50,  3 users,  load average: 1.31, 1.38, 1.51
Tasks: 134 total,   3 running, 131 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.7%us, 22.3%sy,  1.5%ni, 68.1%id,  2.7%wa,  0.7%hi,  3.8%si,  0.0%st
Mem:   3224096k total,   782064k used,  2442032k free,    69032k buffers
Swap:  3919824k total,        0k used,  3919824k free,   415992k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                           
 1504 root      15  -5     0    0    0 R   26  0.0  56:42.96 md1_raid5                                                                                                         
 1506 root      15  -5     0    0    0 D    6  0.0  15:13.70 md1_resync                                                                                                        

```

Is this normal for a raid5 array to immediately go into resync on boot?  I don't think so, but it IS a new array and I'm not well versed in how mdadm handles raid arrays.  (Maybe it's setting something up?  Maybe?)  It's been doing this for a few hours now!

The hard drive controller light is continuously on.  The system is responsive, but throwing 30% of the CPU away right off the top while doing nothing *bugs* me.

But here's the weird thing...  if I run iotop, *nothing* is going out to the hard drives!

```

Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO>    COMMAND                                                                                                               
    1 root           0 B/s       0 B/s  0.00 %  0.00 % init
    2 root           0 B/s       0 B/s  0.00 %  0.00 % [kthreadd]

```


So what's going on here?  Is this normal?  A bug in jaunty?  Should I be concerned?  Will the system eventually figure out my raid 5 is OK and knock it off?  Do I just have to 'wait it out'?

Thanks!!

(BTW, I did some very preliminary reading/writing to the jfs partition and that seemed to go OK.  So it's responsive, but something weird is going on here, I think.)

---

### Post by TheKorn2 on 2009-03-26
Of course, not ten minutes after I write all that, it knocks it off!  I *guess* the first thing the system does after building a raid array is resyncs it for three hours???

I guess; I wouldn't think there would be much to sync on an empty partition!

---

### Post by fjgaude on 2009-03-26
If memory serves, what takes so long with these huge partitions is placing a filesystem on the array... the syncing likly is the filesystem being placed all the drives in the array.

What was the disk activity like during the high CPU useage?

It's a good idea to use this whenever a new array is placed online:

```
sudo watch cat /proc/mdstat
```

I've never even thought of doing what you did... glad you are home free.

---

### Post by TheKorn2 on 2009-03-26
> **fjgaude said:**
> If memory serves, what takes so long with these huge partitions is placing a filesystem on the array... the syncing likly is the filesystem being placed all the drives in the array.

I guess...  The only thing that causes me to question that is I shouldn't be able to write to a filesystem if it isn't all there yet.  But right from the first boot I can mount that partition and copy stuff to it.  (I didn't copy A LOT to it, but I made a couple of directories and copied some trivial files there.)

> What was the disk activity like during the high CPU useage?

Well I rebuilt the system and the array with the amd64 version of jaunty, just because I want to see if there is any performance difference between the two.  (I'm not expecting any more disk performance, but it'd be nice if I could knock the CPU down a few pegs.)  

Anyway, iostat again reports absolutely nothing going through the hard drives.  The HD access light on the PC is continuously on, though you wouldn't have any idea that they're doing anything without it.  (Though if they're simply stepping through all sectors, that shouldn't make a whole lot of noise!)

My theory is that whatever is going on is happening at too low of a level for iotop to 'see' it.

> It's a good idea to use this whenever a new array is placed online:

```
sudo watch cat /proc/mdstat
```
[/quote]

```

Every 2.0s: cat /proc/mdstat                                                           Thu Mar 26 15:08:44 2009

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid5 sdb3[1] sda3[0] sdd3[3] sdc3[2]
      2883386112 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
      [================>....]  resync = 83.7% (805246176/961128704) finish=35.0min speed=74020K/sec

md0 : active raid1 sdb1[1] sda1[0] sdc1[2](S) sdd1[3](S)
      14651136 blocks [2/2] [UU]

unused devices: <none>

```

> 
I've never even thought of doing what you did... glad you are home free.

Yeah, me too!  Though I'm going down the road intentionally a second time, it's much easier knowing there's something at the end worth getting to!  :)

(Now to test various readaheads in 64-bit mode, and to fail a disk, and and and...)

---

### Post by windependence on 2009-03-26
Try to reboot your machine. Your boot records cannot be on your RAID array if you are using software RAID. With hardware RAID you can do it, but I wouldn't.

-Tim

---

### Post by kpatz on 2009-03-26
> **windependence said:**
> Try to reboot your machine. Your boot records cannot be on your RAID array if you are using software RAID. With hardware RAID you can do it, but I wouldn't.

-TimThere are ways to boot off a software RAID.  A RAID 1 should be fine to boot off anyway, since the partitions are simply mirrored.

After creating a new array, it will take a while to sync, and this will consume CPU and I/O cycles.  It runs in the background at a low priority so you shouldn't see a significant performance hit from it.  You can start using the array immediately (e.g. create a filesystem on it/copy files to it) while it's syncing.

---

### Post by TheKorn2 on 2009-03-26
> **windependence said:**
> Try to reboot your machine. Your boot records cannot be on your RAID array if you are using software RAID. With hardware RAID you can do it, but I wouldn't.

Booting off of a mirrored array works just fine.  I even yanked one of the drive's cables and was able to boot the system after acknowledging it was running in degraded mode (as intended!).

Only problem is that once it booted, it reconstructed the raid 1 boot array with the three existing drives.  That's fine, but I can't figure out how to get mdadm to re-add the last drive to the raid 1 array...

...er, nevermind.  Duuuh.

```

sudo mdadm --add /dev/md0 /dev/sda1

```

Was all that I needed.   (I must have had my arguments backwards; I *swear* I tried that before and it couldn't do it because it was busy!)


```

~$ sudo mdadm --query --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Thu Mar 26 12:16:36 2009
     Raid Level : raid1
     Array Size : 14651136 (13.97 GiB 15.00 GB)
  Used Dev Size : 14651136 (13.97 GiB 15.00 GB)
   Raid Devices : 2
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Mar 26 19:20:00 2009
          State : active
 Active Devices : 2
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 2

           UUID : 30e55caa:7b37846c:2f942441:c20bfe15
         Events : 0.71

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8       17        1      active sync   /dev/sdb1

       2       8        1        -      spare   /dev/sda1
       3       8       49        -      spare   /dev/sdd1

```

---

### Post by windependence on 2009-03-27
Just remember that this won't work with anything other than RAID 1 because the array is not set up until the machine boots with software RAID. The machine cannot boot if it can't find the disk. I prefer hardware RAID for this reason, but software RAID has it's applications also. I'm actually running a small SAN on Software RAID with FreeBSD, but I have the boot records and OS on a separate drive.

-Tim

---

### Post by TheKorn2 on 2009-03-27
> **windependence said:**
> Just remember that this won't work with anything other than RAID 1 because the array is not set up until the machine boots with software RAID. The machine cannot boot if it can't find the disk. I prefer hardware RAID for this reason, but software RAID has it's applications also. I'm actually running a small SAN on Software RAID with FreeBSD, but I have the boot records and OS on a separate drive.

My purpose for setting up RAID was to be able to keep going (with a reboot) upon a single drive failure.  If you move your boot and OS to a separate drive, you still have the situation where the failure of a single drive can cause your entire system to be unbootable.  That's not acceptable IMHO; a small raid 1 for the boot drive makes *a lot* more sense in that case.

(Though I need to change my raid 1 from active-active-spare-spare to active-active-active-active ; I don't want the system to have to re-mirror the boot partition right after a drive failure.)

---

### Post by fjgaude on 2009-03-27
Great, but do let us know of your progress toward perfection! <smile>

---

