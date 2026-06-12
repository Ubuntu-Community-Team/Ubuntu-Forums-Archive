---
title: "mdadm RAID 5 headaches"
date: 2011-02-05
forum: Server Platforms
---

### Post by ashikaga on 2011-02-05
*TL;DR - I am trying to create a new mdadm RAID 5 device /dev/md0 across three disks where such an array previously existed, but whenever I do it never recovers properly and tells me that I have a faulty spare in my array. More-specific details below. Advice/help much appreciated!*

Hi all,

I recently installed Ubuntu Server 10.10 on a new box with the intent of using it as a NAS sorta-thing. I have 3 HDDs (2 TB each) and was hoping to use most of the available disk space as a RAID5 mdadm device (which gives me a bit less than 4TB.)

I configured /dev/md0 during OS installation across three partitions on the three disks - /dev/sda5, /dev/sdb5 and /dev/sdc5, which are all identical sizes. The OS, swap partition etc. are all on /dev/sda. Everything worked fine, and I was able to format the device as ext4 and mount it. Good so far.

Then I thought I should simulate a failure before I started keeping important stuff on the RAID array - no point having RAID 5 if it doesn't provide some redundancy that I actually know how to use, right? So I unplugged one of my drives, booted up, and was able to mount the device in a degraded state; test data I had put on there was still fine. Great. 

My trouble began when I plugged the third drive back in and re-booted. I re-added the removed drive to /dev/md0 and recovery began; things would look something like this:
```
user@guybrush:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdc5[3] sdb5[1] sda5[0]
      3779096448 blocks level 5, 64k chunk, algorithm 2 [3/2] [UU_]
      [>....................]  recovery =  3.3% (63301376/1889548224) finish=475.2min speed=64049K/sec
      
unused devices: <none>

user@guybrush:~$ sudo mdadm --detail /dev/md0 
/dev/md0:
        Version : 00.90
  Creation Time : Mon Jan 31 20:57:18 2011
     Raid Level : raid5
     Array Size : 3779096448 (3604.03 GiB 3869.79 GB)
  Used Dev Size : 1889548224 (1802.01 GiB 1934.90 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Jan 31 21:14:55 2011
          State : clean, degraded, recovering
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 3% complete

           UUID : 8a4693a5:ede69266:fcf6955a:9b6dcba1
         Events : 0.11

    Number   Major   Minor   RaidDevice State
       0       8        5        0      active sync   /dev/sda5
       1       8       21        1      active sync   /dev/sdb5
       3       8       37        2      spare rebuilding   /dev/sdc5

```
This looks as-expected to me. However, when I come back after several hours of rebuilding, I get this:
```
user@guybrush:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdc5[3](S) sdb5[1] sda5[4](F)
      3779096448 blocks level 5, 64k chunk, algorithm 2 [3/1] [_U_]
      
unused devices: <none>
user@guybrush:~$ sudo mdadm --detail /dev/md0 
/dev/md0:
        Version : 00.90
  Creation Time : Mon Jan 31 20:57:18 2011
     Raid Level : raid5
     Array Size : 3779096448 (3604.03 GiB 3869.79 GB)
  Used Dev Size : 1889548224 (1802.01 GiB 1934.90 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Feb  1 01:26:08 2011
          State : clean, degraded
 Active Devices : 1
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 8a4693a5:ede69266:fcf6955a:9b6dcba1
         Events : 0.24

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       21        1      active sync   /dev/sdb5
       2       0        0        2      removed

       3       8       37        -      spare   /dev/sdc5
       4       8        5        -      faulty spare   /dev/sda5
```
Not good. After a few days of messing around trying to fix this, I think to myself that I'll just start again with a new mdadm array. So I fail/remove all the drives and stop the array, and then create a new one like so:

