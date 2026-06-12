---
title: "ZFS as storage for Ubuntu 17.10 Desktop."
date: 2018-03-08
forum: Ubuntu, Linux and OS Chat
---

### Post by lammert-nijhof on 2018-03-08
Looking for information about zfs the file system, I detected a number of old threads.  The conclusion was that zfs is NOT for desktops. I disagree and will show how and when zfs can be used on a desktop.
I have an old 4-core Phenom II, maxed out to 8GB and 3 HDDs; 2 x 2.5" 320GB (78 and 86MiB/s) and a 500GB 3.5" (135MiB/s) hdd. To be blunt I own a 10 year old HP dc5850, ripe for the graveyard. I use ZFS, but in contradiction to the normal file server use, I do depend on partitions. I put the partitions for the Virtual Machines in the first part of the disks, because of the 20-30% higher transfer speeds there. Besides I did use the fastest and biggest HDD for the OS and the swap partition. The partition are.
sda: 22GB ext4 for the OS, 4GB swap, 135GB zfs Virtual Machines, 339GB zfs Data.
sdb; 90GB zfs Virtual Machines.  230GB zfs Data.
sdc; 90GB zfs Virtual Machines.  230GB zfs Data.

I have declared two zfs datapools (note that you need admin privileges); ```
zpool create vms sda3 sdb1 sdc1
zpool create data sda4 sdb2 sdc2
```
And two dataset with the same name, too lazy to come up with a new name; ```
# zfs create <pool name>/<dataset name>
zfs create vms/vms 
zfs create data/data
```
Using nautilus I did put the permissions the way I liked it. I compressed the data/data dataset: ```
zfs set compression=on data/data 
``` 
Two time per week through crontab I run a snapshot: ```
zfs snapshot data/data@v1 and v2
``` and one time per week I back-up using two old USB disks, the oldest a 320GB IDE disk. I scrub the datapools each week, scrubbing is a consistency check and if data has been corrupted, I get alarmed and I can restore it from, a snapshot or backup. Note that the Virtual Machines are not compressed and I do not use the snapshots there, because I prefer to rely on the Vbox snapshots.
I restricted the huge memory requirements for the disk cache as follows. 
```
sudo gedit /etc/modprobe.d/zfs.conf

# Min 32MB / Max 1536 MB Limit
options zfs zfs_arc_min=33554432
options zfs zfs_arc_max=1610612736

```
I believe, I had to create that file the first time. Nowadays I even reduced that disk cache to 1GB instead of 1.5GB.
I use Conky to monitor the performance of the zfs sub-system.

