---
title: "Do you back up?"
date: 2008-05-05
forum: The Cafe
---

### Post by Irony on 2008-05-05
I'm always stunned at the number of people who will go through the process of installing or upgrading a system with having done a backup of their current system... every time Ubuntu comes out with a new version, angry people will rant and rave that they have lost their data or borked their system!

I do a simple copy [backup]("http://ubuntuforums.org/showthread.php?t=416710") another method is to use [partimage]("http://www.psychocats.net/ubuntu/partimage")... there are many other methods. 

So own up, do you do a backup?

P.S. By back up I mean a full operating system backup.

---

### Post by Ardrias on 2008-05-05
> **Irony said:**
> 
So own up, do you do a backup?

No. I just can't be bothered :D

---

### Post by swoll1980 on 2008-05-05
all my files are backed to dual layer dvds I don't trust hardrives if they break it would cost me a fortune to recover my data

---

### Post by FuturePilot on 2008-05-05
I have Sbackup scheduled for a once a week backup. I set it and forget it. :) Automatically backs up my /home once a week.

---

### Post by Ozor Mox on 2008-05-05
I back up my main folder every so often (depends how many important changes) to an external hard drive using rdiff-backup. I then sync the external drive with my laptop using rsync, so I have two backup copies. Quite paranoid I know, but if I lost the stuff in that folder it would be a nightmare!

---

### Post by _sAm_ on 2008-05-05
I understand what you mean, just read about one guy installing Ubuntu in dualboot with Vista - and he lost 70gig of his data! How can people do so without backup...? 

I have a simple home server(with Ubuntu as OS), and use Unison(via ssh) to do the backup of my important folders on my Ubuntu pc - it works great.

---

### Post by noynac on 2008-05-05
I backup my entire drive every week or so using Acronis True Image Home. This backup includes Hardy, WinXP, swap, and Fat32 partitions. I've restored files, folders, partitions, and the entire drive on a great many occasions, and True Image has never failed me. 

At least once a day I backup the data in my home directory to a flash drive using a simple shell script.

---

### Post by herbster on 2008-05-05
rsync + cron, piece of cake.

---

### Post by illu45 on 2008-05-05
I use MozyHome for backing up Windows machines. I don't generally have anything vital on linux partitions (not quite made that transition yet), but I usually burn important files to a CD or DVD, depending on the size.

---

### Post by billgoldberg on 2008-05-05
> **Irony said:**
> I'm always stunned at the number of people who will go through the process of installing or upgrading a system with having done a backup of their current system... every time Ubuntu comes out with a new version, angry people will rant and rave that they have lost their data or borked their system!

I do a simple copy [backup]("http://ubuntuforums.org/showthread.php?t=416710") another method is to use [partimage]("http://www.psychocats.net/ubuntu/partimage")... there are many other methods. 

So own up, do you do a backup?

P.S. By back up I mean a full operating system backup.

No.

I don't back up the operating system.

I do back up all my videos, music, pictures and documents to an external hard drive, manually.

I can't be bother to ghost the entire drive.

It's not like there is any important data on it anyway.

---

### Post by schauerlich on 2008-05-05
EDIT: Deleted, moved new question to new thread.

---

### Post by hessiess on 2008-05-05
laptop and desktop synced with unison, but i havent worked out how t do it atomaticly yet.

---

### Post by beercz on 2008-05-05
I backup up my /home directory *every day*, automatically to a file server using [rsnapshot]("http://rsnapshot.org")

Easy, automated, incremental backups - probably my most important utility!!

Never lost any data.  (Been in the IT industry for about 17 years).

---

### Post by Darkhack on 2008-05-05
I honestly don't have any data that is "life or death" to me.  I backup stuff onto CDs but I keep them on my desk less than three feet away from the computer, so a fire would ruin all of that.  The computer has always been more of an entertainment device than a work device.  I'm a college student so I don't have anything too critical.

I do have reports that need to be typed but I do them all on Google Docs so that I can access them from any computer.  One downside is if I lost an internet connection, but I can usually go to the library or school computers to get online.  I can't think of a time I'd need to go out Californee-way to find some internets.  There is usually a connection available somewhere.

