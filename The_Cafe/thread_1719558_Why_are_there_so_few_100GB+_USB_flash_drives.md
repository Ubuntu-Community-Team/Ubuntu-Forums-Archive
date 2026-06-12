---
title: "Why are there so few 100GB+ USB flash drives?"
date: 2011-04-01
forum: The Cafe
---

### Post by brawnypandora0 on 2011-04-01
Is it because the higher the storage, the more error prone it is?  

Also, which online sites offer free USB flash drives? Would they offer it at sizes of 2GB and above?

---

### Post by Paqman on 2011-04-02
> **brawnypandora0 said:**
> Is it because the higher the storage, the more error prone it is?  


No, it's because packing that kind of storage into a small package is still reasonably expensive (for now).

You're aware of Moore's Law? Basically the number of components on a chip of a given cost doubles about every 18 months. So give it a little while and 100GB memory sticks will be very common. I still have a 128MB memory stick I use all the time, when I bought it a few years ago it was one of the bigger ones you could get, now you'd struggle to find one under 1GB.

---

### Post by jerenept on 2011-04-02
> **brawnypandora0 said:**
> Is it because the higher the storage, the more error prone it is?  

unfortunately, 2.5' HDD's are still waaaaaay cheaper.

> Also, which online sites offer free USB flash drives? Would they offer it at sizes of 2GB and above?

Free? I know where you can buy flash drives :P

---

### Post by mmsmc on 2011-04-02
and sadly there are alot of known problems with storing files on large usb drives, and there format is usually very different from any other one do to its size(my 32 gb is only format able to fat32)

---

### Post by Shibblet on 2011-04-02
> **Paqman said:**
> No, it's because packing that kind of storage into a small package is still reasonably expensive (for now).

You're aware of Moore's Law? Basically the number of components on a chip of a given cost doubles about every 18 months. So give it a little while and 100GB memory sticks will be very common. I still have a 128MB memory stick I use all the time, when I bought it a few years ago it was one of the bigger ones you could get, now you'd struggle to find one under 1GB.

Moore's Law is in full effect!  I went to get a 250gb external usb hard drive the other day, and all they had was 500gb.  The guy at the store told me they don't even stock the 250 anymore.

---

### Post by youbuntu on 2011-04-02
Large flash drive? Meh, no thanks, I'd rather have a hdd. :)

There is a famous saying "don't put all your eggs in one basket", which people seem to ignore. Lots of 8Gb microSD cards/flash drives is infinitely better than one big one. Why? Redundancy!

---

### Post by disabledaccount on 2011-04-02
There is no big difference from having big flash drive or having external hdd - it depends on what kind of  data is really important

---

### Post by youbuntu on 2011-04-02
> **tomazzi said:**
> There is no big difference from having big flash drive or having external hdd - it depends on what kind of  data is really important

No big differences? Yes there are:

1/ Nand cells wear faster than magnetic hdd platters

2/ Nand write times are still *very* slow indeed

3/ Massive difference in the price

Flash storage & SSDs are still very immature, in relation to magnetic HDDs. If you value your data, you'll use RAID'ed HDDs.

---

### Post by Paqman on 2011-04-02
> **Shibblet said:**
> Moore's Law is in full effect!  I went to get a 250gb external usb hard drive the other day, and all they had was 500gb.  The guy at the store told me they don't even stock the 250 anymore.

For sure. I built a HTPC a couple of years ago. The minimal OS and XBMC was going to take up less than 3GB, but the smallest 2.5" hard drive I could buy was 80GB.

---

### Post by Icehuck on 2011-04-02
> **glossywhite said:**
> No big differences? Yes there are:

1/ Nand cells wear faster than magnetic hdd platters

2/ Nand write times are still *very* slow indeed

3/ Massive difference in the price

Flash storage & SSDs are still very immature, in relation to magnetic HDDs. If you value your data, you'll use RAID'ed HDDs.


