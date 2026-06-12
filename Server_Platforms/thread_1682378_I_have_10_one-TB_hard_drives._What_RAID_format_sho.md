---
title: "I have 10 one-TB hard drives. What RAID format should I use?"
date: 2011-02-05
forum: Server Platforms
---

### Post by B34ST1Y on 2011-02-05
I have 10 one-TB hard drives. What RAID format should I use? I want the greatest capacity I can achieve out of it, but still want to retain enough redundancy so if one or two drives fail, it is still rebuildable.

---

### Post by Hedgehog1 on 2011-02-05
Do you already own a raid controller (or two)?  If so, what raid options does it support.  We can advise based on those it offers.

If you don't have a raid controller (or controllers) yet, what is your budget for it/them?

Will you be stuffing them into your PC's case, or going with an external case?
Perhaps you were thinking of putting them into a NAS?
Did you want a hot-swappable disk option in case of failure?

Give us a little to work with...

:KS

**Added** What are the models of the hard drives?  Not all large hard drives work well in a RAID situation (other than Raid 0)...

---

### Post by YesWeCan on 2011-02-05
it is a tricky question as i am discovering as i learn more about how different raid levels work in practice. the only level that mdadm supports that is tolerant to two HD failures is RAID6. you would get 8TB capacity.

However, it isn't this simple. These Gallois Field systems are all very well on paper but what they do, as I understand it, is to make every disk critical because every disk is needed to reconstruct the contents of a failed disk, or two failed disks in the case of raid 6. This is a risk when the raid controller tries to reconstruct: it must not encounter a single error in the whole of the rest of the array...if it does you cannot rebuild the array. What are the chances?

Another consideration is write performance. All the parity calculations can take a significant toll on performance. From what I have read it is not untypical for a RAID5 to write at half the speed it will read. RAID6 is worse in this regard.

A RAID 10 on the other hand will only give you 5TB and will survive at least 1 disk failure and at most 5. There are no parity calculations. But, importantly, if a disk fails it can be reconstructed from its mirror only. So you only need 1 disk to restore the array rather than being dependent on the whole array.

Another factor that I am exploring is the ability of mdadm to deal with complexity. I have read a couple of alarming stories about mdadm just not working as expected in the RAID5 scenario when a disk fails. This concerns the quality of the algorithms and the reliability of the coding. I have normal concerns about both of these and I would certainly not commit critical data without doing extensive failure mode/recovery trials. I am not aware of just how robust the coding quality control is and the testing.

RAID 10 is not very capacity efficient but it is fast and it is relatively simple from an algorithmic and coding point of view.

I have read that If you are intending to use this for a huge database you are better off, performance-wise, using five RAID1 arrays rather than one RAID10. This is because database applications can effectively do the striping themselves by virtue of their ability to spread data across multiple volumes.

---

### Post by Vegan on 2011-02-06
I suggest a high performance RAID card. With 10 disks RAID6 is appropriate as it can tolerate up to 2 disks failing.

I suggest keeping at least 1 spare disk on hand should one become problematic.

---

### Post by CharlesA on 2011-02-06
> **Vegan said:**
> I suggest a high performance RAID card. With 10 disks RAID6 is appropriate as it can tolerate up to 2 disks failing.

I suggest keeping at least 1 spare disk on hand should one become problematic.

+1. It's a good idea to go with RAID6 over RAID5 on anything with 4 or more disks, as it can handle 2 disks going out.

---

### Post by kevinthecomputerguy on 2011-02-06
+1, whenever you have more than (3) disks, go raid 6.
 
Raid 5 with a spare is always a good idea, but with that number of disk, raid 6 for sure.
 
*remember, no one solution is ever complete, you should still be backing up this system, with that said sometimes its good to have such a decreased capacity from the raid config, because you will still need somehow to back that up.
 
Raid 6 keeps me on my toes, with half the capicity, i always have someway to back it up. If i made some crazy 10 TB raid, i probably wouldnt have a way to completley back it up.

---

