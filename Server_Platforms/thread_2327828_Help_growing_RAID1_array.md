---
title: "Help growing RAID1 array"
date: 2016-06-14
forum: Server Platforms
---

### Post by drfox on 2016-06-14
Hello. I ran out of space on my server. I had 2 TB drives configured as md2
I followed this guide [http://http://www.zedt.eu/tech/linux/migrating-existing-raid1-volumes-bigger-drives/]("http://http://www.zedt.eu/tech/linux/migrating-existing-raid1-volumes-bigger-drives/") to grow them using 4TB drives.

This is what I get after issuing this command: mdadm --grow /dev/md2 --size=max

root@litterbox:/home/drfox# mdadm --detail /dev/md2
/dev/md2:
        Version : 1.2
  Creation Time : Sun Dec 22 09:40:09 2013
     Raid Level : raid1
     Array Size : 3906886471 (3725.90 GiB 4000.65 GB)
  Used Dev Size : 3906886471 (3725.90 GiB 4000.65 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Tue Jun 14 18:28:28 2016
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : Microserver:2
           UUID : dda8e4f0:2fbe4703:da928de0:cc547ce4
         Events : 4783378

    Number   Major   Minor   RaidDevice State
       2       8       49        0      active sync   /dev/sdd1
       3       8       33        1      active sync   /dev/sdc1

so it appears that the machine knows how large the drives are, but when I issue the command 
root@litterbox:/home/drfox# resize2fs /dev/md2
resize2fs 1.42.13 (17-May-2015)
resize2fs: Device or resource busy while trying to open /dev/md2
Couldn't find valid filesystem superblock.

I have rebooted my server and I get this when I ssh into it:
Welcome to Ubuntu 16.04 LTS (GNU/Linux 4.4.0-24-generic x86_64)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

  System information as of Tue Jun 14 18:28:52 CDT 2016

  System load:  1.34                Processes:            165
  Usage of /:   24.5% of 213.35GB   Users logged in:      0
  Memory usage: 2%                  IP address for eth0:  192.168.15.15
  Swap usage:   0%                  

  => /data is using 95.4% of 1.79TB

fdisk -l gives me the following (only showing pertinent information):
Disk /dev/md2: 3.7 TiB, 4000651746816 bytes, 7813772943 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/mapper/Microserver-data: 1.8 TiB, 2000259383296 bytes, 3906756608 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

/data is my only partition on /dev/md2

How do I get /data to use the entire 4TB?

Thanks for your help.

---

### Post by darkod on 2016-06-15
First of all, are you using /dev/md2 or /dev/mapper/microserver-data? Because the latter looks like lvm.

Also, /data needs to be unmounted to do filesystem resize. If you are using /dev/md2 directly simply unmount /data and resizefs /dev/md2 should work.

If you are using lvm you probably need to resize the VG first (check if its current size is 2TB or 4TB) then rezise the data LV, and then resize its filesystem.

---

### Post by drfox on 2016-06-15
Thank you!
I had totally forgotten about lvm.
I followed this tutorial [http://http://www.tecmint.com/extend-and-reduce-lvms-in-linux/]("http://http://www.tecmint.com/extend-and-reduce-lvms-in-linux/") to resize the volume.
It took me 5 minutes after you pointed me in the right direction.
Larry

---