RAID is not a valid backup solution. If your data is important, then actually back it up properly.

---

### Post by youbuntu on 2011-04-02
> **Icehuck said:**
> RAID is not a valid backup solution. If your data is important, then actually back it up properly.

Define: "properly"? You meant TAR? DVD? Blu Ray?


I think "not valid" is a strange thing to say...

---

### Post by Paqman on 2011-04-02
> **Icehuck said:**
> RAID is not a valid backup solution. If your data is important, then actually back it up properly.

I don't think he actually said it was a backup solution. RAID can create redundancy, which is a good thing. Yes, you should have backups too, but he wasn't wrong per se.

---

### Post by red_Marvin on 2011-04-02
> **glossywhite said:**
> Define: "properly"? You meant TAR? DVD? Blu Ray?
I think "not valid" is a strange thing to say...

When using raid, the two (or more) disks are still in the same house.
If there is a fire...

---

### Post by youbuntu on 2011-04-02
> **red_Marvin said:**
> When using raid, the two (or more) disks are still in the same house.
If there is a fire...

Could be remote RAID, using something like this:

[http://www.etherboot.org/wiki/relatedlinks](http://www.etherboot.org/wiki/relatedlinks)

---

### Post by Phrea on 2011-04-02
Follow-up question then:  
Why are microSD's SO much bigger, in density, than normal SD cards, or USB drives?

---

### Post by MasterNetra on 2011-04-02
> **mmsmc said:**
> and sadly there are alot of known problems with storing files on large usb drives, and there format is usually very different from any other one do to its size(my 32 gb is only format able to fat32)

Seriously? You can't format to EXT3 or EXT4 with gparted?

---

### Post by fela on 2011-04-02
> **MasterNetra said:**
> Seriously? You can't format to EXT3 or EXT4 with gparted?

I think he/she meant that as opposed to being able to format to FAT16.

---

### Post by MasterNetra on 2011-04-02
> **fela said:**
> I think he/she meant that as opposed to being able to format to FAT16.

Why would you want to format to fat16 for?

---

### Post by wizard10000 on 2011-04-02
> **glossywhite said:**
> I think "not valid" is a strange thing to say...

Then let me restate it - RAID is not a backup solution.  Your data still has a single point of failure.

A sysadmin who works for me almost became unemployed last year for thinking the RAID10 array on his SMS server made backups unnecessary.

To make a long story short a RAID controller failure wrote garbage to the array - eight drives and none of the data was recoverable.  He lost thousands of hours of work and probably 400 software packages and OS patches that had to be repackaged before we could automate software distribution again.

Nope.  RAID only helps to keep your data live - you still need to have a backup somewhere off the machine, and if your data's really important that backup should be stored offsite.

---

### Post by fela on 2011-04-02
> **MasterNetra said:**
> Why would you want to format to fat16 for?

Cross compatibility, although I don't see why you'd choose this over FAT32. But anyway, I highly doubt that the OP's drive only supports FAT32 (as opposed to other filesystems like ext4 xfs jfs reiserfs zfs btrfs hfs+ ntfs etc.).

---

### Post by fela on 2011-04-02
> **wizard10000 said:**
> Then let me restate it - RAID is not a backup solution.  Your data still has a single point of failure.

A sysadmin who works for me almost became unemployed last year for thinking the RAID10 array on his SMS server made backups unnecessary.

Why was he a sysadmin if he made that sort of judgement?

PS. what is an SMS server, lol :)

---

### Post by youbuntu on 2011-04-02
> **wizard10000 said:**
> Then let me restate it - RAID is not a backup solution.  Your data still has a single point of failure.

A sysadmin who works for me almost became unemployed last year for thinking the RAID10 array on his SMS server made backups unnecessary.

To make a long story short a RAID controller failure wrote garbage to the array - eight drives and none of the data was recoverable.  He lost thousands of hours of work and probably 400 software packages and OS patches that had to be repackaged before we could automate software distribution again.

