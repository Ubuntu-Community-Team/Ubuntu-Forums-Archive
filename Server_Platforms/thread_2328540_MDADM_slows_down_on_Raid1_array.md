---
title: "MDADM slows down on Raid1 array"
date: 2016-06-22
forum: Server Platforms
---

### Post by karel5 on 2016-06-22
I am using Xubuntu 16.04 Desktop on a Core i5 machine with 16G RAM. Boot up is from a 120Gb SSD. I have installed an additional mdadm Raid1 array consisting of two identical WD 2TB disks, mounted as md0. The machine is (also) used as a general file, mail and web server inside a small home domain.

After booting up, read/write speeds to the Raid1 array are something like 50-70 Mb/sec, which is fine. When I store larger amounts of data to the array, write speeds start to drop. After writing about 3G of data, they are down to around 1 Mb/sec, and will remain like that until I reboot the machine.

I have made sure that there is no resyncing going on in the backgound. The array is reported to be faultless. Resyncing has been made faster by setting the speed_limit_min and speed_limit_max speeds to 50000 and 2000000 respectively. It takes about 4 hours to resync the array -which is fine. 

CPU load on each of the 4 cores is less than 2% on average and memory usage is around 10% of the 16G installed.

It seems like a cache is filling up and not refreshing itself or something like that.

I would appreciate some advice on how to ensure proper read/write speeds of the Raid1 array on a continuous basis.

Thanks.

Karel

---

### Post by TheFu on 2016-06-22
Setup monitoring of the system for 24/7 data capture. That way you can see the system-wide performance and get a better idea of what is really happening. Munin is pretty easy to setup, but Monit is too.  Capture some data for a few days before making any changes. Make 1 change - did it help or not?    Do this first, before anything else.

a) tune the disks separately.  The source for my article on this isn't availble to me anymore: 
 [http://blog.jdpfu.com/2011/10/17/hdd-performance-tuning-and-results](http://blog.jdpfu.com/2011/10/17/hdd-performance-tuning-and-results)
b) tune the array; add more disks + striping, use tuned block sizes for the workload. 
   [http://ubuntuforums.org/showthread.php?t=1494846](http://ubuntuforums.org/showthread.php?t=1494846) read and follow the warnings.
c) manage the disk buffers used. More is better to a certain point.  If you are moving large files around, huge is better so the transfers happen quickly RAM-to-RAM and the disks have time to catch up.  **free -mh ** can provide an overview of buffer use.
d) Don't let the disks get full. 95% is about the max before performance degrades.
e) Don't use cheap controllers. If you want performance, get a quality disk controller from LSI or a Supermicro AOC-SAS2LP-MV8 which is well supported.
f) Don't have a huge swap partition and don't let the swap be used much, if at all. On a desktop, 4.1G is the correct size for a swap partition. On a server, tune the running applications so that ZERO swap is needed and remove it. RAM is cheap.

g) Don't use bad disks. Cheap seagates are an issue in certain sizes. I've been burned a few times with these - their 500G and smaller drives were fantastic but something happened with any that were larger. Bad engineering is my guess and they don't seem to have fixed it in the last 8+ yrs. Sad, really.

---

