---
title: "Extremely slow hard drive (backing up)"
date: 2015-03-15
forum: Server Platforms
---

### Post by ian77 on 2015-03-15
I'm experiencing an unbelievably slow transfer rate to a new hard drive I've just installed in my home server.
The drive is being used as a place to backup all my data.

By my calculations the drive to being written to at around 6MB/s.

**Backup Store**
Single hard drive mounted at /backup
/dev/sde
4TB
WD40EZRX
Write speed 150MB/s
ext4 file system

When I created the 4TB partition with parted, I made sure the partition was no misaligned. I used the --optimal option.
Partitioning all looks fine.

**Data Store**
4 disk raid 5 array.
/dev/md2
btrfs filesystem
Mounted at /data

**Backup Process**
Simple rsync from /data to /backup

**Expected performance**

Backing up 1.7TB of data.
I don't expect the full transfer rate of 150MB/s, so say half that 75MB/s

1.7TB @ 75MB/s = 7 hour 15min to back up the data.

EDIT: Also completed a dd copy to the disk and can see it can handle speeds around 80MB/s to 100MB/s
```
 dd if=/dev/zero of=/backup/test bs=4G count=1 oflag=direct 
```

**Current performance**
The backup has been running for about 16 hours and has only transfered 350GB of data.

Looking at iostat I can see the drive is only being written to at around 6MB/s

> 
Device:             tps        kB_read/s        kB_wrtn/s        kB_read               kB_wrtn
sda                      9.76          1829.82                483.03            245616047     64836662
md2                     19.90      6591.03            1169.98        884713044        157045792
md0                    0.00             0.01                     0.00                     1508                           256
md1                    3.18            70.46                  46.45                9457360             6235484
sdc                      9.10         1773.40            475.90             238043783         63880174
sdd                       9.16   1776.25            472.77           238426347          63459574
**sde                  13.38           2.56          6482.56              344019        870153476**
sdb                       8.72         1771.86         478.98             237836975         64293378

Device:           rrqm/s       wrqm/s         r/s         w/s        rkB/s        wkB/s     avgrq-sz     avgqu-sz       await     r_await     w_await      svctm      %util
sda                      28.19         106.64       5.51     4.22    1828.97   481.44        474.66             0.11              11.31       14.72            6.85            4.78          4.65
md2                      0.00             0.00        15.04    4.83    6589.53  1166.03       780.49            0.00               0.00           0.00            0.00            0.00            0.00
md0                      0.00            0.00         0.00       0.00        0.01           0.00              7.95                0.00              0.00            0.00            0.00             0.00           0.00
md1                     0.00            0.00          0.97       2.21      70.41        46.33           73.48               0.00             0.00             0.00            0.00             0.00           0.00
sdc         29.52       104.99       4.98      4.10     1772.61   474.33        494.87            0.23             25.76          32.57          17.49          8.78           7.97
sdd         30.91      104.20        5.03      4.11     1775.46   471.21       491.78             0.27            29.89          38.13           19.81          9.50           8.68
**sde                    0.58           2.65       0.06   13.32       2.55    6480.81   969.23          5.00       374.01       13.63       375.65      5.10        6.82**
sdb                    28.90       105.79         4.92    3.79      1771.10    477.40       516.71              0.50           57.78            54.65          61.83         10.85         9.44


Any ideas why this transfer is so slow?

Cheers

---

### Post by TheFu on 2015-03-15
Lots of reasons.
* bad sata port
* bad cables
* improperly tuned drive settings for the OS and hdparms
* improperly tuned RAID settings
* slow disks
* Cheap disks that don't support all the commands RAID demands.
* Improperly tuned rsync command.
* using a beta-quality file system

[http://blog.jdpfu.com/2011/10/17/hdd-performance-tuning-and-results](http://blog.jdpfu.com/2011/10/17/hdd-performance-tuning-and-results) might help you with some ideas. Be certain to test BEFORE making any changes, so you know if it is better or worse.

---

### Post by ian77 on 2015-03-15
Copying with CP works fine at 33MB/s which isn't too bad.
I looked back at my rsync command and could see I was using some incorrect options which was causing the issue. Just a simple rsync -a is working great now.

---

### Post by TheFu on 2015-03-15
We've all been there. Thanks for the follow up. 33MB/s is 264Mbps ... not bad at all. I would suspect that is mostly RAM buffers. Even so, I'm jealous about that performance.

rsync is one of those commands that I always learn something new by reviewing the manpage.  When I don't need anything special, the command I use is:
[B]rsync -avz --stats --progress source target
[/B]
When on the same machine, I would use different options. Plus we shouldn't forget that rsync uses ssh by default for all network transfers, if keys are setup. That is probably a good thing for all network transfers.

---