Nope.  RAID only helps to keep your data live - you still need to have a backup somewhere off the machine, and if your data's really important that backup should be stored offsite.

Although I agree with you, how often do RAID *controllers* bork like that? Yes, off-site remote server/s with a second image is a better plan :)

---

### Post by wizard10000 on 2011-04-02
> **fela said:**
> Why was he a sysadmin if he made that sort of judgement?

PS. what is an SMS server, lol :)

He almost wasn't after that  :D

SMS = Microsoft Systems Management Server - it's used for hardware and software inventories and to package and push software and patches to some or all workstations in an enterprise.  It's been replaced by System Center Configuration Manager, which performs the same function and then some.

---

### Post by wizard10000 on 2011-04-02
> **glossywhite said:**
> Although I agree with you, how often do RAID *controllers* bork like that? Yes, off-site remote server/s with a second image is a better plan :)

How often have I seen it?  Two, maybe three times out of 150 or so servers over the last ten years.

Actually I've seen MS Exchange data stores get corrupted fairly often.  It doesn't have to be hardware that writes garbage to the array - software can do it as well.

---

### Post by youbuntu on 2011-04-02
> **wizard10000 said:**
> How often have I seen it?  Two, maybe three times out of 150 or so servers over the last ten years.

Actually I've seen MS Exchange data stores get corrupted fairly often.  It doesn't have to be hardware that writes garbage to the array - software can do it as well.

So, how can you be sure it *was* hardware at fault?

---

### Post by fela on 2011-04-02
> **glossywhite said:**
> So, how can you be sure it *was* hardware at fault?

Whether it was the hardware or the software at fault, the point is that RAID mirroring isn't sufficient backup. The only potential data loss disaster that it could recover is a failed hard drive.

BTW, the best backup solution (if you REALLY need to keep your data) is an offsite medium, however one that isn't connected to the net and doesn't have any sort of operating system on it (ie. is just a hard drive with data on it, or tape drive or whatever medium you choose).

Software = potential for something bad to happen :P

---

### Post by youbuntu on 2011-04-02
> **fela said:**
> Whether it was the hardware or the software at fault, the point is that RAID mirroring isn't sufficient backup. The only potential data loss disaster that it could recover is a failed hard drive.

BTW, the best backup solution (if you REALLY need to keep your data) is an offsite medium, however one that isn't connected to the net and doesn't have any sort of operating system on it (ie. is just a hard drive with data on it, or tape drive or whatever medium you choose).

Software = potential for something bad to happen :P

[SIZE=4]150%[/SIZE] agreeance!

---

### Post by Dustin2128 on 2011-04-02
> **MasterNetra said:**
> Seriously? You can't format to EXT3 or EXT4 with gparted?
Well, thing is, journaling file systems if I recall correctly are not meant to be used with flash based storage. Something about rewriting the disc quite a lot, which I'm sure most of you know, significantly shortens the life of the drive. AFAIK, there shouldn't be any problems with ext2 though.

---

### Post by youbuntu on 2011-04-02
> **Dustin2128 said:**
> Well, thing is, journaling file systems if I recall correctly are not meant to be used with flash based storage. Something about rewriting the disc quite a lot, which I'm sure most of you know, significantly shortens the life of the drive. AFAIK, there shouldn't be any problems with ext2 though.

Ergo, my viewpoint holds water. HDD > SSD (for now).

---

### Post by fela on 2011-04-02
> **Dustin2128 said:**
> Well, thing is, journaling file systems if I recall correctly are not meant to be used with flash based storage. Something about rewriting the disc quite a lot, which I'm sure most of you know, significantly shortens the life of the drive. AFAIK, there shouldn't be any problems with ext2 though.

What about things like SSDs then? Are they not vulnerable to data loss from things like power outtages when not used with journals?

