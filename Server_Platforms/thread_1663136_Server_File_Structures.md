---
title: "Server File Structures"
date: 2011-01-09
forum: Server Platforms
---

### Post by expatCM on 2011-01-09
I am about to build a new home server.  I will replace an existing server that is running Debian 5, it manages my Internet connection and acts as a file server.  I will also merge in the media from another computer that has about 3-4TB of data on individual drives.  The objective being to set up a media server with a bit more protection in the event of failed hard drives than there is at present.

It is at this point that I start to get confused.  I was thinking to run RAID 5 simply so that I can swap out distressed drives without data loss.  However ...  I also get the idea that in order to manage partitions efficiently it would be better to run LVM on top of RAID 5.   Any views on that?

---

### Post by CharlesA on 2011-01-09
I'm running a RAID-5 array on my file server using a normal EXT4 partition. I didn't bother with LVM, but I don't see any reason why it would not work.

IMO: It's not a good idea to have a file server on the same box as something that is running routing software. If the box is compromised you are pretty much out of luck. All your eggs in one basket kind of thing.

---

### Post by vortmax on 2011-01-09
Every time I've tried LVM, I wound up dumping it for something else.  For me, it's just more of a pain than its worth.  I also don't trust software RAIDs.  If you can swing it, I would just invest in a hardware RAID controller and be done with it.

My experience with RAID5 is also not that great.  It sounds great to have single drive fault tolerance...until a drive drops.  Then you are left with an entire array with zero fault tolerance.  If you happen to have a 2 drive failure, you are toast.  It sounds unlikely, but I have personally seen it enough times that I don't trust RAID5 anymore.  I also do not trust any RAID level for absolute data security...it is very important to maintain offline backups of your data.

I would go with RAID6 and offline backups.  Actually, if you don't add new media very often, you could use a single drive for the system disk, then setup a RAID0 array for the media.  The RAID0 is not fault tolerant, but as long as your offline backup is up to date, you can just replace the drive and restore from backup.  That would maximize your drive utilization at the cost of a longer rebuild time.

---

### Post by CharlesA on 2011-01-09
+1 to offline backups.

That's the way I have mine set up (RAID-5 with daily backups + monthly). Haven't had a drive go down yet, but if/when one does, I don't want to lose data if another one goes down during the rebuild.

---

### Post by Vegan on 2011-01-09
In my shop disks do not seem to last long. So I backup the backups etc.

I like USB disks, as they are cheap and off-line so they are immune to most hazards.

---

### Post by kevxh on 2011-01-09
Take a step back and think for a moment .... It's a home media server so how far should you go?

Are you really going to benefit from dynamically modifiable partitions? Probably not.
LVM is really useful in certain situations ie you can add a disk in and extend existing logical partitions across that new volume, great, but you can't randomly extend a Raid array so what would you really be looking to achieve?

Multiple redundant disks? In a home media server? Are you serious? Spending lots of money on extra disks and raid controllers is both inefficient and completely unnecessary. This isn't a company with essential data that needs 100% reliability and uptime.

Your movies and music are easily replaceable. All you need is a backup disk for your files and pictures - you could probably even just use an online backup solution for your irreplaceable personal files and pictures.

Throwing money at the problem doesn't produce the most efficient solution, throw your intellect at it instead.

---

### Post by vortmax on 2011-01-09
I'm going to disagree here.  3 to 4 Tb is a LOT of data to be "easily replaceable".  Think about how long it would take you to rip 3 or 4 Tb worth of DvD's to disk?  Heck, think about how long it would take to just download that much over a normal cable modem connection? Also consider the possibility that some of that is DVR recordings...how do you replace that if your drives crash?

As for online backup, take a look at Amazon cloud storage.  Their cheap version is $0.09 per gig up to 1 Tb then $0.08 per gig for the next 49...per month.  That works out to $170 a month to store, and even more to upload and download.

My problem with software raids is that they are unreliable.  If you reinstall the OS, you have to reconfigure it.  What happens when you upgrade the system and a package breaks and you can no longer mount the RAID? You spend hours figuring out how to fix it.  However, with my hardware raid, the system could really care less, the kernel just sees a big sata drive.

It's all a game of diminishing returns.  You can put a price on the time and hassle it would take to rebuild your array as well as the cost of maintaining backups.  There is also a difference between throwing money at a problem and spending some money to come up with an elegant and efficient system instead of kludging something together.

Yes, a full hardware raid may be a little excessive, but it depends on how much restoring the raid from a total failure will cost you(including man hours and pain and suffering).  If I had that much data in media, then I (personally) could easily justify the investment.

---

### Post by expatCM on 2011-01-10
Thank you for all the responses, they do help a lot.

I think I should give some comments ....

> IMO: It's not a good idea to have a file server on the same box as something that is running routing software. If the box is compromised you are pretty much out of luck. 

Yes, that is a good point, especially when you are like me and have only half a clue of what you are doing.  The practical perspective however is that you end up with yet another box and that does not always make good politics with the wife.

> I also don't trust software RAIDs. If you can swing it, I would just invest in a hardware RAID controller and be done with it.

