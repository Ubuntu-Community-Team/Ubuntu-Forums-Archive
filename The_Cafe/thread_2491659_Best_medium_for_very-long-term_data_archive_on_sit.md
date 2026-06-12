---
title: "Best medium for very-long-term data archive on site?"
date: 2023-10-16
forum: The Cafe
---

### Post by klundermann on 2023-10-16
What's the best way to keep on-site electronic copies of important documents for the rest of my life?  This would be for things I need not access often but want to be confident will be readable decades from now.

(I'm considering off-site storage with e.g., DropBox, too, but I would like to have my own medium, since a 3rd-party could suddenly go out of business, be subject to some kind of legal injunction or just plain fail to perform as promised.)

For example, one approach that gets a few mentions is to use high-quality BluRay disks.  Obviously I would need to get a BluRay drive and take good care of it.

Or would it be just as good to use, e.g., a USB sticks or an  external HDD, provided that I read and rewrite the data once in a while (like annually)?

---

### Post by SeijiSensei on 2023-10-16
Multiple copies on different physical devices is a easy solution. I back everything up to an external drive nightly and make a copy of the most recent backup on a separate drive. I've used a 2 TB Seagate external like [this one](https://www.newegg.com/seagate-model-stkm2000400-2tb/p/N82E16822184950) as the primary device for few years now, and it has worked flawlessly. (I've since bought a 14 TB Seagate external that will probably take the place of the 2 TB device.)

---

### Post by klundermann on 2023-10-19
Thanks much, SeijiSensei.

But what about files that you seldom, if ever, access? I have important documents on my internal SDD that I want to keep but will most likely never open. I do daily Deja Dup backups to an external HDD. Deja Dup seems only to write files that have changed, so if I don't touch my important documents for years, is there a danger that the associated backup files on the external HDD will suffer bit rot and will become unreadable if, heaven forbid, I should need them 10 years from now?

Second question, if I may. To free up space, I would actually prefer not to keep all of the important documents on my active SDD. So that means writing them to an HDD or other device that is usually off-line. How can I maintain the integrity of the off-line files for years into the future?

---

### Post by klundermann on 2023-10-19
And what are the pros and cons of using a USB stick instead of an external HDD for backup?

---

### Post by #&amp;thj^% on 2023-10-19
USB Sticks Or thumb drives fail faster is one that come to mind quickly.

---

### Post by klundermann on 2023-10-19
Faster meaning in fewer read/write cycles or, if left unused for a long time, in fewer months or years?

---

### Post by #&amp;thj^% on 2023-10-19
All of the above, except if left unused

---

### Post by TheFu on 2023-10-19
m-Disc is designed for 50+ yrs of storage.  [https://en.wikipedia.org/wiki/M-DISC](https://en.wikipedia.org/wiki/M-DISC)

OTOH, having a device like that and ensuring there is access to the hardware for all that time. Drivers change. Hardware support changes.
In a prior job, I was tasked to migrate "national treasures" from old projects to ensure they weren't lost.  At the time, we expected to need to do that at least every 10 yrs, if not more often.  Optical media that consumers can build might make it 10 yrs before bitrot starts corruption of some of the disks, so that really isn't an option.  I pulled everything off the older media and placed it onto 4mm tapes. This was much higher density and at the time 4mm was the "new hotness" approved for long term storage.  I suppose all that data has been migrated off those tapes (I hope so). It was 20+ yrs ago.  All media becomes obsolete.

In the consumer world, we've seen tape use effectively gone now that 10TB HDDs are relatively cheap.  Most critical files for a family will easily fit into 50GB, so really the best answer is probably to have two cheap spinning 3.5in HDDs.  Depending on how often you update them, place one in your safety deposit box at the bank and keep another at home. Both should be encrypted if they aren't just family photos, videos, and insurance-like information.

Bitrot happens on all media, so the best plan is to 

a) ensure the files can all be read. Weekly/monthly backups is a good way to test this. Backups are an easy thing to automate, but ensure non-media files are versioned, since bitrot can trash your last "good" copy. Using versioned backups means that any large/unexpected changes are a problem.

