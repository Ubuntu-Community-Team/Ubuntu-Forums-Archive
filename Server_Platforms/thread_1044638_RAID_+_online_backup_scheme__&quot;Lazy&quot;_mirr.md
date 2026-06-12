---
title: "RAID + online backup scheme?  &quot;Lazy&quot; mirroring?"
date: 2009-01-19
forum: Server Platforms
---

### Post by kpatz on 2009-01-19
I'm still tossing around file server ideas, in particular, how I'll handle data storage and backups.

Basically, I want to build a server that's reasonably power-efficient, but also robust (as in I won't lose everything if a drive dies).  I've tossed around ideas such as:

1.  Simple RAID 1 mirror.  Pros:  simple, cheap (only 2 drives needed), redundant.  Cons:  No recovery from accidents (deleted/overwritten/corrupted files), drives need to be online full-time.

2.  2-drive "lazy" mirror.  Basically, one drive that's live and a 2nd that is mirrored or rsynced to the first drive nightly.  Pros: cheap, enough redundancy for my needs, some protection from "oopses" (accidentally delete a file, recover it from the lazy mirror), 2nd drive can be spun down when the backup isn't being run.  Cons: not fully redundant, but chances are I can live with losing a day's worth of data.

3.  RAID 5.  Pros:  Redundant, higher performance, array can be expanded easily.  Cons:  No accident recovery, 3 or more drives need to be spinning 24/7.

4.  The Masochist:  RAID 5 + nightly backup to 2nd set of drive(s).  The best of both worlds.  Cons:  need lots of drives (at least 4, probably 5), backup drive set would need to have capacity at least matching the array.

In addition to the online backups, I'll also do periodic offline backups to external USB enclosures.

Thoughts?

---

### Post by fjgaude on 2009-01-19
If there is any value to your data your option 4) is the only way to go. I use three backups, one online, one near-line, and finally, one off-line. I use **Grsync** and **Unison**, depending where the backups go. Four-drive **mdadm** raid5.

---

### Post by windependence on 2009-01-19
I agree with [fjgaude]("http://ubuntuforums.org/member.php?u=236865"), if your data is mission critical you need to go this way. Power consumption is not what you think it is. I have a FULL rack of servers running 24/7/365, and my electric bill at the house is only $120 per month including the rest of the house (electric range, A/C, etc). Spinning down 2 hard drives is not even going to be noticed, and will probably cause you more headache than benefit.

-Tim

---

### Post by kpatz on 2009-01-20
This is a home server, not business, it's not exactly "mission critical".  But I have archival data (e.g. photos) that I don't want to lose.

The amount of data changing on a day-to-day basis is minimal, much of the stuff is of the backup-once-because-it-never-changes category.  If I kept all my stuff on a drive, and it dies, it's not the "new" stuff I'm so concerned about (as it can be recreated/re-downloaded), it's the old stuff (photos that are long gone from the camera memory, old emails, etc).

And it isn't just "energy consumption", it's heat and noise too.  I don't need a jet plane in my office.

I figure the main drive/array will be 1-1.5 TB in size (though it won't be full, for a while anyway).  The near-line backup drive(s) would be similarly sized obviously.

I'll be running virtualbox on the machine as well, hosting development/test environments (e.g. trying out Windows 7 beta, or what have you).

---

### Post by kpatz on 2009-01-23
I just came up with a cool idea while replying to a thread on another forum WRT backups...

I could build the server with a built-in drive, and a removable hot-swap drive bay, configured as a RAID 1 array.  I would also have a couple extra drives available for the bay.  With RAID 1, the internal drive would be mirrored to the removable drive in real-time, and to "take a backup", I would just pull the removable drive and pop another one in.  The new drive would be synced up automatically and the removed drive can be taken offsite for storage.

That approach could kill multiple birds with one stone.  I would have redundancy with the RAID 1, offline backups by swapping drives periodically, and if the day comes that I need to expand storage, just install a larger drive and then copy from one of the backups.  And the "green" in me finds two drives spinning 24/7 a bit more friendly than 5-6.

---

### Post by fjgaude on 2009-01-23
Great, let us know how things work out.

---

### Post by Cracauer on 2009-01-23
> **kpatz said:**
> I just came up with a cool idea while replying to a thread on another forum WRT backups...

I could build the server with a built-in drive, and a removable hot-swap drive bay, configured as a RAID 1 array.  I would also have a couple extra drives available for the bay.  With RAID 1, the internal drive would be mirrored to the removable drive in real-time, and to "take a backup", I would just pull the removable drive and pop another one in.  The new drive would be synced up automatically and the removed drive can be taken offsite for storage.

That approach could kill multiple birds with one stone.  I would have redundancy with the RAID 1, offline backups by swapping drives periodically, and if the day comes that I need to expand storage, just install a larger drive and then copy from one of the backups.  And the "green" in me finds two drives spinning 24/7 a bit more friendly than 5-6.

Bad idea.

1) This only works right if you downgrade your filesystem to readonly status during the mirroring.