```
user@guybrush:~$ sudo mdadm --create /dev/md0 --raid-devices=3 --level=5 /dev/sd[abc]5
mdadm: /dev/sda5 appears to contain an ext2fs file system
    size=1889548288K  mtime=Thu Jan  1 09:30:00 1970
mdadm: /dev/sda5 appears to be part of a raid array:
    level=raid5 devices=3 ctime=Thu Jan 27 21:53:02 2011
mdadm: /dev/sdb5 appears to contain an ext2fs file system
    size=1889548288K  mtime=Thu Jan  1 09:30:00 1970
mdadm: /dev/sdb5 appears to be part of a raid array:
    level=raid5 devices=3 ctime=Thu Jan 27 21:53:02 2011
mdadm: /dev/sdc5 appears to be part of a raid array:
    level=raid5 devices=3 ctime=Thu Jan 27 21:53:02 2011
Continue creating array? y
mdadm: array /dev/md0 started.
user@guybrush:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdc5[3] sdb5[1] sda5[0]
      3779096448 blocks level 5, 64k chunk, algorithm 2 [3/2] [UU_]
      [>....................]  recovery =  0.0% (70412/1889548224) finish=1341.6min speed=23470K/sec
      
unused devices: <none>
user@guybrush:~$ sudo mdadm --detail /dev/md0 
/dev/md0:
        Version : 00.90
  Creation Time : Mon Jan 31 19:13:38 2011
     Raid Level : raid5
     Array Size : 3779096448 (3604.03 GiB 3869.79 GB)
  Used Dev Size : 1889548224 (1802.01 GiB 1934.90 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Jan 31 19:13:38 2011
          State : clean, degraded, recovering
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 0% complete

           UUID : 8248ef08:045b27c6:5c2140b8:d80035c5 (local to host guybrush)
         Events : 0.2

    Number   Major   Minor   RaidDevice State
       0       8        5        0      active sync   /dev/sda5
       1       8       21        1      active sync   /dev/sdb5
       3       8       37        2      spare rebuilding   /dev/sdc5

```
And at this point, I find myself in an infinite loop - recovery seems to proceed as expected, but when it finishes it reports /dev/sda5 as a faulty spare (as in the previous pasted output) and I'm unable to start my array. 

Things I have tried:
[LIST]
[*]mdadm --zero-superblock /dev/sd[abc]5 before I try to create the array again
[*]Writing a bunch of zeroes to each partition with dd before I try to create the array again
[*]Reformatting each partition /dev/sd[abc]5 before I try to create the array again
[*]Basically every mdadm command on the man page, out of sheer frustration
[/LIST]
Of course, I've considered wiping my installation completely and starting again, but then I have no guarantee I won't wind up in the same spot again. Right now, I would really love to have a RAID device at /dev/md0 in a clean state with three active devices /dev/sd[abc]5... if you have any ideas as to how I might be able to get to this point, I'd love to hear them!

Best regards,
ashikaga.

---

### Post by rubylaser on 2011-02-05
Have you verified that the drives all pass a SMART test?  Zeroing the superblocks, and clearing out your /etc/mdadm/mdadm.conf file should set it back as if you never had a mdadm array.  Just as a test, I would stop your array, then remove each disk from the array, remove the mdadm.conf file, and zero the superblocks again.

```
mdadm --stop /dev/md0
```

```
mdadm /dev/md0 -r /dev/sda5
mdadm /dev/md0 -r /dev/sdb5
mdadm /dev/md0 -r /dev/sdc5
```

Destroy the array configuration from each disk (this will destroy all the data from your disks)
```
dd if=/dev/zero of=/dev/sda5 bs=1M count=1024
dd if=/dev/zero of=/dev/sdb5 bs=1M count=1024
dd if=/dev/zero of=/dev/sdc5 bs=1M count=1024
```

```
rm /etc/mdadm/mdadm.conf
```

That should completely remove the array, and the superblocks from the drives.

Then, just try to make a 2 disk mirror with the two of the drives. If that works, you should be able to repeat the previous process to completely remove the mirror.

Then retry to create your RAID5 array
```
mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sd[abc]5
```

Watch the build progress
```
watch cat /proc/mdstat
```

and, recreate your mdadm.conf file
Now that we have set up the array, we need to edit the mdadm configuration so it knows how to reassemble it when the system boots.

