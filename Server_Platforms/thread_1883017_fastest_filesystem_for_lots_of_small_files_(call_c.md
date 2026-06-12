---
title: "fastest filesystem for lots of small files (call center recording)"
date: 2011-11-18
forum: Server Platforms
---

### Post by gregfaust on 2011-11-18
I have a server that provides NFS storage to 8 custom asterisk based middleware machines that are used to record phone calls.  Typically I record about 30k phone calls per day.  I have see as many as 500 concurrent phone calls being recorded.  The average file size is 350K.  It seems that the 500 simultaneous calls combined with relatively small file size generates almost perfectly random IO, so although I have plenty of bandwidth to disk, I may have a bottle neck in the number of IOPS per second as load increases

setup:
Dual Quad Core server with 16GB RAM
Ubuntu 10.04 64-bit
16x 1TB disks
mdadm RAID10 array of 12 disks plus 3 spares and a dedicated disk for root

Currently I am using ext4 with the following options:
mkfs.ext4 -b 4096 -E stride=32,stripe-width=192
tune2fs -o journal_data_writeback
errors=remount-ro,data=writeback,nobh,barrier=0,relatime,nouser_xattr,commit=60

This setup seems to give pretty good write performance characteristics.  My system is 99% write and 1% read.

In the near future load will double.  Does anyone have any advice for a filesystem that may be faster than ext4?  

I really dont' want to purchase 16TB worth or SSD.  I backup this system 6 times per day with rsnapshot, so I'm willing to trade safety for performance (within reason).

I'm thinking BTRFS because the "copy on write" characteristics may help turn the random IO into linear IO, but it scares me that I don't have a fsck tool for BTRFS.  ZFS would be perfect but doesn't exist within Linux.

Any advice is appreciated.

---

### Post by SeijiSensei on 2011-11-18
Have you tried ext2 which has no journaling?  ext4 may be the "latest and greatest" of the extended filesystems, but it has more overhead than ext2.

---

### Post by Jonathan L on 2011-11-18
> **gregfaust said:**
> I have a server that provides NFS storage to 8 custom asterisk based middleware machines that are used to record phone calls.  Typically I record about 30k phone calls per day.  I have see as many as 500 concurrent phone calls being recorded.  The average file size is 350K.  It seems that the 500 simultaneous calls combined with relatively small file size generates almost perfectly random IO, so although I have plenty of bandwidth to disk, I may have a bottle neck in the number of IOPS per second as load increases

setup:
Dual Quad Core server with 16GB RAM
Ubuntu 10.04 64-bit
16x 1TB disks
mdadm RAID10 array of 12 disks plus 3 spares and a dedicated disk for root

Currently I am using ext4 with the following options:
mkfs.ext4 -b 4096 -E stride=32,stripe-width=192
tune2fs -o journal_data_writeback
errors=remount-ro,data=writeback,nobh,barrier=0,relatime,nouser_xattr,commit=60

This setup seems to give pretty good write performance characteristics.  My system is 99% write and 1% read.

In the near future load will double.  Does anyone have any advice for a filesystem that may be faster than ext4?  

I really dont' want to purchase 16TB worth or SSD.  I backup this system 6 times per day with rsnapshot, so I'm willing to trade safety for performance (within reason).

I'm thinking BTRFS because the "copy on write" characteristics may help turn the random IO into linear IO, but it scares me that I don't have a fsck tool for BTRFS.  ZFS would be perfect but doesn't exist within Linux.

Any advice is appreciated.

Hi 

Just as Seiji was thinking: why not cut some layers out?  My first question would be: why RAID at all?  Why not have lots of mounts being written to at random?  If you go to a non-journaling filesystem you'll be in much better shape for overhead.

Are you able to change anything else, like the directory structure or any intervening software?

I'd also think about the directory tree being written to: you might have  a lot of directory lookup which you might be able to get rid of by  planning how they're used.

I presume if the file server crashes you lose the current writing conversations anyway? Or do the Asterisk sytems hold off until the file server is back?  Do they write real-time or just write the conversation at the end of the call?

And another idea: do the conversations really need a file each?  

But perhaps the only thing you can change easily is the filesystem

Interesting problem!  Do let us know how you progress.

Just some thoughts.

Kind regards,
Jonathan.

---

### Post by gregfaust on 2011-11-18
> **Jonathan L said:**
> Hi 

Just as Seiji was thinking: why not cut some layers out?  My first question would be: why RAID at all?  Why not have lots of mounts being written to at random?  If you go to a non-journaling filesystem you'll be in much better shape for overhead.

Are you able to change anything else, like the directory structure or any intervening software?

I'd also think about the directory tree being written to: you might have  a lot of directory lookup which you might be able to get rid of by  planning how they're used.

I presume if the file server crashes you lose the current writing conversations anyway? Or do the Asterisk sytems hold off until the file server is back?  Do they write real-time or just write the conversation at the end of the call?

And another idea: do the conversations really need a file each?  

But perhaps the only thing you can change easily is the filesystem

Interesting problem!  Do let us know how you progress.

Just some thoughts.

Kind regards,
Jonathan.

Unfortunately, I can not change the directory structure.  The middleware is hard coded with a structure of /year/month/dayOfMonth

I also can't get away from having 1 file per recording.  At this point, we are considering this a legacy system and we just need to keep it on life support while the new platform (based on Voxeo) is being built and tested.

If the file server dies, each middleware machine will use it's internal disk for recording until NFS is mounted again, which needs to be within a few days or the 40GB internal disks will fill up.

The files are written "real time".  Each file is a .WAV file written in wav49 format which is basically a way of storing G.711 and G.729 audio stream from the SIP session without a need to transcode, as a bonus, these formats are highly compressed.

I guess I could also go with some sort of batch process where calls are recorded to a tmpfs (RAM) and then moved to disk on an interval.  I have seen other folks who have had success with this config for 10s of thousands of calls.  I would need to get approval from the business, because as calls are recorded, the recordings will be unavailable until they are moved to disk which might cause a delay in the availability of the recordings.

Before I go the route of writing scripts and cron jobs for batch processing, I'd like to squeeze every drop of performance out of the current config.

What about ext4 with the journal disabled?

I also saw this which seems interesting: [http://zfsonlinux.org/](http://zfsonlinux.org/)

---

### Post by rubylaser on 2011-11-18
ZFS is great, but isn't known as a speed champion based on all of the things that it does.  And, NFS is particularly slow because every write action is synced.  You either need to disable the default sync behavior, or setup a mirrored ZIL device ([DDRdrive X1]("http://www.ddrdrive.com/") are great, but cost around $1,500 with their discount).  I have a couple Solaris 11 ZFS servers that I manage, and they're great, but I wouldn't want to try what your suggesting on ZFS without alot more RAM and sync disabled on my NFS shares.

ext2 is a good idea to start with.  Or an SSD array, because this sounds like an IOPS problem more than anything.

---

### Post by SeijiSensei on 2011-11-18
> **rubylaser said:**
> NFS is particularly slow because every write action is synced.

+1

I forgot about the NFS mounts.  Try using async in the export options.

---

### Post by Jonathan L on 2011-11-18
Hi again Greg

Thanks for answers previously:

> I can not change the directory structure.  The middleware is hard coded with a structure of /year/month/dayOfMonthCan you tell us what the eight Asterisk systems are writing to underneath the /mountpoint/y/m/d ?  Do they have a subdirectory each or are they putting all 30,000 files/day in the one directory (uniquised with phone number and time of day or something like that?)

> The files are written "real time".How long a call makes a 350 kbyte file?  My understanding is that G.711 is 64 kbit/s which would mean an average call time of 350/8=43.75 sec, and the G.729 is 8kbit/s=350 sec.  Just trying to get a sense of the rates, as they're 8-fold different.

NFS: could you tell us which version you're using, and whether it's over TCP or UDP?

And could you give a suggestion of what is the business consequence of losing a call's recording?  I suppose I'm asking if it's "quality and training purposes" (prove you were offensive to the electricity company), "contractual share dealling" (prove they did order all those Icelandic bonds) or "life and death" (replay the address of the 999 call).  Wouldn't want to suggest anything that's completely innappropriate to your organisation.

Kind regards,
Jonathan.

---

### Post by gregfaust on 2011-11-18
Thanks for all the replies.

> **Jonathan L said:**
> 
Can you tell us what the eight Asterisk systems are writing to underneath the /mountpoint/y/m/d ?  Do they have a subdirectory each or are they putting all 30,000 files/day in the one directory (uniquised with phone number and time of day or something like that?)


All 8 asterisk machines record to the same directory for each day, basically all of the information about the call other than the actual recording is stored in a SQL database.

> **Jonathan L said:**
> 
How long a call makes a 350 kbyte file?  My understanding is that G.711 is 64 kbit/s which would mean an average call time of 350/8=43.75 sec, and the G.729 is 8kbit/s=350 sec.  Just trying to get a sense of the rates, as they're 8-fold different.


At a glance it seems we have a mix of about 90% short calls and 10% long calls, with not much in between.  I don't have a quick way to get statistics on the ratio of G.711 vs G.729.

> **Jonathan L said:**
> 
And could you give a suggestion of what is the business consequence of losing a call's recording?  I suppose I'm asking if it's "quality and training purposes" (prove you were offensive to the electricity company), "contractual share dealling" (prove they did order all those Icelandic bonds) or "life and death" (replay the address of the 999 call).  Wouldn't want to suggest anything that's completely innappropriate to your organisation.


It's not life and death, but it's potentially a life changing event if we can't find a recording, i'm afraid I can't go into detail.

> 
NFS is particularly slow because every write action is synced.


NFS is exported with the async and no_subtree_check options.  This has a huge impact on concurrency.  If we were running synchronous NFS we would have hit the limit on our call recording solution a long time ago.  Using NFSv3.

One thing I haven't tried is disabling the journal on ext4 (similar to ext2).
> 
tune2fs -O ^has_journal /dev/sdx


---

### Post by pdoes on 2011-11-18
So if ZFS would be perfect why not install FreeBSD?

---

### Post by Jonathan L on 2011-11-20
Hi Greg

> 

[LIST]
[*] All 8 asterisk machines record to the same directory for each day
[*] At a glance it seems we have a mix of about 90% short calls and 10% long calls, with not much in between.
[*]I don't have a quick way to get statistics on the ratio of G.711 vs G.729.
[*]potentially a life changing event if we can't find a recording
[*]NFS is exported with the async and no_subtree_check options.  This has a huge impact on concurrency.  If we were running synchronous NFS we would have hit the limit on our call recording solution a long time ago.
[*]Using NFSv3.
[*]One thing I haven't tried is disabling the journal on ext4 (similar to ext2).
[/LIST]
    As I have a similar bit of benchmarking I have to do over NFS, I was rather interested in your problem.  The main thing that I'd think about your situation is I'd test it if I possibly could, with something as close to your real application as possible.  And as I have some rate-limiting multi-process file-writing program, I thought it might be of use to you as well.  Hence source attached which perhaps will help you find out how much headroom you really have.

I ran it with an NFS server and two clients each running 500 processes writing at 8 kbyte/sec to the same directory, with randomised sizes, and much to my surprise, nothing broke!

Attached file: is fakecall.tar.gz containing just fakecall.c
```

tar xzf fakecall.tar.gz
make fakecall
cp fakecall client1:/usr/local/bin-or-wherever
```On clients, mount as /mnt-or-wherever

```
fakecall -v -d /mnt -p client1 -b 500 -c 3 -s 350 -r 8 -j
```It will make 500 processes (really!) each making three files with an average size of 350 kbyte, writing at 8 kbyte/sec, in /mnt with uniquesed names (client-timestamp-childnum-filenum)

Any use?

Kind regards,
Jonathan.

---

### Post by matt_symes on 2011-11-20
Hi

> **gregfaust said:**
>  ZFS would be perfect but doesn't exist within Linux.

[http://zfsonlinux.org/](http://zfsonlinux.org/) ?

I have never used it so i have no advice or opinion  to offer.

Kind regards

---

### Post by gregfaust on 2011-11-23
I have a test system and can give benchmark a try right after Thanksgiving.

---

### Post by PCFreak2 on 2011-11-23
Why don't you try ext3??

---