EDIT: if I had an SSD I'd probably only use it for my OS+apps, and have whatever was stored on it mirrored to a good ol' hard drive :P

---

### Post by Sporkman on 2011-04-02
> **wizard10000 said:**
> He almost wasn't after that  :D


I'll bet he won't make that mistake again. :) Too bad it was such a costly lesson.

---

### Post by youbuntu on 2011-04-02
So many cons to SSDs, as compared to the pro of "it's shockproof & fast". So what...

---

### Post by Sporkman on 2011-04-02
> **glossywhite said:**
> So many cons to SSDs, as compared to the pro of "it's shockproof & fast". So what...

Compact too.

---

### Post by youbuntu on 2011-04-02
> **Sporkman said:**
> Compact too.

More "meh".

---

### Post by fela on 2011-04-02
> **Sporkman said:**
> Compact too.

I wouldn't say they were any more compact than 2.5" HDDs. Don't they go all the way to 1TB now? Compared with what, 512GB max for SSDs, right?

---

### Post by Paqman on 2011-04-02
> **glossywhite said:**
> So many cons to SSDs, as compared to the pro of "it's shockproof & fast". So what...

There's really only two cons to SSDs and that's their size and price. They're a win in every other regard. If you want cheap and/or big, then sticking with magnetic is the way to go.

---

### Post by youbuntu on 2011-04-02
Imagine a 1Tb flash drive... USB...








Now imagine LOSING it! :lolflag:

---

### Post by fela on 2011-04-02
> **Paqman said:**
> There's really only two cons to SSDs and that's their size and price. They're a win in every other regard. If you want cheap and/or big, then sticking with magnetic is the way to go.

I'm a cheap and big man myself :)

---

### Post by youbuntu on 2011-04-02
> **fela said:**
> I'm a cheap and big man myself :)

I'll stick with what's been tried and tested since the 1970/80s(?) thanks all the same.

---

### Post by Paqman on 2011-04-02
> **glossywhite said:**
> I'll stick with what's been tried and tested since the 1970/80s(?) thanks all the same.

It's not really an either/or IMO. SSDs and HDDs have different strengths and weaknesses, so are suited to different tasks.

---

### Post by Dustin2128 on 2011-04-02
> **glossywhite said:**
> Ergo, my viewpoint holds water. HDD > SSD (for now).
I disagree. The mechanical hard drives which you so advocate have their undoing right in the name. How many hard drives (under normal, constant use conditions, mind you) have lasted more than, say, 15-20 years? That's the average life of SSDs. 95% of the time, after 15 years, your drive will have either failed or you'll have moved on to a bigger device. But keep in mine, unlike disk drives, SSDs don't suffer too much from the test of time. 15-20 years of *continuous *usage. Use it for a few years, bin it, fire it back up to recover your data and it'll still be there. The HDD could've failed simply due to age by that point. Yes, I know I'm feeding a troll :P

---

### Post by youbuntu on 2011-04-02
> **Paqman said:**
> It's not really an either/or IMO. SSDs and HDDs have different strengths and weaknesses, so are suited to different tasks.

Granted, but it is DEF an "or" for me.

---

### Post by Paqman on 2011-04-02
> **Dustin2128 said:**
> 15-20 years? That's the average life of SSDs.

Hmm, as a reliability engineer i'd say that's a pretty bold claim, given that there's no data backing it up. Manufacturers' MTBF figures should be taken with a dumptruck-sized pinch of salt.

Having said that, I would definitely expect an SSD to outlast a HDD. HDDs are notoriously unreliable, and the SSD eliminates a lot of the moving parts that fail in HDDs.

---

### Post by fela on 2011-04-02
> **glossywhite said:**
> I'll stick with what's been tried and tested since the 1970/80s(?) thanks all the same.

Wasn't the first HDD developed in the fifties? Measured in kilobytes, mind you :P (or was it just bytes even O.o)