```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
echo "MAILADDR root@localhost" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

Good luck.

---

### Post by ashikaga on 2011-02-05
Thanks for the help rubylaser!

I've previously tried all those things to the letter, unfortunately, no dice. But nice to confirm that I was going down the right track anyway. I hadn't run any SMART tests though - I installed smartmontools and ran some tests/checked the logs - all looked OK.

In the end I decided to start from scratch with a clean install - my new /dev/md0 device comes up fine and re-synced successfully overnight with all three devices active. If I come up against a similar circumstance again and figure anything out, I'll post the results here for posterity. Most likely I just did something completely dumb when I was starting out - I was totally new to mdadm a few weeks ago when I started this.

One thing I'm still curious about - what do people usually do in order to test a RAID 5 configuration? Do you physically disconnect a drive (as I did), or do you just do a --fail and --re-add with mdadm?

Thanks again.

---

### Post by kevinthecomputerguy on 2011-02-05
I've seen this whole scenerio before, and the diff for me was powering off the server for a minute, and UNPLUGGING EVERYTHING, instead of just reboots.
 
Hope this helps, note +1 rubylaser, you always has top-notch md advise.

---

### Post by ashikaga on 2011-02-09
Argh... so, this is still driving me completely nuts! I tried to test my new, clean 3-device array by failing, removing and re-adding /dev/sda1, (I'm using sd[abc]1 now instead of 5 on my fresh installation), but when I re-add it, I get the same old problem. The third drive re-adds as a "spare", like so:

```