[ATTACH=CONFIG]278869[/ATTACH]
Note that in Conky and Ubuntu you use the mount-point folder and for the dataset vms/vms, that is by default /vms/vms. You cannot use the three VMS and Data disks displayed by Nautilus in "other locations" instead you should add a bookmarks for /vms/vms and /data/data to Nautilus. Fortunately those bookmarks end up on the first page. 
Note also that the sda partition numbering in .conkyrc deviates from my example because that sda disk has been re-used and re-arranged many times
That part of the .conkyrc file looks like; 
```
    ${voffset 2}${color cyan}${font HeldustryFTVBasic Demi:size=12}STORAGE: zfs / ext4 ${font HeldustryFTVBasic Demi:size=8}${hr 2}
    ${voffset 2}${color}System ${offset 10}ext4 $alignr Free: $color${fs_free_perc /}% / ${fs_free /} of ${fs_size /} 
    ${fs_bar /} 
    ${voffset 1}${color}Data ${offset 8}zfs $alignr Free: $color${fs_free_perc /data/data}% / ${fs_free /data/data} of ${fs_size /data/data} 
    ${fs_bar /data/data} 
    ${voffset 1}${color}VMS ${offset 28}zfs $alignr Free: $color${fs_free_perc /vms/vms}% / ${fs_free /vms/vms} of ${fs_size /vms/vms} 
    ${fs_bar /vms/vms} 
    ${color}${voffset 3}sda 500GB, ${alignr}${diskio /dev/sda}/s of 130Mib/s   T=${hddtemp /dev/sda}°C
    ${color}${voffset 1}sdb 320GB, ${alignr}${diskio /dev/sdb}/s of   78Mib/s   T=${hddtemp /dev/sdb}°C
    ${color}${voffset 1}sdc 320GB, ${alignr}${diskio /dev/sdc}/s of   86Mib/s   T=${hddtemp /dev/sdc}°C
    ${color}${voffset 2}System = ${diskio /dev/sda4} 
    ${diskiograph /dev/sda4 25,256 009acd f0f8ff -l -t} 
    ${color}Data: sda/b/c = ${diskio /dev/sda3} / ${diskio /dev/sdb2} / ${diskio /dev/sdc2}
    ${diskiograph /dev/sda3 25,80 009acd f0f8ff -l -t}   ${diskiograph /dev/sdb2 25,80 009acd f0f8ff -l -t}   ${diskiograph /dev/sdc2 25,80 009acd f0f8ff -l -t} 
    ${color}VMS: ${offset 20}sda/b/c = ${diskio /dev/sda1} / ${diskio /dev/sdb1} / ${diskio /dev/sdc1}
    ${diskiograph /dev/sda1 25,80 009acd f0f8ff -l -t}   ${diskiograph /dev/sdb1 25,80 009acd f0f8ff -l -t}   ${diskiograph /dev/sdc1 25,80 009acd f0f8ff -l -t}

```
I am very happy with zfs on my desktop for the following reasons.
[LIST]
[*]it mounts automatically no fstab nor mount command
[*]it keeps my data very secure, no undetected corruption of e.g. music files due to the frequent Caribean power breaks and/or software errors in the many music players or Alpha OSes I tried
[*]Fast, It uses all disks in parallel despite the difference in size and speed. I did see it running at 150/200MiB/s during scrubbing and vdi file transfers (10-30GB/file). Note that Conky measures the real device speeds without the effect of the 1GB memory cache for the disks. Here we have some unfinished work based on the ZFS CLI, measure the speed achived by zfs including the cache. And what is preferable running 3 VMs with a 1GB disk cache or running 2 VMs with a 2GB disk cache. I also like to add say a cheap 120GB SSD for booting the Host OS and as secondary zfs disk cache for at least the VMs.
[/LIST]
**CONCLUSION:**
ZFS is very usefull if you have high reliability requirements for your data, but ZFS is also useful if you have HDDs or SSDs of different sizes and you want to use them in parallel (RAID-0 like) to speed up your processing with Virtual Machines, Containers and/or other disk intensive workloads.  I do not think you should mix SSDs and HDDs in one data pool, but I expect, you could use a partition of that SSD as secondary cache for a HDD data pool. You could also boot your (Host-)OS from a ZFS datapool/dataset, but that is relatively complex, so up to now I ducked that challenge. My excuse is; the Host system is currently up for 3 days and 11 hours, because normally I only boot 2 or 3 times per week.  All experiments are in the VMs and consequently they boot sometimes 10 times per hour. That is, why I like that ZFS SSD cache.
 
I will **not** use ZFS on my laptop, since that one has only a single 1TB SSHD, so I have no speed advantages due to parallellisme and I have already a 32GB built-in SSD cache. I do not try new software on my laptop and together with the battery, it is more resilient against corruption. And ext4 is fast on a single disk. So for my laptop ext4 remains my choice.

---

### Post by mastablasta on 2018-03-09
or you could use btrfs.
ext4 is a stop gap measure before moving to more advanced file systems. work fine though for normal desktop use... but no snapshots and other goodies.

---

