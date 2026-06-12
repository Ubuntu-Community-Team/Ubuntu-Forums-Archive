---
title: "RAID 1 of OS device"
date: 2016-08-03
forum: Server Platforms
---

### Post by courtney2 on 2016-08-03
I'm looking at doing a computer setup with 3 hard drives doing RAID-Z1, and I also want to have 2 SSDs to mirror the OS disk, so if one SSD fails I can limp along with the mirrored one while I rebuild a new SSD. Is this possible? And how? I want it to look like what FreeNAS does (section 5.3.1) [https://doc.freenas.org/9.3/freenas_system.html#boot](https://doc.freenas.org/9.3/freenas_system.html#boot)

---

### Post by darkod on 2016-08-04
You can configure mdadm raid1 array for the OS and raidz1 array for the data.

But I think a raid1 of SSDs is an overkill, especially since default ubuntu server install is 2GB. To dedicate not one but two SSDs to it would be a waste...

Besides, depending on the applications and roles you intend to run, the OS can be easily (and fast) recovered by doing a new install and copying few important config files... That's one idea...

---

### Post by mastablasta on 2016-08-04
i run it form USB 3.0 driver and i can't say i notice any sloweness. OS disk is rarely used. server has plenty of RAM. i guess if there was more trafic it might need mor eof the OS disk. 

DATA is on hard drives in raid1 - also haven't noticed any slowness on that end.

---

### Post by courtney2 on 2016-08-07
I was afraid it would be overkill in terms of performance, but I really wanted to do SSDs more for reliable flash than performance. Plus it was hardly much more for the SSDs vs good flash drives. This will be a busy computer though so I'm hoping it wasn't a waste. I wanted to do RAID1 of the OS disk because I need at least 99% uptime. I would rather like a notification of a dead drive and have time to recover it instead of scurrying to recover it with extra downtime. I would consider returning them in place for more RAM but even with the money regained, I still wouldn't have enough for additional RAM. Now that I think of it though, it might be a wise idea to do the flash drives instead. It might be much easier to have more easily accessible hardware than a "special" item like an SSD

---

### Post by mastablasta on 2016-08-08
what kind of server is this? is it a business server? if so, leave the SSD. flash drives can fail without warning. if you need high uptime - did you get a hot swap server? that would be ideal. in case drive fails the other one should continue to work while you replace the failed one.

SSD are as much as USB now? i got 8 Gb good quality usb for 5 EUR. i don't need the uptime so badly. and the only thing with my serve ri sthat the bugger wants to boot from the empty USB, so i haven't made an efficient backup of the OS yet. but i do image it manually about every month. aside from update i didn't change much settings. so if it goes bad again, i can restore from last good image, do the update and i am back in business. 

another option i was thinking might be a good alternative ot RAID is simply doing porpper backups form the system disk. that way you can restore the exact point  of failure. of course you can also use ZFS or BTRFS to do the imaging, but they might (or not) slow down the whole thing. i guess it all depends on how much the data is changing on the OS drive.

---

### Post by courtney2 on 2016-08-08
This is for business. Well to be fair the 64GB is relatively close in price to a nicer, faster flash drive. A standard 64GB flash drive in the US is about $18 USD and an 8GB is about $9 USD. 

The board determines whether or not the drives are hot swappable right? Honestly I couldn't find much info on that. My case allows for easy swapping of drives but not sure if that matters if the board supports it or not. Should though because it is a server board.

What do you mean by imaging with ZFS or BTRFS, are you talking about snapshots? I saw btrfs snapshots are pretty easy to restore from. I guess that's another question to ask. If I want to RAID1 the storage drives what's the best way to do this? EXT4 boot partition and then do the rest with BTRFS and do mdadm (I think I messed that up) for the mirror of the OS disk? I don't know how much will be changing on the OS disks aside from updates since I plan on doing LXD containers within the ZFS pool. I might be diving head in to something I'm novice about (IE RAID and containers) but the owner of the company knows I'm still learning so I have a greater level of forgiveness as long as things don't blow up and cause him total hell! The final product will be very busy though

---

### Post by mastablasta on 2016-08-09
well you plan for ZFS, then just use ZFS+Raid1.

not all server boards have hot swapping, though those more expencive ones should have it. they might also have a raid controler (if you want to do hardware raid). the thing to remember when setting up is that raid is not a backup solution. but zfs with raid just might be (i am not sure). you need versioned back ups of the os which you can restore quickly, on demand. there is plenty of threas arround here on various solutions. since it's a business it might also make sense to have offsite backups

---

### Post by courtney2 on 2016-08-09
> **mastablasta said:**
> well you plan for ZFS, then just use ZFS+Raid1.

not all server boards have hot swapping, though those more expencive ones should have it. they might also have a raid controler (if you want to do hardware raid). the thing to remember when setting up is that raid is not a backup solution. but zfs with raid just might be (i am not sure). you need versioned back ups of the os which you can restore quickly, on demand. there is plenty of threas arround here on various solutions. since it's a business it might also make sense to have offsite backups

I will investigate the board further and hope it does. I did buy a higher end board so we will see. I plan on doing weekly backups and keeping the drive offsite, maybe even have 2 backup drives for additional safety

---

### Post by mastablasta on 2016-08-10
otherwise a good, light command line backup tool is rdiff-backup.

if you plan to use server to backup other computers on the LAN there is urbackup or something like that which manages and pulls files from PC all via a descent GUI.

---