user@guybrush:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Wed Feb  9 18:30:11 2011
     Raid Level : raid5
     Array Size : 3710934912 (3539.02 GiB 3800.00 GB)
  Used Dev Size : 1855467456 (1769.51 GiB 1900.00 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Feb  9 18:30:40 2011
          State : clean, degraded, recovering
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 1% complete

           UUID : 9dcd0817:2ed979dc:81bf4dd3:6ea0a8fb
         Events : 0.4

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       3       8       33        2      spare rebuilding   /dev/sdc1
user@guybrush:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdc1[3] sdb1[1] sda1[0]
      3710934912 blocks level 5, 64k chunk, algorithm 2 [3/2] [UU_]
      [>....................]  recovery =  1.7% (32199192/1855467456) finish=384
.3min speed=79058K/sec

unused devices: <none>


```I have followed rubylaser's instructions above to the letter, re zeroing superblocks, using dd etc. before re-creating the array. I also tried creating a two-device RAID1 with just /dev/sdb1 and /dev/sdc1 as suggested - this worked fine, with both devices listed as active sync. Does anyone have any idea as to how I can re-create my RAID5 properly without having to re-install again, or as to why this might be happening? :-? If you need more details then please let me know. 

Thanks for the tip, kevinthecomputerguy - I have been powering the machine off regularly, but I tried pulling the power cable out for a while as well in-between trying to create a new array - doesn't seem to have made any difference.

---

### Post by rubylaser on 2011-02-09
For some reason, your drives are falling out of the array.  Have you looked at your logs to see if it's showing drive disconnects?  I'm thinking you either have a bad SATA cable or head on your motherboard.  Or, you're trying to use the Western Digital Green drives, and they're taking too long to respond and getting kicked out of the array.

Reinstalling isn't going to help.  mdadm writes itself to the superblock on each hard drive in the array. The benefit of this is that you can pull the array out of one system and put it into another, an bring your array right back up, because the drives contain all of the information necessary to do this.  That's why removing the config file, and zeroing the superblocks on the drives completely removes an array.

At this point, it looks to be a hardware issue more than mdadm.  It appears to be a problem with sdc (SATA cable, motherboard SATA Head, or hard drive).  That's the drive that always is showing as rebuilding.  Try putting this drive on a different head and different cable, and rebuild the array again.  This should help you diagnose the problem.

---

### Post by ashikaga on 2011-02-10
> **rubylaser said:**
> Or, you're trying to use the Western Digital Green drives, and they're taking too long to respond and getting kicked out of the array.
That's right - all the drives are WD20EARS, which I realise in hindsight was not a great choice for a RAID configuration! 

I haven't yet had time to try replacing cables or switching SATA ports around; however, as suggested in another thread, I tried disabling NCQ on all three drives and re-created the array, and this morning it seemed to have re-built successfully! All three drives came up as 'active sync'. I might try failing the other two drives and re-adding them to make sure it still works, but assuming it does, is this likely to be a reliable fix? Any significant problems with disabling NCQ? (The server is never going to be under heavy load, just for home-use.)

Thanks again. :D

```

sudo -i
echo 1 > /sys/block/sda/device/queue_depth
echo 1 > /sys/block/sdb/device/queue_depth
echo 1 > /sys/block/sdc/device/queue_depth
exit
```

---

### Post by YesWeCan on 2011-02-10
[QUOTE=ashikaga]
One thing I'm still curious about - what do people usually do in order to test a RAID 5 configuration? Do you physically disconnect a drive (as I did), or do you just do a --fail and --re-add with mdadm?[/quote]

I am interested in this. I am running a RAID10 but I am not yet sure I trust it. On the basis that testing should be as realistic as possible and as severe as possible, I am considering:
1) While stream writing data to the array, pull out the power cord
2) " pull out a sata cable
3) Use dd to corrupt a few bytes of a disk and then try reading the affected file

I had a curious experience just this evening. My desktop froze completely. It does this every few weeks and I haven't diagnosed it yet. I remotely logged in and rebooted. To my surprise, mdadm decided to declare one of my 4 raid disks to be a "spare" and began resyncing the whole thing. Why would it do this? I read the syslog and couldn't find an explanation. I couldn't find an mdadm log anywhere. Still looking for one.

---

### Post by rubylaser on 2011-02-10
> 1) While stream writing data to the array, pull out the power cord
2) pull out a sata cable
3) Use dd to corrupt a few bytes of a disk and then try reading the affected file

1. While writing data, pulling the power may lead to hitting the RAID5 write hole.  Hopefully you wouldn't fall victim to this in real life, because I hope anyone running RAID has their computer plugged into a UPS, so that the system can gracefully shutdown if power is lost.

2. These are fun tests :)  I've pulled out a SATA drive out of a running hot swap bay in the past a few times.  This works fine and is easy to recover from.

3. Never tried to dd a specific disk, but this in theory should be repaired as well.  After doing it, you'll probably want to run a consistency check afterward and see what happens.
```
echo check >> /sys/block/md0/md/sync_action
```

I think I'll try to simulate these in a virtual machine and see what happens.

---

### Post by disabledaccount on 2011-02-11
Frem end to begin:

This is critical to have write-intent bitmap configured with such big array -> rebuild can take seconds (in many cases only fraction of second) instead of hours.

Rubylaser: This array uses v90 superblock, what means that you have to erase last 128+/-64KB on the drive:
```

eraseNumKB=256
totalSec=$(fdisk -ul /dev/sdc 2>/dev/null | grep 'total' | cut -d" " -f8)
offset=$(echo "$totalSec/2-$eraseNumKB" | bc) #offset in KB
dd if=/dev/zero of=/dev/sdc bs=1K seek=$offset count=$eraseNumKB

```v0.90 superblock has one big defect: it can (and often do) confuse md auto-array-detection, especially if there is only one partition on the drive. In such case array can be assembled both as partition-based and device-based, but one of those arrays will be broken. Furthermore, mdadm -D wont show any errors. That's why superblock v1.x were designed and 1.2 (v1.02) is most safe. Of course properly configured mdadm.conf can prevent such errors (by using ARRAY mdX, devices= )

ashikaga: NCQ is known to cause problems, but untill you show SMART reports and system logs for time range when array becomes degraded it's hard to say what happened.

---

### Post by kevinthecomputerguy on 2011-02-11
Ashikaga-
 
You have my full attention :- )
 
I am also using (3) 2TB Western Digital green drives, in a RAID 5 config.
Im not having any problems yet, but that NCQ stuff is good to know (thanks)
 
I wonder if im not having problems because my /boot partition is on a USB flash drive (to overcome a GPT grub problem) I wonder if that being on USB flash drive, seperate from the array, gives the array another second or two to spin up, before its actually accessed.
 
*Side note, im pretty happy with having the /boot partition on USB flash drive. I have a dd image of it incase it ever fails, and i have had much better experiences with grub since moving /boot off the array.
 
**I also have a 4th 2tb disk, off the array, for the heavy duty stuff, so not only im i maybe getting lucky with /boot being off the array, the array doesnt do any heavy lifting.

---

### Post by ashikaga on 2011-02-12
> **tomazzi said:**
> NCQ is known to cause problems, but untill you show SMART reports and system logs for time range when array becomes degraded it's hard to say what happened.
Thanks for the help, and the clarification re. mdadm superblocks. Since I've been tinkering with this stuff, I've also upgraded mdadm (to the latest stable, 3.1.4 I think it was) and so my current device has the newer superblock format.

I'm currently gathering some logs which should be of interest, which will just take a while due to waiting for SMART tests to complete. However, I've already tried re-enabling NCQ on all drives and then forcing the array to rebuild, and I had the same problems as before. I suspect now that my re-sync attempts have actually never been finishing (I've been leaving them go overnight), and that IO errors have been consistently messing it up at some point. 

```

[ 4898.151049] md: recovery of RAID array md0
[ 4898.151058] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
[ 4898.151064] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for recovery.
[ 4898.151076] md: using 128k window, over a total of 1855465984 blocks.
[22564.458532] sd 5:0:0:0: [sdb] Unhandled error code
[22564.458541] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_TIMEOUT
[22564.458551] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 9b 03 3b 28 00 00 d8 00
[22564.458569] end_request: I/O error, dev sdb, sector 2600680232
[22564.458679] md/raid:md0: read error not correctable (sector 2600678184 on sdb1).
[22564.458689] md/raid:md0: Disk failure on sdb1, disabling device.
[22564.458692] <1>md/raid:md0: Operation continuing on 1 devices.
[22564.458884] md/raid:md0: read error not correctable (sector 2600678192 on sdb1).
[22564.458891] md/raid:md0: read error not correctable (sector 2600678200 on sdb1).
[22564.458897] md/raid:md0: read error not correctable (sector 2600678208 on sdb1).
[22564.458903] md/raid:md0: read error not correctable (sector 2600678216 on sdb1).
[22564.458910] md/raid:md0: read error not correctable (sector 2600678224 on sdb1).
[22564.458916] md/raid:md0: read error not correctable (sector 2600678232 on sdb1).
[22564.458922] md/raid:md0: read error not correctable (sector 2600678240 on sdb1).
[22564.458929] md/raid:md0: read error not correctable (sector 2600678248 on sdb1).
[22564.458935] md/raid:md0: read error not correctable (sector 2600678256 on sdb1).
[22564.458986] sd 5:0:0:0: [sdb] Unhandled error code
[22564.458990] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_TIMEOUT
[22564.458997] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 9b 03 42 30 00 00 b8 00
[22564.459013] end_request: I/O error, dev sdb, sector 2600682032
[22564.459149] sd 5:0:0:0: [sdb] Unhandled error code
[22564.459154] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_TIMEOUT
[22564.459160] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 9b 03 43 00 00 00 d8 00
[22564.459175] end_request: I/O error, dev sdb, sector 2600682240
[22564.459306] sd 5:0:0:0: [sdb] Unhandled error code
[22564.459310] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_TIMEOUT
[22564.459316] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 9b 03 43 d8 00 00 28 00
[22564.459331] end_request: I/O error, dev sdb, sector 2600682456
[22564.459440] sd 5:0:0:0: [sdb] Unhandled error code
[22564.459445] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_TIMEOUT
[22564.459451] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 9b 03 44 00 00 01 00 00
[22564.459465] end_request: I/O error, dev sdb, sector 2600682496
[22564.459600] sd 5:0:0:0: [sdb] Unhandled error code
[22564.459604] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_TIMEOUT
[22564.459610] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 9b 03 45 00 00 00 28 00
[22564.459625] end_request: I/O error, dev sdb, sector 2600682752
[22564.459733] sd 5:0:0:0: [sdb] Unhandled error code
[22564.459737] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_TIMEOUT
[22564.459743] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 9b 03 45 28 00 00 d8 00
[22564.459758] end_request: I/O error, dev sdb, sector 2600682792
[22564.459891] sd 5:0:0:0: [sdb] Unhandled error code
[22564.459895] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_TIMEOUT
[22564.459902] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 9b 03 46 00 00 01 00 00
[22564.459916] end_request: I/O error, dev sdb, sector 2600683008
[22564.460070] sd 5:0:0:0: [sdb] Unhandled error code
[22564.460074] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_TIMEOUT
[22564.460080] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 9b 03 47 00 00 00 30 00
[22564.460095] end_request: I/O error, dev sdb, sector 2600683264
[22564.460222] sd 5:0:0:0: [sdb] Unhandled error code
[22564.460226] sd 5:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_TIMEOUT
[22564.460233] sd 5:0:0:0: [sdb] CDB: Read(10): 28 00 9b 03 47 30 00 00 20 00
[22564.460248] end_request: I/O error, dev sdb, sector 2600683312
[22564.910252] md: md0: recovery done.
[22564.957789] RAID conf printout:
[22564.957799]  --- level:5 rd:3 wd:1
[22564.957805]  disk 0, o:1, dev:sda1
[22564.957811]  disk 1, o:0, dev:sdb1
[22564.957815]  disk 2, o:1, dev:sdc1
[22565.040946] RAID conf printout:
[22565.040954]  --- level:5 rd:3 wd:1
[22565.040961]  disk 0, o:1, dev:sda1
[22565.040965]  disk 1, o:0, dev:sdb1
[22565.040977] RAID conf printout:
[22565.040981]  --- level:5 rd:3 wd:1
[22565.040985]  disk 0, o:1, dev:sda1
[22565.040989]  disk 1, o:0, dev:sdb1
[22565.120945] RAID conf printout:
[22565.120953]  --- level:5 rd:3 wd:1
[22565.120959]  disk 0, o:1, dev:sda1

```Once the SMART tests are finished, I'll disable NCQ again and try to resync the array and post back with my findings.

---

### Post by ashikaga on 2011-02-12
Result of SMART tests on all three drives (just posted once - results identical for all three drives):

```


user@guybrush:~$ sudo smartctl -l selftest /dev/sda
smartctl 5.40 2010-03-16 r3077 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%       344         -

```

SMART info on all three disks:

/dev/sda
```


user@guybrush:~$ sudo smartctl -a /dev/sda
smartctl 5.40 2010-03-16 r3077 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD20EARS-00MVWB0
Serial Number:    WD-WMAZA1679191
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Feb 13 08:06:26 2011 CST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (36780) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 255) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x3035)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   253   253   021    Pre-fail  Always       -       966
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       42
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       353
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       40
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       16
193 Load_Cycle_Count        0x0032   199   199   000    Old_age   Always       -       4770
194 Temperature_Celsius     0x0022   116   106   000    Old_age   Always       -       34
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       8

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%       344         -
# 2  Short offline       Completed without error       00%       275         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

