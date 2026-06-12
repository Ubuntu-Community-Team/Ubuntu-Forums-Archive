---
title: "Simple data transfer from Ubuntu Server 12.04 to NAS"
date: 2013-07-17
forum: Server Platforms
---

### Post by ulyssesAU on 2013-07-17
My skill level is definitely newbie, but I am learning fast! I am trying to understand the best method for large data transfers over a network.

I am about to embark on an upgrade of my server from its current setup (4 x Hard Drive RAID + 1 x Hard Drive for OS) to something larger (8 x Hard Drive RAID w/ RAID Card + 2 x Mirrored RAID Hard Drives for OS). Basically I plan to start from the beginning and build a new server.

**Equipment relative to this post:**
Standalone server running Ubuntu Server 12.04
3TB WD MyBookLive NAS
Macbook Pro
HP 1810-8G Gigabit Managed Switch (of which all the above is hard wired too)

**Question:**
I have 1.7TB of data on my existing server RAID setup that I would like to backup to my 3TB WD MyBookLive NAS. I then need to do the same in reverse once I re-build my server. I would like to know what is the best way to accomplish this?

**My initial thoughts are:**
1) Using my Macbook, simply copy from RAID array (which is accessible via SAMBA on Macbook) and paste into NAS (again accessible via Macbook interface)
[LIST]
[*]Will this work effciently with this data size and are their any drawbacks?
[*]Is my switch intelligent enough to effect the transfer without routing through my Mac by knowing the data origin and destination?
[*]If not and the data must pass through my Mac, will this even matter that much?
[/LIST]
 2) Using command line interface on the Server to simply copy entire RAID directory structure to NAS (which I will mount as an accessible drive).
[LIST]
[*]Will this work effciently with this data size and are their any drawbacks?
[*]What is the best command to execute this?
[/LIST]
3)Using Rsync to sync the RAID to the NAS
[LIST]
[*]I have only briefly read up on this and so would be the harder (and likely more troublesome) option.
[*]I have read this can be slow to complete the initial data transfer?
[*]I do not require continual backups (for now), and only need to copy the data once each way.
[/LIST]

I am sorry for all the questions! But knowing the answers would be great to help with my general understanding.

Of course I may not have suggested the best option, so all opinions are appreciated!

Thanks for your time!

---

### Post by SeijiSensei on 2013-07-17
Mount the drive someplace (I'll use /media/NAS), then run this rsync command:

```
cd /path/to/source/parent; sudo rsync -av directory /media/NAS
```

For instance, if you wanted to transfer /home to /media/NAS, you would run:

```
cd /; sudo rsync -av home /media/NAS
```

The "-v" ("verbose") switch prints out a list of the files being transferred.  The copied directories and files will be placed in /media/NAS/home.

---

### Post by ulyssesAU on 2013-07-18
Perfect! Easy enough and does exactly what I need. Thanks for your reply!

---