### Post by YesWeCan on 2011-02-06
> *from Wikipedia:* Data recovery in the event of a failed array
With larger disk capacities the odds of a disk failure during rebuild are not negligible. In that event the difficulty of extracting data from a failed array must be considered. Only RAID 1 stores all data on each disk. Although it may depend on the controller, some RAID 1 disks can be read as a single conventional disk. This means a dropped RAID 1 disk, although damaged, can often be reasonably easily recovered using a software recovery program. If the damage is more severe, data can often be recovered by professional data recovery specialists. RAID 5 and other striped or distributed arrays present much more formidable obstacles to data recovery in the event the array fails.
So the suggestion of taking backups of the array and not relying on "potential" redundancy is not to be taken lightly.
What's the optimum trade off here I wonder? It seems to me any use of distributed parity RAID demands backups, which demands additional storage capacity. But presumably one chooses this type of RAID in order to maximize array capacity - else one would choose RAID1.
Interesting.

---

### Post by CharlesA on 2011-02-06
> **YesWeCan said:**
> So the suggestion of taking backups of the array and not relying on "potential" redundancy is not to be taken lightly.
What's the optimum trade off here I wonder? It seems to me any use of distributed parity RAID demands backups, which demands additional storage capacity. But presumably one chooses this type of RAID in order to maximize array capacity - else one would choose RAID1.
Interesting.
Indeed.

The major disadvantage of RAID-1 is the loss of storage capacity, since you need one drive for each drive in the array.

RAID-5 and RAID-6 are the compromise between RAID-0 and RAID-1 (speed and redundency)

---

