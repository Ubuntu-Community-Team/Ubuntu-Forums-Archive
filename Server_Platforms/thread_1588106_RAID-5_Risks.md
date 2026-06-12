---
title: "RAID-5 Risks?"
date: 2010-10-04
forum: Server Platforms
---

### Post by kgatan on 2010-10-04
Hi,

I guess this has probably been discussed before but i cant find an satisfying information by searching.

I have an ubuntu server at home to host all my dvd´s etc and it will probably within 2 years store 3tb+ which means i cant backup the entire storage.

I though sofware RAID-5 should be perfect for me since the server is locked away and the only cause for data loss should be fire or intrusion which is a risk i can accept.
Read/write performance is also not a big issue for me.


But after reading up on software raid-5 it seems corruption of data is a big risk as well.
Is this true or have i got it wrong?

Growing the array also seams like a big risk in case of problems during rebuild.
And i know that i will need to expand in the future.


When calculating all the risk involved i come to the conclusion its more likely id lose the whole array instead of a single disk if not using raid.


Is data corruption with raid-5 common?
How can i protect my self from data corruption? 
Hardware raid/software raid security wise? 
Is ZFS a better alternative for software raid?
Is RAID-5 in general dangerous to a novice user in linux?

---

### Post by CharlesA on 2010-10-04
I can't speak for software RAID, but I've been running a Hardware RAID-5 array for over a year now with little problems.

RAID isn't a replacement for backups, and having a good backup is key to dealing with accidental deletion/data corruption.

Note: I've had to backup my media to a separate external drive and my documents and junk to another, since 3TB externals are quite pricey atm and I really care more about my data then my movies that I can just rip again should I lose the data.

With RAID-5, there is always the chance that 2 drives will go out, and you'll have lost all your data.

---

### Post by BobVila on 2010-10-04
In theory, and in production environments, RAID 5 arrays with disks greater than 1TB can pose a significant risk. There's a chance that two drives could go out simultaneously, but the real danger is this: one disk goes out, so you find/order a replacement and pop it in. Given that the drives are so big, the rebuild will take a while, and this is where you're the least protected.

For personal use, things can be fudged a bit. I still backup my important documents, etc. But I don't bother with all the media that lives on a software RAID 5 array. I've been running software RAID 5 for about 6 years, 1 year with 1.5tb disks, and haven't had any catastrophes yet. 

Long story short, back up the invaluable stuff, and roll the dice with the rest unless you've got the cash to burn for a larger backup.

---

### Post by fjgaude on 2010-10-04
BobVila gives good advice... I've been using software raid-5 for about the same time, 6 years, without isssues. But, and this is a big but: I backup all important data, which is about 40G to other drives on other machines.

To use **mdadm**, software raid, you have to learn lots before you go about changing out drives, adding storage, etc. The documentation is complete if you understand what is being said. The issue is the extreme flexibility provided by mdadm. So many folks just jump-in and think they can handle any situation without studying what all the commands do. Yes, mdadm is command-line driven.

The huge drives these days, 2TB, have given software raid, any raid, issues that have to be considered. In the old days raid-5 was used to increase storage capacity and speed over that of one drive. Nowadays neither speed nor capacity is a major issue.

Think about using only one big drive and another big drive for backup. Do you really wish more than 2TB of media? <sigh>

---

### Post by CharlesA on 2010-10-04
> **BobVila said:**
> In theory, and in production environments, RAID 5 arrays with disks greater than 1TB can pose a significant risk. There's a chance that two drives could go out simultaneously, but the real danger is this: one disk goes out, so you find/order a replacement and pop it in. Given that the drives are so big, the rebuild will take a while, and this is where you're the least protected.

For personal use, things can be fudged a bit. I still backup my important documents, etc. But I don't bother with all the media that lives on a software RAID 5 array. I've been running software RAID 5 for about 6 years, 1 year with 1.5tb disks, and haven't had any catastrophes yet. 

Long story short, back up the invaluable stuff, and roll the dice with the rest unless you've got the cash to burn for a larger backup.

A big +1 to that.

---

### Post by memilanuk on 2010-10-04
Just checking, as I've been reading RAID stuff until my head hurt for the last week or so... wanna make sure I got things straight.

