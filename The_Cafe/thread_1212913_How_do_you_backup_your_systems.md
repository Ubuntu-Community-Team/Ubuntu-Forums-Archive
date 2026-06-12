---
title: "How do you backup your systems?"
date: 2009-07-14
forum: The Cafe
---

### Post by Dragonbite on 2009-07-14
The usual thought is that everybody should back up their data, and not enough people do.

If you back up your systems, how do you do it?  What applications do you use?  If you use rsync, what does your script look like?

How do you backup (and recover) your system files, or do you just reinstall in case that happens?

How do you backup (and recover) your system files; DVD-R, external usb drive, in the cloud, USB stick, how?

I'm trying to figure out a good scheme for backing up my laptop, desktop and server and preferably in a format for being able to put a copy of the backups in my parents house for cases where the area floods or the house burns down.  This is added insurance in case of more than just a hard drive or operating system crash.

---

### Post by TuckLive on 2009-07-14
I just bought a Western Digital My Passport 400Gb drive just for backup purposes.  I'm using rsync to backup my home directory for my desktop.

```
sudo rsync --delete -azvv /home/tucklive/ /media/disk/Adam/Bigbox/
```

For my servers I use Webmin.

---

### Post by Chilli Bob on 2009-07-14
I'm lazy.  Every couple of months I just copy my /home partition to a 300GB external drive and leave it at a friend's house.  I know I should do my system partition too, but, as I said, I'm lazy.

---

### Post by Dragonbite on 2009-07-14
> **Chilli Bob said:**
> I'm lazy.  Every couple of months I just copy my /home partition to a 300GB external drive and leave it at a friend's house.  I know I should do my system partition too, but, as I said, I'm lazy.

Would just mean you'd have to reinstall the OS and applications. I think there's a place in Symaptic  which allows you to backup the list of applications you have installed so you could run a massive "sudo apt-get install applicationX applicationY applicationZ ..." command to get all your applications (from the repositories) installed in one shot.

At least don't have to worry about having to Activate the OS! :)

---

### Post by Skripka on 2009-07-14
I keep...let me see here...

1
.
.
.
2
.
.
.
3  backups on different drives of my /home directory...as well as a backup of my installed packages.

---

### Post by jromer on 2009-07-14
I have a dualboot system with XP and Ubuntu. (5 total partitions)

I use Acronis to backup the entire disk image to an external drive. I've sucessfully restored the disk (or any partion I choose) many times. So I feel very confident in experimenting with re-partitioning or anything else that has inherent risks. 

I've also used clonzilla for the same purpose and successfully restored a number or times.

So I trust both approaches, it's just that Arconis has a nicer interphase to me.

---

