---
title: "Ubuntu + ZFS + iSCSI , does it work?"
date: 2014-10-14
forum: Server Platforms
---

### Post by darren18 on 2014-10-14
Hello everyone, first time posting been using Ubuntu desktop edition for a long time now though.... For starters i found out my original plans to make a file server with FreeNAS isn't going to work out due to lack of 10GB network support, so I'm considering ubuntu for this task now but would like to use the ZFS file system. I found some helpful posts that the ZFS file system works great on Ubuntu as long as it isnt for the actual install. 

My plan is to install Ubuntu on a pair of raid1 SSD's for boot and then create my ZFS file system on my 28-32TB array for storage...

Heres the questions:
1. Is ZFS a good option in my situation?
2. is it in fact stable?
3. Is there a way to use RAIDZ2 if ZFS is stable and recommended
4. Does Ubuntu support iSCSI, and is it stable/recommended? 

I ask a lot out of something so powerful yet free, so if anyone can make some recommendations i would greatly appreciate it :)

---

### Post by lukeiamyourfather on 2014-10-15
> **darren18 said:**
> Hello everyone, first time posting been using Ubuntu desktop edition for a long time now though.... For starters i found out my original plans to make a file server with FreeNAS isn't going to work out due to lack of 10GB network support...

What 10GbE adapter in particular? Because FreeNAS supports the Intel X540-T1 and X540-T2 from what I've read. Old forum posts discussing a lack of support might be for older versions of FreeNAS.

> **darren18 said:**
> 1. Is ZFS a good option in my situation?

That depends on what your situation is. In my opinion ZFS is the best option out there right now for a file system to be used for a file server.

> **darren18 said:**
> 2. is it in fact stable?

Yes, ZFS on Linux is stable and production ready. I've been using it for about a year on a pair of file servers at work used by video editors and artists.

> **darren18 said:**
> 3. Is there a way to use RAIDZ2 if ZFS is stable and recommended

Yes, RAID Z2 can be used. If you can share specifics about your hardware I can make recommendations for configuring it. One huge VDEV is not a good idea with a lot of disks.

> **darren18 said:**
> 4. Does Ubuntu support iSCSI, and is it stable/recommended?

Yes Ubuntu can be either the initiator or target and it's stable. Whether or not it's recommended depends on your planned use.

---

### Post by darren18 on 2014-10-15
[SIZE=2][FONT=verdana]Thanks for all the answers lukeiamyourfather, the 10GB adaptors i purchased are Qlogic QLE3142 NX3-20G. I managed to get ubuntu desktop installed first just to verify the adaptors are there and they are :) , i have since installed Ubuntu 14.04LT server edition on my one dev server that i will be testing ZFS and iSCSI target on to my dev windows 2012 R2 server with iSCSI initiator. 

I will be hosting all 12xx of my movies, all 70+ TV shows, as well as my 116,xxx songs for my plex server to serve. As well as several other TB of data.

My current plan is to create a 24-38TB ZFS array using my M1015 cross flashed to IT mode which will allow ubuntu to see them as normal drives and then build 3-4 6 or 7 hdd arrays .

I purchased x3 IBM M1015 cards that are crrossflashed to be HBA's, I plan to use 24 harddrives either 2TB or 3TB. I would create 3 or 4 vdevs each with 6-7 in RAIDZ2. I plan to use my above 10GB fiber cards to direct attach my Ubuntu iscsi target to my windows server 2012 r2 iscsi initiator. It will not exactly be a SAN it will be more of a DAS (direct attached storage rather then storage attach network). 

Spec's:

Motherboard: SUPERMICRO MBD-X8DTE-F-O [/FONT][/SIZE]
[SIZE=2][FONT=verdana]CPU&#8217;s: x2 Intel Xeon X5560 Quad core @ 2.80Ghz
[/FONT][/SIZE]RAM: 24GB DDR3 ECC 1333Mhz
[SIZE=2][FONT=verdana]CPU Coolers: x2 NH-U9DX [/FONT][/SIZE]
[SIZE=2][FONT=verdana]Case: x2 Rosewill RSV-L4500
Caches: x2 Intel 520 160GB (RAID1)
RAID/HBA Cards: x3 M1015 Crossflashed P16 IT Mode
SAS to SATA: x6 HighPoint Int-MS-1M4S SFF-8087