2) It puts horrible load on your primary drive and it will die sooner.

3) It's a classic "old backup is killed at the beginning of the new backup" situation. if the primary drive dies right after you started syncing you are dead.

---

### Post by Cracauer on 2009-01-23
> **kpatz said:**
> I'm still tossing around file server ideas, in particular, how I'll handle data storage and backups.

Basically, I want to build a server that's reasonably power-efficient, but also robust (as in I won't lose everything if a drive dies).  I've tossed around ideas such as:

1.  Simple RAID 1 mirror.  Pros:  simple, cheap (only 2 drives needed), redundant.  Cons:  No recovery from accidents (deleted/overwritten/corrupted files), drives need to be online full-time.

2.  2-drive "lazy" mirror.  Basically, one drive that's live and a 2nd that is mirrored or rsynced to the first drive nightly.  Pros: cheap, enough redundancy for my needs, some protection from "oopses" (accidentally delete a file, recover it from the lazy mirror), 2nd drive can be spun down when the backup isn't being run.  Cons: not fully redundant, but chances are I can live with losing a day's worth of data.


For most people, the most important data is small, such as files they edited.

You can have an increased rsync rate for different parts of the filesystem. And you can also have multiple rsync points for small files to have older versions around (filesystem snapshots are better, of course).

> **kpatz said:**
> 
3.  RAID 5.  Pros:  Redundant, higher performance, array can be expanded easily.  Cons:  No accident recovery, 3 or more drives need to be spinning 24/7.


Raid-5 isn't faster for all things. Most access patterns, yes, but overall raid-1 does pretty well. Faster re-sync, too.

> **kpatz said:**
> 
4.  The Masochist:  RAID 5 + nightly backup to 2nd set of drive(s).  The best of both worlds.  Cons:  need lots of drives (at least 4, probably 5), backup drive set would need to have capacity at least matching the array.


The second set of drives should be on a second power supply. There is a non-ignorable risk that a dying power supply takes down all harddrives.

Also think of physical accidents that happen to your primary computer case.

> **kpatz said:**
> 
In addition to the online backups, I'll also do periodic offline backups to external USB enclosures.


USB harddrive still lack proper error handling, it's a little dicey.  I don't now whether all layers have been cleared up by now.

I back up to a second machine in the basement holding a RAID of older harddrives.  If you use a filesystem with snapshots for that box you also have safety against silently corrupted files.

---

### Post by kpatz on 2009-01-23
> **Cracauer said:**
> 1) This only works right if you downgrade your filesystem to readonly status during the mirroring.That isn't true is it?  I thought RAID mirroring happens in the background.  If a drive dies in an array, and you swap it, you aren't stuck in read-only while the array rebuilds itself.> 2) It puts horrible load on your primary drive and it will die sooner.Do you have proof of this?> 3) It's a classic "old backup is killed at the beginning of the new backup" situation. if the primary drive dies right after you started syncing you are dead.Not entirely true.  The drive just pulled out has a current backup.  The only data at risk is anything that is new/changed after the drive is pulled but before the re-sync is complete.  This is a home server that won't have a lot of "critical" data changing on a daily basis.  I won't be updating my Quicken files during a re-sync, in other words. :)

