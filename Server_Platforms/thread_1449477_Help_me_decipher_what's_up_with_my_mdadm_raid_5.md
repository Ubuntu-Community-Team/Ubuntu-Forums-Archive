---
title: "Help me decipher what's up with my mdadm raid 5"
date: 2010-04-07
forum: Server Platforms
---

### Post by zackiv31 on 2010-04-07
My 4 disk mdadm raid5 kicked out some disks and I can't remount it.  I'm hoping someone can help me rebuild the thing without losing my data.

```

me@me:~$ sudo mount /dev/md0 
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

```

me@me:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sda1[0](S) sdc1[4](S) sdb1[1](S) sdd1[3](S)
      2930287616 blocks
       
unused devices: <none>

```

```

me@me:~$ sudo mdadm --examine /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : d2c23e07:3fe5324d:c0db825b:3b9df22e
  Creation Time : Sat Nov  7 12:47:02 2009
     Raid Level : raid5
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
     Array Size : 2197715712 (2095.91 GiB 2250.46 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon Apr  5 20:43:42 2010
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 7acaed53 - correct
         Events : 1158263

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       8       49        3      active sync   /dev/sdd1
   4     4       8       33        4      spare   /dev/sdc1

```

```

me@me:~$ sudo mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : d2c23e07:3fe5324d:c0db825b:3b9df22e
  Creation Time : Sat Nov  7 12:47:02 2009
     Raid Level : raid5
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
     Array Size : 2197715712 (2095.91 GiB 2250.46 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Wed Apr  7 21:13:17 2010
          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 7acd977d - correct
         Events : 1158278

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       0        0        0      removed
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       8       49        3      active sync   /dev/sdd1
   4     4       8       33        4      spare   /dev/sdc1

```

```

me@me:~$ sudo mdadm --examine /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : d2c23e07:3fe5324d:c0db825b:3b9df22e
  Creation Time : Sat Nov  7 12:47:02 2009
     Raid Level : raid5
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
     Array Size : 2197715712 (2095.91 GiB 2250.46 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Wed Apr  7 21:13:17 2010
          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 7acd978d - correct
         Events : 1158278

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8       33        4      spare   /dev/sdc1

   0     0       0        0        0      removed
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       8       49        3      active sync   /dev/sdd1
   4     4       8       33        4      spare   /dev/sdc1

```

```

zivester@zives:~$ sudo mdadm --examine /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : d2c23e07:3fe5324d:c0db825b:3b9df22e
  Creation Time : Sat Nov  7 12:47:02 2009
     Raid Level : raid5
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
     Array Size : 2197715712 (2095.91 GiB 2250.46 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Wed Apr  7 21:13:17 2010
          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 7acd97a1 - correct
         Events : 1158278

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       49        3      active sync   /dev/sdd1

   0     0       0        0        0      removed
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       8       49        3      active sync   /dev/sdd1
   4     4       8       33        4      spare   /dev/sdc1

```

If there's anything else that would help please let me know!

---

### Post by samborambo on 2010-04-08
It looks like something changed after you examined /dev/sda1. sdc1 seems to have been replaced with a clean drive, correct? sda1 has also been administratively removed from the array. In RAID 5 you need a minimum of N-1 drives active in order to rebuild the remaining drive. In your case you need 3 drives "active sync".

Try:

```

mdadm --re-add /dev/sda1
mdadm --examine /dev/sda1
(assuming "active sync" on sda1)...
mdadm --run /dev/md0

```

With the three active drives and one hot spare, the array should start running. In the background it will start rebuilding /dev/sdc1 while online.

---

### Post by zackiv31 on 2010-04-08
Sorry I should have said this... none of the drives have been replaced or touched... Came home... the RAID wasn't active, restarted and this is what I'm left with... Do you still recommend the same steps?

I feel like it got all confused and now doesn't know what's what (a superblock issue?)  I'm sure the drives are fine, I just want it to rebuild itself correctly. (At least thats the first thing I want to try)

---

### Post by zackiv31 on 2010-04-10
I still haven't made any progress on this... any mdadm experts out there?

---

### Post by beers on 2010-04-12
sudo mdadm --stop /dev/md0
sudo mdadm --assemble --force /dev/md1 /dev/sd[abcd]1

See if it comes online then.
I've been having the same issues with mine.

New patch/updates changed drive letters and gave mdadm fits.
Adding the new change forced it as a spare *sigh*
the force option seems to assign drives to "active sync" instead.

---

### Post by zackiv31 on 2010-04-12
Your response gave me hope, but no luck:

```

me@me:~$ sudo mdadm --stop /dev/md0
mdadm: stopped /dev/md0
me@me:~$ sudo mdadm --assemble --force /dev/sd[abcd]1
mdadm: /dev/sda1 assembled from 2 drives and 1 spare - not enough to start the array.

```

Any other ideas?

---

### Post by beers on 2010-04-12
Once the spare is finished building, it should be added to your array.

sudo mdadm --detail /dev/md0

---

### Post by zackiv31 on 2010-04-12
I feel like something changed...

```

Every 2.0s: cat /proc/mdstat                                            Mon Apr 12 22:28:08 2010

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md127 : inactive sdb1[1](S) sdc1[4](S) sdd1[3](S)
      2197715712 blocks

unused devices: <none>

```

---

### Post by zackiv31 on 2010-04-12
On reboot I get this

```

Every 2.0s: cat /proc/mdstat                            Mon Apr 12 22:33:00 2010

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sda1[0](S) sdb1[1](S) sdd1[3](S) sdc1[4](S)
      2930287616 blocks

unused devices: <none>

```

```

me@me:~$ sudo mdadm --detail /dev/md0 
mdadm: md device /dev/md0 does not appear to be active.

```

---

### Post by zackiv31 on 2010-04-12
This magic page helped me out: [http://www.linuxquestions.org/questions/linux-general-1/raid5-with-mdadm-does-not-ron-or-rebuild-505361/](http://www.linuxquestions.org/questions/linux-general-1/raid5-with-mdadm-does-not-ron-or-rebuild-505361/)

Not really knowing what this did, but making sure that only one of my drives was unlike the other:
```

sudo mdadm -E /dev/sd[a-d]1 | grep Event
         Events : 1158263
         Events : 1158278
         Events : 1158278
         Events : 1158278

```

Ok... so one drive is outta wack... raid 5 can handle that.  So I jumped back to the -scan option:

```

me@me:~$ sudo mdadm --assemble --force --scan /dev/md0
mdadm: forcing event count in /dev/sda1(0) from 1158263 upto 1158278
mdadm: /dev/md0 has been started with 3 drives (out of 4) and 1 spare.

```

and....!!!....

```

me@me:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sda1[0] sdc1[4] sdd1[3] sdb1[1]
      2197715712 blocks level 5, 64k chunk, algorithm 2 [4/3] [UU_U]
      [>....................]  recovery =  0.5% (4089600/732571904) finish=480.1min speed=25286K/sec
      
unused devices: <none>

```


I think it's working?!

---

### Post by Cracauer on 2010-04-12
> **zackiv31 said:**
> Your response gave me hope, but no luck:

```

me@me:~$ sudo mdadm --stop /dev/md0
mdadm: stopped /dev/md0
me@me:~$ sudo mdadm --assemble --force /dev/sd[abcd]1
mdadm: /dev/sda1 assembled from 2 drives and 1 spare - not enough to start the array.

```

Any other ideas?

That command is a mistake to give here. You should have said
```

mdadm --assemble --force /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1

```

Because almost certainly your pre-reboot problem was that /dev/sda wasn't where is was supposed to be, probably on some random other /dev/sd[e-z].

If you haven't use shell globbing then you would have gotten a clean error message, such as "/dev/sda1: no such file or directory" instead of the shell just silently giving three filenames where you expected four.

The rebuild looks good. Let's hope you don't have another drive die from the resync stress.

---

### Post by zackiv31 on 2010-04-13
This just doesn't look right...  ughhh

```

me@me:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sda1[4](F) sdc1[5](S) sdd1[3] sdb1[1]
      2197715712 blocks level 5, 64k chunk, algorithm 2 [4/2] [_U_U]
      
unused devices: <none>

```

```

zivester@zives:~$ sudo mdadm --detail /dev/md0 
[sudo] password for zivester: 
/dev/md0:
        Version : 00.90
  Creation Time : Sat Nov  7 12:47:02 2009
     Raid Level : raid5
     Array Size : 2197715712 (2095.91 GiB 2250.46 GB)
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

[B]    Update Time : Tue Apr 13 06:44:01 2010
          State : clean, degraded
 Active Devices : 2
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 1[/B]

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : d2c23e07:3fe5324d:c0db825b:3b9df22e
         Events : 0.1158302

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       17        1      active sync   /dev/sdb1
       2       0        0        2      removed
       3       8       49        3      active sync   /dev/sdd1

       4       8        1        -      faulty spare   /dev/sda1
       5       8       33        -      spare   /dev/sdc1

```

```

me@me:~$ sudo mdadm -E /dev/sd[a-d]1 | grep Events
         Events : 1158299
         Events : 1158304
         Events : 1158304
         Events : 1158304

```

For the record, sd[abcd] are all still my raid drives.

---

### Post by zackiv31 on 2010-04-15
Spare, Fauly Spare... what's going on?

So I think sda is a failed drive... but I can get it back online for a long enough time to copy off some files... just not all.

sdc says it's a spare... hmm... but that was the drive that was just rebuilding... or so I thought.

```

me@me:~$ sudo mdadm -E /dev/sd[a-d]1 | grep E
         Events : 1159768
         Events : 1159781
         Events : 1159781
         Events : 1159781

```

Is it possible for me to put this array back together with b,c,d and replace the a drive later?  How do I tell which drives in my array are clean and which ones are lagging behind?

---

### Post by Cracauer on 2010-04-15
I don't get how your formally 4-disk raid5 can even come up with 2 disks. Any ideas? I must overlook something.

---

### Post by zackiv31 on 2010-04-15
It has never come up with 2 disks... but I think it might have come up twice with different sets of disks....

All I want is to get this thing up and running... is there someone I can pay to help me on this?  I've been outta commission for over a week now and I need to get this up and running, even if it's only with 3 disks.

---

### Post by zackiv31 on 2010-04-16
I tried a rebuild again, but the system froze around 2:10am, recovery was at 55.9%.

Here are some messages from the kernel log:

```

Apr 16 01:48:41 zives kernel: [15651.012538] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x280000 action 0x6 frozen
Apr 16 01:48:41 zives kernel: [15651.012544] ata3: SError: { 10B8B BadCRC }
Apr 16 01:48:41 zives kernel: [15651.012551] ata3.00: cmd 35/00:00:3f:2e:d1/00:01:2c:00:00/e0 tag 0 dma 131072 out
Apr 16 01:48:41 zives kernel: [15651.012552]          res 40/00:00:f6:52:54/00:00:00:00:00/f0 Emask 0x4 (timeout)
Apr 16 01:48:41 zives kernel: [15651.012555] ata3.00: status: { DRDY }
Apr 16 01:48:41 zives kernel: [15651.012561] ata3: hard resetting link
Apr 16 01:48:41 zives kernel: [15651.362533] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Apr 16 01:48:41 zives kernel: [15651.652240] ata3.00: configured for UDMA/100
Apr 16 01:48:41 zives kernel: [15651.652250] ata3: EH complete

```


Here is the last cat /proc/mdstat before the system haulted:
```

Fri Apr 16 02:12:24 2010
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 

md0 : active raid5 sda1[0] sdc1[4] sdd1[3] sdb1[1]

      2197715712 blocks level 5, 64k chunk, algorithm 2 [4/3] [UU_U]

      [===========>.........]  recovery = 55.9% (409843456/732571904) finish=209.9min speed=25620K/sec

      

unused devices: <none>

```


And here is what the system is doing on hard reset:
```

me@me:~$ cat /proc/mdstat 
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10] 
md1 : active raid5 sdc1[4] sda1[0] sdb1[1] sdd1[3]
      2197715712 blocks level 5, 64k chunk, algorithm 2 [4/3] [UU_U]
      [=>...................]  recovery =  5.2% (38139136/732571904) finish=446.5min speed=25915K/sec
      
unused devices: <none>

```


This is never going to end at this rate, I'm sure when I come home it'll be frozen again... ughhhhhh

---

### Post by Cracauer on 2010-04-16
That disk is dead, that's all.

---

### Post by zackiv31 on 2010-04-18
Which disk?  How to I get it to build in degraded mode so I can copy off of it?

---