[/FONT][/SIZE]I will be using both of the server cases above to create a custom 8U x30 HDD storage server 

[SIZE=2][FONT=verdana]
I am on mobile now when i get back to my desktop i will share all specs of my upcoming build :)

Thanks so much![/FONT][/SIZE]

---

### Post by lukeiamyourfather on 2014-10-15
> **darren18 said:**
> I purchased x3 IBM M1015 cards that are crrossflashed to be HBA's, I plan to use 24 harddrives either 2TB or 3TB. I would create 3 or 4 vdevs each with 6-7 in RAIDZ2. I plan to use my above 10GB fiber cards to direct attach my Ubuntu iscsi target to my windows server 2012 r2 iscsi initiator. It will not exactly be a SAN it will be more of a DAS (direct attached storage rather then storage attach network).

With 24 drives I'd probably do four RAID Z2 with 6 drives each. It gives a good balance between redundancy, IOPS, and capacity. The machine could lose up to 2 drives per VDEV without loss of data or interruption (up to 8 drives total). Actual usable capacity with that configuration would be roughly 43.6 TiB with 3 TB drives or 29.1 TiB with 2 TB drives. Maybe able to squeeze more out of it with LZ4 compression but I'd pass on LZJB compression because it's not as fast on uncompressable data like media files using an efficient modern codec.

Be sure to use ECC memory with ZFS! It's not an "if" but a "when" you'll run into problems running ZFS without ECC memory. If you haven't yet check out zfs-auto-snapshot which takes rolling snapshots and removes older ones based on criteria the user specifies in the scripts. Snapshots are handy if the data isn't backed up and you accidentally delete something. Of course backup is always better than snapshots because snapshots protect you only so much (can still lose data other ways like rogue hardware, malware, fire, flood, theft, power surge, etc.).