/dev/sdb
```

user@guybrush:~$ sudo smartctl -a /dev/sdb
smartctl 5.40 2010-03-16 r3077 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD20EARS-00MVWB0
Serial Number:    WD-WMAZA1624914
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Feb 13 08:07:52 2011 CST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (37500) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 255) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x3035)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   253   253   021    Pre-fail  Always       -       1016
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       42
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       353
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       40
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       16
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       511
194 Temperature_Celsius     0x0022   116   105   000    Old_age   Always       -       34
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       15

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%       344         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

/dev/sdc
```

user@guybrush:~$ sudo smartctl -a /dev/sdc
smartctl 5.40 2010-03-16 r3077 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD20EARS-00MVWB0
Serial Number:    WD-WMAZA1825456
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Feb 13 08:09:09 2011 CST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (37260) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 255) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x3035)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   199   199   051    Pre-fail  Always       -       63
  3 Spin_Up_Time            0x0027   253   253   021    Pre-fail  Always       -       1108
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       36
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       353
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       35
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       12
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       349
194 Temperature_Celsius     0x0022   117   106   000    Old_age   Always       -       33
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%       344         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

I'll now disable NCQ again and try to re-create the array. If that works then I'm pretty confident that NCQ and possibly other power-saving features of the WD Green drives are the culprit. Although, if anyone else disagrees with this diagnosis I'm keen to hear it! :)

