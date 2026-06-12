---
title: "SoftRAID 5 complains bout drive. Drive tests fine."
date: 2011-11-08
forum: Server Platforms
---

### Post by Demented ZA on 2011-11-08
Hi, 

I have 3 WD Caviar Black 2 TB drives in a degraded Raid 5 volume. Bout three days ago /dev/sdc failed. I disconnected the drive and plugged it into a PC used for testing and used the Western digital data lifeguard diagnostics do do a short and long test, and it didn't find any faults.

I thought that the drive cable might just have come loose, so I plugged it back in, using a different sata port and cable just to be sure. It took about a day to resync with the array, and afterwards it says the array is clean, but I still get mails from the server that read:
```


_**Subject:DegradedArray event on /dev/md0:server**_
This is an automatically generated mail message from mdadm running on server. 

A DegradedArray event had been detected on md device /dev/md0.  

Faithfully yours, etc.  

P.S. The /proc/mdstat file currently contains the following:  

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] 
[raid4] [raid10]  md0 : active raid5 sda2[1] sdb2[0] sdc2[3](F)       
3883364224 blocks level 5, 64k chunk, algorithm 2 [3/2] [UU_]        
unused devices: <none>
```Am i wrong to assume that /dev/sdc2 is faulty? Or could it be something else? If the drive is faulty, I'd like some conclusive proof so that I can RMA the drive. It'll be difficult otherwise with the recent flooding of the WD factory and the fact that HDDs are suddenly so much more scarce.

---

### Post by rubylaser on 2011-11-08
Based off that email it looks like sdc2 has been removed from the array.  What's the output of
```
cat /proc/mdstat
```
and
```
mdadm -E /dev/sd[abc]2
```
also...
```
smartctl -a /dev/sdc
```

---

### Post by Demented ZA on 2011-11-08
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [ra
id10]
md0 : active raid5 sda2[1] sdb2[0] sdc2[3](F)
      3883364224 blocks level 5, 64k chunk, algorithm 2 [3/2] [UU_]

unused devices: <none>
```

mdadm -E /dev/sd[abc]2
```