If I understand things correctly, the problem with RAID 5 is that drives don't always go bad all at once.  They might develop a bad sector that might go undetected for a while - doesn't hurt much, especially with another drive providing some degree of backup.  But when one of the other drives does go down for the count... during the process of recovery, that one bad spot on one drive can cause the whole restoration process to fail, since your 'extra' is no longer in the array as a backup (drive, not backup backup).  Given the increasing size of drives today, and how long it takes to completely rebuild a 2TB drive as a part of a RAID 5 array (I've seen numbers like 20+ hours mentioned), the odds of having one bad spot on a drive, right where it hurts, start making RAID 5 problematic.

My understanding is that RAID 6 (like RAID 5 but with another drive for parity) basically gives you one more drive worth of protection.  I've been wondering as I read some of the information around... when RAID 6 is going to start becoming more popular and seen as a regular option on things like the consumer NAS boxes (which normally list RAID 0, 1, 5, 10 as options, but no 6)?

Supposedly ZFS and the upcoming btrfs file systems are supposed to offer some improved capabilities in these areas, from what I hear.  

Monte

---

### Post by CharlesA on 2010-10-04
> **memilanuk said:**
> If I understand things correctly, the problem with RAID 5 is that drives don't always go bad all at once.  They might develop a bad sector that might go undetected for a while - doesn't hurt much, especially with another drive providing some degree of backup.  But when one of the other drives does go down for the count... during the process of recovery, that one bad spot on one drive can cause the whole restoration process to fail, since your 'extra' is no longer in the array as a backup (drive, not backup backup).  Given the increasing size of drives today, and how long it takes to completely rebuild a 2TB drive as a part of a RAID 5 array (I've seen numbers like 20+ hours mentioned), the odds of having one bad spot on a drive, right where it hurts, start making RAID 5 problematic.

Not exactly. All drives develop bad sectors eventually, and most of the time those are remapped to spare sectors without any problem. It only becomes a problem when the drive runs out of spare sectors. After that happens, the drive might lose data if there is data stored on one of the sectors that goes bad.

What they are referring to is this: One drive on an array goes dead (multi-terabyte or not) and gets replaced. After a drive goes out on a RAID array, the array needs to be rebuilt and that can take a very long time depending on how much data is on the array. If it's in the process of rebuilding and another drive fails (on a RAID-5), the array is toast and all your data is gone.

> My understanding is that RAID 6 (like RAID 5 but with another drive for parity) basically gives you one more drive worth of protection.  I've been wondering as I read some of the information around... when RAID 6 is going to start becoming more popular and seen as a regular option on things like the consumer NAS boxes (which normally list RAID 0, 1, 5, 10 as options, but no 6)?

RAID 6 would be nice to have if you have a load of data - multi-terabyte arrays would be a bit more redundant, since it could handle the loss of two drives, instead of just one.

I ended up just running a cheap HW RAID card instead of getting a consumer NAS box, since I wanted to "do it myself" as well as have a multifunction box. I don't know of any NAS box that can run VMs just yet. :P

EDIT: I just took a look at a couple HW RAID cards that can do RAID 5 and 6, and the lowest one from a good vendor was around 300 bucks. The cheapo RAID 5 card I've got is 130. Software RAID gets around that, of course.

---

### Post by Vegan on 2010-10-04
RAID5 is passe, time to use RAID6 which can support a double disk failure.

---

### Post by kgatan on 2010-10-05
Thanks for all the feedback!

As someone said a rebuild of a 2tb or 1tb disk takes long time and any interference can possibly smoke the entire array which is a risk i dont think i can live with.
RAID-6 doesnt feel viable either since i was aiming at 4 disk setup in which 2 would be lost for parity and i might as well have backup.


Regarding NAS,
I believe why you don't see RAID-6 in many NAS devices is because its slower and need alot more CPU for double parity then RAID-5.

If the cost is no big problem would it be more safe to buy an RAID-X NAS instead?


However,
I believe the most valid option would be a ZFS RAID-Z array.
A drive failure with ZFS seams to rebuild in a diffrent way which means its not vulnerable to problems during the rebuild. But im not 100% sure of that.

Its also experimental on freenas which is a risk as well.

---

### Post by memilanuk on 2010-10-05
Here's an interesting blog article on the subject... I've been reading a bit of this guy's stuff lately as I've been reading about people with these insanely large RAID arrays, and wondering what they do for backup as I read about other people having RAID failures and struggling to recover :(

[Why-raid-5-stops-working-in-2009](http://www.zdnet.com/blog/storage/why-raid-5-stops-working-in-2009/162)

also of interest...

[Why-raid-6-stops-working-in-2019](http://www.zdnet.com/blog/storage/why-raid-6-stops-working-in-2019/805?tag=rbxccnbzd1)

---

### Post by CharlesA on 2010-10-05
Read errors happen, I guess that's why you really need to have a good backup and test said backup regularly.

---

### Post by kgatan on 2010-10-06
Interesstng blogs which i think confirms the problem with raid-5 for a home user.
Byt that i mean any business users always have backups.

With that i guess the only really viable option for home storage is mirror or alternative raid options?

I mean if you have backup of everything you dont really have any use of the raid-5/6 feature since uptime is not a big thing for a home user.
You might as well stripe instead and gain performance.


I hope i dont sound negative :) Just want to find out what fits me best as a home server user with large amounts of media data considiring cost and security.

---

### Post by CharlesA on 2010-10-06
The main problem with a stripe is that if you lose one drive, you lose all your data. Granted if you have a good backup that isn't *that* bad, but the whole point of RAID is to have redundency.

---

### Post by memilanuk on 2010-10-06
I think what he may be getting at, and I admit the idea has occurred to me as well... is that if you need a large enough storage space that you need to span multiple disks, say 8TB just to throw out a number... that'd be four 2TB drives plus one or two more for RAID 5 or 6.  But if you have have a complete backup of *that* array, at another (at least) 8TB... are the 'extra' one or two drives in each array worth it?  if you have a drive fail on the first array, you already have a backup (both information and drive) in the second array, right?  Replace the bad drive and mirror the information back, which as I understand it would be considerably faster than rebuilding a RAID 5/6 array of that size...

---

### Post by CharlesA on 2010-10-06
I guess I am misunderstandering.

The way I do it is this: RAID-5 array has three 2TB drives with about 2.5TB of data on it. You split the media on one backup drive and documents on another drive.

If one of the drives in the array fails, you swap the failed drive out for a new drive and let it rebuild.

If the array is totally toast, you replace the drives that failed and then copy the backup onto the array.

Is that what you are getting at, or is it something else? From the wording, it sounded like you keep a backup of each individual drive's data and just swap it out, but that's not how RAID works.

---

### Post by memilanuk on 2010-10-06
What I'm saying (I think ;) ) is how do you backup a 2.5 TB RAID 5 array worth of data?  Won't fit on any one hard drive (assuming current capacity of 2TB, although 3TB drives are starting to appear), so you need another array... or a bunch of tapes.  Most people seem to be opting for a second raid array of equal or bigger size (or only backing up the really important stuff to a smaller drive).  So if you have to have a second array to back up the first array... why pay the extra $$$ for the parity drive(s) in the first array, if the odds are increasingly bad that you may suffer a second drive error while recovering it and have to restore from the backup (second array) anyway?  

I realize that for business purposes, any unscheduled downtime is bad, so they may have a legitimate need for the first array to *not* go down during business hours and thus justify RAID 5/6 but for home users where it's mostly just an inconvenience having to wait while restoring from backup...

---

### Post by CharlesA on 2010-10-06
> **memilanuk said:**
> What I'm saying (I think ;) ) is how do you backup a 2.5 TB RAID 5 array worth of data?  Won't fit on any one hard drive (assuming current capacity of 2TB, although 3TB drives are starting to appear), so you need another array... or a bunch of tapes.  Most people seem to be opting for a second raid array of equal or bigger size (or only backing up the really important stuff to a smaller drive).  So if you have to have a second array to back up the first array... why pay the extra $$$ for the parity drive(s) in the first array, if the odds are increasingly bad that you may suffer a second drive error while recovering it and have to restore from the backup (second array) anyway?

That kinda makes sense with that amount of data. I've known of people who have so much data that they just swap out drives as they go down. They backup the important stuff, but have no backup of the stuff that can be replaced, like media and such.

I know I could not bother with backing up my dvd collection, but I don't feel like wasting a ton of time ripping the dvds again. :P 

That being said, I split my backups between two external drives: dvds on one, everything else on the other. I also have a full backup of everything on one drive. That's not feasible if you have more then 2 or 3TB of data, unfortunately.

> I realize that for business purposes, any unscheduled downtime is bad, so they may have a legitimate need for the first array to *not* go down during business hours and thus justify RAID 5/6 but for home users where it's mostly just an inconvenience having to wait while restoring from backup...

Indeed. We lost a server at the place I work with no (recent working) backups of it. The main drive was a mash-up of a RAID5 with 3 partitions on the array. It was a pathetic mess and we lost a ton of data due to the machine going down.

Having a backup would have saved our butts in that case. :|

---

### Post by fjgaude on 2010-10-07
There's an interesting article here:

[HTML]http://www.linux-mag.com/id/7876?hq_e=el&hq_m=1088458&hq_l=5&hq_v=639c52755a[/HTML]

Details the issues with our digital media.

---

### Post by annoyingrob on 2010-10-09
> **kgatan said:**
> 
However,
I believe the most valid option would be a ZFS RAID-Z array.
A drive failure with ZFS seams to rebuild in a diffrent way which means its not vulnerable to problems during the rebuild. But im not 100% sure of that.

Raid 5 (and raid 6 I believe as well) suffer from what's known as the raid-5 write hole. If your machine loses power between when the data was written, and when the parity is calculated and written, your data will become corrupt and lost. 

This is avoided in ZFS and BTRFS in the way it handles writes, by first writing the new data to a new place, and then changing the pointer from the old data.

ZFS (and I think BTRFS) has one MAJOR advantage over simple raid is the fact that it's a self-healing file system. It CRCs every file, and will detect and repair read and write errors seamlessly. 

IMO ZFS is the way to go over raid any day, unfortunately the only real playform available for it these days is freebsd (freenas). ZFS-fuse on linux is slow, and naitive support is still in development.

---