### Post by lammert-nijhof on 2018-03-09
I use Peppermint 8 frequently with an old Pentium 4 and in a VM and that OS is using brtfs. I never had any issues. However I did hear Red Hat stopped supporting it and there seems to be some issues with the more complex RAID configurations. Those rumors have been the reason, that I started with zfs and I want to try-out somewhat more, but my next project will be brtfs and/or xfs, probably after the summer. Like with zfs, I will set up a VM to try out the raid-0 type of usage and look more general, what is functionally possible in my use case. For performance you have to use the real HW, if old brick keeps surviving. After that try-out I will make a choice. Will brtfs or xfs replace zfs? Maybe.

---

### Post by mastablasta on 2018-03-09
btrfs is used  on SUSE EL server by default. 

the issue appears to be file encryption. 

and also Red Hat pushing their tech.: [https://www.phoronix.com/scan.php?page=news_item&px=Stratis-Red-Hat-Project](https://www.phoronix.com/scan.php?page=news_item&px=Stratis-Red-Hat-Project)

will it be a repeat of the "awesome" systemd ? we'll see.

---

### Post by kevdog on 2018-03-11
Sorry to chime in here -- I could be totally wrong -- however I thought I read somewhere the btrfs project was recently abandoned.  I've got a FreeNas Server with a ZFS filesystem (Freenas run on FreeBSD), however when I build the box, I built it specifically for ZFS -- meaning RAIDZ2 (Like a RAID-6) with once disk acting as l2arc.  I understand this system is a lot different than a desktop.  I've never tried ZFS on linux although I've looked at the sight a lot.  It would be interesting if those using ZFS are using it in conjunction as the /boot drive or simply zfs for data or the /home partition for example.

---

### Post by mastablasta on 2018-03-12
BTRFS doesn't seem abandoned to me at all: [https://btrfs.wiki.kernel.org/index.php/Status](https://btrfs.wiki.kernel.org/index.php/Status)

in fact the opposite might be th eissue. still under development. new features, new bug fixes...

---

### Post by lammert-nijhof on 2018-03-24
Using zfs now for two weeks, I did run into some performance issues. The max throughput of the system was around 150MB/s and that has been somewhat disappointing, because using the two laptop disks in Raid-0 with ext4, I achieved 140MB/s. Looking in some more detail using zfs iostat and the gnome-disk utility showed me that the Samsung laptop disk only achieved half of its ext4 throughput. The result has been, that for say 20% of the time the two other disks were waiting for the Samsung disk to complete his write operations. 

The number of write (and consequently read) operations is balanced by zfs more or less equal to the size of the partition (UPDATE: To be more precise, it is based on the free space on the disk or partition). If throughput is important, take the easy way(1) or the cheap way(2):
[LIST=1]
[*]Buy the same disks or
[*]Use existing disks and use partitions. Choose the partition size (S) on each disk based on that disk&#8217;s throughput (T).
[LIST]
[*]Tsda : Tsdb &#8230;. Tsdz = Ssda : Ssdb &#8230;. Ssdz
[/LIST]
[/LIST]
It nicely balances the number of IO operations based on available throughput of each disk. In higher load situations it avoids that 2 or 3 disks are waiting until another one has catched up. 
Use the remaining space for less performance critical stuff, like back-ups, music, photos, office files etc. 

The total throughput is 135+80+30 ~ 245MB/s. I wanted 320GB for the vms datapool, So I did choose my partitions sizes as:
sda 135/245*320GB~176GB; Data remains 324GB
sdb   80/245*320GB~104GB; Data remains 216GB
sdc   30/245*320GB~  40GB; Data restrict to 120GB
For the Samsung disk I only could use 160GB without a performance penalty, so I replaced that disk with a slightly slower 160GB laptop disk. Now I use the Samsung disk with USB 3.0 and ext4 and it runs again at 80MB/s. 

Why was the Samsung disk running at half the ext 4 throughput in a zfs environment? The only difference with the other laptop disk was the physical sector size. The Samsung disk physical sector size was 512 bytes, while the other two did have a physical sector size of 4096 bytes. The Samsung disk needed 8 times as many IO operations than the others. Consequently it had a higher chance to just miss the next sector and thus needed more or less double the revolutions for the same amount of data. So my first conclusion is: 

Do not mix disks with different physical sector sizes. 

There is a lot of discussion about zfs and physical sector sizes. Maybe I have to recreate the datapool and force it to use a sector size of 4096 (ashift=12), that seems to be the best value to choose. Currently I'm running with the default ashift=0. I do not expect much result, since according the gnome-disk utility everything runs at its top speed, except the 160GB disk. 

That 160GB disk could run 25% faster using ext4, but using zfs with sector size 512, it will probably need 25% more revolutions to read the same amount of data. It looses less throughput than the 320GB, because it has less sectors/tracks and probably somewhat larger gaps and so it offers the driver/controller just a little bit more time between sectors.  

Unbelievable that 160GB disk running with ext4 at 40MB/s has been sold to me in a Windows Vista laptop a Dell Inspiron 1521 and I only blamed Vista for the poor performance.

After 2 weeks I'm disappointed about the currently achieved throughput in copying a VDI file of 9GB. It just reaches 160MB/s (half reads and half writes), that is 65% of the accumulated performances as measured by the gnome disk tool. On the other hand the copy operation take less time, because the real compressed file size is 5.5GB. Why do I stay with zfs? 
 

[LIST]
[*]All VMs boot in between 35 (Win XP) and 65 (Win 10) seconds and that is 20-30% faster then before with RAID-0, mainly caused by the compression.
[*]My Guest OS Ubuntu 18.04 is more responsive and faster then my Host OS Ubuntu 17.10.
[*]If I measure the performance of the system disk of my virtual machines with the gnome-disk tools, I reach read-throughputs above 400MB/s and writes above 100MB/s.
[*]Comparable results happen in Win 7 with Crystal Disk Mark, which reports 340MB/s read and 177MB/s write throughput.
[/LIST]

Both speeds are measured directly after booting and are that high (higher than my SATA-2 throughput), because a large portion of the benchmark  is already read from the zfs memory cache.
The Host is more efficient with the video processing, the Guest requires in general 15-20% more CPU load for displaying YouTube videos with 3D acceleration enabled. Without 3D the CPU load runs up to 90% for HD YouTube videos.

---

### Post by lammert-nijhof on 2018-04-01
I upgraded the host OS to Ubuntu 18.04, mainly because its zfs version supports compression for the zfs memory cache. The cache is 1.5GB and it now stores effectively 3GB of data and code. Basically it means that I can run at least two VMs from cache memory. The virtual machines are on a compressed dataset now too. That reduces the number of disk I/O operations and it avoids compressing/decompressing going from cache to disks and back. 

That perceived throughput limitation is not as bad I thought. I did look in somewhat more detail and changed the measurement method using zfs tools and logs. The current theoretical write throughput is approx 164Mb/s. In a copy/paste operation the measured peak throughput was 140MB/sec, which is around 85% of the above theoretical maximum for writes. In performing a zfs scrub operation (file system consistency checking) I reached a peak throughput of 220MB/s, which is around 95% of the accumulated read throughput of 235MB/s (lost 10MB/s by introducing the very slow 160GB HDD). I calculated that throughput by adding together all measured values of the three HDDs.  I used the benchmark of the gnome-disk utility for the measurement of the zfs partition of each HDD.

Up to now I only could display the HDD partitions individually without any totals for the dataset divided over all 3 HDDs, but I now display the throughput for the whole datasets. I use it as measured by "zpool iostat", a function nice as display, but not very usable in scripts. It has been somewhat complex, writing the output of zpool iostat to a file, writing some scripts to translate those raw values to conky friendly formats and use those in conky $exec and $execgraph. It is my zfs version of the $diskio and $diskiograph function of conky.

---

