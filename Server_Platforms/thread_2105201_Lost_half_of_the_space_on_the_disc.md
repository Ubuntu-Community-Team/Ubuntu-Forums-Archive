---
title: "Lost half of the space on the disc"
date: 2013-01-15
forum: Server Platforms
---

### Post by pax0r on 2013-01-15
I am using Ubuntu Server 12.04 as Domain Controller (for roaming profiles) with Samba. It is used by less than 10 Windows 7 and XP clients.

I am using RAID 1+0 and the final partition has 1.9TB.

I have strange issue with the disc space. I have no idea where I lost half of it. du command on root folder reports that all files are using about 700GB (most of it in homes as there are all users files) and it is about how much mine users used. But for some reason the left space on the drive is just 500GB!

When I am using df it reports:

/dev/md1              1,9T  1,4T  423G  76% /
But du on root reports: 671G.

So where is mine disc space?

---

### Post by darkod on 2013-01-15
How about du -sh or du -sf (I always mix them up). First move to / and execute something like:
```
cd /
du -sh *
```

The * means it will show the size of all subfolders of /, exactly what you need. It might take a while until it scans everything.

If the second command gives you an error, try du -sf *. I always mix it up. :)

---

### Post by TheFu on 2013-01-15
> **pax0r said:**
> I am using Ubuntu Server 12.04 as Domain Controller (for roaming profiles) with Samba. It is used by less than 10 Windows 7 and XP clients.

I am using RAID 1+0 and the final partition has 1.9TB.

I have strange issue with the disc space. I have no idea where I lost half of it. du command on root folder reports that all files are using about 700GB (most of it in homes as there are all users files) and it is about how much mine users used. But for some reason the left space on the drive is just 500GB!

When I am using df it reports:

/dev/md1              1,9T  1,4T  423G  76% /
But du on root reports: 671G.

So where is mine disc space?

Could it be in deleted files that are still **open** by someone using a program?  For example, if a video file is being watched, but the file is removed, the directly entry gets removed so that nobody can find and open it, but the inode remains until it is closed.  Perhaps large backup sets are still open? I dunno.

Using any LVM snapshots?

---

### Post by pax0r on 2013-01-15
Thanks for your responses!
@darkod
I tried it. Thats the problem, du from / show only about 700GB occupied so I cant find where is the rest of the disc :D

@TheFu
How could I find such open but deleted files?
I already tried to restart system to kill all process but just after start it already show 1.4TB occupied.
I am not using LVM snapshots (but I do a copy of important data over samba every day via cron).

It really looks like used space is calculated twice for which I should have on disc...

---

### Post by TheFu on 2013-01-15
/ is probably not where your disk array is mounted.  Doing a **du /** will only show the storage on that single file system.

The easiest way to see all the mounted file systems and use data is:
$ **df -k**

Then you can use df -k /whatever-the-mount-point-is to return only the specific file system you care about.

How to find deleted, yet open files?  Search for inodes that don't have directory entries. I don't know how to do that off the top of my head - there must be a script.  Rebooting the box will close all files, so if you've done that, you are done.  Sometimes we can't reboot machines for months and need to find who/which process is holding onto some specific files.

There's a command - **lsof** - list open files. It is very powerful and works for any file - including sockets and pipes.

---

### Post by pax0r on 2013-01-15
Ok, so for sure I can exclude not closed files (As I've done restart and just after it is still the same).

To be honest mine partition is actualy mounted at /.

When I check size of all files on that partition is the half of the used space and I have no idea where is the rest of it...

It is a file server so storage is very important. And when I am checking size of all files created by users it is 700GB so I have no idea where the other 700GB had gone...

Could it be something with size of the blocks? But I dont belive that there are AS much AS small files...

---

### Post by TheFu on 2013-01-15
> **pax0r said:**
> Ok, so for sure I can exclude not closed files (As I've done restart and just after it is still the same).

When you reboot, all files are closed - PERIOD - well unless you are running a cluster and the mount automatically fails over and back again, but you'd know much more about this stuff if that were the case.

> **pax0r said:**
> To be honest mine partition is actualy mounted at /.

When I check size of all files on that partition is the half of the used space and I have no idea where is the rest of it...

It is a file server so storage is very important. And when I am checking size of all files created by users it is 700GB so I have no idea where the other 700GB had gone...

Could it be something with size of the blocks? But I dont belive that there are AS much AS small files...

Have you tried finding all the really large files on the machine? Perhaps find all the files over 2G and start from there.  

Users store all sorts of crap on network storage.  It is a good idea to enable user quotas.

---

### Post by pax0r on 2013-01-15
> **TheFu said:**
> 
Users store all sorts of crap on network storage.  It is a good idea to enable user quotas.

No, no, that is exactly mine problem! All user content is about 650GB!
I crawled through the drive and all files together are using about 700GB! And still it reports that 1.4 is in use...

---

### Post by TheFu on 2013-01-15
> **pax0r said:**
> No, no, that is exactly mine problem! All user content is about 650GB!
I crawled through the drive and all files together are using about 700GB! And still it reports that 1.4 is in use...

How did you "crawl through the drive?"

---

### Post by pax0r on 2013-01-16
eh... I found the problem.
It was like allways trivial and stupid...

I am doing backup over samba of almost everything.

And it looks like one day samba share wasnt mounted and so it copies everything to /mnt/backup on local drive instead of samba share.

Again when I was trying to find missing space share was mounted ok so I couldnt find this files (as /mnt/backup was now poiting to the samba share, not local dir).

Anyway thanks for your help!
Any way to avoid this in future?

---

### Post by TheFu on 2013-01-16
> **pax0r said:**
> eh... I found the problem.
It was like allways trivial and stupid...

I am doing backup over samba of almost everything.

And it looks like one day samba share wasnt mounted and so it copies everything to /mnt/backup on local drive instead of samba share.

Again when I was trying to find missing space share was mounted ok so I couldnt find this files (as /mnt/backup was now poiting to the samba share, not local dir).

Anyway thanks for your help!
Any way to avoid this in future?

You aren't the first person to hit this exact issue. I have too. There are a number of ways.
a) Always check for a known file inside a mounted file system to validate it is actually mounted.
b) Place a NO-MOUNTED file in the top directory of the mount point and look for it before starting the backup job. If it exist, the mount ain't there.
c) Check your current mounts (mount or df) to see if the specific backup area is mounted
d) Stop using samba - it only leads to evil. ;)

Even if you do "d", one of the others makes sense too.

I'm using "a" - after a similar issue a few yrs ago.

There was a thread here about this same thing a few months ago. I think rsync was being used and the guy using it considered it a program failure to not know that the place he wanted all his backups placed wasn't there. Interesting perspective.

When you store backup files on an NTFS share, how do you ensure the owner/group/permissions are maintained?  How do you handle softlinks vs hardlinks vs normal files?  There are lots of file system issues using NTFS, methinks.

---

### Post by pax0r on 2013-01-16
yes, I am aware of the downsides of this backup aproach. I used it as we had spare NAS with only samba avaible.
Thanks for advices, I think I wll modify backup script to check if samba is mounted next time.

---