### Post by tjoff on 2009-07-14
I use rsync to do incremental backup of home /home to a remote computer.
I use a script something like [http://www.samba.org/rsync/examples.html](http://www.samba.org/rsync/examples.html)
to make incremental backup.
Crontab is used to do this automatically every day.

For my parents Desktop computer I consider doing the same thing, but as they do not have access to a backup server, I would use a usb stick, permanently connected on the dusty backside of their computer (Possible since they have <4 GB of data to backup).

Every time I install an application, I add the install command to a script.
This script, I will run whenever i should decide to reinstall Ubuntu.
This was something I started doing, before i found out that it can be done automatically. My method works for manually installed stuff too, though.

---

### Post by Chilli Bob on 2009-07-14
> **Dragonbite said:**
> Would just mean you'd have to reinstall the OS and applications. I think there's a place in Symaptic  which allows you to backup the list of applications you have installed so you could run a massive "sudo apt-get install applicationX applicationY applicationZ ..." command to get all your applications (from the repositories) installed in one shot.

At least don't have to worry about having to Activate the OS! :)

Yeah, there is a way of doing that, but I'm too lazy to look it up.  Anyway, if I trash my system partition, it's just an excuse to install the latest Ubuntu release, or maybe try a different distro while waiting for the next Ubuntu.

---

### Post by Anzan on 2009-07-14
rdiff cron job nightly to an external USB drive.

---

### Post by CharmyBee on 2009-07-14
I painstakingly sort files into categories, put them in 4.3gb sized 'burn' directories, and make redundant copies. For complete hard-drives, I just image it all, then 7z them into small parts for more reliable copy (and recovery if one part is bad). DVD-Rs rock.

---

### Post by doas777 on 2009-07-14
I'm still trying to figure out how to back up 6TB of data without spending another 600$

---

### Post by juancarlospaco on 2009-07-14
[B]-BackInTime backup
-Clonezilla image
-UbuntuOne backup docs[/B]

docs signed and encrypted on UbuntuOne.

---

### Post by earthpigg on 2009-07-14
> **Dragonbite said:**
> I think there's a place in Symaptic  which allows you to backup the list of applications you have installed so you could run a massive "sudo apt-get install applicationX applicationY applicationZ ..." command to get all your applications (from the repositories) installed in one shot.

where? 

file -> generate package download script generates an empty script with just #!/bin/sh on line 1, and no more lines...

edit: for anyone looking to generate/restore a giant list of apps from the repos in one command: [http://ubuntuforums.org/showthread.php?t=1210796&page=2](http://ubuntuforums.org/showthread.php?t=1210796&page=2) <--- method i currently use, in conjunction with backing up /home.

---

### Post by jskandhari on 2009-07-14
I don't Backup the System.. Just use norton Ghost i you want...

All i do is copy 4 folder to my external
Pictures
Videos
Documents
Downloads

i.e. in Vista My documents.. Rest all my OS reffer to the same location for the respective items inturn concentrating my data to these 4 folders

---

### Post by blur xc on 2009-07-14
Backing up is for pansies!  Anyone who like living on the edge doesn't waste their time w/ that crap!


> **doas777 said:**
> I'm still trying to figure out how to back up 6TB of data without spending another 600$

Well, you've got me beat.  I've only got around 300gigs on a 1tb drive, that not at all backed up.  Still working on that though, I just don't know the best way to go about it.  Mind if I ask what takes up 6 gigs?  Do you do a lot of video work?

I would love to have a system to do automatic daily backups...

There are too many options, and I don't know what the best route.  The disk image setup sounds nice, but complicated.  Where I used to work, they did nightly tape backups.  They'd do 7 days worth of backups, and after the 7th day, that tape was cycled to the front of the line.

BM

---

### Post by MasterNetra on 2009-07-14
> **Barna Madau said:**
> Backing up is for pansies!  Anyone who like living on the edge doesn't waste their time w/ that crap!




Well, you've got me beat.  I've only got around 300gigs on a 1tb drive, that not at all backed up.  Still working on that though, I just don't know the best way to go about it.  Mind if I ask what takes up 6 gigs?  Do you do a lot of video work?

I would love to have a system to do automatic daily backups...

There are too many options, and I don't know what the best route.  The disk image setup sounds nice, but complicated.  Where I used to work, they did nightly tape backups.  They'd do 7 days worth of backups, and after the 7th day, that tape was cycled to the front of the line.

BM

He said 6TB not 6GB, ^.^
@doas777 But yea...what the heck do you have that takes up 6 Terabytes?

---

### Post by Ozor Mox on 2009-07-14
I have a personal folder on my desktop which I rsync -av to a 250 GB external hard drive. I then rsync the external drive to our family computer so I always have 3 copies. Occasionally I run the --del option with the rsync to clean up the extra stuff on the backup that I've since deleted from the live copy.

I'm still trying to decide if keeping one of the copies away from my house is being sensible, or just plain paranoia... Any thoughts?! ;)

---

### Post by JohnFH on 2009-07-14
> **Ozor Mox said:**
> 
I'm still trying to decide if keeping one of the copies away from my house is being sensible, or just plain paranoia... Any thoughts?! ;)

How precious is your data to you?  For example if it's a backup of your OS, application settings, etc. then I would suggest that it's not worth it (to me anyway), but if the data consists of personal photos then I would want to make sure I don't lose them no matter what happened.  I can recreate application settings, re-install my OS, etc, but I can't retake photos.  It's all very subjective though.

---

### Post by blur xc on 2009-07-14
> **MasterNetra said:**
> He said 6TB not 6GB, ^.^
@doas777 But yea...what the heck do you have that takes up 6 Terabytes?

my bad- I meant 6tb...  

BM

---

### Post by FuturePilot on 2009-07-14
Weekly backups with Sbackup and every month or so I image my systems with Partimage

---

### Post by Dragonbite on 2009-07-14
What I would love to do is set up a server at my parent's house and run a job that will [LIST=1]
[*]Each system backs up onto a centralized server periodically (sync changes only on every shutdown?)
[*]Open a VPN tunnel to the server at my parents house
[*]Upload the backups (incremental or complete)
[*]disconnect
[*]wait until another day...
[/LIST]

Then, could also set up one in reverse (backing up their files onto a server in my house).  That one would HAVE to be automated, as they will not run it on their own.

---

### Post by BrokenKingpin on 2009-07-14
I store anything of any importance on my file server. My file server has two 500 gig drives. Every night I have an rsync script run to sync the second drive to the first drive. And then once a week I sync the second drive to an external drive.

---

### Post by doas777 on 2009-07-14
> **MasterNetra said:**
> He said 6TB not 6GB, ^.^
@doas777 But yea...what the heck do you have that takes up 6 Terabytes?

yup video. lots and lots of video. unfortunately most video streams don't compress all that much, seeing as they have already been compressed. Most of it was on disk, but they are starting to go bad (darn 5 year lifespan on most optical media) so I'm laboriously copying it up to the server. 

I guess I'll just have to increase my capacity a few months at a time, until i can back it up fully.

thank goodness storaged has finally fallen below 100$/TB.

---

### Post by blackxored on 2009-07-14
I use Bacula for backing up everything. But since I'm in an enterprise environment, might not suite to you. Only notice it.

---

### Post by Ratscallion on 2009-07-14
I just want that script that auto updates with all packages you download/install so I just run that and boom! it's all back.

---

### Post by doas777 on 2009-07-14
> **blackxored said:**
> I use Bacula for backing up everything. But since I'm in an enterprise environment, might not suite to you. Only notice it.
I thought he was only good for turning star trek into dogma for the supposed war on terror.

---

### Post by mamamia88 on 2009-07-14
i really don't backup i have everything important on external media for better portability to other computers anyway

---

### Post by beercz on 2009-07-14
[rsnapshot.org]("http://rsnapshot.org")

Executed via cron to back up to a linux file server.

Automated - simple, reliable, brilliant.

Been using it for years without problem,

---

### Post by Ozor Mox on 2009-07-14
> **JohnFH said:**
> How precious is your data to you?  For example if it's a backup of your OS, application settings, etc. then I would suggest that it's not worth it (to me anyway), but if the data consists of personal photos then I would want to make sure I don't lose them no matter what happened.  I can recreate application settings, re-install my OS, etc, but I can't retake photos.  It's all very subjective though.

It is 37 GB of largely irreplaceable stuff such as university work, photos, music, compositions etc. I don't backup my operating system or programs since I don't care if they get lost, I can just reinstall them.

When put like that, I suppose a backup offsite isn't a bad idea.

---

### Post by twright on 2009-07-14
I usually keep key files in my dropbox and then back up my entire home directory to a 1TB external harddrive periodically. I do not bother to back up the whole system as I would not really care if I had to reinstall as long as my data was safe - I test and distro hop a lot so I am used to reinstalling by now.

---

### Post by juancarlospaco on 2009-07-14
*iSCI Tape drive its kinda cheaper, or wait the BlueRay.*

---

### Post by richg on 2009-07-15
I cut and paste all my personal files to a external drive. Every few months I burn the files to a DVD and destroy the old DVD. The DVD is not kept on site.

I have a second drive configured exactly like the primary drive. If the primary drive fails. I can change drives in about 60 sec and be back online. No problem.

I use web based email so no issues there.

Some years ago a drive failed on me. I am ready this time.

Rich

---

