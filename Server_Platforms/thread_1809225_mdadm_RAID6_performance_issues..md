---
title: "mdadm RAID6 performance issues."
date: 2011-07-21
forum: Server Platforms
---

### Post by Supachikn on 2011-07-21
Hi.
I am relatively new to administering a linux server, and I am having issues with an md array I have set up on a 11.04 machine. I am not really sure how to best diagnose the problem and I would appreciate any assistance offered. I seem to have slow read and write speeds to my RAID6 array. Following is the output of mdadm -D /dev/md0
My system is a C2D E6600 at 2.4GHz, and I have 2GB RAM. When viewing top, I have load averages over 3 when disk activity is high and wa% often hovers around the 96% mark but is usually around 50%
The drive consists of 7 x 1TB drives attached to the sata ports of a Promise Supertrax EX8350, with each drive in it's own JBOD array as set up by the Promise utility. I do not have access to any of the SMART information through this interface. This card is a PCI-E x4 card and it has 8 sata II ports. I am wondering if I have a configuration issue, or a hardware fault, or whether I am just expecting too much from the device. I get the impression that the actual throughput is fluctuating wildly over a period of 10-30 seconds. What other information can I view to see what my actual and expected throughput figures are/should be?

/dev/md0:
        Version : 1.2
  Creation Time : Thu Jun  9 19:06:04 2011
     Raid Level : raid6
     Array Size : 4883807040 (4657.56 GiB 5001.02 GB)
  Used Dev Size : 976761408 (931.51 GiB 1000.20 GB)
   Raid Devices : 7
  Total Devices : 7
    Persistence : Superblock is persistent

    Update Time : Thu Jul 21 23:02:29 2011
          State : active
 Active Devices : 7
Working Devices : 7
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           Name : plunder:0  (local to host plunder)
           UUID : 85ad7319:ca4fa383:18424fa4:72d549bf
         Events : 25

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       16        1      active sync   /dev/sdb
       2       8       32        2      active sync   /dev/sdc
       3       8       48        3      active sync   /dev/sdd
       4       8       64        4      active sync   /dev/sde
       5       8       80        5      active sync   /dev/sdf
       6       8       96        6      active sync   /dev/sdg

---

### Post by rubylaser on 2011-07-21
First, you could use hdparm to get a quick sample.
```
hdparm -tT /dev/md0
```
Then, I would use dd to view the read and write to the array.  Something like this to measure write speeds.
```
dd if=/dev/zero of=/<mount_point_of_array>/testfile.out bs=1M count=10000
```
Then, measure read speeds.
```
dd if=/<mount_point_of_array>/testfile.out of=/dev/null bs=1M
```

Paste the outputs of those commands back so we can see what you're looking at. Also, what do you have going on in top, that's using so much processor?  Unless mdadm is doing a consistency check, or re-syncing the array, it shouldn't use that much processor.

```
ps -eo user,pcpu,pid,command | sort -r -k2 | head -11
``` should show you your top ten CPU intensive processes.

---

### Post by Supachikn on 2011-07-21
Thanks for taking the time to reply.

I ran hdparm repeatedly over a few minutes and got varying results.

/dev/md0:
 Timing cached reads:   7598 MB in  2.00 seconds = 3802.31 MB/sec
 Timing buffered disk reads:  58 MB in  3.43 seconds =  16.91 MB/sec

/dev/md0:
 Timing cached reads:   6998 MB in  2.00 seconds = 3501.93 MB/sec
 Timing buffered disk reads:  58 MB in  3.34 seconds =  17.34 MB/sec

/dev/md0:
 Timing cached reads:   7192 MB in  2.00 seconds = 3599.00 MB/sec
 Timing buffered disk reads: 572 MB in  3.00 seconds = 190.67 MB/sec

/dev/md0:
 Timing cached reads:   6788 MB in  2.00 seconds = 3396.14 MB/sec
 Timing buffered disk reads: 582 MB in  3.00 seconds = 193.88 MB/sec

I wrote the test file and then read it back a few times and it seemed to be more consistent over a longer period of time.

[FONT="Courier New"]root@plunder:~# dd if=/dev/zero of=/raid/temp/testfile.out bs=1M count=10000
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 245.102 s, 42.8 MB/s
root@plunder:~# dd if=/raid/temp/testfile.out of=/dev/null bs=1M
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 53.7301 s, 195 MB/s
root@plunder:~# dd if=/raid/temp/testfile.out of=/dev/null bs=1M
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 52.8979 s, 198 MB/s
root@plunder:~# dd if=/raid/temp/testfile.out of=/dev/null bs=1M
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 53.3128 s, 197 MB/s
[/FONT]

Here you can see the cpu usage while writing and reading.

[FONT="Courier New"]
root@plunder:~# ps -eo user,pcpu,pid,command | sort -r -k2 | head -11
USER     %CPU   PID COMMAND
root      5.6 26409 dd if=/dev/zero of=/raid/temp/testfile.out bs=1M count=10000
root      3.4 26903 /bin/bash
root      2.5 26363 [flush-9:0]
plunder   0.9 26757 -bash
root      0.7  8961 [md0_raid6]
root      0.2 26896 sudo -s
root      0.1 26461 [kworker/0:0]
plunder   0.1 12008 watch df -h
root      0.0     9 [ksoftirqd/1]
nut       0.0   975 /sbin/upsmon
root@plunder:~# ps -eo user,pcpu,pid,command | sort -r -k2 | head -11
USER     %CPU   PID COMMAND
root      2.0 26363 [flush-9:0]
root     13.8 27068 dd if=/raid/temp/testfile.out of=/dev/null bs=1M
root      0.7  8961 [md0_raid6]
plunder   0.3 26757 -bash
root      0.2 26903 /bin/bash
plunder   0.1 12008 watch df -h
root      0.0     9 [ksoftirqd/1]
nut       0.0   975 /sbin/upsmon
root      0.0   973 /sbin/upsmon
nut       0.0   971 /sbin/upsd[/FONT]


Are these speeds reasonable for reading and writing contiguous files with no other disk activity? How can I determine speed for different usage patterns, namely reading and writing from/to different locations on the disk simultaneously? My perceived slowdowns are when transferring to and from array across the network.

---

### Post by tgalati4 on 2011-07-21
The network (and using SMB) will kill your throughput.  Spinning drives will normally put out 66-88 MB/sec, so with your RAID you are getting ~200 which is good.

---

### Post by Supachikn on 2011-07-22
Thanks for your help guys.
I guess I really had no idea what kind of speeds to expect from the array. You've given me some tools to help in the future. I appreciate it.

---

### Post by rubylaser on 2011-07-22
tgalati4 is correct in saying that using SMB can be the culprit for slow network transfers. But, your write speeds around ~43 MB/s is pretty darn slow for the hardware that you have. I have a (10) RAID6 array, but mine is hooked up to a flashed IBM m1015 card, and I see much higher results.  This is a quick sample taken just now, while my computer is unraring some archives (it's normally a bit higher than this).

```
root@fileserver:~# dd if=/dev/zero of=/storage/testfile.out bs=1M count=10000
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 59.3943 s, 176 MB/s
root@fileserver:~# dd if=/storage/testfile.out of=/dev/null bs=1M
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 28.1131 s, 373 MB/s
```

To test, you could use dd across the network to the mount point from a Linux guest, or on Windows, you could just watch the transfer speeds in the window.

---

### Post by Supachikn on 2011-07-23
I might try my luck with a different HBA in that case. I suspect the supertrak might be the culprit here.

---

