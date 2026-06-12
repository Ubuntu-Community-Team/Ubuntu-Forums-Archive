---
title: "mdadm rebuild extremely slow"
date: 2010-06-05
forum: Server Platforms
---

### Post by pegler on 2010-06-05
Hi all,

I currently have 9.04 desktop x64 installed.  I have 6 2TB drives configured in raid5, but the build is extremely slow.  On the order of 200K/sec for the build.  This will take about 3 months to complete.  This can't possible be correct.  I have tried changing the speed_limit_min and max, but nothing changed.  Is there something I am missing?

Also, if it is not possible to somehow speed this up, is there some way to configure it to continue the build from where it left off instead of restarting after a reboot?

Thanks for your help,

Matt

---

### Post by richardjh on 2010-06-05
This could be due to the disks. 
Seagate SATA disks can be affected in the way you describe.


I was stuck on the same problem and spent ages investigating mdadm, until ,by chance I found this solution of adding the kernel option all-generic-ide at boot time.


Check out [this  forum thread]("http://ubuntuforums.org/showthread.php?t=1422633") I previously posted about slow RAID rebuild times and post back if this  doesn't fix the issue.

---

### Post by Xianath on 2010-06-05
Several things come to mind:

[LIST]
Did you set up /sys/block/md*/md/sync_speed_* or /proc/sys/dev/raid/speed_limit_* ? There used to be a bug in mdadm about the former not working, not sure when they fixed it. 
[/LIST]
[LIST]Try bumping up /sys/block/md*/md/stripe_cache_size to a large number like 2048. Just be careful that stripe_cache_size * <number of disks> * <stripe size> doesn't become too large (like a quarter of your RAM) or you will start running into issues.
[/LIST]
[LIST]Read-ahead **really** helps with rebuilds. Try "sudo blockdev --setra <2 * drive cache in KB> /dev/sd?"
[/LIST]
[LIST]CPU frequency scaling, at least for me, doesn't take into account kernel load. In other words, your CPU could be struggling with RAID5 checksums and still be running at its lowest frequency setting. Try "sudo cpufreq-set -g performance".
[/LIST]
[LIST]If you still don't see a noticeable improvement, please provide the output of the following (you will need the sysstat package):
sar -bdpqu -P ALL 60 1
[/LIST]

---

### Post by pegler on 2010-06-07
I added "all_generic_ide" to the boot options.  Slight improvement to 

I set sync_speed_min to 20000 and sync_speed_max to 200000.  no improvement.

I set speed_limit_mind to 20000 and max to 200000.  This decreased performance.  Not sure if that was a fluke.

setting the readahead really helps.  pretty much linear depending on how much I increase the ra size.  Though decreasing it back down doesn't seem to do anything.  So it may have been a coincidence again.

How long should I have given each of these changes to see effect?  I waited about a minute before remeasuring the performance.

Here's the output of "sar -dbpqu -P ALL 60 1"

sda, b, c, e, f, g are all in the RAID 5.  They are all 2TB drives.  sdd is the OS drive (250 GB).  All WD drives.

```

Linux 2.6.28-11-generic (mantherbox)    06/06/2010      _x86_64_        (4 CPU)

09:42:08 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
09:43:08 PM     all      0.01      0.00      0.08      0.00      0.00     99.91
09:43:08 PM       0      0.00      0.00      0.00      0.00      0.00    100.00
09:43:08 PM       1      0.00      0.00      0.00      0.00      0.00    100.00
09:43:08 PM       2      0.00      0.00      0.22      0.00      0.00     99.78
09:43:08 PM       3      0.03      0.00      0.12      0.00      0.00     99.85

09:42:08 PM       tps      rtps      wtps   bread/s   bwrtn/s
09:43:08 PM      8.92      8.05      0.87   2438.10    483.48

09:42:08 PM   runq-sz  plist-sz   ldavg-1   ldavg-5  ldavg-15
09:43:08 PM         0       188      1.00      1.00      0.87

09:42:08 PM       DEV       tps  rd_sec/s  wr_sec/s  avgrq-sz  avgqu-sz     await     svctm     %util
09:43:08 PM       sda      2.26    487.62      0.00    216.18      0.02      9.96      2.01      0.45
09:43:08 PM       sdb      2.21    487.62      0.00    221.09      0.02      9.18      1.94      0.43
09:43:08 PM       sdc      1.70    487.62      0.00    286.12      0.01      3.84      2.16      0.37
09:43:08 PM       sdd      0.32      0.00      4.41     13.89      0.00      0.21      0.21      0.01
09:43:08 PM       sde      1.04    487.62      0.00    470.71      0.01     12.13      6.52      0.68
09:43:08 PM       sdf      0.85    487.62      0.00    572.24      0.01     11.45      7.76      0.66
09:43:08 PM       sdg      0.55      0.00    479.06    868.85      4.51   8123.64   1818.18    100.25
09:43:08 PM       md0      0.00      0.00      0.00      0.00      0.00      0.00      0.00      0.00

Average:        CPU     %user     %nice   %system   %iowait    %steal     %idle
Average:        all      0.01      0.00      0.08      0.00      0.00     99.91
Average:          0      0.00      0.00      0.00      0.00      0.00    100.00
Average:          1      0.00      0.00      0.00      0.00      0.00    100.00
Average:          2      0.00      0.00      0.22      0.00      0.00     99.78
Average:          3      0.03      0.00      0.12      0.00      0.00     99.85

Average:          tps      rtps      wtps   bread/s   bwrtn/s
Average:         8.92      8.05      0.87   2438.10    483.48

Average:      runq-sz  plist-sz   ldavg-1   ldavg-5  ldavg-15
Average:            0       188      1.00      1.00      0.87

Average:          DEV       tps  rd_sec/s  wr_sec/s  avgrq-sz  avgqu-sz     await     svctm     %util
Average:          sda      2.26    487.62      0.00    216.18      0.02      9.96      2.01      0.45
Average:          sdb      2.21    487.62      0.00    221.09      0.02      9.18      1.94      0.43
Average:          sdc      1.70    487.62      0.00    286.12      0.01      3.84      2.16      0.37
Average:          sdd      0.32      0.00      4.41     13.89      0.00      0.21      0.21      0.01
Average:          sde      1.04    487.62      0.00    470.71      0.01     12.13      6.52      0.68
Average:          sdf      0.85    487.62      0.00    572.24      0.01     11.45      7.76      0.66
Average:          sdg      0.55      0.00    479.06    868.85      4.51   8123.64   1818.18    100.25
Average:          md0      0.00      0.00      0.00      0.00      0.00      0.00      0.00      0.00

```