---

### Post by ashikaga on 2011-02-12
syslog and mdadm -D output after array re-creation and recovery with NCQ turned off again:

```

[81812.472627] md: bind<sda1>
[81812.472836] md: bind<sdb1>
[81812.484139] md: bind<sdc1>
[81812.487898] md/raid:md0: device sdb1 operational as raid disk 1
[81812.487907] md/raid:md0: device sda1 operational as raid disk 0
[81812.488772] md/raid:md0: allocated 3230kB
[81812.488842] md/raid:md0: raid level 5 active with 2 out of 3 devices, algorit
hm 2
[81812.488971] RAID conf printout:
[81812.488976]  --- level:5 rd:3 wd:2
[81812.488981]  disk 0, o:1, dev:sda1
[81812.488985]  disk 1, o:1, dev:sdb1
[81812.489037] md0: detected capacity change from 0 to 3799994335232
[81812.489360] RAID conf printout:
[81812.489365]  --- level:5 rd:3 wd:2
[81812.489370]  disk 0, o:1, dev:sda1
[81812.489374]  disk 1, o:1, dev:sdb1
[81812.489379]  disk 2, o:1, dev:sdc1
[81812.489493] md: recovery of RAID array md0
[81812.489498] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
[81812.489503] md: using maximum available idle IO bandwidth (but not more than
200000 KB/sec) for recovery.
[81812.489515] md: using 128k window, over a total of 1855465984 blocks.
[81812.490664] md0: detected capacity change from 0 to 3799994335232
[81812.490689]  md0: unknown partition table
[102981.961162] md: md0: recovery done.
[102982.046770] RAID conf printout:
[102982.046780]  --- level:5 rd:3 wd:3
[102982.046787]  disk 0, o:1, dev:sda1
[102982.046793]  disk 1, o:1, dev:sdb1
[102982.046797]  disk 2, o:1, dev:sdc1
user@guybrush:~$ sudo mdadm -D /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Sun Feb 13 08:41:38 2011
     Raid Level : raid5
     Array Size : 3710931968 (3539.02 GiB 3799.99 GB)
  Used Dev Size : 1855465984 (1769.51 GiB 1900.00 GB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Sun Feb 13 14:34:29 2011
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : guybrush:0  (local to host guybrush)
           UUID : 200e9d9c:306144f2:b3c96404:87e125d7
         Events : 22

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       3       8       33        2      active sync   /dev/sdc1
```So I guess I'll now mark the thread as solved, as my original issue (couldn't successfully fail and rebuild the array) seems to be consistently fixed by disabling NCQ on all drives. 