b) validate that the files have correct data. **par2** can be used to create parity files that can be used later to validate no corruption has happened.  Set a schedule, like every 6 months, to perform the validation.  I think 1 yr is too long.  I've lost data between my validation attempts.  par2 has saved me from bitrot 50+ times. Don't trust just the built-in hardware CRC to correct issues.  I use 10% par2 files.  For some less important files, 1% would be sufficient to know it the files are good or not.

c) migrate to newer storage media when tiny corruption happens on any of the media from the same age and type. This can be a pain.  For example, I had 500+ optical DVDs and when a few started showing bitrot, as validated by par2 files, I would just move those specific discs to new.  Over time, more and more and more started failing.  Without par2 files, the corruption would have beyond repair and lost.  I migrated from optical discs to 4TB HDDs.  This made automation (I wrote some scripts) to validate the par2 parity across the entire partition.  I've switched to larger HDDs, but retain the 4TB file system size limit so that any of my disks can be swapped with whatever is cheapest.  For the last 3 yrs, I've been buying 8TB disks - WD Blacks - since they have a 5 yr warranty and my experience with them has proven they are more like 10-15 yr disks, unlike drives with lesser warranties.  I've also had luck with WD-Gold data center drives. YMMV.

Holding data is a responsibility. Thinking you have it, when you really don't isn't good.  Always have at least 2 copies, 3 would be better for actively used data.

Flash storage isn't good for long term and they have a terrible limited write cycle limit. I don't know if SSDs have this same issue or not.  I think for shelf-stable storage, spinning SATA HDDs are best for now. The interface isn't going anywhere and drivers aren't being talked about to be removed.  IDE, SCSI, and USB are constantly changing. Many USB controllers have problems with new/other USB controllers, so I can't recommend those for long term storage.  SATA and SAS are stable, for now.

---

### Post by DuckHook on 2023-10-19
As he so often is, TheFu is spot on.

The short answer to your question is: there is no answer.

It's the nature of technology to change. It's the nature of IT, in particular, to change quickly. This means that old tech invariably becomes obsolete. That, in turn, is the nature of change.

I don't believe that there is any single storage medium that will last more than 20 years. We shouldn't expect them to. You'll just have to keep transferring from old medium to newer. Be prepared to stay on that particular hamster wheel forever.

I still have old VHS tapes of the kids from 40 years ago. I have no idea how I'm going to deal with them.

---

### Post by TheFu on 2023-10-19
> **DuckHook said:**
>  I still have old VHS tapes of the kids from 40 years ago. I have no idea how I'm going to deal with them.

You need to convert them to digital formats.  VHS is 240i, so when you do convert, there's little need to go with a higher resolution, unless you want to waste space and get fuzzy output.  Double check the resolution. I could be wrong, but it is well below DVD (480p).

If you have a VHS player still, get almost any ATSC Tuner and it will likely support taking yellow RCA video and S-Video inputs, plus 2 stereo RCA (L/R) audio.  I have a Plextor ConnectX PX-TV402U-NA Divx USB device that will convert to either Divx or MPEG2 files.
Also have a Haupauge 950Q ATSC tuner that will convert the yellow cable, and I think, S-Video. As you can tell by the age of those devices, I converted many years ago. 
There are lots of other options.  VHS tapes degrade over time. Much faster than almost any other type of media. Don't wait.

---

### Post by DuckHook on 2023-10-19
:lolflag:

Oh, I know how to convert them. I just can't muster the energy to actually do so. There are so many. I can always pay an outfit to do it for me I suppose.

The problem is not knowledge or technique but inertia and sloth. Afraid there's not much you can help me with there. :-({|=

---

### Post by TheFu on 2023-10-19
You can do it!  This weekend would be a good time to setup the VHS, recording device, and run a few tests.
Then just do 1-2 tapes each day.  When I was doing my 20 or so VHS tapes, I just set an alarm to remind me to change the recording every 2 hrs (or so) and pressed "play" on the VHS and "record" on the computer.  One in the morning and one when I got home from work.  Consistent progress is all that matters.

Plus the VHS tapes are losing data every day, little by little.  Those little magnetic particles are losing their power just a bit every day. Time is the enemy.

---

### Post by SeijiSensei on 2023-10-23
> **klundermann said:**
> But what about files that you seldom, if ever, access? I have important documents on my internal SDD that I want to keep but will most likely never open.