Thanks for all your help.

Edit: for reference, it is building at around 200K/sec.  Will end up taking about 4 months to build.

---

### Post by borahshadow on 2010-06-07
Is this a new array or are you replacing a failed drive?

Are these drives some of WD's new advanced format drives?

---

### Post by Xianath on 2010-06-07
sdg is your problem, it's at 100% utilization with almost 2 seconds service time per request. Let's focus on that drive first. Check its SMART status with smartctl (you need to install smartmontools)

sudo smartctl -s on /dev/sdg
sudo smartctl -A /dev/sdg

Let's also get a look at its partition table:

sudo sfdisk -d /dev/sdg

---

### Post by pegler on 2010-06-07
so the drive has failed out of the array.  so I am assuming that is the cause of the slowness.  I'll let you know how it goes once it is replaced.

thanks for all your help.

---

### Post by borahshadow on 2010-06-07
wait it just failed? I thought thought you were rebuilding after you replaced a failed drive. I don't understand

---

### Post by pegler on 2010-06-07
I was building the array initially.

---

### Post by pegler on 2010-06-07
just an update.  Since it was building for the first time, and one of the drives is bad, I ended up just creating a raid5 with the 5 remaining drives to check the speed.  It is going 100x faster with the one bad drive removed.  So it looks like hardware can really mess things up.

thanks again for all the help.

---

### Post by borahshadow on 2010-06-07
ok so let me make sure I under stand this.

You were creating the array for the first time with 6 disks
One of them was bad? = slow
removed the bad disk and now it is building fast.

just to check are these Western Digital Advanced format drives?

---

### Post by freefallden on 2010-09-01
Just wondering what speed other mdraid users are getting on rebuild? I assume if varies if RAID-1 or RAID-5 for example... In my case with an older server with a dual-core athlon 4800+ and serverworks HT1000 sata controller, I'm getting only around 2500KB/s as per /proc/mdstat. The HD drives are new though, 1TB Western Digital Green w/64 meg of cache...
 
Needless to say its taking a LONG time. :(

---

### Post by freefallden on 2010-09-01
> **Xianath said:**
> Several things come to mind:[LIST=1]
[*]Did you set up /sys/block/md*/md/sync_speed_* or /proc/sys/dev/raid/speed_limit_* ? There used to be a bug in mdadm about the former not working, not sure when they fixed it.
[*]Try bumping up /sys/block/md*/md/stripe_cache_size to a large number like 2048. Just be careful that stripe_cache_size * <number of disks> * <stripe size> doesn't become too large (like a quarter of your RAM) or you will start running into issues.
[*]Read-ahead **really** helps with rebuilds. Try "sudo blockdev --setra <2 * drive cache in KB> /dev/sd?"
[*]CPU frequency scaling, at least for me, doesn't take into account kernel load. In other words, your CPU could be struggling with RAID5 checksums and still be running at its lowest frequency setting. Try "sudo cpufreq-set -g performance".
[*]If you still don't see a noticeable improvement, please provide the output of the following (you will need the sysstat package):
[*]sar -bdpqu -P ALL 60 1
[/LIST]
 
[COLOR=black][FONT=Verdana][COLOR=black][FONT=Verdana]First off, thanks for the input Xianath, its much appreciated![/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Unfortunately more questions as per your comments above if you don’t mind :) I'm running 10.04 x64 server edition:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Point #2: Stripes are for RAID-5 arrays, not RAID-1 correct?[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]#3: Why is the default on my system (256) so much lower than the number you are suggesting? Are there any issues when changing this?[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]#4 Does cpufreq interfere with loadcpufreq script in /etc/init.d? [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]In any case with these tips I got rebuild to go from 2700kb/s up to 6,000kb/s so thx again![/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Tim[/FONT][/COLOR]
[/FONT][/COLOR]

---