In summary, my experience serves as a(nother) case study that WD Green drives should probably be avoided where possible in mdadm RAID applications. I'm email-subscribed to the thread still, so if anyone has any other questions or wants me to try anything else, feel free to post. 

Thanks kindly to all who helped me out.

---

### Post by YesWeCan on 2011-02-13
> **ashikaga said:**
> In summary, my experience serves as a(nother) case study that WD Green drives should probably be avoided where possible in mdadm RAID applications. I'm email-subscribed to the thread still, so if anyone has any other questions or wants me to try anything else, feel free to post. 

Thanks kindly to all who helped me out.
Not very satisfactory, though. It seems to me Native Command Queuing helps to reduce drive wear and this is something you want if you are using a RAID. Do you think this problem is a due to incorrect implementation of NCQ by WD or do you think it is a undesirable limitation of mdadm?

---

### Post by ashikaga on 2011-02-13
> **YesWeCan said:**
> Not very satisfactory, though. It seems to me Native Command Queuing helps to reduce drive wear and this is something you want if you are using a RAID.
I am no expert in these things, but from what I've read concerning NCQ and RAID, I don't think it really matters in my scenario (i.e. a file storage server on a home network which will only be used by one or maybe two users at a time.) Most people on the forums seem to recommend turning NCQ off in RAID applications, e.g. [here.]("http://ubuntuforums.org/showthread.php?t=1494846") 