### Post by doogy2004 on 2011-02-06
You may want to checkout ZFS for file systems that large. [http://www.zfsbuild.com/](http://www.zfsbuild.com/) is a good resource.

RAIDz is similar to RAID5 
RAIDz2 is similar to RAID6

---

### Post by YesWeCan on 2011-02-06
> **CharlesA said:**
> Indeed.

The major disadvantage of RAID-1 is the loss of storage capacity, since you need one drive for each drive in the array.

RAID-5 and RAID-6 are the compromise between RAID-0 and RAID-1 (speed and redundency)

Ok. Comparing like for like, an 8TB RAID6 array needs ten 1TB disks and an 8TB RAID10 needs sixteen. But a RAID10 is inherently a lot faster, especially on writes. So to match the speeds one would have to buy faster disks/fast RAID controller for RAID6. Therefore the difference in cost between the two may be insignificant.

If the cost difference were insignificant I think I would go for RAID10 for the increased reliability of recovery from failure.

---

### Post by CharlesA on 2011-02-06
> **YesWeCan said:**
> 
If the cost difference were insignificant I think I would go for RAID10 for the increased reliability of recovery from failure.

True. But the price difference between 10 1TB drives and 16 1TB drives is a few hundred dollars.

---

### Post by YesWeCan on 2011-02-06
Yes it is. Maybe $500 depending on the speed of the disks. A really fast hardware RAID controller for RAID6 may cost a similar amount.

I think if I were, say, an IT pro responsible for other peoples' data and, indeed, minimized downtime/slow time during a drive resync, a few hundred dollars would be insignificant to me.

But I'm just thinking aloud here. I have no experience to back up my musings. And as we all know, it is important to have good backup. :p

---

### Post by rubylaser on 2011-02-07
A question posed like this really needs more info.  Like what are you going to use the array for?  File Storage, Media Storage, Database Server, etc.  Otherwise, trying to spec the right solution is a shot in the dark.  

For media storage, something like Unraid, Flexraid, ZFS (nexenta core, freebsd w/ zfs, or Openindiana) or mdadm will be more than fast enough to stream your media, and all all either free or much cheaper than a hardware RAID card.  Also, if you're going for media storage, I'd be going for bigger drives as 2TB seems to be the best price point right now, and having fewer spindles will reduce your energy consumption, and potentially reduce the chance of failure.

If it's File Storage a RAID6 array will work fine on a hardware RAID card.

If it's a database server, I'd strongly lean towards RAID10 simply for the speed over RAID5/6.

My 2 cents.

---

### Post by B34ST1Y on 2011-02-07
Wow -- didn't expect such a strong reply, thanks guys and gals.


Let me clarify:

I want to build a NAS that will be used in a very small community (3-4 people in a house) to store private & important data. Ideally, I'd like to use full disk encryption (PGP ?) and most importantly, have the array be able to scale later on if I decide to add more drives (run out of space). Rebuilding the entire array manually wouldn't be fun :( 

My initial budget, not to include hdd's is about 200 dollars -- I have spare PC parts, so I could probably build a basic computer w/Linux to manage it..

---

### Post by CharlesA on 2011-02-07
If that's the case, go for software RAID-6. That would meet yer budget requirements. :)

---

### Post by rubylaser on 2011-02-07
Well $200 bucks rules out all but used hardware RAID cards, so you'll either want to go with mdadm or ZFS.  I would suggest mdadm, so you can go with an Ubuntu file server, and RAID6.  Here's some directions to follow.
```
http://linuxgazette.net/140/pfeiffer.html
```

I personally would not bother with encryption as I assume this isn't leaving the house, and if you have physical access to a machine, it isn't secure anyways.  I'm only saying this because it adds another layer of complexity on top of other technology, that can make troubleshooting difficult.

---

### Post by CharlesA on 2011-02-07
> **rubylaser said:**
> 
I personally would not bother with encryption as I assume this isn't leaving the house, and if you have physical access to a machine, it isn't secure anyways.  I'm only saying this because it adds another layer of complexity on top of other technology, that can make troubleshooting difficult.

+1. I've thought about using encryption on my file server, but it won't be leaving the house and it'll be more of a pain in the butt to get backups and whatnot running.

---

### Post by YesWeCan on 2011-02-07
Does anyone know how many disk reads one should expect between unrecoverable errors/failures?


I was looking up the unrecoverable read error rate of the WD Caviar Black 1TB disk. I use these. WD claim <1 unrecoverable read error in 10^14 bits read. I reckon 10^14 bits is about 13 full disk reads.


In the context of choosing a RAID array type, what failure rate per full disk read should one assume? Specifically, what rate for the remaining disks once one disk has failed.

---

### Post by ratcheer on 2011-02-07
I managed Oracle database servers on systems comprising hundreds  of disk drives over a period of about 10 years. I only recall a handful of actual drive failures, probably less than five. Most data recovery was necessitated by controller failures or firmware errors or other system failures. I always ran RAID 1+0 (aka RAID 10) and, in the event of an actual disk drive failure the systems continued to run while the failed drive was replaced and the mirror was reestablished.

The only time RAID 1+0 requires an actual data recovery would be if two drives of the same mirror pair failed, simultaneously. That said, data backups are still an absolute necessity.

Tim

---

### Post by Vegan on 2011-02-07
RAID6 is plenty fast when using a good quality controller from a respectable outfit.

For backup, another server is the best choice. Then replication can be used.

[http://www.windows-it.tk/papers/raid.php]("http://www.windows-it.tk/papers/raid.php")

[http://www.windows-it.tk/papers/archive.php]("http://www.windows-it.tk/papers/archive.php")

[http://www.windows-it.tk/papers/disk-reliability.php]("http://www.windows-it.tk/papers/disk-reliability.php")

---

### Post by rubylaser on 2011-02-07
I would agree with using RAID6 with a hardware RAID card, but he OP stated they only have a $200 budget.  If you can show me a new RAID card that supports RAID6 on 10 drives from a respectable RAID card vendor, I'll buy 4 myself right now :)

An unfortunately, those error rates are averages.  Probably the best advise is to not buy all the disks at the same time from the same vendor (not all from the same batch).  If one fails, it certainly shows that those drives are all potentially vulnerable.

And, you'll need to setup alerting so that you get a warning when a disk fails.  So many people fail in this step with software RAID, and don't catch a disk failure, which when another disk fails 2 months later they loose their data because they never knew about the failure.

---

### Post by YesWeCan on 2011-02-08
> **ratcheer said:**
> I managed Oracle database servers on systems comprising hundreds  of disk drives over a period of about 10 years. I only recall a handful of actual drive failures, probably less than five. Most data recovery was necessitated by controller failures or firmware errors or other system failures. I always ran RAID 1+0 (aka RAID 10) and, in the event of an actual disk drive failure the systems continued to run while the failed drive was replaced and the mirror was reestablished.

The only time RAID 1+0 requires an actual data recovery would be if two drives of the same mirror pair failed, simultaneously. That said, data backups are still an absolute necessity.

Tim
Thanks. What sort of disks were you using...did they have higher reliability specs than the sort of desktop disks us amateurs would buy?

---

### Post by YesWeCan on 2011-02-08
[QUOTE=rubylaser]An unfortunately, those error rates are averages.  Probably the best advise is to not buy all the disks at the same time from the same vendor (not all from the same batch).  If one fails, it certainly shows that those drives are all potentially vulnerable.[/QUOTE]
Great advice, I would say, to mitigate against a "correlation trap".

---

### Post by ratcheer on 2011-02-08
> **YesWeCan said:**
> Thanks. What sort of disks were you using...did they have higher reliability specs than the sort of desktop disks us amateurs would buy?

Good question. Yes, the disks were bought from Sun as part of their disk arrays with service contracts and, as such, they were very expensive. However, I never could see any difference between them and a regular consumer disk drive. Bottom line - I don't know.

Tim

---

### Post by YesWeCan on 2011-02-09
It seems to me that a mathematical analysis is demanded. It is easy to make a judgement based on how many drives an array can lose and still, in theory, rebuild itself. But is this really relevant? 

The question I want answered is: given a disk has failed in my array what are the odds of the array successfully repairing itself? I would instinctively hope its better than 90%.

I have done some maths on this and my conclusion is counter-intuitive. RAID 6 seems to be worthwhile compared to RAID 1 only for arrays where the number of disks worth of data is 4 or less. Above this, RAID 6 deteriorates very rapidly. RAID 6 also rapidly declines in effectiveness as the reliability of disks declines, much faster than RAID 1 (which is not at all what you want).

For want of a better number, I have used 1 in 10^14 (WDs number for Caviar Black) as the disk read fail rate, or 8% of full reads of a 1TB disk.
a) For a 4TB system the odds of recovering the RAID6 (6 disks) is 95% and the RAID1 (8 disks) is 92%.
b) For an 8TB system RAID6 (10 disks) is 84% and RAID1 (16 disks) is 92%.

It gets worse, though. The odds of a drive failure should include system failure rate (drive dead) as well as read errors. Also, by the time the first disk fails the remaining disks will be older and arguably more prone to failure. They will also have had a similar usage history. So a factor ought to be included to account for the reduction in reliability of the remaining array. What should this be? 2x, 3x, 10x?

If I use 2x for case b)
RAID6 is 57% and RAID1 is 84%

If I use 3x for case b)
RAID6 is 33% and RAID1 is 76%

If I use 10x for case b)
RAID6 is <1% and RAID1 is 20%