I may set up a filesystem/drive structure that puts archival data (stuff that tends to remain static once created, like photos) on one drive, and frequently-changing data on another, and have different backup schedules for each.> The second set of drives should be on a second power supply. There is a non-ignorable risk that a dying power supply takes down all harddrives.Takes them down, yes, but once you pop in a new power supply, the drives are back online.  I don't need 24/7 availability, just protection against losing stuff I've accumulated over the years (photos, music, etc).

Also, much of the "archival" stuff this machine would be keeping are just copies of stuff already on other computers, so they would already be backups of other stuff.  Instead of having 1 copy of my photos on my desktop PC, I would have a copy on my desktop, a copy on the server, and then whatever backups I generate from the server.  The server would act to centralize my backup scheme, my other systems would back up to the server, so I wouldn't have to manually back up data on each machine separately.

I need to research this snapshot thing people are talking about.

---

### Post by hyper_ch on 2009-01-23
raid is no backup... however if you want to backup by raid mirroring, make at least raid1 with 3 drives... 2 drive constantly run in degraded mode and then adding another one for the backup whenever you feel like it...

However I'd use rsync to create incremental snapshot style backups once a day (or more)

---

### Post by Cracauer on 2009-01-23
> **kpatz said:**
> > 
Originally Posted by Cracauer View Post
1) This only works right if you downgrade your filesystem to readonly status during the mirroring.That isn't true is it?  I thought RAID mirroring happens in the background.  If a drive dies in an array, and you swap it, you aren't stuck in read-only while the array rebuilds itself.

It will statistically, mostly work if you do it on a read-write mounted filesystem. You'll see most files intact.

But blocks for files might be reallocated during write operations and then you lose if you pull out the drive.  

In other words: the beginning of your backup drive has the state from an hour earlier than the end of the backup drive.

To solve this you have to downgrade the filesystem to readonly status.

It's the same problem as any backup of the raw device, has nothing to do with RAID.

 > **kpatz said:**
> 

Do you have proof of this?



Uh? The block device layer has no idea which blocks were changed and which blocks are even parts of files. If you do a block device backup you always do the whole drive. If you do a solution within the filesystem you don't backup unallocated blocks and if you use rsync you save even more access to the primary drive.

 > **kpatz said:**
>  Not entirely true.  The drive just pulled out has a current backup.  The only data at risk is anything that is new/changed after the drive is pulled but before the re-sync is complete.  This is a home server that won't have a lot of "critical" data changing on a daily basis.  I won't be updating my Quicken files during a re-sync, in other words. :)


If the data doesn't matter why go through the trouble :)

You can improve this particular sub-problem by using two pulled drives so that one is on the shelf while the first is at the beginning of backup.

By you cannot override the first 1% of a block device with a new filesystem state and expect the 99% of the days-old contents after it to be readable.

> **kpatz said:**
> 
I may set up a filesystem/drive structure that puts archival data (stuff that tends to remain static once created, like photos) on one drive, and frequently-changing data on another, and have different backup schedules for each.


That's generally wise.  If you narrow down important data to a small enough size you just rsync it to a different continent. Then you hometown can get nuked and you still have your data :)

> **kpatz said:**
>  Takes them down, yes, but once you pop in a new power supply, the drives are back online.


No. Dying PSUs killing all or most components connected are pretty common.  Harddrives are sometimes killed due to power fluctuations from bad UPSs, too.  Another reason to have your backup set separately.

 > **kpatz said:**
>    I don't need 24/7 availability, just protection against losing stuff I've accumulated over the years (photos, music, etc).


