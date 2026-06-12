---
title: "Mission Critical File Server Quick Recovery"
date: 2009-12-10
forum: Server Platforms
---

### Post by d0lt on 2009-12-10
I need some pointers or links to current best practices for a mission critical file server in a business.  I've looked around the forums here, followed some links, but I feel like I'm missing the best info.

I installed Ubuntu Server 9.04 to replace a Netware file and print server.  Server is a file server using SAMBA to serve up files to DOS clients running a DOS application.  Server also has a separate ethernet connection to the office "Windows" network and the Internet.

Data files are 400MB total.  They grow by 4 MB per week.

1. What are the best methods for backups in 2009/2010?  Tapes are out of the question, flash drive or external hard drive seem to make the most sense.   Server guide mentions Bacula, but that looks outdated and too steep a learning curve for a single server system.

 - I currently have two DOS flash drives installed in USB slots. I have scripts using rsync doing a full backup once per week, then an incremental every night.  These flash drives can be pulled and taken offsite in case of emergency.
 - I also set up a separate backup directory where data is copied every two hours using rsync.  So they have a running snapshot of files in multiple directories.  They connect to this using separate SAMBA shares, and use this for recovering accidental file deletions during the work day.
 
I think I should add an external hard drive, or maybe a RW DVD.  Any suggestions?
  
2. If the hard drive crashes, how to recover within 1 hour?  What should I do NOW to be ready for this event?

 A. CD with Ubuntu, CD with config files, CD with data and a spare hard drive - Would take more than an hour, I guess.
 B. Have a second hard drive installed in the server with the same install of Ubuntu, in system but unplugged.
 C. Have a second hard drive installed in the server with the same install of Ubuntu, and data files being swiped over every hour or two.
 D. A complete system backup to DVD, flash drive or external hard drive that could then be used to restore OS to a new hard drive?
 E. Your suggestions please...
 
Any links to current 2009/2010 best practices, robust scripts, etc are appreciated.

---

### Post by craigp84 on 2009-12-10
Hi,

It sounds like you've got your head screwed on the right way, you seem to be in pretty good shape already.

I think you've nailed the backup options -- flash or HDD. To your existing setup, i'd add rotation of backup media. Physically unplugging the drives means a misplaced "sudo rm -rf" wont destroy your online hot-copies on the flash drives. Also means you're in a slightly better place when a flash drive fails.

Rsnapshot does similar to what you've implemented already. I'd only consider switching to it if you feel your implementation is rough around the edges, otherwise its the same result of what you have already.

If you attach a large external hard drive, you can afford to keep quite a few archive copies (hourly, daily, weekly, monthly, yearly). These are seperate to backups.

2. Good question.

First option -- RAID, software or hardware, doesn't really matter for this volume of data. Once harddrive dies == 0 downtime, and you can go get a new hard drive meantime.

Make sure the data partition where all this is stored, is actually its own partition. Makes recovery much simpler if you're recovering a seperate partition / mount point. The data definately shouldn't be on the same partition as the OS.

I think if you have RAID, then the next layer of defence should be external to the server. This next layer would be to recover when the server gets nuked (motherboard issues, power supply dies etc.)

A second standby system which is switched off, except maybe once a week to load on a fresh backup -- this procedure conveniently also ticks off the weekly "test backups are ok" task in quite a safe & easy way.

---

### Post by kewlrichie on 2009-12-11
I usually keep my data on a different partition (in my case it's /home) so I like to make clonezilla image every month so I have a system back up ready to be cloned to a new drive if something goes wrong and of course I keep a daily back up of my data and configs just incase something goes wrong. Clonezilla is pretty handy unless you have such a simple system that a reinstall and reconfigure will only take you a sort while. In my case I spent alot of sweat and tears getting my mail server just right I would hate to do it over again. So I always like to have a clonezilla image just for safe keeping and without the data should be pretty small

---

### Post by craigp84 on 2009-12-11
Clonezilla rocks.

---