Check out the drives thoroughly before purchase. Make sure they either obey bus and device reset commands or that they have TLER/CCTL/ERC. I'm using ST4000DM000 drives which don't have TLER/CCTL/ERC but they do seem to obey bus and device reset commands. If you get a drive that does neither then they will get kicked form the array if they encounter an unreadable sector (that's bad!) but most drives out there do obey bus and device reset commands. Good luck with the project!

---

### Post by darren18 on 2014-10-15
> **lukeiamyourfather said:**
> With 24 drives I'd probably do four RAID Z2 with 6 drives each. It gives a good balance between redundancy, IOPS, and capacity. The machine could lose up to 2 drives per VDEV without loss of data or interruption (up to 8 drives total). Actual usable capacity with that configuration would be roughly 43.6 TiB with 3 TB drives or 29.1 TiB with 2 TB drives. Maybe able to squeeze more out of it with LZ4 compression but I'd pass on LZJB compression because it's not as fast on uncompressable data like media files using an efficient modern codec.

Be sure to use ECC memory with ZFS! It's not an "if" but a "when" you'll run into problems running ZFS without ECC memory. If you haven't yet check out zfs-auto-snapshot which takes rolling snapshots and removes older ones based on criteria the user specifies in the scripts. Snapshots are handy if the data isn't backed up and you accidentally delete something. Of course backup is always better than snapshots because snapshots protect you only so much (can still lose data other ways like rogue hardware, malware, fire, flood, theft, power surge, etc.).

Check out the drives thoroughly before purchase. Make sure they either obey bus and device reset commands or that they have TLER/CCTL/ERC. I'm using ST4000DM000 drives which don't have TLER/CCTL/ERC but they do seem to obey bus and device reset commands. If you get a drive that does neither then they will get kicked form the array if they encounter an unreadable sector (that's bad!) but most drives out there do obey bus and device reset commands. Good luck with the project!

I just updated the parts list, the Xeons i am using is dual quad cores and 24GB of DDR3 ECC RAM (ECC is on all my servers for obvious reasons). I run crashplan pro to backup my current data (a little over 6TB in total) to backup to the cloud so i will be continuing that practice even after this storage is built and configured. I planned to use Western Digital RE-4 Harddrives. Making 4 RAID Z2 with 6 harddrives each is definitely a preferred option and i like the features of it so that works perfect for what i am trying to achieve.

From my parts list above do you have any recommendations for what you currently have as ZFS servers for data? Is it comparable to what you have/have seen?

---

### Post by lukeiamyourfather on 2014-10-16
> **darren18 said:**
> I planned to use Western Digital RE-4 Harddrives.

Those are awfully expensive drives for what you get. For the price of a 2 TB drive in that line you could get a 4 TB from HGST in the Deskstar NAS line (has TLER/CCTL/ERC).

> **darren18 said:**
> From my parts list above do you have any recommendations for what you currently have as ZFS servers for data? Is it comparable to what you have/have seen?

The case choice seems a bit odd but if you can make it work then go for it. Be sure to either use vdev_id.conf to setup aliases or create the pool with disk-by-id because that's a lot of drives to keep track of, especially without hot swap bays that can be labeled.

---

### Post by darren18 on 2014-10-16
I can purchase the RE4 2TB drives for roughly 50$ a piece. I planned to purchase 30 in total to keep some as spares if I come across ones durning burn in/testing that are failing/defective. And keep the others as cold spares. I will be able to label the harddrives and I'll be keeping documentation on what drives are in which case and there exact location (left,middle,right. 1-5). I am also considering just getting 4TB drives off the bat I'm a little inbetween options :)

The case option is cooling + ascetics, i plan to cut the bottom of one case and leave the top off the other. I will essentially be frankensteining x2 4U cases to create a single 8U 30 hdd case

---

### Post by darren18 on 2014-10-17
I have just confirmed my 10G network cards and SFP's are functional, i created a dev box using Ubuntu desktop + iscsi target and was able to successfully get my windows 2012 with other 10G network card to connect via iscsi initiator AND read/write data. I have not gotten around to configuring ZFS for the test disk yet....but at the moment i only have 1 harddrive to test with...soon to change :D

---

### Post by lukeiamyourfather on 2014-10-17
If you just want to tinker with how ZFS works you can use files as fake drives. So you could create a pool, add fake drives to it, delete one, rebuild it, etc. This is of course just for learning and testing.

[http://www.cuddletech.com/blog/pivot/entry.php?id=446](http://www.cuddletech.com/blog/pivot/entry.php?id=446)

---

### Post by darren18 on 2014-11-12
I managed to get some hardware and get it fired up with a test ZFS raidz2 pool and everything working pretty darn well, until i unplugged the flash drive i used to install ubuntu with and the server reboot....it then lost the zpool because the /dev/sd(x) changed....Any idea how to make it persistent/static/permanent? 

I also managed to make iSCSI work as well :P i'm using a raidz2 pool with 4 harddrives (for now) and on that pool is a zvol that is then mounted via iSCSI. So i have NTFS running with a underlying file system of ZFS. Read/write speeds arent *amazing* but with a pool of 4 harddrives , no cache (yet), i am getting write speeds on average of 88Mbps. Thats also with standard off the shelf seagate drives i had laying around.

---

### Post by bab1 on 2014-11-13
> **darren18 said:**
> I managed to get some hardware and get it fired up with a test ZFS raidz2 pool and everything working pretty darn well, until i unplugged the flash drive i used to install ubuntu with and the server reboot....it then lost the zpool because the /dev/sd(x) changed....Any idea how to make it persistent/static/permanent? 

Use the UUID number for the partition or a partition label.  The device name /dev/sd<whatever> is enumerated upon order of discovery when the host is booted up.  This can change as you experienced when devices come and go.

You can see the UUID's for the partitions with this command```
sudo blkid -c /dev/null -o list
```

---

### Post by darren18 on 2014-11-13
Ah perfect bab1, ill look into it later on today and see what i can come up. But that seems like it is indeed the solution. Thank you! :)

---