If your photos are important you must also guard against silent data corruption such as from bad memory (you probably don't even have ECC memory in that box, right?).

You can't just blindly overwrite all backups with what you primary array holds. In 10 years you'll find you corrupted your best shots 5 years ago.

This is why I go for snapshots on the backup server. Doing checksums on data that's marked as immutable (photos generally are) is another way to do that.

---

### Post by Robstarusa on 2009-01-23
Don't raid5.  Google "raid 5 write hole"

Use raid 1 or raid 10

---

### Post by windependence on 2009-01-23
> **Robstarusa said:**
> Don't raid5.  Google "raid 5 write hole"

Use raid 1 or raid 10
And you think RAID 1 is better because?

RAID 5 will increase your data bandwidth because you have more spindles, and you get fault tolerance as well. Most commercial enterprises use RAID 5. 

Google "Aspirin" and then tell me if you want to take any.

-Tim

---

### Post by Robstarusa on 2009-01-23
> **windependence said:**
> And you think RAID 1 is better because?

RAID 5 will increase your data bandwidth because you have more spindles, and you get fault tolerance as well. Most commercial enterprises use RAID 5. 

Google "Aspirin" and then tell me if you want to take any.

-Tim

Where do you see most commercial enterprises use raid5????  Did you just make that up or do you have a reputable source?

Raid5 has a parity stripe.  Raid 1/10 does not.

Also, read this: 
[http://blogs.zdnet.com/storage/?p=162](http://blogs.zdnet.com/storage/?p=162)

---

### Post by fjgaude on 2009-01-23
Okay, coming from the big corporation work space, though retired now, and I have relatives working for huge ones, I can attest to the fact they use raid5 and raid6. In fact, many of the drive nodes are actually 3-drive raid5 arrays. You talk about speed and availability!

A five-drive raid5 array has four times the bandwidth as a single drive. Eight drives are more usual at the big sites.

---

### Post by windependence on 2009-01-24
> **Robstarusa said:**
> Where do you see most commercial enterprises use raid5????  Did you just make that up or do you have a reputable source?
No, not really just like you don't have any idea what goes on in the enterprise. I thought maybe because I worked for some smaller companies like IBM, Swift Transportation, and Mattel, I might have some idea but I guess I was wrong. Are you from some other planet?

> **Robstarusa said:**
> Raid5 has a parity stripe.  Raid 1/10 does not.

...And your point is? Why would that be BAD? Oh you mean I can have one drive fail and I can safely replace it without having to restore my backup? Seriously dude, you need to pick up a good book on storage systems and then read the chapter on RAID.

The poster above (MR. RAID!  ;)) is quite correct. Most server OS drive configs were 3  or 4 drives in RAID 5. I also ran several AS/400s for IBM and you know, it's funny, those nasty DASD boxes had groups of 6 drives in a parity set in ....yep, you guessed it, RAID 5. We used very little RAID 1 and I NEVER saw RAID 10 in the enterprise. BTW, most servers didn't have terabytes of storage either. Main storage was on the SAN.

> **Robstarusa said:**
> Also, read this: 
[http://blogs.zdnet.com/storage/?p=162](http://blogs.zdnet.com/storage/?p=162)

Where do you GET this FUD? The first commenter sums it up quite well:
> 
after more thought **The unrecoverable error rate is measured in bits. There are 8 bits to a 1 byte. So if the error rate is 1 in 100 trillion bits, then who gives a flip? **

If one bit in a byte is messed up, then the hard drive can use built-in ecc to fix it. Many drives depend on this feature for normal operation. This process depends on how the data-to-ecc ratio is set and other factors. So, purely on a hard drive level, it's doubtful this would be an issue. A data protection feature would eventually kick in and reallocate the data to another sector if the error rate goes beyond a certain threshold-- though the sector is still readable. Which brings me to the whole purpose of SMART to analyze report and report said data to the controller and signal when a TEC occurs. 

So, while there are clusters in your RAID 5/6 setup, that will correspond to a specific number of sectors on a hard drive, which consist of a fixed number of bytes/sector (remember CHS, anyone?), and depending on the architecture, every sector will have a specific amount of data and ecc. So, ECC + RAID Parity = a whole lotta protection.

You'd have to have multiple levels of failure to have this "2009" problem IMHO. 	 	 	

I do this for a living, now working as a consultant. I have a full rack in my spare room where I host client web sites......on RAID 5 arrays.....

You might want to stop believing all the stuff you read on blogs unless you can really verify the information. Do you really think drives won't be solid state in just a few short years? Technology is advancing faster than I can keep up. Do you really think drive manufacturers aren't looking at this or hadn't thought if it before?

-Tim

---

### Post by windependence on 2009-01-24
> **kpatz said:**
> I just came up with a cool idea while replying to a thread on another forum WRT backups...

I could build the server with a built-in drive, and a removable hot-swap drive bay, configured as a RAID 1 array.  I would also have a couple extra drives available for the bay.  With RAID 1, the internal drive would be mirrored to the removable drive in real-time, and to "take a backup", I would just pull the removable drive and pop another one in.  The new drive would be synced up automatically and the removed drive can be taken offsite for storage.

That approach could kill multiple birds with one stone.  I would have redundancy with the RAID 1, offline backups by swapping drives periodically, and if the day comes that I need to expand storage, just install a larger drive and then copy from one of the backups.  And the "green" in me finds two drives spinning 24/7 a bit more friendly than 5-6.

Just wanted to mention I do this for several of my commercial customers (their idea). About once a month I go to a certain companies CoLo where they host their websites nationwide on SuSE 10.2. I plug in a blank SCSI drive and dd the entire drive over *while the system is running. *Then, we pull the drive and store it offsite. We can plug in the drives and boot them just like the original drives without any problems so far. Technically, yes it would be best to unmount the drives, but this works for me. :)

-Tim

---

### Post by Ein2015 on 2009-01-24
I've been using Dropbox ([http://getdropbox.com](http://getdropbox.com)) to sync up files on multiple computers and to serve as online backups.  It updates whenever a file somewhere has changed and only sends the changed data between computers.

Could be worth looking to.  I only use the free (2gb) version, though... although I think they offer something like up to 50gb for a fee.

Not sure how much data you're talking about there.  :)

---

### Post by kpatz on 2009-01-24
Yeah, looks like rsync would be more efficient than swapping drives and mirroring.

So maybe, a raid5 array + a removable drive that data gets rsync'd to daily or so.  I could organize the folders in the array into categories such as archival (rarely change), regular (changes occasionally) and important (changes often) and schedule the rsyncs based on that.  For offline backups, just swap the drive out in the bay, and then the next rsync will update the new drive.

Another possibility (though more costly) would be to build a 2nd box and locate it elsewhere in the house and rsync to that.  I would still need offsite backups in case of fire etc.

Speaking of fire, I had one back in '05, destroyed the house, but I lost no data.  How?  Because I had offsite backups?  No.  Because I had online backups?  No.  My last backup was on DVDs that melted.  The hard drives in my computers survived the fire, as the computers were towers on the floor, they didn't get as hot as the DVDs on a high shelf.  So, if you can't easily go offsite for backups, keep one backup near the floor (or in the basement) where fire is less likely to destroy it, and one up in the attic, where a flood is less likely to destroy it. :)

---

### Post by Cracauer on 2009-01-26
> **fjgaude said:**
> 
A five-drive raid5 array has four times the bandwidth as a single drive. Eight drives are more usual at the big sites.

That's a much too broad statement. Different access patterns have very complicated performance characteristics changes when you move from one raid level to another.

%%

The problem of raid holes can't be solved without going into the filesystem layer. You need something like ZFS and the associated multi-drive array mechanisms.

I think in practice the RAID write hole isn't terribly likely to occur. Although it is an obvious lie that a harddrive can empty it's cache after a power fail using the energy stored in the rotating disks, it will probably be able to write *one* sector (people who leave the write cache on have much bigger problems anyway). That would leave use with problems of the CPU/system becoming disabled after writing to one but not all disks.

---

### Post by fjgaude on 2009-01-26
> **Cracauer said:**
> That's a much too broad statement. Different access patterns have very complicated performance characteristics changes when you move from one raid level to another.

You are correct about that but the intent was really to show the performance increase, generally, of raid5 over bare drives, especially if you are using SCSI and not SATA.

Thanks for your insight.

---

### Post by Cracauer on 2009-01-26
> **fjgaude said:**
> You are correct about that but the intent was really to show the performance increase, generally, of raid5 over bare drives, especially if you are using SCSI and not SATA.

Thanks for your insight.

Can't say I noticed that my SATA drives, after getting all the AHCI with NCQ up and running, show anything that would make them less suitable for RAID-5 than my SCSI drives (for comparable disks).

---

### Post by kpatz on 2009-02-03
Back on the "greenness" factor:  what if I used laptop hard drives instead of desktop ones, such as [this one](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136314).

RAID-5ing a bunch of those would likely draw less power than a smaller number of 3.5" drives, right?

---

### Post by Cracauer on 2009-02-04
> **kpatz said:**
> Back on the "greenness" factor:  what if I used laptop hard drives instead of desktop ones, such as [this one](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136314).

RAID-5ing a bunch of those would likely draw less power than a smaller number of 3.5" drives, right?

From my experience laptop drives cannot stand the load of a home server. You'd want 2.5" SAS drives, that would work.

Modern 3.5" drives take about 10 watts idle. Might not be worth the trouble.

---

### Post by kpatz on 2009-02-06
Here's the parts I'm thinking of using:

**[GIGABYTE GA-MA78G-DS3HP AM2+/AM2 AMD 780G HDMI ATX AMD Motherboard](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128373)**
I chose this mobo because it has integrated video, 6 SATA ports and built-in gigabit ethernet.

**[AMD Athlon X2 4850e 2.5GHz Socket AM2 45W Dual-Core Processor](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103255)**
I picked this because it's 45 watts, one of AMD's greenest chips.  I've been tossing around putting a quad-core Phenom II in for better VM performance but those suck a lot of power (how are they when idle?)

**[Kingston 4GB 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Desktop Memory Model KVR800D2N6/4G](http://www.newegg.com/Product/Product.aspx?Item=N82E16820134863)**
I want 8 GB RAM and room to expand, and DDR2 1066 4GB DIMMs are expensive.

**[Western Digital Caviar Green WD10EADS 1TB SATA 3.0Gb/s Hard Drive](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136317)**
At least 3 of these in a RAID 5 configuration.  I'll probably get 4 and keep one as a spare, or maybe more to set up some kind of backup system.

**[Antec P182 Gun Metal Black 0.8mm cold rolled steel ATX Mid Tower Computer Case](http://www.newegg.com/Product/Product.aspx?Item=N82E16811129025)**
I like this case, and it has plenty of room for hard drives, and good cooling too.

[b][url=http://www.newegg.com/Product/Product.aspx?Item=N82E16835103040]
COOLER MASTER RR-CCH-LB12-GP 120mm Sleeve CPU Cooler[/url][/b]
Overkill I know, but I always go overboard with CPU cooling.  If the airflow in the case is good enough, and I use the 45W CPU, I may be able to forego the fan on this HS.

Haven't decided on a PSU yet, but I want one that's at least 85% efficient if possible.  Most of the highest-efficiency PSUs are 800 watts and higher, and I don't need that much.

Thoughts?  Ideas?  Suggestions?

---

### Post by mregister on 2009-02-06
> **windependence said:**
>  Seriously dude, you need to pick up a good book on storage systems and then read the chapter on RAID.



I need to learn all I can about storage systems so do you have any good book recommendations on that? Any and all recs are much appreciated. Love this thread btw, lot's of good points to consider. Thanks to all.

-Mark

---

### Post by fjgaude on 2009-02-06
> **mregister said:**
> I need to learn all I can about storage systems so do you have any good book recommendations on that? Any and all recs are much appreciated. Love this thread btw, lot's of good points to consider. Thanks to all.

-Mark

To get started there's lots of online stuff that educates:

[http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html)
[http://www.hscripts.com/tutorials/linux-services/mdadm.html](http://www.hscripts.com/tutorials/linux-services/mdadm.html)
[http://users.piuha.net/martti/comp/ubuntu/en/raid.html](http://users.piuha.net/martti/comp/ubuntu/en/raid.html)

---

### Post by kpatz on 2009-02-24
Well, I ordered parts the other day so hopefully this weekend I'll be putting together my new file server!

Here's what I ended up going with:

[ASRock A780GXE/128M AM2+/AM2 AMD 780G ATX AMD Motherboard](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157139)
It's cheap and has the features I want--integrated video, 6 SATA ports, Gigabit ethernet, AM3 ready.

[AMD Phenom II X4 920 2.8GHz Socket AM2+ 125W Quad-Core Processor](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103472)
Quad core, yummy!

[Western Digital Caviar Green WD10EADS 1TB SATA 3.0Gb/s Hard Drive](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136317)
4 for a RAID array.

[Antec P182 Gun Metal Black 0.8mm cold rolled steel ATX Mid Tower Computer Case](http://www.newegg.com/Product/Product.aspx?Item=N82E16811129025)
I don't need hot swap bays, and cases with those are expensive.  This one has nice quiet cooling.

[Kingston HyperX 4GB 240-Pin DDR2 SDRAM DDR2 1066 Desktop Memory Model KHX8500D2K2/4G](http://www.newegg.com/Product/Product.aspx?Item=N82E16820104073)
I'm getting 2 pair (4 DIMMs) for 8GB total, for running virtual machines.

[Rosewill RCX-Z940-SL 92mm 2 Ball CPU Cooler](http://www.newegg.com/Product/Product.aspx?Item=N82E16835200023)
I always use aftermarket coolers in my AMD builds, as they cool better.

[COOLER MASTER SAF-S12-E1 120mm Case Fan](http://www.newegg.com/Product/Product.aspx?Item=N82E16811999072)
to go in the front of the case to keep the drives cool...

And last but not least...

[SILVERSTONE ST60F 600W ATX12V / EPS12V SLI Certified CrossFire Ready 80 PLUS BRONZE Certified Modular Active PFC Power Supply](http://www.newegg.com/Product/Product.aspx?Item=N82E16817163109)
Efficient, quiet, cheap (w/rebate), modular, and has plenty of SATA power connectors.

I have a stash of extra DVD burners in my closet so I'll drop one of those in.

Should have the stuff in time for the weekend!  :D

---

### Post by fjgaude on 2009-02-24
Pray, do tell us how you are doing with all that wonderful stuff. <smile>

---

### Post by alfonso78 on 2011-03-07
> **kpatz said:**
> Well, I ordered parts the other day so hopefully this weekend I'll be putting together my new file server!

Here's what I ended up going with:

[ASRock A780GXE/128M AM2+/AM2 AMD 780G ATX AMD Motherboard](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157139)
It's cheap and has the features I want--integrated video, 6 SATA ports, Gigabit ethernet, AM3 ready.

[AMD Phenom II X4 920 2.8GHz Socket AM2+ 125W Quad-Core Processor](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103472)
Quad core, yummy!

[Western Digital Caviar Green WD10EADS 1TB SATA 3.0Gb/s Hard Drive](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136317)
4 for a RAID array.

[Antec P182 Gun Metal Black 0.8mm cold rolled steel ATX Mid Tower Computer Case](http://www.newegg.com/Product/Product.aspx?Item=N82E16811129025)
I don't need hot swap bays, and cases with those are expensive.  This one has nice quiet cooling.

[Kingston HyperX 4GB 240-Pin DDR2 SDRAM DDR2 1066 Desktop Memory Model KHX8500D2K2/4G](http://www.newegg.com/Product/Product.aspx?Item=N82E16820104073)
I'm getting 2 pair (4 DIMMs) for 8GB total, for running virtual machines.

[Rosewill RCX-Z940-SL 92mm 2 Ball CPU Cooler](http://www.newegg.com/Product/Product.aspx?Item=N82E16835200023)
I always use aftermarket coolers in my AMD builds, as they cool better.

[COOLER MASTER SAF-S12-E1 120mm Case Fan](http://www.newegg.com/Product/Product.aspx?Item=N82E16811999072)
to go in the front of the case to keep the drives cool...

And last but not least...

[SILVERSTONE ST60F 600W ATX12V / EPS12V SLI Certified CrossFire Ready 80 PLUS BRONZE Certified Modular Active PFC Power Supply](http://www.newegg.com/Product/Product.aspx?Item=N82E16817163109)
Efficient, quiet, cheap (w/rebate), modular, and has plenty of SATA power connectors.

I have a stash of extra DVD burners in my closet so I'll drop one of those in.

Should have the stuff in time for the weekend!  :D

Hi kpatz,

I know this thread is quite old, but you seem to be facing the same issues I'm facing today.

so what was your choice at the end?

I hear ZFS is really a superior choice, it's too bad there is no stable support in Linux.

I'm thinking at either RAID5 or RAID6 and use crashplan (3USD/month) for external backup.

my question is: how can I test that the RAID works? before trusting all my data to my new box, I'd like to make sure I know how to handle a drive failure and rebuild the array.

any suggestion?

thanks!

---

### Post by rubylaser on 2011-03-07
Set it up in Virtualbox to match your long term setup (use smaller virtual disks though).  Then write some data to the array.  md5 checksum it.  Then remove disks from the virtual machine, add them back to watch it resync.  Fail, and remove disks and replace with new, etc.  Remove a disk while writing, etc. When you're all done testing md5 checksum your original data and verify that it matches.

You can watch here if you're interested in the progress of ZFS on linux.[http://zfsonlinux.org/]("http://zfsonlinux.org/")

---

### Post by alfonso78 on 2011-03-08
> **rubylaser said:**
> Set it up in Virtualbox to match your long term setup (use smaller virtual disks though).  Then write some data to the array.  md5 checksum it.  Then remove disks from the virtual machine, add them back to watch it resync.  Fail, and remove disks and replace with new, etc.  Remove a disk while writing, etc. When you're all done testing md5 checksum your original data and verify that it matches.

You can watch here if you're interested in the progress of ZFS on linux.[http://zfsonlinux.org/]("http://zfsonlinux.org/")

great idea! thank you! :)

---

### Post by alfonso78 on 2011-03-08
> **rubylaser said:**
> Set it up in Virtualbox to match your long term setup (use smaller virtual disks though).  Then write some data to the array.  md5 checksum it.  Then remove disks from the virtual machine, add them back to watch it resync.  Fail, and remove disks and replace with new, etc.  Remove a disk while writing, etc. When you're all done testing md5 checksum your original data and verify that it matches.

You can watch here if you're interested in the progress of ZFS on linux.[http://zfsonlinux.org/]("http://zfsonlinux.org/")

sorry, one more thing, do you know what happens in case resync encounters an unrecoverable read error (URE)?
I've been reading these article and similar:
[http://www.tomshardware.com/news/RAID-5-Doomed-2009,6525.html](http://www.tomshardware.com/news/RAID-5-Doomed-2009,6525.html)

Is there a chance to instruct resync to simply tell me which file is hit by the URE and continue the resync process rather than get stuck and abandon? (I will use software RAID, not an HW RAID controller)

thanks!

---

### Post by rubylaser on 2011-03-08
Yes, your Tom's Hardware example is possible.  Neil Brown the lead developer of mdadm, has at Bad Block log at the log of his list of things to do.  Here's a link
[http://neil.brown.name/blog/20110216044002]("http://neil.brown.name/blog/20110216044002")

This will greatly reduce the risk of potential loss as well as minimizing the scope of the loss.  When all of these features are implemented mdadm will be amazing (really, it already is).

---

### Post by alfonso78 on 2011-03-09
> **rubylaser said:**
> Yes, your Tom's Hardware example is possible.  Neil Brown the lead developer of mdadm, has at Bad Block log at the log of his list of things to do.  Here's a link
[http://neil.brown.name/blog/20110216044002]("http://neil.brown.name/blog/20110216044002")

This will greatly reduce the risk of potential loss as well as minimizing the scope of the loss.  When all of these features are implemented mdadm will be amazing (really, it already is).

Great link!! Thanks a lot.

Too bad support is not there, great that it's the 1st item in the roadmap!

Do you know which release of md raid is implemented in ubuntu 10.10?

---

### Post by rubylaser on 2011-03-09
I always grab the deb package of the newer version of mdadm.  But based on the repository, it looks like mdadm 2.6.7.1.  3.1.4 is now the stable version.  Here's how I set it up typically (this is the 64 bit version) from Debian.
```
wget http://ftp.us.debian.org/debian/pool/main/m/mdadm/mdadm_3.1.4-1+8efb9d1_amd64.deb
dpkg -i mdadm*.deb
```

---

