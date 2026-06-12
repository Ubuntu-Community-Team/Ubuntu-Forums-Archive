---
title: "Automatic Hard Drive Backups"
date: 2008-01-03
forum: Server Platforms
---

### Post by papayiya on 2008-01-03
Hi everyone,

Has anyone found a good solution for automatically backing up an entire hard drive using Ubuntu?  I'd like to have a second hard drive in my server that gets shadowed (maybe not instantaneously, but soon after) so that if the main hard drive crashes all I would need to do is plug in the backup hard drive.

I'm curious to know your experiences/thoughts,
Thanks,
George

---

### Post by hockey97 on 2008-01-03
hi I havent found one. but  just wanted to say would it be smart as to have a server to  mainly have it automaticly backup?? like if you get a virus  and with the new backup you back that  up with the new backup. If that virus can crash your computer  the the backup would be pointles if your back up has the same virus.

I am look for a good way to backup. I was thinking to use my second computer to save a backup of the main server.  I mainly want to find some way tp backup  2 times one would be a base and then the other one would be something like an automatic backup.

---

### Post by gilgongo on 2008-01-03
I just pay money. Amazon S3 via JungleDisk. Infinite storage. I just back up my home directory, by the way.

---

### Post by MJN on 2008-01-03
There are many options available to you, one being of the isntantaneous type using RAID whereby a second disk contains an exact mirror of the first at all times. Alternatively, you can employ any backup solution that can be scheduled to keep the disks in sync periodically.
 
I use the latter method, to both a local backup disk and offsite to a disk in my brother's machine, using rsync. It is perfect for my needs - simple to use, ultra-reliable, low-level filesystem access so as not to tie me into any particular recovery method/tool (and providing easy access to invidivdual files in the backu), and efficient (only copies files that have changed, and indeed only those *parts* of the files - perfect for the offsite (slow link) transfer). The important aspect to my setup is that is has been tested in a real live environment - I had my first ever disk crash and the recovery went smoothly.
 
I would suggest searching the archives and the multitude of discussions on the web before diving in to any one solution - learning what's available will help you define your own requirements and hence the best solution to fit *your* needs.
 
Mathew

---

### Post by papayiya on 2008-01-03
> **gilgongo said:**
> I just pay money. Amazon S3 via JungleDisk. Infinite storage. I just back up my home directory, by the way.

Yeah that's an option, but I want to be able to connect (on-demand) the backup hard drive and have the server function normally.  Now if we could one day boot from S3 (even just the home directory) that would be pretty crazy.. but I would imagine bandwidth costs would become excessive.

---

### Post by papayiya on 2008-01-03
> **MJN said:**
> There are many options available to you, one being of the isntantaneous type using RAID whereby a second disk contains an exact mirror of the first at all times. Alternatively, you can employ any backup solution that can be scheduled to keep the disks in sync periodically.
 
I use the latter method, to both a local backup disk and offsite to a disk in my brother's machine, using rsync. It is perfect for my needs - simple to use, ultra-reliable, low-level filesystem access so as not to tie me into any particular recovery method/tool (and providing easy access to invidivdual files in the backu), and efficient (only copies files that have changed, and indeed only those *parts* of the files - perfect for the offsite (slow link) transfer). The important aspect to my setup is that is has been tested in a real live environment - I had my first ever disk crash and the recovery went smoothly.
 
I would suggest searching the archives and the multitude of discussions on the web before diving in to any one solution - learning what's available will help you define your own requirements and hence the best solution to fit *your* needs.
 
Mathew

Hi Mathew,

Very interesting, thanks, I'll look into that.

---

