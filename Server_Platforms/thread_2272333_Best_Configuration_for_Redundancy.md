---
title: "Best Configuration for Redundancy?"
date: 2015-04-05
forum: Server Platforms
---

### Post by Marc-NJ on 2015-04-05
I'm planning on setting up a new Ubuntu 14.04 server (to replace a corrupted 12.04 server), and want to do it the right way this time.  I'm thinking of getting three hard disks (2 x 4 TB and 1 x 6 TB, although the third might also be a 4 TB drive).  I'll configure the 2 x 4 TB drives in a software RAID1 via Ubuntu server installation so that I have protection in case one of them dies (can someone confirm that configuring RAID1 with two drives using software RAID will allow me to easily swap one of the drives out if it dies with a replacement and not lose data or have too much downtime?).

I've also heard that doing software RAID1 this way will allow me to easily move the Ubuntu Server installation to new hardware in case my existing hardware dies somehow but the drives survived - can someone confirm?

As far as the 3rd drive (either another 4 TB drive or a 6 TB drive), I was thinking of doing one of the following:
a) Setting up CrashPlan (headless) or another backup solution so that I can backup data on a near-constant basis from the Ubuntu Server installation to the 3rd drive (and also version it) - this way if I get infected with a virus or something else similar, I can easily recover my data from older versions
-or-
b) Setting up some sort of bare metal recovery software to backup the entire Ubuntu Server installation to the third drive on a schedule (presumably without any intervention - which means the software would need to be installed on the Ubuntu Server and then perform the bare metal backups on a schedule to the third drive without me taking the system offline - is that possible?  And if so, can anyone recommend some good software that will do this?)

Anyone have any suggestions one way or another?  I'm leaning towards the second option, especially since I'll also have CrashPlan (headless) installed on the Ubuntu Server installation anyway to backup selected data to the cloud, so backing it up to the third drive would only serve to decrease the amount of time it would take me to recover the data if ever necessary.  On the other hand, if the software RAID1 works as it should, I should never need to recover from a bare metal backup, right?

Also, any chance someone might be able to point me to an article or other web link that details what data on an Ubuntu Server should be selected for backup?  Obviously the /home directory and sub-directories, but what else? (i.e. MySQL databases, configuration files, etc.)?

As far as the hardware for my new server - I'm thinking it makes sense to spend the most money on Enterprise-class SATA drives (since the data on the drives is the most important) - can anyone let me know if this makes sense, and if so recommend some 4 and 6 TB Enterprise-class drives that won't break the bank?  