BTW, all this talk about reliability is irrelevant. Anyone willing to keep their data would store it in more than one place (and would keep an eye on the age of their storage media).

---

### Post by Dustin2128 on 2011-04-02
> **fela said:**
> Wasn't the first HDD developed in the fifties? Measured in kilobytes, mind you :P (or was it just bytes even O.o)

BTW, all this talk about reliability is irrelevant. Anyone willing to keep their data would store it in more than one place (and would keep an eye on the age of their storage media).
I know there was heavy use of magnetic storage in the 50's, most of it was tape but I think they did start developing the HDD then. 

@Paqman
Agree completely.

---

### Post by youbuntu on 2011-04-02
> **Dustin2128 said:**
> I disagree. The mechanical hard drives which you so advocate have their undoing right in the name. How many hard drives (under normal, constant use conditions, mind you) have lasted more than, say, 15-20 years? That's the average life of SSDs. 95% of the time, after 15 years, your drive will have either failed or you'll have moved on to a bigger device. But keep in mine, unlike disk drives, SSDs don't suffer too much from the test of time. 15-20 years of *continuous *usage. Use it for a few years, bin it, fire it back up to recover your data and it'll still be there. The HDD could've failed simply due to age by that point. Yes, I know I'm feeding a troll :P


Please do not call me a troll; that's not nice, and likely to cause undue tension.

Thanks :)

---

### Post by pi3.1415926535... on 2011-04-03
I think that the reasoning behind this is purely economical, because as far as I am aware, big advances in storage size are made very quickly, and it is just businesses parcelling out this change over time, so they continue to make money. At this point in time, storing any significant amounts of data, for the average user, a hard drive is by far the best. Because the amount of storage is greatly increased, and the price is greatly reduced. As to reliability, I find standard hard drives quite reliable any way. Most people do not even need the speed offered by SSDs. If one needs some of the speed advantages of SSDs, Hybrid Drives are a reasonable option, as they are not that much more expensive than HDD, and they are not much slower than SSDs for daily tasks.

---

### Post by LowSky on 2011-04-03
> **brawnypandora0 said:**
> Is it because the higher the storage, the more error prone it is?  

Also, which online sites offer free USB flash drives? Would they offer it at sizes of 2GB and above?

Back on track....

The problem with flash drive is size. How many chip you cans fit into a small 1.5" of plastic housing. The second issue it the format of the memory. Most use FAT32. The problem with FAT32 is that it cannot save files over 4GB in size, and you cannot format a FAT32 partition over 32GB on Windows systems. A huge limitation for such large drives. You are not supposed to use journaling formats like NTFS or EXT3 because of the writing cycles of those, so your choice are limited. Especially if you require Windows support, as Windows doesn't support anything other than FAT and NTFS. There is a newer file system called FAT64 (or exFAT) released by Microsoft that deals with all these issues. Linux support is very limited at this time.

---

### Post by fela on 2011-04-03
> **LowSky said:**
> Back on track....

The problem with flash drive is size. How many chip you cans fit into a small 1.5" of plastic housing. The second issue it the format of the memory. Most use FAT32. The problem with FAT32 is that it cannot save files over 4GB in size, and you cannot format a FAT32 partition over 32GB on Windows systems. A huge limitation for such large drives. You are not supposed to use journaling formats like NTFS or EXT3 because of the writing cycles of those, so your choice are limited. Especially if you require Windows support, as Windows doesn't support anything other than FAT and NTFS. There is a newer file system called FAT64 (or exFAT) released by Microsoft that deals with all these issues. Linux support is very limited at this time.

Or you could just use ext4, disable journalling, and forget about Windows...in a perfect world, I mean :)

---

### Post by Sporkman on 2011-04-03
I read somewhere that the new, up-and-coming brtfs filesystem has a flash mode for better operation on a flash-based device.

---