My paper calculations based on these assumptions suggest that RAID6 is good when you have a small number of drives or when the drives are very reliable. In a way, RAID6 is best when you don't really need it.

As for RAID5...who's idea was this? :p

---

### Post by rubylaser on 2011-02-09
The problem with RAID1 obviously is all of the space lost when using multiple disks (you can only use half your spindles).  Your math seems good to me.  But, I don't think any sane person would throw all of their disks into massive array.  Normally, you'd want to break those arrays into smaller arrays, mirror/stripe from there. Also, the best thing to keep in mind is the RAID is no subsititue for backups.   Although RAID adds redundancy, there is no way to make your data perfectly secure in all situations.

Or, you could choose to go with something like Unraid that does parity, but each individual drive is also readable by itself.  So, even if you lose more drives than you have parity, you'll still be able to recover the data from the remaining drives.

---

### Post by kevinthecomputerguy on 2011-02-09
+1 rubylaser
 
What I have been doing is raid 5 with a 4th disk left out of the array for rsync cron jobs, or raid 6 with a 5th drive left out of the array for rsync cron jobs.
 
This then devolped into moving my hard-core I\O intensive stuff to the non-array disk, then rsync'ing that back to the array as a backup.
 
I usually have to have a few beers before if starts to make sense, but basically there isnt anything that isnt backed up, and there isnt anything super I\O intensive LIVE on the raid, but nothing is left un-raided or scheduled backed up to the raid.
 