/dev/sda2:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : e13cdce3:c5383107:a3425302:c7f2ca6f
  Creation Time : Sun Apr 24 00:06:36 2011
     Raid Level : raid5
  Used Dev Size : 1941682112 (1851.73 GiB 1988.28 GB)
     Array Size : 3883364224 (3703.46 GiB 3976.56 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Tue Nov  8 21:37:49 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : cb08fe5d - correct
         Events : 326765

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8        2        1      active sync   /dev/sda2

   0     0       8       18        0      active sync   /dev/sdb2
   1     1       8        2        1      active sync   /dev/sda2
   2     2       0        0        2      faulty removed
/dev/sdb2:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : e13cdce3:c5383107:a3425302:c7f2ca6f
  Creation Time : Sun Apr 24 00:06:36 2011
     Raid Level : raid5
  Used Dev Size : 1941682112 (1851.73 GiB 1988.28 GB)
     Array Size : 3883364224 (3703.46 GiB 3976.56 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Tue Nov  8 21:37:49 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : cb08fe6b - correct
         Events : 326765

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       18        0      active sync   /dev/sdb2

   0     0       8       18        0      active sync   /dev/sdb2
   1     1       8        2        1      active sync   /dev/sda2
   2     2       0        0        2      faulty removed

```

smartctl -a /dev/sdc
```

smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.0.0-12-server] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

Smartctl open device: /dev/sdc failed: No such device

```

Since the above showed a "no such device", I also did
fdisk -l

```

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn
't support GPT. Use GNU Parted.


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  3907029167  1953514583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn
't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  3907029167  1953514583+  ee  GPT

Disk /dev/md0: 3976.6 GB, 3976564965376 bytes
2 heads, 4 sectors/track, 970841056 cylinders, total 7766728448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

```

:-k So ya, /dev/sdc is not showing up. Everytime I've gotten this message, the disk was still showing up. This is the first time its missing.

I suppose its entirely possible that I tested the wrong drive and thats why it didn't show as faulty.

I listed the drives  and their serial numbers with
```
hdparm -i /dev/sd[abc]
```

Only devices hda and hdb showed up. So the missing serial is the faulty drive. I'm testing it now. Will report back with my find.

---

### Post by rubylaser on 2011-11-08
Certainly looks like a failed drive or at a minimum a bad SATA cable.

---

### Post by Demented ZA on 2011-11-09
> **rubylaser said:**
> Certainly looks like a failed drive or at a minimum a bad SATA cable.

I think you might be quite right.

Following are my test results:
[ATTACH]206755[/ATTACH]


Performance looks good. (Running on a pentium 4 lol)

[ATTACH]206756[/ATTACH]

This is where things get a little curious. Look at the Ultra DMA CRC Error Count, and the WriteError rate. 72 and 32 respectively. 

HDD Scan:
[ATTACH]206760[/ATTACH]


Again, notice the Ultradma CRC Errors gets flagged here. Hex 48 = 72 Dec, 20 Hex = 32 Dec with the write error rate which doesn't get flagged.

All other tests such as surface tests and SMART on the P4 system tests fine. Note I'm using a different cable on this system, as the drive is connected externally via e-sata. Also thats why the temperature is so high, I had no cooling on it here.

So basically the drive doesn't show any faults in another system. Ergo, the problem probably isn't with the drive.

I replaced my cable again, and used an entirely new sata port this time. The array is rebuilding now and will probably take about a day to complete.

What is funny, is that the WD data lifeguard suite doesn't show any CRC or write errors. In fact, I'm not sure what its showing really. Have a look:
[ATTACH]206759[/ATTACH]

Just goes to show, not to use just a single test. Initially I used only the WD tools. Had I had the information I have now, I'd have seen the bigger picture and solved the problem first time around.

On a side note, the first time I put the drive back, I said I replaced the cable, but I might not have. They are all the same colour (orange), and I think I might have mistakenly put the same cable back. So to be sure, I opened a brand new black cable to be sure.

I'll post back in a day or so to report my finds. I'm confident the problem should be solved now, or that I'm at least homing in on the root cause. But I doubt its the drive itself.

Thanks for your help!!

---

### Post by Demented ZA on 2011-11-11
Meh, after all the above trouble a couple of days later:

```

cat /proc/mdstat 

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [ra
id10]
md0 : active raid5 sdc2[3](F) sda2[1] sdb2[0]
      3883364224 blocks level 5, 64k chunk, algorithm 2 [3/2] [UU_]

unused devices: <none>


```

This has got to be the drive doesn't it?

I'm gonna take the drive out and use it in my PC for a while and see what happens. It seems the drive dies after a while.

Any advice?

---

### Post by rubylaser on 2011-11-11
Does anything show up in dmesg?  It looks like a problem with the drive or the SATA port on the motherboard if you've tried a new cable.

---

### Post by Demented ZA on 2011-11-13
> **rubylaser said:**
> Does anything show up in dmesg?  It looks like a problem with the drive or the SATA port on the motherboard if you've tried a new cable.

Yes, I replaced the sata cable and connected to adifferent port on the Motherboard (same controller though).  /dev/sda and sdb are on a different controller than /dev/sdc. Could be significant.

This is what I can find in dmesg. There might be more, but not sure what  to search for. Dmesg contains a lot of other stuff like traffic etc.
 ```

 $ sudo cat /var/log/dmesg | grep md0
 [    2.804443] md/raid:md0: device sda2 operational as raid disk 0
 [    2.804446] md/raid:md0: device sdb2 operational as raid disk 1
 [    2.804814] md/raid:md0: allocated 3230kB
 [    2.804966] md/raid:md0: raid level 5 active with 2 out of 3 devices, algorithm 2
 [    2.805066] md0: detected capacity change from 0 to 3976564965376
 [    2.806541]  md0: unknown partition table
 [    3.040040] EXT4-fs (md0): INFO: recovery required on readonly filesystem
 [    3.040043] EXT4-fs (md0): write access will be enabled during recovery
 [    4.455530] EXT4-fs (md0): recovery complete
 [    4.458776] EXT4-fs (md0): mounted filesystem with ordered data mode. Opts: (null)
 [    9.423066] EXT4-fs (md0): re-mounted. Opts: errors=remount-ro
 
```
 
Also, not quite sure how to read the timestamps.

Well I did recall having an IRQ error being printed to the terminal  roughly around the same time. Been recieving it ever since the upgrade  to 11.10. Can't find it now though. Its probably in one of my archived  logs.

---

### Post by Demented ZA on 2011-11-13
I replaced the board of the server on Friday as I'm upgrading from an i5 to an i7. 

Not the ideal time to be doing this because I havn't solved the RAID problem, I know, but this was the only time I had put aside to do it.

I was hoping that it could at least help with the RAID problem by eliminating the Sata controler.

This mourning (Sunday) when I cot to my PC, I got another email from the server (with the new board and only /dev/sda and adb connected since Friday afternoon):
```


Subject:DegradedArray event on /dev/md0:server

This is an automatically generated mail message from mdadm
running on server

A DegradedArray event had been detected on md device /dev/md0.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sda2[0] sdb2[1]
      3883364224 blocks level 5, 64k chunk, algorithm 2 [3/2] [UU_]
      
unused devices: <none>


```
I recieved the above message Sunday mourning 6:59 am, and two others like it on Saturday mourning, one at 6:40 am, the other at 11:35 am.

Is mdadm just letting me know its missing /dev/sdc, or did another problem occur with the RAID array containing /dev/sda /dev/sdb allone? How do I check?

---

### Post by Demented ZA on 2011-11-13
I just had /dev/sdc disconnect itself from my PC while running a HD Tune bechmark on it. When I plugged it out and back in to the other port, the UDMA CRC count has increased by 1. I'm gonna keep running tests on it to see if it re-occurs. If it is the drive, this is still not enough to get an RMA. Our suppliers will just briefly test it and say "no fault found" :-(

Edit: Plugging the drive back into the same port where it failed during benchmark, the drive won't pick up till I restart the PC. Not using the same cable here. Have an e-sata bay in the front of my PC. Just slot the drive in.

Edit: I've learned a few things about the controller in this PC and how to prevent the above. Bottom line: above mentioned problems have nothing to do with the problems I'm experiencing on my server. I'm keeping a close eye on it though.

---

### Post by Demented ZA on 2011-12-05
Its been three weeks since the last post. After posting that last message, I completely re-installed my server with Ubuntu 11.04 (since 11.10 was where I started picking up problems). I Still havn't replaced any drives. 

Since re-installing Ubuntu, I havn't had a stitch of problems. Can 11.10 really be the problem? For now I'm hessitant to upgrade. One day when I have time, I'll make a complete backup and then maybe risk it, hopefully when 11.10 is more mature, or 12.04 is out.

---

### Post by rubylaser on 2011-12-05
I still run 10.04 on my server just because it's the LTS and very stable.  Unless there's some pressing reason, I'd suggest sticking with the LTS releases.

---

### Post by Demented ZA on 2011-12-05
> **rubylaser said:**
> I still run 10.04 on my server just because it's the LTS and very stable.  Unless there's some pressing reason, I'd suggest sticking with the LTS releases.

Good advice thanks!

---

