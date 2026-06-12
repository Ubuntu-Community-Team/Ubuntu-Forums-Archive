---
title: "kjournald2 blocked for more than 120 seconds"
date: 2009-11-16
forum: Server Platforms
---

### Post by sicn on 2009-11-16
This is my first post here so go easy on me ;)

I've got a problem which I've encountered after installing a new server with Karmic 64-bit (fully patched). The server is running a Core 2 Duo 2,8GHz, 2x Western Digital Caviar Green 1,5TB SATA drives (TLER enabled), 4GB DDR2 RAM. The moterboard uses Intels ICH7 chipset, no "hardware RAID" capabilities.

The disk configuration is as following. I've got four partitions on each disks (100MB boot, 64GB /, 1,4TB /home and 8GB swap), all of the partitions are configured as RAID1 md-devices (software mdraid), chunk size is 64k and all of them except swap are ext4.

The problem is that my system frequently locks up completely to the point that I will see two messages in the log:

"kdmflush: Blocked for more than 120 seconds"
and
"kjournald2: Blocked for more than 120 seconds"

iostat reveals that sda and sdb alternatively often go up to 100% utilization and all too often I receive iowait of 100% (this is where everything is stuck for several seconds until I get the messages quoted above).

I did the usual things:

1.) Increase readahead from the default 256k to 1024k, all up to 8192k => Didn't help.
2.) Set /proc/sys/fs/raid/speed_limit_min[/max] to considerably lower values. I first tried 1000/20000, then 1000/10000, in the end I had 1/500. => Didn't help, even though the disks give much higher read/write values when checking read/write performance with "dd".
3.) Disabled TLER on the WD-disks => Didn't help so I re-enabled.
4.) Tried both LVM on md1 and four partitions approach (which quoted on top) so LVM (which I originally though was the problem) doesn't seem to be the problem either.
5.) Reformatting everything to ext3 => Didn't help, so I went back to ext4.

The funny thing is that the moment I intentionally do a mdadm fail /dev/md1[|2|3] /dev/sdb2[3|4]" everything runs perfectly without a hickup.

I searched the net and didn't find many helpful articles about this (except speed_limit_min/max and adjusting readahead).

In the end I thought that the excessive ext4 journal-writing might be the reason for the freezes and set noatime as mount parameter in /etc/fstab, which didn't help either.

So now I am wondering if any of you guys have a clue as to what other parameters I could adjust to see if the problem disappears?

Thanks in advance!

PS.: I forgot to mentoin, I even tried Fedora 12 RC and it shows the same behaviour, that's why I am under the impression that it might be configuration-related.

---

### Post by fjgaude on 2009-11-16
Likely has something to do with all the partitions going into arrays under mdadm. Most folks simple use mdadm as a data array. Those that use raid1, booting off the array, usually have troubles one way or another.

Are you streaming video off the array when you get the iowait delays?

---

### Post by sicn on 2009-11-16
No, I am not streaming. It seemingly happens randomly.

Any suggestions regarding array reconstruction?

---

### Post by sicn on 2009-11-17
Here is a little iostat-printout showing the problem... This occours basically the second there is any disk activity (even using VIM, which creates small backup-files can cause this).

```

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.50    0.00    0.00   99.50    0.00    0.00

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.00     0.00    0.00    2.50     0.00     4.00     1.60     0.04   16.80   4.80   1.20
sdb               0.00     0.00    0.00    2.50     0.00    36.00    14.40     4.00 2307.20 400.00 100.00
md1               0.00     0.00    0.00    2.50     0.00     4.00     1.60     0.00    0.00   0.00   0.00
md0               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
dm-0              0.00     0.00    0.00    0.50     0.00     4.00     8.00     1.69 19920.00 2000.00 100.00
dm-1              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
dm-2              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
dm-3              0.00     0.00    0.00    0.50     0.00     4.00     8.00     1.14 2496.00 2000.00 100.00
dm-4              0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
dm-5              0.00     0.00    0.00    0.00     0.00     0.00     0.00     1.00    0.00   0.00 100.00

```

---

### Post by sicn on 2009-11-23
I know that the problem seems fairly specific and that nobody can help, but what the heck, I'll try some more...

I played around with the chunk size and raised it all the way to 1024. The fun thing is, iowait is no longer 100%, ever.

However, I still get unexplained "stalls" where all disk I/O just freezes for a couple of seconds and continues.

An example: I unpack a 2GB ZIP-file... In the beginning its unpacking at somewhere around 70MB/s but eventually it stalls and it goes down to 0MB/s for a couple of seconds only to resume at maybe 35MB/s and then it goes down again to 0MB/s... and so on. The interesting thing: Once the system came to the point that it stalled once, it will continue to stall during unpacking until all user I/O seizes and when I unpack the next 2GB ZIP-file it will once again run full speed until somewhere in the middle it will start to stall.

Oh, and I use a very aggressive 64M readahead cache now, but I will probably lower it again as it doesn't seem to speed things up that much.

Any ideas?

---

### Post by sicn on 2009-12-10
Well, I seem to have solved the problem.