My main server has a RAID-1 array mounted as /home which is backed up to an external device. I have files on that array that are over a decade old. Still intact.

---

### Post by TheFu on 2023-10-23
> **klundermann said:**
> Thanks much, SeijiSensei.

But what about files that you seldom, if ever, access? I have important documents on my internal SDD that I want to keep but will most likely never open. I do daily Deja Dup backups to an external HDD. Deja Dup seems only to write files that have changed, so if I don't touch my important documents for years, is there a danger that the associated backup files on the external HDD will suffer bit rot and will become unreadable if, heaven forbid, I should need them 10 years from now?

Second question, if I may. To free up space, I would actually prefer not to keep all of the important documents on my active SDD. So that means writing them to an HDD or other device that is usually off-line. How can I maintain the integrity of the off-line files for years into the future?

Multi-staged backups are common in the business world, especially for govt regulated businesses.  Sometimes, records AND ACCESS TO THOSE RECORDS, must be possible forever.  The ultimate backup medium that is proven to work for many hundreds of years is paper.  If probably stored, I'd be surprised if paper in a home environment couldn't be stored for at least 500 yrs.  There's an entire science around using paper to hold binary data that can be scanned and restored later.  [https://ollydbg.de/Paperbak/](https://ollydbg.de/Paperbak/) is an implementation. About 3MB/page.  There are better options.

If you organize your data by the creation year and how long it needs to be retained, then you can figure out your storage needs for each type.

Keeping things on an SSD that isn't actively used is a very expensive option for primary storage.  For about $45, a quality 500GB SSD can be bought, assuming NVMe/SATA connections. No case included.  For $45, a new 2TB HDD or a 4TB used "enterprise" HDD can be bought.  For things that a home would need to keep forever, I don't see much over 500GB necessary.

So we need at least 3 copies of the data and a way to ensure that data isn't corrupted.
[LIST=1]
[*]Primary Storage
[*]Local Backup Storage
[*]Remote Backup Storage
[/LIST]
Making backups from primary storage to the local backup should happen either daily or weekly.  A full understanding of the backup tool being used should ensure that no more than 1 month elapses between proven access from the primary storage to that local backup.  For many backup tools, this is addressed by every backup performing validation that the source and target files match.  This should not just be size + timestamp validation, but block-by-block validation.  

To get the 3rd copy, i.e. the remote copy, there are many ways. Regardless, if the data might have anything sensitive on it, if the storage isn't directly under your full control and locked, then using encryption is required.  For many people, swapping an external USB storage drive every week between their home and office desks meets this "remote" storage need. Having 2 USB HDDs that are are swapped once a week as the "local" backup storage is a good way to avoid having 4 copies, while still having local and remote backups.  It is OK if remote backups are a little older than local backups, provided you actually do swap those disks around every week or so.

For things that will seldom or never be used, but legally you are required to keep .... (or blackmail photos of your kids) ... I'd go with a separate long-term backup method that is basically the same as the 3-disk method, but just has the swapping slowed down to once every 6 months.

In no way would I use SSDs or USB Flash storage (nor SDHC) for backup media. When not powered, those devices seem to have more bitrot over time.

I'd avoid optical storage, unless you specifically get M-Disc and can be assured that the access using the proprietary m-disc hardware will be possible with a future OS version.  I don't know enough to say that drivers work for every OS.  I do know that m-disc optical media holds 50GB and is priced at a premium cost because it is supposed to hold data 50 yrs.  Just throwing out an option.

Deja Dup is an old-school type of backup tool. They recommend taking full backups monthly, then doing differential backups for all the days of the month.  This is different from modern backup tools, which effectively do full backups nightly, but in a highly efficient way so they are extremely fast.  OTOH, DejaDup (duplicati and duplicity) all allow backing up to non-file system places, encrypting the backups and chunk the backups into bite-sized bits to support remote transfers better.  However, I would encourage everyone using any of those 3 tools to search for corruption issues with backups using them.  A corrupted backup is worthless.  Anyway, be 100% certain you don't just leave Deja Dup on autopilot doing incremental backups more than a month between Full backups. Avoid the corruption.  [https://duplicity.us/FAQ.html#long_chains](https://duplicity.us/FAQ.html#long_chains)    
> The bottom line is simple.&#8195;Keep the number of incrementals for a maximum of one month, then do a full backup.
I'm not making this up.