For the system itself, I was planning on using a several-years old HP desktop (HP Pavilion a6400f) that has numerous SATA ports on the motherboard and can support up to 8 GB of RAM (which I'm maxing out).  It's a Pentium Dual Core I believe - I know this isn't state-of-the-art hardware, but I happen to have it lying around not being used, and figured if I outfit it with 8 GB of RAM and some nice hard drives and aren't stressing it out too much with my applications, it should be sufficient and ultimately protected (i.e. data redundancy, etc.).  Does that make sense?

Thanks for any help/advice!

---

### Post by MAFoElffen on 2015-04-06
A few things... You ask for "Best"... but limit that with old desktop hardware, so this is based on what you say you want to use...

RAID1 with 2 disks and backup up to a 3rd disk... Best option. Depending on how old the motherboard is, your throughput on SATA would be 1.5GB. 3GB or 6GB. On what you described, I'm thinking it might be only 1.5GB. That is still going to be faster to backup to disk that to the cloud.

The thing to remember, is that RAID is not a replacement for a backup. Backups are faster to disk, than to tape or to a remote device. Yes, you can recover RAID1, but that is if it didn't carry over errors prior to the failure... Stressing the importance of those backup iterations. If you setup the third disk to LVM, then you can easily add more space to that volume later... 

This is what I do for my system volumes (mirrored)... then for my virtuals, I put those on LVM volumes. I take backups and do snap shots to other LVM volumes elsewhere.

To do an iteration of backups, you are going to need 2-3 times the space on your backup media... to hold those. Less, if you plan on using compression for archiving. So 6TB should be fine for 3-4TB Mirrored Drives. (depending)

I use Enterprise drives. Yes, they cost more. I think the longer warranty and the higher fault tolerances are a peace of mind thing for me. I do 2TB drives rated at 6TB transfer, rated to be in banks of 8 to 15 drives... Mine are in banks of 10. Drives rated for this should hopefully build less heat and be tolerant to more heat caused by being close to other Server drives. The servers those are on... rebel on larger than 2TB drives... which is what you may want to check out... that your older hardware will support over 2TB drives... before investing in them. I bought 4TB drives for those, and ended up using them on other servers, because they thought they were 2TB drives!!!

But if your throughput is only 1.5GB, then spending more money is not going to make things any faster... than that slowest piece (the old drive controller). Then 5400 rpm drives would be fine, would be more dependable for you, and build less heat than 7400 rpm drives.

If your are doing yours in an old desktop case... Think seriously about adding more fans.

---

### Post by TheFu on 2015-04-06
What is the budget and what are the RTO and RPO requirements?  That is how a professional attacks this question. You can look up RTO/RPO on wikipedia.

As to what you should backup - for the lowest risk - EVERYTHING. Backups are 10000x more important than RAID-anything. Get your backups working the way you need them BEFORE doing anything with RAID the first time.  There are RAID issues that only a backup can solve - viruses, file corruption, etc.

RAID is for HA and maybe performance (in some situations).

HW RAID or SW-RAID?  Each has pros/cons.   Speed vs flexibility. What happens if the HW-RAID card fails?  Do a little research about that BEFORE you go that direction.

In a home environment, RAID is usually overkill.  Is it really worth having a $400 RAID card so your wife can still stream *Desperate Housewives* without interruption after a failure?  Can't she wait until you get home, with new HDD, and swap the backup for the failed drive and replace the backup with the new drive? Excellent backups are much, much, much, much more important.

Of course, if you want to learn about RAID - running a RAID setup will teach you much - especially when there are issues.

---

### Post by Marc-NJ on 2015-04-06
> **MAFoElffen said:**
> A few things... You ask for "Best"... but limit that with old desktop hardware, so this is based on what you say you want to use...

RAID1 with 2 disks and backup up to a 3rd disk... Best option. Depending on how old the motherboard is, your throughput on SATA would be 1.5GB. 3GB or 6GB. On what you described, I'm thinking it might be only 1.5GB. That is still going to be faster to backup to disk that to the cloud.

The thing to remember, is that RAID is not a replacement for a backup. Backups are faster to disk, than to tape or to a remote device. Yes, you can recover RAID1, but that is if it didn't carry over errors prior to the failure... Stressing the importance of those backup iterations. If you setup the third disk to LVM, then you can easily add more space to that volume later... 

This is what I do for my system volumes (mirrored)... then for my virtuals, I put those on LVM volumes. I take backups and do snap shots to other LVM volumes elsewhere.

To do an iteration of backups, you are going to need 2-3 times the space on your backup media... to hold those. Less, if you plan on using compression for archiving. So 6TB should be fine for 3-4TB Mirrored Drives. (depending)

I use Enterprise drives. Yes, they cost more. I think the longer warranty and the higher fault tolerances are a peace of mind thing for me. I do 2TB drives rated at 6TB transfer, rated to be in banks of 8 to 15 drives... Mine are in banks of 10. Drives rated for this should hopefully build less heat and be tolerant to more heat caused by being close to other Server drives. The servers those are on... rebel on larger than 2TB drives... which is what you may want to check out... that your older hardware will support over 2TB drives... before investing in them. I bought 4TB drives for those, and ended up using them on other servers, because they thought they were 2TB drives!!!

But if your throughput is only 1.5GB, then spending more money is not going to make things any faster... than that slowest piece (the old drive controller). Then 5400 rpm drives would be fine, would be more dependable for you, and build less heat than 7400 rpm drives.

If your are doing yours in an old desktop case... Think seriously about adding more fans.

Thanks so much for the reply - a lot of good information to digest!

A few follow-ups:

1) Would you recommend CrashPlan for backups to the 3rd drive, or some sort of full bare metal backup software (to grab the entire OS and data, similar to how Norton Ghost used to work I guess, presumably with incremental capabilities) so that I can easily be up and running using the bare metal backup if I need to on another hard drive, or some other backup software?  I was thinking CrashPlan, since RAID1 should allow me to recover if one of the two hard drives goes, and CrashPlan backup on the 3rd drive (and to the cloud also) will allow me to recover if I get a virus infection, some other sort of data loss, etc.