The other downside is when teachers spy on me and tell me to stop sending emails and get back to work.  They assume everyone is using Microsoft Word to type their documents, so it looks like I'm not working when I'm on Google Docs.  I always get the last laugh though when I hear a fellow classmate cry out in a panic that they overwrote their document, didn't save, or that they need to go back to a previous revision.  Google Docs has revision control built right in and autosaves my work.  Plus I don't need to bother with emailing myself the document back and forth or mess with flash drives.  Most teachers allow me to use it when I explain the benefits, but others can get really anal if they don't see the pretty blue GUI of Office 2003 on every screen.

---

### Post by Tux.Ice on 2008-05-05
no. every six months i "clean" my home folder ;)

---

### Post by SuperSon!c on 2008-05-05
> **Ardrias said:**
> No. I just can't be bothered :D

oh, you will be "bothered" one of these days, just wait.


and to the OP:  yes, religiously.

---

### Post by game_plan on 2008-05-05
As soon as the new system is installed (always do clean install, I've had fewer issues I've found) I make an image of the system, then reconnect to the Samba server, which is where the files are anyways. The server is backed-up using the GFS system.

---

### Post by regomodo on 2008-05-05
all the time. I back up basically everything minus the OS using cron to run a rdiff-backup script once every 2 hours.

```
#! /bin/sh
mount -v /media/sdc1
sleep 3
nice -19 rdiff-backup -v5 --check-destination-dir /media/sdc1/sda1_bkp
nice -19 rdiff-backup -v5 /media/sda1 /media/sdc1/sda1_bkp
nice -19 rdiff-backup -v5 --check-destination-dir /media/sdc1/sdb1_bkp
nice -19 rdiff-backup -v5 /media/sdb1 /media/sdc1/sdb1_bkp
nice -19 rdiff-backup -v5 --check-destination-dir /media/sdc1/home_bkp
nice -19 rdiff-backup -v5 /home/jon /media/sdc1/home_bkp
umount -v /media/sdc1
```
oh and partimage is awesome, except for NTFS partitions

> **SuperSon!c said:**
> oh, you will be "bothered" one of these days, just wait.

too right. I was in the same mindset for a while, then wammo! Loads of work, pictures and music went bye-bye.

---

### Post by PetePete on 2008-05-05
daily rsync /home to external hdd.
daily rsync of 'my documents + photos' folder to remote server incase my house burns down/gets robbed.

all set in cron so 0 effort required. 

also very useful having the remote server backup, means if I ever require a file and Im not by my PC I just need an internet connection and can pull it off my server.

---

### Post by SuperSon!c on 2008-05-05
> **PetePete said:**
> daily rsync /home to external hdd.
daily rsync of 'my documents + photos' folder to remote server incase my house burns down/gets robbed.

all set in cron so 0 effort required. 

also very useful having the remote server backup, means if I ever require a file and Im not by my PC I just need an internet connection and can pull it off my server.

is the server actually yours outside of your home or something you're paying monthly for?

---

### Post by herbster on 2008-05-05
The "can't be bothered" is incredibly strange when it can be automated and as brainless a thing to have as one could, unless the data is unimportant or whatnot of course.

---

### Post by manicman on 2008-05-05
I Backup my /home every few weeks or so but I have over 800GBs of video footage and can't afford another hard drive to back it up. hopefully I will soon though.

---

### Post by spamzilla on 2008-05-05
I backup my data before a reinstall / upgrade, but I don't bother to do a backup of my OS as I don't have any important data I need stored safe somewhere (although I do have a back up of my data, albeit an old / probably out of date backup.)

---

### Post by ugm6hr on 2008-05-05
Only backup personal files.  The OS/apps etc is replaceable from CDs / online. 

Used to do it manually, but finally got around to installing with a separate /home partition.

Now I use Grsync to backup /home.  Easy for those of us happier with a GUI ;)

---

### Post by PetePete on 2008-05-05
> **SuperSon!c said:**
> is the server actually yours outside of your home or something you're paying monthly for?

server is in my mum's house, luckly for me she has broadband and didn't mind me having a server (old laptop, so min power/space usage) at hers in exchange for 24/7 tech support from me!

Don't think I'd trust a 3rd party to host my personal docs, not without the use of encryption anyway.

---