---

### Post by klundermann on 2023-10-25
Thanks very much, TheFu. You've provided so much information in your posts that it's taking me some time just to formulate cogent follow-up questions.

I confess I've been on duplicity autopilot for a long time, doing incremental backups (I presume) daily and full backups only infrequently. Am I correct in understanding that if I stay with duplicity, I should get in the habit of using a tool like par2 (thanks for that - I was not familiar with it) every so often to verify the files created by duplicity?

Could you mention any of the backup tools readily available for Linux that are more modern than duplicity?

Finally, the only way, so far as I know, to connect an external HDD to my laptop is via the USB port, unless I obtain and figure out how to set up NAS. So I'm a little puzzled by your comments about the risks of USB becoming obsolete. How else would I connect my HDD?

---

### Post by klundermann on 2023-10-25
By the way, I happen to have an ancient [Drobo]("https://www.drobo.com/") lying around. It was left behind by the previous owner when I bought an apartment. I've used it for videos and music, so I know it works. It has four 1-TB HDDs and, as I understand it, is designed to be very robust against HDD failure. I was thinking it could be part of my backup solution, but then it occurred to me that, being 15+ years old, its circuitry might not be terribly reliable at this point.

---

### Post by TheFu on 2023-10-25
> **klundermann said:**
> 
I confess I've been on duplicity autopilot for a long time, doing incremental backups (I presume) daily and full backups only infrequently. Am I correct in understanding that if I stay with duplicity, I should get in the habit of using a tool like par2 (thanks for that - I was not familiar with it) every so often to verify the files created by duplicity?

Duplicity, and most backup tools that aren't just copying files, have a built-in validation capability. They do something like par2 already.  I don't recall, and I'm not going to re-read this thread to remember, but I only use par2 for things that I don't backup using a real backup tool.  Basically, just for file-copy methods like rsync.  Then only for the most important files that I want to ensure don't succumb to bitrot.  So, I don't do it for movies that I have on DVDs already, but it to use par2 for family videos which were costly to transfer from 8mm-16mm film.

> **klundermann said:**
> 
Could you mention any of the backup tools readily available for Linux that are more modern than duplicity?
Duplicity follows the same full, increment, increment, increment, increment, increment, increment, full backup method that has been around since the 1960s.  Nothing wrong with it, except that people need to understand when they need to do fulls and when it is ok to use incremental backups.  dump/restore is how this was handled in the first UNIX systems.  'tar' supports this too, but today (and for the last 20+ yrs), nobody should be using tar to backup a system if they don't use tape as their backup media. TAR = Tape ARchive.  Why am I having to explain that in 2023?  Don't use tar if you wouldn't use a ZIP file, so don't use tar for anything over about 50MB.  Tar was designed when 20MB was considered huge.  The world has changed.
Duplicity is fairly modern, except that is requires using periodic full backups.  If you like it and it meets your needs, keep using it, provided you know the caveats.

OTOH, if you don't need more than 1 "full" backup and can do either incremental or diff backups, then there are more efficient tools that maybe don't check all the "feature" boxes that duplicity checks.  I use a tool that does reverse-diff backups.  The latest backup looks like a mirror of the source, but going back in time, there are reverse differential files to track data and metadata changes over time.  For my needs, this is much more efficient. Plus, if I need to restore, I don't need the backup tool to accomplish it.  cp or rsync can be used.

We each have different requirements.  My restore process begins by asking what I need to restore.  1 file ... I'll probably use scp.  1 directory (plus all subdirs), I'll use rsync.  If I need a full system restore, I begin by doing a fresh install of the OS.  I've posted my full restore process in these forums a few times.  It isn't 1 command, but it is extremely flexible.  Takes less than 45 minutes from decision to restore until it is finished.  For some people, they need a 1-command restore.  My method won't work for them.

> **klundermann said:**
> 
Finally, the only way, so far as I know, to connect an external HDD to my laptop is via the USB port, unless I obtain and figure out how to set up NAS. So I'm a little puzzled by your comments about the risks of USB becoming obsolete. How else would I connect my HDD?

How many floppy drives do you have today? Are they still used?  Medium and connectivity changes all the time.

