---
title: "Re: Ubuntu as NAS: what can I use for automatic backup?"
date: 2018-09-28
forum: Server Platforms
---

### Post by weeedos on 2018-09-28
> **TheFu said:**
> Nobody has the "ideal" setup, only the best for our abilities and knowledge at the time. Then over time we learn more and our skills expand.

In the 1990s, I'd ZIP files together and copy to a different disk. Then I moved to using tar and gzip - tar retains the permissions. But tar was designed for 50MB storage and really can't be scaled beyond 500MB. Think of tar as ZIP. Would you try to backup a system using ZIP? Round 1996, I stopped using tar for backups.

Next was dump/restore. These are built-into many Unix systems. They are part of the weekly "full" and daily "incremental" backup method. After a failure, the restore is a multi-step process. Restore the most recent "Full", then each of the incremental backups in the correct order. Some modern backup tools still working this way, like duplicity and the tools based on it like deja dup, duplicati, ... Only used these for a few years.

Then I moved to rsync-based backups using hardlinks for versioning. There must be 20 tools that work this way. rsnapshot, rbackup, 500 personal scripts, back-in-time, many, many more. The issue with rsync-based versioned backups is that only the last permissions are stored. Permission changes over time are very important for OS and application files. As applications change, the permissions for the data files often become more secure. If you just backup HOME directories, then this isn't often very important. I was "pushing" the backups from each client to the server. I used that method until around 2009.

All the time this was happening, I was learning other things and code version control was something I started with in the 1980s. This got me addicted to having simple access to different versions. rsync with hardlinks was handling it, but the storage used had to be Unix (not NTFS) to retain the last permissions.

Around 2008, our systems all switched over to being virtual machines. Using rsync the backups were taking longer and longer. Soon we couldn't finish them all in the allowed overnight period. I had to find a better solution and while I was at it, fix some other areas where the backups were lacking. I looked at about 20 different backup tools. duplicity checked all the boxes for being an amazing tool. Unfortunately, my testing showed it was slow and on Windows, painfully slow was putting it nicely. Over 8 hrs to backup 100GB?!!! At the time, it wasn't ready.

rdiff-backup checked almost all the boxes, had a command line that looked like rsync, it was FAST - VERY FAST, and it retained file permissions with the versioning data. Testing showed that backups were like rsync the first time and 1-3 minutes for every backup after that. The last backup is presented like an rsync mirror, which is wonderful. Older versions are stored as gzip-diffs, so storage use is minor. Only changes. This also explains why the backups are so very fast. rdiff-backup and "push" or "pull" the backup data. It works over ssh like rsync does, so all the normal ssh authentication and security works. 

Plus a minor issue was always a hassle - scheduling when each client was allowed to "push" the backup to their assigned server without conflicts.

I started out using the "push" method, until I thought about security a little more. Some of my systems are high risk. They provide services over the internet and if someone is able to hack in and take control, escalate to root, then use ssh to connect to the backup server, all our data can be wiped. Sure, something like crypto-locker wasn't likely to do that, but systems of all sorts are hacked every day. Linux isn't immune. By switching the "pull" backups, the authentication for backups can be locked down to just the backup servers which aren't on the internet-facing LAN. More security that retains the capabilities is good. And the scheduling for each backup was removed. The server would backup each client machine in turn. 

Then crypto-locker malware became "a thing". I talked over the new attack vector with some admin friends and security professionals. We call came to the realization. "Pull" and versioned backups were the solution. If a client gets encrypted files, the prior version will still be there, available for restore. 1 day of data loss. Plus the size of the backup would be huge, so the admin would notice that quickly. I get daily reports about each system in my backup responsibilities. An example:
```
=== Backups  spam2 === 
StartTime 1537510264.00 (Fri Sep 21 02:11:04 2018)
EndTime 1537510272.69 (Fri Sep 21 02:11:12 2018)
ElapsedTime 8.69 (8.69 seconds)
TotalDestinationSizeChange 1309 (1.28 KB)
```
That system doesn't have **any** data, it is just an email gateway. 9 sec to backup. Quite acceptable. My desktop system takes a little longer.
```
=== Backups  lubuntu === 
StartTime 1537506906.00 (Fri Sep 21 01:15:06 2018)
EndTime 1537507183.25 (Fri Sep 21 01:19:43 2018)
ElapsedTime 277.25 (4 minutes 37.25 seconds)
TotalDestinationSizeChange 39783642 (37.9 MB)
```

All raspberry pi systems have limited I/O capabilities. All that I/O goes through a single USB2 controller ... so total, theoretical bandwidth is limited to 480Mbps. Nobody ever gets that. It is shared by all USB ports and the network port. 100Mbps is the ethernet and it does fill that. For storage I/O, USB2 is fast enough to stream hidef movies, but not really sufficient to backup TB of data commonly seen these days. Even 100G will be painful, IMHO.

A Rock64 SBC or ODroid do have GigE networking and I think both support SATA/USB3 connections. That changes everything. The R-pi v3 claims to have a GigE network port, but it only achieves about 280Mbps due to the USB2 shared bus.

But if you don't have something better, **any** backup, even simple rsync mirrors without any versioning, are better than nothing. OTOH, rdiff-backup commands are almost the same as rsync and provide so much more capability.

And don't for get to use lvm snapshots when you are doing backups, so the services and system are still available to users.

Wow, this is a very extensive reply... thanks for sharing your knowledge and experience, its priceless for an inexperienced user like myself. 

I am planning to set up home backup/NAS solution based on [ODROID-XU4]("https://www.hardkernel.com/main/products/prdt_info.php") and [CloudShell 2 Case2 for XU4]("https://www.hardkernel.com/main/products/prdt_info.php?g_code=G150575879656") with two 2TB WD Reds in RAID1 configuration. I have one windows 10 machine, 1 MacBook Pro, one iPhone, and one Android device. Hopefully everything can be backed up... Also, my wish is to run [Nextcloud]("https://nextcloud.com") server on the same ARM based NAS/backup server.
For now I have more questions then answers (starting with what version of Ubuntu should I use for this purpose, considering automatic security updates etc.).

Hopefully there are people that had similar project and can help with good advice.

---

### Post by QIII on 2018-09-28
Moved to its own thread from [here]("https://ubuntuforums.org/showthread.php?t=2401243").

Please to do not hijack the threads of other users.  Such threads become confusing for the original poster, for all those who are trying to to help -- and for you.  Please start your own threads with your particular issues if your post is not directly related to solving the OP's issue.

Thanks.

---