### Post by fela on 2011-04-03
> **Sporkman said:**
> I read somewhere that the new, up-and-coming brtfs filesystem has a flash mode for better operation on a flash-based device.

I'm not surprised, seems like they're sticking every FS goodie under the sun in BTR. No wonder it's gonna be 'better' :D

---

### Post by Shining Arcanine on 2011-04-03
> **glossywhite said:**
> Flash storage & SSDs are still very immature, in relation to magnetic HDDs. If you value your data, you'll use RAID'ed HDDs.

It might be safer to store it on a tape drive.

---

### Post by fela on 2011-04-03
> **Shining Arcanine said:**
> It might be safer to store it on a tape drive.

Well, I heard they recovered a HDD's data from a space shuttle that disintegrated in the upper atmosphere.

---

### Post by youbuntu on 2011-04-03
> **fela said:**
> Well, I heard they recovered a HDD's data from a space shuttle that disintegrated in the upper atmosphere.

Surely a space shuttle has ample connectivity technology to stream a multitude of HDDs back to earth for backup, in a matter of seconds or minutes, what with all the satellite tech NASA own.

---

### Post by fela on 2011-04-03
> **glossywhite said:**
> Surely a space shuttle has ample connectivity technology to stream a multitude of HDDs back to earth for backup, in a matter of seconds or minutes, what with all the satellite tech NASA own.

Yes but they weren't anticipating the whole spaceship blowing up, and even if they were I think they had other things on their mind, or rather, what used to constitute their minds were now burning in the atmosphere.

---

### Post by Paqman on 2011-04-03
> **glossywhite said:**
> Surely a space shuttle has ample connectivity technology to stream a multitude of HDDs back to earth for backup, in a matter of seconds or minutes, what with all the satellite tech NASA own.

Spacecraft do transmit a lot of telemetry data down to the surface yes. It's not inconceivable that there is some data that is downloaded at the end of a mission though. Maybe someone on the forum with more experience in spaceflight knows for sure.

---

### Post by Ranko Kohime on 2011-04-06
> **jerenept said:**
> unfortunately, 2.5' HDD's are still waaaaaay cheaper.
2.5 FOOT drives?  Where can I buy one of those?  They may only run at 2400 RPM, but the storage must be massive!  :P

---

### Post by Sporkman on 2011-04-06
> **Ranko Kohime said:**
> 2.5 FOOT drives?  Where can I buy one of those?  They may only run at 2400 RPM, but the storage must be massive!  :P

FOOT driver work bi pedal power.

---

### Post by fela on 2011-04-06
> **Ranko Kohime said:**
> 2.5 FOOT drives?  Where can I buy one of those?  They may only run at 2400 RPM, but the storage must be massive!  :P

Or you could get a big bunch of disks and put them in a foot-sized rectangle. If each drive was 2TB, you do the maths :)

I estimate that you could fit 64 drives in the same shape, enlarged so the 3.5" dimension is now a foot long. That's 128 TB :O

---

### Post by psusi on 2011-04-06
> **glossywhite said:**
> Although I agree with you, how often do RAID *controllers* bork like that? Yes, off-site remote server/s with a second image is a better plan :)

More often than you would think.  I've had it happen twice.  Once with an expensive hardware raid card in a server, and once on a friend's motherboard fakeraid.  At least in the latter case I was able to recover it after spending a few hours hex editing the raid metadata.

The more common problem though is simple mistakes like overwriting or deleting the file.  Raid doesn't help with that, which is why it is NOT a backup solution.  Raid is for speed and uptime, not backup.

> **Dustin2128 said:**
> Well, thing is, journaling file systems if I recall correctly are not meant to be used with flash based storage. Something about rewriting the disc quite a lot, which I'm sure most of you know, significantly shortens the life of the drive. AFAIK, there shouldn't be any problems with ext2 though.

FAT also constantly rewrites part of the disk ( the FAT ), which is why the disks are built to do internal wear leveling so prevent those areas from failing early.

---