> Do you think this problem is a due to incorrect implementation of NCQ by WD or do you think it is a undesirable limitation of mdadm?
I don't presume to know enough about WD drives or mdadm's implementation to be able to answer that. I don't really see how I could place any blame at the feet of mdadm - if the Linux SCSI driver reports that /dev/sdx has several read timeouts (as shown in my earlier logs above), then it makes sense for mdadm to drop the drive out of the array. In fact, I don't really think I can blame any individual component of my system - I think it's really just a case of me trying to use hardware that isn't fit for my intended usage.

Ultimately, the best "fix" and lesson-learned here is to stay well away from so-called "power-saving" drives for Linux software RAID. Some other users have reported using the same drives without a hassle, but if you're starting a system from scratch and can choose what hardware to use, then I wouldn't personally take the risk. If I had just done a bit more research about what I was doing before I went ahead bought my gear, then I wouldn't have got the same drives - you live and learn. :)

---

### Post by disabledaccount on 2011-02-15
ashikaga: unfortunatelly logs and and SMART reports don't provide clear answer, but they do show couple of interesting things:

1. Power problems.
All Your drives reporting Power-off-retract count of 12, 16, what means:
 - You have forced power-off because hardware/os hungs (but one of the drives was connected later so it has counted less P-O-R events)
- You have broken/overloaded/low-quality PSU or unstable power grid voltage - and this can explain all strange phenomenons

2. Two of your disks have Multi-Zone read errors. This is not critical usually, but those disks have also bigger P-O-R, what can be considered as confirmation of power problems.

3. I'm guessing that sdc was sdb at the time when your array was degraded -> it has Raw_Read_Error_Rate of 63 -> there were real read problems that could lead to big I/O delays and dropping device from array.
But, if we take into account possible power problems, then other scenario is also possible: SATA controller errors/unstable behaviour.

Watch SMART reports in regular periods, as your drives are not in perfect condition - any change should warn you, but also can give more precise info about what is going  on. SMART is most valuable when You can tell what have changed, so its good idea to save current reports.

---

### Post by ashikaga on 2011-02-15
Thanks for the help tomazzi!

I checked the SMART logs again just now, and the metrics you mentioned are all stable (i.e. same values as the logs above), but I'll keep an eye on them. It's certainly feasible that the power-off count is due to a lot of (highly unsuccessful) messing around I did with FreeNAS early on.

For posterity's/interest's sake, my PSU is a stock 350W one from the [Antec NSK1380]("http://www.antec.com/pdf/flyers/NSK1380_flyer_EC.pdf") ([COLOR=DarkRed]PDF warning[/COLOR] on that link!) and mobo is the [ASUS M4A88TD-M.]("http://www.asus.com/product.aspx?P_ID=dCFJVtaiZVk1PJCL") Drives are all WD20EARS as previously mentioned.

Thanks again. :)

---

### Post by BakCompat on 2011-03-21
ashikaga, just curious about your usage of WD20EARS drives... have you disabled the 8 second head park on them using the WDIDLE3 utility? Default of 8 seconds might be fine as a standalone drive for data, but in a RAID array, many people with these drives recommend setting it to at least 2 minutes to prevent high Load Cycle Count (LCC value in SMART) values from accruing. As the drive is listed as having a 300,000 LCC warranted value for it's 3 year warranty period, the people who discovered this info last year were pretty surprised to see LCC values from 100,000 to 200,000 inside their first year.

I've had a RAID1 array set with the WDIDLE value "disabled" - actually set to 5 minutes I think - and I never had these sort of issues in 3 months of running. Granted, it's RAID1, not RAID5. I've ordered a couple more drives and am going to change that box around somehow.. haven't decided exactly how yet.. maybe raid5 with a backup disk or something else..

I have not used any hdparm modifications and have not changed anything regarding NCQ.

---