Apperantly it's Western Digital's Green disks which aren't what I would call "compatible" to us Linux-users. The IntelliPark feature seems to constantly park the disk heads thus causing the I/O-wait.

After trying the exactly setup with two Samsung F2 EcoGreen disks everything was going smoothly, so I went back, told Western Digital support (which said that they don't offer support for Linux) and ultimately tried with WD's unspported [WDIDLE3]("http://home.arcor.de/ghostadmin/wdidle3_1_00.zip")-tool to remove the parking feature. Unfortunately, WD's newer disks don't support disabling the parking altogether so I raised the timeout to it's max ([WDIDLE3]("http://home.arcor.de/ghostadmin/wdidle3_1_00.zip") /S255). This made the problem appear a little less, but still not good enough.

I then searched the internet high and low and found the dirty_writeback_centisecs and dirty_expire_centisecs values. I first tried to set them lower than the timeout, so I tried with 2000 and 500... this had no impact, though.

I eventually set dirty_writeback_centisecs and dirty_expire_centisecs to a 100 each, and now it seems to work without IOWAIT or kjournald2 blocked-messages.

So if you have the same problem, either return your disks and get yourself some good ones or add a file called 10-{whateveryouwant}.conf to /etc/sysctl.d and add following two lines to it:

vm.dirty_writeback_centisecs=100
vm.dirty_expire_centisecs=100

Cheers!

---

### Post by frankO on 2010-01-14
Hi I am having a similar problem. The hard drives are all WD Caviar Green 1tb drives. 
sdb/c/d are part of a raid 5 md0. sda is used for booting and has the / mount. sdf and sde are external drives via usb.

I am running Mythbuntu 9.10 64 bit. I had this problem with 9.04, so I upgraded to 9.10 hoping it would fix the problem.  

The mother board is a gigabyte ga-g41m-es2h. 

As you can see below sdc and sdd have 100% util but are doing nothing except a small write.
It is always 2 discs.
If I move the sata connections the pairings will change. Currently they are sda and sdb. They are currently randomly going to 100% util.
The usb drives sde and sdf do not give any problems.


```
12/01/10 14:24:19
avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           1.80   49.70    1.20    0.00    0.00   47.30

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sdb               0.00     0.00    0.00    0.20     0.00     1.60     8.00     0.01   40.00  40.00   0.80
sdc               0.00     0.00    0.00    0.20     0.00     1.60     8.00     1.00 3400.00 5000.00 100.00
sdd               0.00     0.00    0.00    0.20     0.00     1.60     8.00     1.00 3400.00 5000.00 100.00
md0               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sde               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sdf               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
```

I tried the "vm.dirty_writeback_centisecs=100" and "vm.dirty_expire_centisecs=100" but it did not help.

I don't know if it is hardware or software.
Because I can change the sata connections and get different pairings then I think it might be hardware, But then it could be software.
It seems random, but then a large amount of io such as moving 4gb can cause the above problem. Then again there might be a small amount of traffic like above and it can happen.

I don't know my next move. I don't want to spend money on a motherboard when it is not a hardware problem. 

I thought it might be the green hard drives but 
sudo hdparm -C /dev/sda
shows 
drive state is:  active/idle
which does not tell me much

The below shows a bit of traffic on sda because of mythtv but little on sdb but the util for both is near 100%.
The myth-frontends crashed or stuttered through this.

```

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.00    95.20    2.80    0.60   156.80     8.00    48.47    37.23 3910.59 294.12 100.00
sdc               0.40     0.00    3.40    0.40   384.00     3.20   101.89     0.02    6.32   4.74   1.80
sdd               0.00     0.00    3.60    0.40   371.20     3.20    93.60     0.02    4.50   3.50   1.40
sdb               1.00     0.00    2.80    0.00   385.60     0.00   137.71     3.28 1662.14 355.00  99.40

```

---

### Post by sicn on 2010-01-14
I am afraid you are out of luck. I tried my best to mitigate the problem by all possible and impossible settings (BIOS, Linux, jumpers), however, in the end I gave up.

I sent an e-mail to Western Digital and gave them a very detailed description of the problem to which they simply answered "We just support Windows".

The WD disks are now electronic waste on some landfill and I bought Samsung instead, they work perfectly. :D

---

### Post by wazham on 2010-03-23
This is very interesting. I too have bought a Western Digital Caviar Green disk (10EADS) and it's journalling away like mad. I didn't see anything on the internet about this problem when searching for what disks to buy - pity. I would be interested to know why WD are so uninterested in non-Windows users.

Anyway, I shall be monitoring my own situation as best I can but I can't help thinking it might be helpful to future noobs like myself considering buying new drives to perhaps change the title to reflect that this is a Western Digital problem, or perhaps should there be a new thread?

Thanks for all the detailed info, sicn, and for coming back with the resolution.

---

### Post by superFerra on 2010-10-12
Thank you all,
I have the same problem. I will try the workaround proposed by sicn and report you back soon.
My setup had the same issue (high iowait) both with mdrain and dmraid too. I'm using 2x(WD caviar green 1Tb) in raid-mirror mode

---