2) Good call on ensuring that I can use drives greater than 2 TB - I know I had an older HP Elite HPE-390t desktop (maxed out from a few years ago since I had bought it and used it as my desktop PC for some time) that I was planning on initially using as my "server" and I had to actually modify the BIOS to insert the newer Intel RST option ROM (OROM) so that it would support drives greater than 2 TB, but not sure if I can do the same on this machine - will definitely check first, but either way I think going with 2 x 4 TB and 1 x 6 TB makes sense - right?

3) Can you suggest what sort of Enterprise drives I should look at for the 4 and 6 TB ones?  I was thinking maybe WD RE series, or HGST, but am open to anything.  And what sort of prices should I be looking to get them for?  

4) How would I add more fans in the desktop case?  I was only going to get 3 hard drives anyway since the case supports 2 x 3.5" drives and 2 x 5.25" drives (one slot already taken up with the CD drive and I ordered a 5.25 to 3.5" bracket so I could use the other slot) - so do you think I need to add more fans?

Thanks so much for the information!

---

### Post by Marc-NJ on 2015-04-06
> **TheFu said:**
> What is the budget and what are the RTO and RPO requirements?  That is how a professional attacks this question. You can look up RTO/RPO on wikipedia.

As to what you should backup - for the lowest risk - EVERYTHING. Backups are 10000x more important than RAID-anything. Get your backups working the way you need them BEFORE doing anything with RAID the first time.  There are RAID issues that only a backup can solve - viruses, file corruption, etc.

RAID is for HA and maybe performance (in some situations).

HW RAID or SW-RAID?  Each has pros/cons.   Speed vs flexibility. What happens if the HW-RAID card fails?  Do a little research about that BEFORE you go that direction.

In a home environment, RAID is usually overkill.  Is it really worth having a $400 RAID card so your wife can still stream *Desperate Housewives* without interruption after a failure?  Can't she wait until you get home, with new HDD, and swap the backup for the failed drive and replace the backup with the new drive? Excellent backups are much, much, much, much more important.

Of course, if you want to learn about RAID - running a RAID setup will teach you much - especially when there are issues.

Thanks for all the info - greatly appreciated!

1) As far as RTO and RPO requirements - I don't have any specifically.  My old server has been down for several weeks, but I've been able to recover data from the online/cloud CrashPlan backup when needed, and since this was one of two Ubuntu servers I had, I'm managing to live without it.  However, if I'm going to do the replacement server the right way, I'll probably move some of the stuff I have on my other Ubuntu server over to this (my remote access application, my business data, etc.), and therefore will want to ensure better continuity and redundancy for this one.  I'm a one-man show though, so I don't necessarily have specific time frames that absolutely must be adhered to or else dire consequences will occur :)

2) For what I should backup - what I meant was that if I go with a bare metal backup solution, then everything gets backed up anyway.  But if I go with CrashPlan (either for local backups to the 3rd drive, and/or for cloud backups), I can't tell it to backup everything, and there usually isn't a need to backup everything.  For instance, I don't backup my Windows folder from my Win8 workstation because it's basically unnecessary - I need the data, and would like to get the configuration saved as well, but don't actually need the OS files backed up, right?  But since I don't fully understand Ubuntu's file structure system (I have an OK handle on some of it, such as knowing obviously that I should be backing up /home, etc.), I was wondering if there was a good article or support document out there that detailed what is critical and important to back up, or at least details how the file structure works so I can get a better idea of what I should be backing up.  Does that make sense?

3) I've done a good amount of research thus far on hardware RAID vs. software RAID.  Was actually initially going to use a fakeRAID system (the previously mentioned HP Elite HPE-390t), but quickly nixed that idea, and then was looking at a Lenovo ThinkServer TS440 with hardware RAID, but am now thinking that might be overkill if I do software RAID with two drives, and a third drive for backup, plus cloud backup.  Thoughts?  And will software RAID1 allow for easy recovery if one of my two main RAID1 drives goes bad?  I can't seem to find a specific document that outlines an easy recovery process for software RAID1.

P.S. Sorry if I didn't make this clear in my initial post - I run a one-man business, so while this server will be located in my home office, and will be used somewhat for personal reasons, it will mostly be a business server and so having some RAID seems to be a necessity given that my last server's HD crashed (I have backups, so no data loss, but plenty of downtime since I still haven't set up a replacement).

Thanks again! :)

---