We don't know.  In 1998, USB didn't exist. We used CDROMs, tape or floppy disks for backups.  The future is unknowable.  We don't know if USB is like a steering wheel in cars or like quadraphonic 8-track tapes at this point.  CDROMs are effectively a dead medium now.  USB might become dead in the next 10 yrs. I don't know, but I can plan for that to happen and be prepared when/if it does.

---

### Post by TheFu on 2023-10-25
> **klundermann said:**
> By the way, I happen to have an ancient [Drobo]("https://www.drobo.com/") lying around. It was left behind by the previous owner when I bought an apartment. I've used it for videos and music, so I know it works. It has four 1-TB HDDs and, as I understand it, is designed to be very robust against HDD failure. I was thinking it could be part of my backup solution, but then it occurred to me that, being 15+ years old, its circuitry might not be terribly reliable at this point.

I had an external disk array (DAS) die in July. It was new in 2007 or so.  I'd swapped the HDDs inside a few times.  All HDDs rail.  I setup the mdadm arrays and the file systems on that DAS device, so I knew how to store it.  Can you do the same with the DROBO?  If not, don't trust it.  I don't use RAID-anything for backup storage.  I use simple, JBOD, 1 disk, 1 partition, methods.  When it is time to restore from backups, I don't want any surprises.

My DAS device was a little circuit board that converted 4-SAS connections to Infiniband. I'd be surprised if I couldn't find one of those boards for $50 today.  The fan and PSU were still working.  I pulled all the HDDs out and moved them into a 4-drive cage that fit inside another computer. No data loss.  Actually, I pulled the RAID over too.  Here's the 2 arrays in the new system:
```
$ more /proc/mdstat 
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [ra
id10] 
md2 : active raid1 sdb2[1] sde2[0]
      1338985536 blocks [2/2] [UU]
      
md1 : active raid1 sdc3[2] sdd2[3]
      1943010816 blocks super 1.2 [2/2] [UU]
$ lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
NAME                             TYPE  FSTYPE              SIZE FSAVAIL FSUSE% LABEL          MOUNTPOINT
sdb                              disk                      1.8T                               
&#9500;&#9472;sdb1                           part                    125.5M                               
&#9500;&#9472;sdb2                           part  linux_raid_member   1.3T                               
&#9474; &#9492;&#9472;md2                          raid1 ext4                1.3T  809.8G    30% R2-Array       /raid2
&#9492;&#9472;sdb3                           part  ext4                586G                Back2          
sdc                              disk                      1.8T                               
&#9500;&#9472;sdc1                           part                      128M                               
&#9500;&#9472;sdc2                           part  ext4                9.8G                               
&#9500;&#9472;sdc3                           part  linux_raid_member   1.8T                lubuntu:1      
&#9474; &#9492;&#9472;md1                          raid1 ext4                1.8T   42.7G    93% RAID1-Array    /raid1
&#9492;&#9472;sdc4                           part  ext2                  1M                               
sdd                              disk                      1.8T                               
&#9500;&#9472;sdd1                           part  ext4                9.9G                               
&#9492;&#9472;sdd2                           part  linux_raid_member   1.8T                lubuntu:1      
  &#9492;&#9472;md1                          raid1 ext4                1.8T   42.7G    93% RAID1-Array    /raid1
sde                              disk                      1.8T                               
&#9500;&#9472;sde1                           part                    125.5M                               
&#9500;&#9472;sde2                           part  linux_raid_member   1.3T                               
&#9474; &#9492;&#9472;md2                          raid1 ext4                1.3T  809.8G    30% R2-Array       /raid2
&#9492;&#9472;sde3                           part  ext4                586G                Back1          


```
All is good. I've moved all the data off those RAID1 drives to other storage and have a few months of backups for the data, so the RAID really isn't needed any longer.  I think the current HDDs are all nearly 10 yrs old in those RAID-sets.

Of course, only you can decide if the risks are worth the reward for your situation. I'd look up where people try to recover data from their drobo devices and check how long they normally last before deciding.  Where the people who try to restore successful or not? Are your skills similar? Greater/less?  I wouldn't have a NAS that I didn't ujnderstand how to restore the data from the storage myself. To me, it isn't worth it.  YMMV.

Always remember, RAID never replaces backups. Never.  Sometimes the only recovery from a failed RAID is to restore from backups to new storage.

---