### Post by p_quarles on 2008-05-05
I mirror my /home partition to a backup hdd every day. I occasionally make tarballs of /etc and /var, which I save to /home/me, where they get backed up. 

Basically, I could wipe my main disk and still have everything the way I wanted it within an hour. I've spent a lot of time tweaking things, and I don't like wasting energy.

---

### Post by SuperSon!c on 2008-05-05
> **PetePete said:**
> server is in my mum's house, luckly for me she has broadband and didn't mind me having a server (old laptop, so min power/space usage) at hers in exchange for 24/7 tech support from me!

Don't think I'd trust a 3rd party to host my personal docs, not without the use of encryption anyway.

ah, thanks =)

---

### Post by original_jamingrit on 2008-05-05
I rarely back up.  Any important work tends to exist as several copies on several partitions + my mp3 player.  I guess that kind of counts.  But I don't really consider it backed up untill I have it written to a DVD, and I only do that with finished work or read-only files.

---

### Post by Xerp on 2008-05-05
I tend to only backup important files, music, pictures, documents.. that sort of thing. For the most part everything else is just a reinstall away!

I have actually invested in a USB drive now though, so more frequent backups will be new for 2008...

---

### Post by Superkoop on 2008-05-05
I backup my /home weekly. But don't bother with the OS, since that's recoverable via Internet and CDs.

---

### Post by scragar on 2008-05-05
I always have 2 partitions, so I always upgrade to a new partition, check it all works, then move a copy of my files/settings over, this way I can always check things work well(I actualy start the upgrade around 1 month before the release, for testing, report any problems I find that arn't already reported, then do this again 2 weeks later, before finaly using final version on the day before/after release(never the day of the release, since I always like to check it the day before, then either move my stuff to it ready, or move back to trash my old system in celebration) :P). so it's not so much a backup, as a whole new install :P

Oh, and all my files are backed up to a seperate tar archive (extention is deliberatly .zip to try and deter people looking at my backups, inside the tar is a password protected rar(password always the same, yet always different. I love basing passwords on a formula applied to the date), so access is hard, people really have to consider if it's truely worth the effort :P) file each week on an external HD, with an extra copy of the latest archive made to a 8GB pen drive placed safely out of the way, so there is no chance of a flood etc destroying my only backups.

Personaly I think I'm protected. :P

---

### Post by Depressed Man on 2008-05-05
I backup my media files (music, video, pictures, etc..). But as for actual file systems or operating systems I don't. But that's because if I do a reinstall or a fresh install I want to make it as fresh as possible since I tend to experiment with random programs whether I use them actively or not.

---

### Post by days_of_ruin on 2008-05-05
I just backup my personal data on dvds.:guitar:

---

### Post by PetePete on 2008-05-06
a good tip if you only want to back up /home but still want to be able to quickly 'restore' the state of your system is to get cron to run this command


dpkg --get-selections > /tmp/installed-software

then get it to copy /tmp/installed-software to your external drive with a copy of /etc/sources.list


Then if you do ever have to restore all the apps on your system it can be easily done with:

dpkg --set-selections < installed-software

followed by
apt-get dselect-upgrade

This has saved me hours..

---

### Post by cdtech on 2008-05-06
A good backup technique can mean the difference between a slight computer setback or living through your own electronic apocalypse.

A lot of computer user&#8217;s do backup their important file's, music or photo&#8217;s but the most important thing, some forget about, is the data. The data: the product of your thought and effort, if this gets corrupted or deleted and there&#8217;s no backup, then your forced to start your work from scratch.

It does take time to configure a desktop computer or a server to the way your comfortable with and, as I know, some information takes a long time to look up, understand and configure so that it works the way it is supposed to. I myself have lost valuable data in my timely approach to having my computer running the way I want it and I could only wish I had a recovery method in place for that lost data.

I keep a complete system backup of my server on a USB stick (4GB), which is set to read/only during idled times (for security reasons). I use the "tar" approach along with "do and don't" text files. My backup is automated for weekly, monthly, and incremental along with all of my databases.

I've used my backup more than once to extract certain files that I may have rm'd or mis configured (such as: tar -zxvpf /backup/full-backup.tar.gz /usr/local/bin/mybackup).

Backup's rock!

---

