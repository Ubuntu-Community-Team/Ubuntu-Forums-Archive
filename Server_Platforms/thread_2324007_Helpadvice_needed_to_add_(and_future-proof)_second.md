---
title: "Help/advice needed to add (and future-proof) second HDD to Plex/NAS server setup"
date: 2016-05-10
forum: Server Platforms
---

### Post by pete_hepple2 on 2016-05-10
Hi there,

I recently took the plunge and built my own home server, primarily to make my MacBook portable again (it was running Plex Media Server, and so was chained to the wall/ethernet port), and although it's going reasonably well, I need a bit of help finishing it off properly.

[B]TL;DR first:

[/B]_Current setup_[INDENT]250GB SSD running Ubuntu 16.04 and PMS[/INDENT]
[INDENT]3TB WD MyBook Live attached via router (ethernet) hosting all media files[/INDENT]

_What I'd like to do_[INDENT]250GB SSD running Ubuntu 16.04 and PMS[/INDENT]
[INDENT]4TB WD Red (+ more later on)[/INDENT]


[B]The director's cut:

[/B]For a number of reasons (large file transfers failing regularly, Sonarr issues) I'd like to take the MyBook Live out of the equation and move all storage internally, starting with a 4TB WD Red and slotting in further drives later on as needed, so that all the drives are seen as one large storage area. Through putting this all together I've become fairly competent with the terminology, Terminal commands, etc, but after a bit of research I'm struggling to get the information I need to be confident I'm doing this right. I'd be grateful if anyone could help me by explaining if/how I can:

[INDENT]1. Add a second HDD to my box to store all my media, replacing the external MyBook Live
2. Set it up so I can expand this storage by adding more drives further down the line as my collection grows[/INDENT]

It would be useful (but not essential) to be able to access the storage from other machines on the network too, for general storage/backup purposes.

Thanks :)

---

### Post by Bucky Ball on 2016-05-10
*Thread moved to **Server Platforms**.*

You'll have better luck here. There is a ton of info out there and sure people will have advice and links. Have a dig around for clues. 

Sounds like RAID will cover the 'multiple drives looking like one big storage area' issue. I know nothing about RAID but plenty do and again, tons of info about RAID setup out there. 

As for installing a new drive, you simply put it in the box, plug it in, format it how you want it (I no longer use more than one partition a drive for storage drives) then transfer the files from the old drive to the new. Done, if I'm understanding you correctly. Ditto for any further drives. 

As I say, not au fait with RAID, but think you'd set up the RAID array once the drive is installed and formatted, prior to transferring data. Don't quote me! Unsure how easy/hard it is to set up later when data is already present on the RAID setup. :-k

Hope that's of some help.

---

### Post by pete_hepple2 on 2016-05-10
Thanks Bucky, that's really helpful :)

I realise I should have done a lot more reading before asking for help - what's apparent now is that I'm not going to be able to run a RAID array or even set myself up for future use with just one HDD, so I'm changing my approach. I hadn't considered the fact that Plex allows me to nominate multiple folders for media, which will effectively combine the contents of separate discs into one collection anyway, so it's not vital for me to have them seen as one large drive at all. I'll just add another drive when needed and tell Plex to also look there for media - problem solved way more simply than I was originally planning!

Thanks again :)

---

### Post by Bucky Ball on 2016-05-10
All good and thanks for marking as solved. ;)

Don't hesitate to post a new thread for any new issues. Good luck with it.

(PS: I generally just plop the drive in, connect it up, launch Gparted and partition. I think you can format with 'Disks' also, which I believe is a default app in Ubuntu.)

---

### Post by bab1 on 2016-05-10
> **pete_hepple2 said:**
> Thanks Bucky, that's really helpful :)

I realise I should have done a lot more reading before asking for help - what's apparent now is that I'm not going to be able to run a RAID array or even set myself up for future use with just one HDD, so I'm changing my approach. I hadn't considered the fact that Plex allows me to nominate multiple folders for media, which will effectively combine the contents of separate discs into one collection anyway, so it's not vital for me to have them seen as one large drive at all. I'll just add another drive when needed and tell Plex to also look there for media - problem solved way more simply than I was originally planning!

Thanks again :)
I feel I should add my 2 cents worth here.  Finding you can't use a RAID array is actually a very good thing.  RAID arrays will ultimately fail with catastrophic consequences (lost data) for all disks when you use large drives (> 1TB).  The error checking on rebuild is guaranteed to fail before it finishes.  

As you have seen there is more than one way to skin a cat.  Most media players will aggregate the data in to human understood categories.  Individual disks at this point are safer for "all the data" than combined arrays.  The mount points for the disks can be a simple as /mnt/disk1 and /mnt/disk2 and /mnt/disk3 or... /mnt/music and /mnt/movies and /mnt/pictures.

One thing you need is reliable backup of the data you consider important.  Backup on a regular basis.  Make that incremental backups so you can go back further than your latest backup if you need to.  No data is safe on any spinning disk for mechanical and digital reasons.  SSD storage is long term untested.  Backup, backup, backup.

---

### Post by Bucky Ball on 2016-05-10
> **bab1 said:**
> Backup, backup, backup.

Literally! The old rule-of-thumb, for old-timers, was grandfather> father> son. In other words, you keep the original on the machine, a copy to an external drive stored in another room when not in use, and a third copy stored in another location altogether. 

Naturally, regular domestic consumers don't generally go this far, but that's my backup routine for valuable stuff where losing it can't be an option (because my life depends on it!), although I've been a bit slack on the off-site version lately. :|  ;)

---

### Post by bab1 on 2016-05-10
> **Bucky Ball said:**
> Literally! The old rule-of-thumb, for old-timers, was grandfather> father> son. In other words, you keep the original on the machine, a copy to an external drive stored in another room when not in use, and a third copy stored in another location altogether. 

Naturally, regular domestic consumers don't generally go this far, but that's my backup routine for valuable stuff where losing it can't be an option (because my life depends on it!), although I've been a bit slack on the off-site version lately. :|  ;)
Also incremental (inc1, inc2, inc3).  Just in case that info you had last Tuesday is corrupted on Thursday.  I'm not a diligent as I used to be.  I backup weekly, monthly and yearly now.  I have 5 years of data tucked away.  ;-)

---

### Post by darkod on 2016-05-10
Plex will work with separate disks, but if you still want to future-proof the setup (imagine you ditch Plex next year) you can take a look at LVM. Creating one large storage area, easily expandable in the future, is not RAID, it is LVM.

You add your first disk as physical device for the LVM, and the corresponding device is called like /dev/VolumeGroupName/LogicalVolumeName. Next year you add one more disk as physical device, and the /dev/VolumeGroupName/LogicalVolumeName stays the same. You simply extend it to use up the newly added space...

Just FYI...

---

### Post by pete_hepple2 on 2016-05-18
Just wanted to pop in again to thank you all for your help and advice - I've just finished configuring an LVM using the new 4TB drive and it looks like it's all working perfectly. I've learned that there's no such thing as a "perfect tutorial" with the endless variations of hardware and software setups so I had to use bits and pieces of around 5 or 6 different ones, but I got there.

Thanks again for steering me in the right direction, I'm a very happy geek right now :)

---

### Post by Bucky Ball on 2016-05-18
> **pete_hepple2 said:**
> I've learned that there's no such thing as a "perfect tutorial" with the endless variations of hardware and software setups ...

Ain't that the truth! And no perfect setup, only what works perfectly for you. :)

Thanks for letting us know, marking as solved and have fun.

---