No one solution is ever going to be right. And one BIG note about rsync, as much as i love it, it is a mirroring backup, not an incremental backup. If you dive deep enough into it, you will see its not truly incremental, its truly mirrored with the smarts to skip files that exists. So becareful there and make sure you have a mirror backup somewhere, --ignore-existing is a tricky switch, have a seperate cron job with --delete to know you have a mirror of that data.
 
And my above advice is not as good as an offsite backup. Offsite backups... do it !
 
Raid every, Backup everything, Raid your backups, there is no one answer.

---

### Post by doogy2004 on 2011-02-11
> **B34ST1Y said:**
> Wow -- didn't expect such a strong reply, thanks guys and gals.


Let me clarify:

I want to build a NAS that will be used in a very small community (3-4 people in a house) to store private & important data. Ideally, I'd like to use full disk encryption (PGP ?) and most importantly, have the array be able to scale later on if I decide to add more drives (run out of space). Rebuilding the entire array manually wouldn't be fun :( 

My initial budget, not to include hdd's is about 200 dollars -- I have spare PC parts, so I could probably build a basic computer w/Linux to manage it..

Sounds like a problem that can be solved with a ZFS solution... you would be able to run a raidz2 for dual disk failure.  So 10 1TB disk you would have 8TB of encrypted storage with the option to add more disks and have the file system automatically expand.

Encryption - [http://download.oracle.com/docs/cd/E19963-01/821-1448/gkkih/index.html](http://download.oracle.com/docs/cd/E19963-01/821-1448/gkkih/index.html)
Adding disks - [http://download.oracle.com/docs/cd/E19253-01/819-5461/gazgw/index.html](http://download.oracle.com/docs/cd/E19253-01/819-5461/gazgw/index.html)

---

### Post by CharlesA on 2011-02-11
If you are going to run ZFS, use *BSD, not *nix as it has better support.

---

### Post by Plecebo on 2011-02-12
I am in a similar sittuation as the original poster. 

I currently have an 8x1TB Raid6 array that I am seriously considering moving over to a raid10 array. 

The issue that struck me is that there are some serious issues with Raid 5/6 when it comes to items of data integrity, and recovery. 

For more specific information look at this group (BAARF) [http://www.miracleas.com/BAARF/BAARF2.html](http://www.miracleas.com/BAARF/BAARF2.html) which advocates strongly against Raid 6/5/4 in favor of more reliable, data safe raid builds (mostly raid10 as alternatives to the raid6/5/4). 

A lot of this information is a bit dated, but as far as I can tell still applies to modern raid. I especially worry about a drive starting to go bad with no indication to me that it is happening, at which point Raid5 continues to raid all the bad info, thereby corrupting your whole array. 

From my understanding raid10 protects your better from such issues. 

For me that is enough, but I also have a specific issue in my setup that makes raid10 a better option for me. My 8x1TB drives are housed in an external enclosure connected to a e-SATA card to the server that does the raiding. Several times (the joys of having pets) one of the cables was knocked loose effectively dropping 4 of my 8 drives very suddenly which as far as I can tell caused some of the data corruption that the BAARF articles speak of, corrupting my whole array, and destroying years of my collection of Music, and family photos. I had backups, but because I had been backing up corrupted data from the array my backups were marginally useful, and I ended up with a lot of lost music and photos, which really hurt. 

A properly setup raid10 would be able to survive a failure of one drive chain (half of your drives) and retain full operating functionality (though loose the protection of hardware redundancy). That coupled with proper monitoring (mdadm makes it stupid easy to send email alerts on array issues). I could log in to the server remotely and shut it down until a proper solution can be figured out.

For these reasons I am moving away from RAID6 (with 8 drives I wouldn't even touch raid5). For me it means a loss of 2TB of disk space, but I found I over planned significantly for my space requirements and even with 4TB I should be able to rip all my Movies and TV shows as well as store all my music and personal files. 

If I run out of space, or the drives start failing I'll replace them with 2TB (or the current price/performance leader) until I have the capacity to expand the FS. 

Just my 2 cents, but I think the Raid5/6 options are not the ideal solution they may appear to be on the surface. 

Of course I'd be happy for someone to prove me wrong, the idea of keeping the 2TB of space is appealing.

---

### Post by CharlesA on 2011-02-12
That is why you have backups of data. Even RAID10 can get data corruption.

EDIT: There are situations where running a RAID10 is better then a RAID5 or 6, but it all comes down to each situation.

The RAID card I have can do RAID 10, as well as RAID 5, but I've been running RAID5 for a while now (with regular backups) and I haven't run into a problem yet. I suppose I'll only run into a problem when one of the drives goes out on me, but time will tell if that's going to be an issue or not.

---

### Post by YesWeCan on 2011-02-12
> **CharlesA said:**
> That is why you have backups of data. Even RAID10 can get data corruption.
Anything can go wrong, but not everything goes wrong with the same consequences, right?
If you are happy to rely on backups anyhow, then there is limited value in using any RAID.
IMO the trouble with distributed parity RAID is that when it goes wrong it can take out your whole array. And there are lots of subtle ways it can go wrong. With mirror systems like RAID1 you lose a single mirror at most. And even then there are ways to extract the data and be able to use it.

> I suppose I'll only run into a problem when one of the drives goes out on me, but time will tell if that's going to be an issue or not.
Hmm.

---

### Post by YesWeCan on 2011-02-12
[QUOTE=Plecebo]Just my 2 cents, but I think the Raid5/6 options are not the ideal solution they may appear to be on the surface[/QUOTE]
I'm just starting to research this myself. I worry a little bit that novices just latch on to the sexy idea of RAID and focus on how it is meant to work in perfect conditions. For example, considering only how many disk failures RAIDn is able (theoretically) to recover and how capacity efficient it is rather than focussing on the odds of successful recovery in the event of failure mode X. There are quite a few X to think about.

When I Google RAID and mdadm and so on I find plenty of articles on how to set a RAID up. I haven't found any that talk about the odds of recovering and the consequences of failures. I'll take a look at those links you posted. Thanks.

---

### Post by CharlesA on 2011-02-12
> **YesWeCan said:**
> Anything can go wrong, but not everything goes wrong with the same consequences, right?
If you are happy to rely on backups anyhow, then there is limited value in using any RAID.
IMO the trouble with distributed parity RAID is that when it goes wrong it can take out your whole array. And there are lots of subtle ways it can go wrong. With mirror systems like RAID1 you lose a single mirror at most. And even then there are ways to extract the data and be able to use it.

Well I don't really "rely" on backups, I have them in case I need them. The reason my server is running RAID at all is mostly due to the fact that I needed a load of space for media and whatnot and that was the only way to get that much space without splitting my files onto different drives. In hindsight, I could have done that, but it would have been a bit of a pain to manage for me.

> 
Hmm.

What I was getting at is that if for some reason the array fails to rebuild, I've got a backup of the entire array. Better safe then sorry IMO.

---

### Post by YesWeCan on 2011-02-12
By my reckoning, if I had a 10 disk RAID5 array as per the OP, then once the first disk failed I would expect to have a 47% chance of rebuilding the lost disk and a 53% chance of losing everything.

---

