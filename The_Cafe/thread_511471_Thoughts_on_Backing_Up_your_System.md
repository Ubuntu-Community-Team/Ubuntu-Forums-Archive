---
title: "Thoughts on Backing Up your System"
date: 2007-07-27
forum: The Cafe
---

### Post by nickburns on 2007-07-27
I tried to start a thread on backing-up, but it fell into the tread graveyard.  

I want to know what everyone does to backup their system.  What they backup and why.  The biggest piece I would like to know is what system do you use and why.  (Like rsync or some program, etc....)

Thanks for all your input.

---

### Post by aysiu on 2007-07-27
I use ```
rsync -av /source /destination
``` It's simple, and it doesn't take up a lot of time, since it will copy only new or modified files.

---

### Post by bread eyes on 2007-07-27
I use the identity function to backup my data.

---

### Post by smoker on 2007-07-27
i tend to just connect up an external drive and drag over the main stuff in my home partition, not very elegant, but with my way of working, incremental backups aren't really possible, besides, it doesn't take that long.

i don't bother backing up the os, ubuntu is that quick to install now, and i'm forever changing the look, so a reinstall would give me an excuse to try new things, rather than be an inconvenience to me that a backup image would allay!

---

### Post by rfruth on 2007-07-27
Mine is pretty simple so I use   TAR:)

---

### Post by starcraft.man on 2007-07-27
Drive imaging for the majority. I back up the images to an external usb. For data, I make redundant copies of important files across my 2 HDs and USB drive. I'm a simple backup person.

---

### Post by init1 on 2007-07-27
I don't backup at all. I should, especially since one of my partitions is dieing.

---

### Post by SunnyRabbiera on 2007-07-27
I use a seagate external HD, seagate externals are ultra awesome with linux

---

### Post by jdong on 2007-07-27
I use an external hard drive, usually cheaply bought via an enclosure and a great HDD online deal. I choose almost exclusively Seagate media -- I will refuse to use any other hard drive brands unless they are SCSI or rated for server use.

As far as backup tools it depends on the job. My home directory is backed up with rdiff-backup, which is essentially a nonfancy version of Apple's Time Machine.

My root filesystems that are XFS are backed up with xfsdump, while non-XFS ones I will usually tarball up every time I make a very significant change.


Every month or so when I get bored, I'll test my backup regime with a test restore onto a spare hard drive and a bootup. I've caught on two occasions backup script/methodology errors that left me with an incomplete restore -- it is **really really important** to test backups.

---

### Post by strabes on 2007-07-28
I manually copy entire contents of /home to the backup folder on my external hard drive before I go to bed every couple of days. On my dell laptop everything works out of the box (except fglrx) so I have minimal work to do after a fresh install + copying back home dir.

---

### Post by herbster on 2007-07-28
Simple Backup does a full backup every Sunday, which I burn to DVD-RW, and have a cronjob that rsyncs it to my webspace, as well as a cronjob rsync'ing my /home to my webspace nightly. It's bootyful!

---

### Post by beercz on 2007-07-28
Every day I backup to a another machine (a linux box running debian).

For this I use [rsnapshot]("http://rsnapshot.org"), and it is done automatically via cron.  I write the results to a log file for examination.

It's fast, it works very well, it's easy (once set up) as it is automated and reliable.

Been using it for years.

And I sleep very well at night thank you very much,

Backup is something I don't worry about.

---

### Post by Ozor Mox on 2007-07-28
About once a week, I plug my external hard drive in and do

```
sudo rsync -avn --del /home/me/Desktop/MyBigFolderFullOfEverything /media/disk
```

to show me what has changed on my computer since the last backup, then

```
sudo rsync -av --del /home/me/Desktop/MyBigFolderFullOfEverything /media/disk
```

to actually copy the changes to my external drive.

I then occasionally use the same commands to rsync my external drive with my other computer, so that I have three copies of all my files in case of extreme catastrophes involving my computer and my backup drive at the same time.

---

### Post by DugieHowsa on 2007-07-28
I use S3 Backup and utilize Amazon's Simple Storage Service (S3).  I backup all my pictures, home movies and documents to it.  All of this is stored on a SimpleTech NAS, but since the device does not have RAID, I feel better that its backed up somewhere else.  And at 10 cents a GB, I hardly even notice the cost on my monthly billing statement.

---

### Post by NiklasV on 2007-07-28
I unfortunately don't do much backup on any of my computers, but on the rare occasions I do, I usually just email some files I'm working on to myself with gmail.

On my parent's computer, I've set up an init script to use rdiff to backup the home directory to a second internal drive automatically when the computer shuts down.

---

