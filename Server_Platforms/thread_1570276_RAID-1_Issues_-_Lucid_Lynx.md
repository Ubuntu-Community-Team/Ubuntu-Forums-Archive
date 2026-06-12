---
title: "RAID-1 Issues - Lucid Lynx"
date: 2010-09-07
forum: Server Platforms
---

### Post by freefallden on 2010-09-07
Hi,
 
I'm currently experiencing some serious issues with WRITE performance on a RAID-1 array.
I'm running Ubuntu 10.04 64 bit server with the latest updates. 
 
To evaluate the performance ran the following test: [http://notemagnet.blogspot.com/2008/08/linux-write-cache-mystery.html](http://notemagnet.blogspot.com/2008/08/linux-write-cache-mystery.html) (great article btw!) 
Using dd to measure, write performance is only at 8.7 MB/s.
Read is great though at 74.5 MB/s.
The tests were ran straight after rebooting and I have not (YET!) done any kernel tuning or customization, running the default server package of the Ubuntu kernel.
Here's the motherboard in the server: [http://www.supermicro.com/Aplus/motherboard/Opteron/HT1000/H8SSL-i.cfm](http://www.supermicro.com/Aplus/motherboard/Opteron/HT1000/H8SSL-i.cfm) with a beta bios to support drives over 300GB.
 
 

Other specs:
[LIST]
[*]Dual Core Athlon 64 4800+
[*]2 GB ECC Ram
[*]/dev/sda is a 32GB OCZ ONYX SSD with latest firmware, mounted as /
[*]/dev/md0 holds /home, composed of 2 Western Digital 1TB Green HD Drives with 64MB of cache (/dev/sdb and /dev/sdc)
[/LIST]Of note here's the output from vmstat when running dd:
```

procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  1      0  53932   4696 1843072    0    0     0     0  230 2121  0  0 49 51
 0  1      0  55296   4704 1843068    0    0     0    12  176 1013  0  0 52 48
 0  1      0  57032   4704 1843072    0    0     0     0   96 1136  0  0 50 50
 0  2      0  16836   4700 1864648    0    0     4 120480  314  848  0 35 21 44
 1  2      0  19100   4700 1864644    0    0     0     0  303 1920  0  1 31 69
 0  2      0  20464   4700 1864644    0    0     0     0  103 1016  0  1 49 50
 0  2      0  22200   4700 1864644    0    0     0     0  115 1259  0  0 50 49
 0  1      0  25176   4700 1864644    0    0     0     0  324 1112  0  0 73 27
 0  1      0  27160   4700 1864644    0    0     0     0  130  195  0  0 90 10
 0  1      0  29144   4700 1864644    0    0     0     0  133  201  0  0 87 13
 0  1      0  31624   4700 1864644    0    0     0     0  178  258  0  0 84 16
 0  1      0  33608   4700 1864644    0    0     0     0  131  204  0  0 90 10
 0  2      0  28276   4708 1870092    0    0     4 12756  137  273  0  2 79 19
 0  3      0  15944   4712 1844580    0    0     4 249444  389 1379  0 34 10 56
 0  3      0  16720   4712 1846840    0    0     0     0  356 2013  0  1 42 57
 0  2      0  16876   4716 1829436    0    0   156 121556  294 1512  0  7 30 64
 0  2      0  19604   4716 1829380    0    0     0     0  197 1939  0  1 48 51
 0  2      0  21836   4716 1829380    0    0     0     0  204 1819  0  0  1 99
 0  2      0  23696   4716 1829380    0    0     0     0  103 1364  0  0 60 40
 0  2      0  25184   4716 1829380    0    0     0     0  112 1099  0  0 59 41

```
As you can see from the bo column there is definitely something stalling. As per top output, the %wa (waiting for i/o) is always around %75 however as per above, writes are stalling.. CPU is basically idle all the time.
Hard drives are quite new and smartctl (smartmontools) does not detect any faults.
 
Help!

---

### Post by R.Bucky on 2010-09-08
I do not have a specific response to your query. However, I will say that one of my servers has a similar hardware configuration, with RAID1 and 1TB Green Drives. The Green Drives are spinning at a lazy 5400RPM and provide relatively poor performance compared to similar 7200RPM drives. Performance was so bad that I had to move my Samba shares off the box to stop the lag. 

I moved the storage to a RAID1 on two Caviar Black 500GB with marked performance increases. Not a real fan of the Green Drives.

---

### Post by freefallden on 2010-09-08
> **R.Bucky said:**
> I do not have a specific response to your query. However, I will say that one of my servers has a similar hardware configuration, with RAID1 and 1TB Green Drives. The Green Drives are spinning at a lazy 5400RPM and provide relatively poor performance compared to similar 7200RPM drives. Performance was so bad that I had to move my Samba shares off the box to stop the lag. 
 
I moved the storage to a RAID1 on two Caviar Black 500GB with marked performance increases. Not a real fan of the Green Drives.
 
Thanks for that... Just curious do you remember if both the writes and reads were slow? As I mention read performance is fine....
 
Having said that you got me thinking and after some research it led me to a feature DISABLED on WD consumer drives:
TLER - Time Limited Error Recovery. As the name explains, drive will not attempt to correct errors beyond a certain period of time. 
ref:
[http://hardforum.com/showthread.php?t=1191548](http://hardforum.com/showthread.php?t=1191548)
[http://hardforum.com/showthread.php?t=1285254](http://hardforum.com/showthread.php?t=1285254)
[http://en.wikipedia.org/wiki/Time-Limited_Error_Recovery](http://en.wikipedia.org/wiki/Time-Limited_Error_Recovery)
This feature is mentioned specifically on the specs of the green drives.
Unfortunately it appears the only way to modify this setting is with a DOS utility... arg!
hdparm makes no real mention apart from two features it shows as being "unknown 206[1x] (vendor specific)"
**FYI anyone using Western Digital consumer hard drives in a raid array should ABSOLUTELY read the wikipedia article above or else risk losing all data in the array.**

---

### Post by R.Bucky on 2010-09-08
Perhaps I was used to Caviar Black 7200RPM drives, but the entire read/write seemed slow. You could really tell the difference when moving large files across the network.

Thanks for the resource links.

---

### Post by freefallden on 2010-09-09
Bump... Is there anywhere else I could get support for this?

---