### Post by TheFu on 2015-04-06
[http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/Linux-Filesystem-Hierarchy.html](http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/Linux-Filesystem-Hierarchy.html) - explains what files go where.  Of course, any UNIX system is extremely flexible and the admin can chose to ignore all that stuff and put files anywhere she/he likes. I've only seen that a few times.

I've never used crashplan. Wouldn't trust any external service with our corporate data, small as it is. We have 2 locations with 1 as primary, and only 500G of data.  I push the changed data to the other location daily using rsync. That push includes rdiff-backup versioned backups - so both locations have versioned backups which can be restored. If I was allowed to use an external provider, it would be after encrypting the data only. I've written a bunch in these forums and on my blog about the most efficient non-image backup methods. My profile has links.  But ... if you can't be bothered to have image-based backups, then IMHO, perhaps RAID really isn't needed. RAID is about HA, with that comes added complexity.  It is possible to achieve similar redundancy with hourly snapshots without the added complexity. If you need RAID, your RTO and RPO will reflect that and justify the added expenses.

Backups are not just the data and programs, but the owner, group, permissions and any ACLs too. Be certain you select a backup method that provides those things with versioning of the permissions over time too - not just the last state. Permissions on files change over time.

I cannot think of any good reason to use FakeRAID on Linux. It has all the bad properties of HW-RAID without any of the performance. Perhaps there are situations where it does make sense?

SW-RAID (most levels) provide great flexibility and do not tie you to hardware. These days any SAS card can be used - assuming you are getting enterprise disks. I've moved SW RAID arrays between completely different systems without issues. It was shocking to me how trivial it was.

Sorry if I missed anything. Too late here to think.

---

### Post by MAFoElffen on 2015-04-08
> **Marc_Bressman said:**
> Thanks so much for the reply - a lot of good information to digest!

A few follow-ups:

1) Would you recommend CrashPlan for backups to the 3rd drive, or some sort of full bare metal backup software (to grab the entire OS and data, similar to how Norton Ghost used to work I guess, presumably with incremental capabilities) so that I can easily be up and running using the bare metal backup if I need to on another hard drive, or some other backup software?  I was thinking CrashPlan, since RAID1 should allow me to recover if one of the two hard drives goes, and CrashPlan backup on the 3rd drive (and to the cloud also) will allow me to recover if I get a virus infection, some other sort of data loss, etc.

I have my own bash scripts that I fire off as cron jobs. For my sys, I do a full / at intervals, those, then incremental on /etc. On the full, that is less /home and dependent on the services that server offers... which I then put those on another schedule, but still from scripts. On the ones on LVM, I do a full, then snapshots for incrementals. I back all mine to my storage server, which is fiber attached.
> 
2) Good call on ensuring that I can use drives greater than 2 TB - I know I had an older HP Elite HPE-390t desktop (maxed out from a few years ago since I had bought it and used it as my desktop PC for some time) that I was planning on initially using as my "server" and I had to actually modify the BIOS to insert the newer Intel RST option ROM (OROM) so that it would support drives greater than 2 TB, but not sure if I can do the same on this machine - will definitely check first, but either way I think going with 2 x 4 TB and 1 x 6 TB makes sense - right?

Good call.
> 
3) Can you suggest what sort of Enterprise drives I should look at for the 4 and 6 TB ones?  I was thinking maybe WD RE series, or HGST, but am open to anything.  And what sort of prices should I be looking to get them for?  

WD RE's are good. I sort of lean towards WD Red Pro's. Same warranty (5 years). Rated for 10 drive NAS. Just a little more in cost per. 
> 
4) How would I add more fans in the desktop case?  I was only going to get 3 hard drives anyway since the case supports 2 x 3.5" drives and 2 x 5.25" drives (one slot already taken up with the CD drive and I ordered a 5.25 to 3.5" bracket so I could use the other slot) - so do you think I need to add more fans?


There is usually a spot in the back of most cases where you can add a fan. Some have a spot for a fan in the front of the card slots. I drill holes through the case cover and add a fan. I have SATA cages, where there are 3 SATA trays, that fit into two 5-1/2" bays. All those have fans. I get fans that mount to the card mounting screws. Other fans I mount to 3-1/2 drives bays (w/ brackets). Just ideas. Most my hardware is traditional server hardware, but my other cases have around 10 fans. In the winter, I don't need to heat my home server room. Most the heat from that is from the drives.

---