Hmmmm  ....   I have a slightly different perspective.  I can download software.  Hardware has to be imported, the local suppliers cannot handle hardware RAID controllers, the market is not there so they do not stock and do not support.  So I would be out in the cold.  I cannot take that risk.

I just had to read and find out what is RAID 6.  So it is RAID 5  with an extra block.  Can probably cope with that just as well.  The danger apparently is the same as RAID 5 - the consequence of two drives failing at the same time and reading a bit more this is normally due to the wrong failed drive being removed from the system when a problem does arise.

RAID 5/6 is no replacement for data backup but I want to run a RAID so that I am less exposed when a drive fails.  At present when a drive fails without warning it really increases my stress levels since there is no backup, I cannot backup the amount of data, this is a home environment.  Some data is also saved to external hard drives but it is not possible to back up most of it.

> Your movies and music are easily replaceable.

Erm ...  nope.  Movies are really hard to replace.  I have a BAD Internet connection, to download one movie could take anything between 12 hours to 8 weeks.   But in any event much of the content is not mainstream so replacement is not a practical possibility.

> What happens when you upgrade the system and a package breaks and you can no longer mount the RAID?

Sadly, that is an excellent point.  

So in some respects it sounds like the suggestions are beware of RAID unless you have a hardware controller card.  

Perhaps I should be looking the other way round and keeping individual hard drives but using some reliable software to monitor the drives and report when there are potential hardware issues.  The negative here of course is that there is a lot of free space on individual drives that does not get used well since if you allocate storage to the drives you have to find a way of splitting up the files between the drives.  I use the alphabet at present to divide movies across drives and that is either very inefficient or means that I have to spend a lot of time reallocating drive space.

---

### Post by paulisdead on 2011-01-10
I've had none of the issues with software RAID mentioned in this thread.  The Linux software RAID is solid and more reliable than a lot of hardware RAID controllers I've seen.  Plus you can bring the drives up on any type of controller, since the RAID meta data is stored on the drives themselves.  I've just dropped RAID sets from another box into my desktop, with the appropriate packages installed, and it saw the /dev/mdX device without me having to do anything else.

True, a good 3ware or Areca RAID card would be awesome, but those cost quite a bit, and not everyone can drop the cash on them just for home usage.  I got lucky and picked up a bunch of 3ware cards when my old work folded, and LVM'd a couple RAID5 arrays together into one big volume for my home server.

LVM is only good if you think you'll need to shrink, grow, or extend the partition onto other devices.  It does add a whole other layer of complexity, and it is kind of a pain to deal with.

RAID6 also requires you lose another whole drives worth of space to keep the extra parity data.  So 4x1TB drives in a RAID6 only gives you 2TBs of space.  It is true when you get up over about 12TBs, you're within the point that drive manufacturer's say a bad sector is statistically likely, and with RAID5, if you've already had a drive failure, it likely means you'll have 1 bad sector in a data set that big.  However, if you're storing videos and music, a single bad sector, or even few can likely be worked around by most players, or only be on a few files.

Smartmontools, and setting up email alerts for mdadm are also useful.

I'm in kind of a similar position, too much to back everything up at home, so I use RAID to mitigate the risk.  Saved my butt a few times last summer.  I do get irreplaceable data backed up nightly, but there's no way I can backup all my videos.

---

### Post by vortmax on 2011-01-10
It's been a while since I've used Linux software raid...maybe it has improved quite a bit.  Might have to revisit it.

It sounds like you have a few disks full of data that you want to stripe into a raid5 array...The issue is that initializing the raid wipes the drives.  You are going to have to either backup the data, initialize the raid and recopy, or build the raid with new drives.  

You may consider the latter option if you can afford some new drives.  1TB drives are fairly inexpensive right now, and if you could get 5 of them to build a 4Tb raid5, you could keep your existing (non-raid) drives as an offline backup.

and don't think that RAID is bad...it is good, but it's just not perfect.  If you move from the city to the country to get away from crime, do you start leaving your door unlocked at night?

---

### Post by expatCM on 2011-01-10
The "grand plan" would be to buy two 2TB drives and take an existing 500GB spare.  Apparently you need three drives to start a RAID.  Then I would copy the data off two 1TB drives and then format and add those in.  Copy the data off the remaining drives and that would be me done.  But I need to properly write this down and think it through exactly, at the end of the day it is not just going to be RAID ...  it will also be what I am going to run on the server and how I set things up.  For me I think it is going to be a significant learning curve.

> If you move from the city to the country to get away from crime, do you start leaving your door unlocked at night? 

My wife does.  It annoys me but that is what she does ... :(

---

### Post by CharlesA on 2011-01-10
> **expatCM said:**
> 
Yes, that is a good point, especially when you are like me and have only half a clue of what you are doing.  The practical perspective however is that you end up with yet another box and that does not always make good politics with the wife.

Valid point. Wife aggro is bad. :P

The way I have mine set up is that I just have a regular router to share my net connection with the rest of the house. Depending on how your stuff is set up, that might be one possibility. :)

Also, one of the advantages to software RAID is that you don't have to use same size disks (but it can get tricky sometimes)

---

