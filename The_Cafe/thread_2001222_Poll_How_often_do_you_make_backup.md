---
title: "Poll: How often do you make backup?"
date: 2012-06-10
forum: The Cafe
---

### Post by David Andersson on 2012-06-10
If you want to, post a comment why you do not make backups, or tell us about your backup solution. Manual or automatic? All files or a selection? Type of media? Stored off site? What program?

Have you verified that you can restore files from the backup medium?

If you have more than one computer, vote about the most interesting or most important one.

(With this poll I hope to remind people of the importance of backing up their data.)

---

### Post by David Andersson on 2012-06-10
I have a home brewed script using rsync copying /home to a secondary hard drive. I start it manually once in a while. I have verified that I can copy back individual files from the backup.

It is an incremental/snapshot backup scheme. The backup disk currently contain snapshots from these dates:

2008-04-21
2008-11-14
2009-07-30
2009-09-19
2009-11-18
2010-05-22
2010-11-15
2011-05-12
2011-11-18
2012-01-14
2012-02-15
2012-03-14
2012-04-16
2012-05-14
2012-05-24
2012-05-31
2012-06-07
2012-06-10

I also have a couple of USB-thumbs with backups of a small selection of important files, copied these dates:

2009-10-03
2011-09-12

---

### Post by MG&amp;TL on 2012-06-10
I never backup. (Or very rarely). 

I don't have any precious pictures or documents or anything, and the code I do want is "up there" in code repositories of some variety.

---

### Post by KiwiNZ on 2012-06-10
I back up on the Fly, in other words constantly.

---

### Post by Tombradyhasamachinehead on 2012-06-10
I used to use time machine but that was when i had my mac. I now just backup my very personal files on my 64GB flash drive and since i use linux exclusivly i have that flash drive formatted ext4 with journalling off

---

### Post by forrestcupp on 2012-06-10
How often do we back up, or how often do we *intend* to back up? :)

> **KiwiNZ said:**
> I back up on the Fly, in other words constantly.Cloud syncing?

---

### Post by Old_Grey_Wolf on 2012-06-10
It depends on what the computer is used for and how important the data is. 

Anywhere form every day to once a month, or constantly by mirroring disk drives in a RAID.

---

### Post by KiwiNZ on 2012-06-10
> **forrestcupp said:**
> How often do we back up, or how often do we *intend* to back up? :)

Cloud syncing?

Local and Cloud

---

### Post by wilee-nilee on 2012-06-10
I use grsync fairly often for home, and clonezilla for images.

I also keep a installed list when ever I get a update in home run with this command, and a reload using dselect, if needed on a install etc.

dpkg --get-selections > installed-software

And if you wanted to use the list to reinstall this software on a fresh ubuntu setup,

Code:
dpkg --set-selections < installed-software

followed by
Code:
dselect

---

### Post by PaulW2U on 2012-06-10
I don't have a very good system as the list below shows but depending on which PC I'm using I copy important files to the following destinations every day. 

[LIST]
[*]Another drive on the same PC
[*]One of two external USB hard drives
[*]A networked hard drive
[*]Upload by FTP to a file storage site
[*]I even copy certain text files to my mobile phone!
[/LIST]
Then about once a year I burn a DVD with as much as I can fit onto it.
As I said, not a very good system. :lolflag:

---

### Post by ratcheer on 2012-06-10
Thank you for reminding me. I just started a backup and my last one was 43 days ago. ;)

I use **Deja Dup**, which is a front-end to Duplicity, which is a front-end to rsync and other standard Linux utilities. I exclude Trash and Downloads and, before I run it, I empty the web browser's cache.

Tim

---

### Post by SeijiSensei on 2012-06-10
I run a scheduled rsync backup from cron onto an external drive each night.  I back up the usual suspects -- /home, /etc, /var/spool, /var/log.  I also make nightly text-based database snapshots with pg_dump and back those up as well.  

On my virtual machine at Linode I pay the extra few bucks for a nightly snapshot backup.  So far I've never needed to use it.

---

### Post by Irihapeti on 2012-06-10
Not as often as I should!

I have a home-made bash script that archives my home directory files (plus a few others) and burns them to DVD. That should happen daily or at least every few days, but often I'll go a fortnight or more without doing it.

On the other hand, if I'm doing a major editing job, I'll back up the file(s) to USB or another drive several times a day - or even hourly or less if I'm making major changes.

Every so often, I'll make an archive of my system minus home directory. It's got me out of a number of awkward situations, so, yes, I know that it works.

---

### Post by markp1989 on 2012-06-10
all my important files are in my Dropbox, so they end up on every machine I own.

on my file server I copy the Dropbox folder using rsync (without the delete flag) to a different hard drive every hour, just encase my Dropbox account ever gets erased for any reason. 

The folder that Dropbox is copied to gets rsynced every night to a VPS I rent, this shouldnt be needed, as the only way I would need this would be if my dropbox account got deleted from all my machines and the extra disk on my file serve fails. But I can be a bit paranoid. 

All my home folders are copied to my file server using Deja-Dup daily

I have been burned before

---

### Post by Roasted on 2012-06-10
Due to certain drive size limitations, I have a pretty selective setup, but it works well for me.

Server - 160GB OS Drive, 2x500GB RAID 1 mirror

Desktop - 60GB OS SSD, 2x1TB RAID 1 mirror

I have a custom startup application which rsyncs my Pictures and Documents to my server. Essentially, each time I log in, those two folders synchronize. I didn't bother doing the rest since my desktop has 1TB drives and my server 500GB drives. I figured since the rest of the data isn't as important as my Docs or Pics, it's at LEAST on an array, even though an array isn't a "real" backup... it's at least a 2nd location.

Laptop - Synchronizes once a day via Deja Dup to server.

Fiance's laptop - Synchronizes once a day via Deja Dup to server.


At my parents house, I set up a spare tower I had with a 250GB drive. I set the BIOS to turn on when power is restored and hooked it up to a surge strip with a timed outlet that activates at 6:50 PM and shuts off at midnight. Server kicks on daily at 6:50 PM, and everybody's system backs up to it over Samba at 7:00 PM. Then at 8:00 PM, I have cron shut the system off. I let the timer run until midnight on the box so I can SSH in and lift the cron shutoff and work on it remotely if I need to. Plus, by it shutting off via cron, it's at least not a "force unplug" type of shutdown like it would be if I let the server run and the electrical outlet do its own powering off.

So whether at my house, or my parents house, my system or my better half's system, everything is backed up at least once a day.

:guitar:

"It's better to have it and not need it than to need it and not have it."

---

### Post by Redblade20XX on 2012-06-10
Separate data partition...rarely back up....

-Red

---

### Post by DingusFett on 2012-06-11
> **Irihapeti said:**
> Not as often as I should!


This. I rarely do, though don't have much on my computer that is important or I can't do without.

---

### Post by Irihapeti on 2012-06-11
> **Redblade20XX said:**
> Separate data partition...rarely back up....


Just because it's a separate partition doesn't mean it's immune to failure.

---

### Post by DingusFett on 2012-06-11
Yeah, my data lives on a completely seperate 1TB HDD, but even that will fail one day.

---

### Post by catlover2 on 2012-06-11
I have all of my data and my home folder on one HDD, and I back it up whenever I make some important changes or weekly, whichever comes first. I use ```
rsync --delete --progress -vrav /Primary_DATA/ /BACKUP/
``` to back up my data to two identical HDDs, one of which is external.

---

### Post by Bachstelze on 2012-06-11
(Almost) never. The only thing I have backed up is a handful of emails.

---

### Post by Bandit on 2012-06-11
I try to backup once a month unless a lot of files have been added or changed. No reason to make additional backups if none of the files have changed. One big reason is the time it takes to make a backup, a full backup can take 3 or 4 hours, incremental can take ~30mins at most. I have a lot of family photos and music I have purchased over the past 20 years. So its a chore..

---

### Post by black veils on 2012-06-11
constantly, to dropbox. then once a week to a usb flash drive.

---

### Post by Erik1984 on 2012-06-11
My /home and shared (with Windows) datapartition are scheduled for daily backup but I don't have the external drive plugged in and mounted all the time. So some days this backup fails. I do let the script produce a notification that backup is due one hour before actual backup.

Really important files I also store in Dropbox and/or UbuntuOne. Those backups are not scheduled however it's more ad hoc and depends on my workflow. If I'm working with some files often I tend to copy them to Dropbox a few times a day.

Weak point in my 'strategy' is verifying backups. I don't really do this except browsing the external drive and dropbox folder now and then to see if everything is in place.

---

### Post by SeijiSensei on 2012-06-11
> **Bandit said:**
> IOne big reason is the time it takes to make a backup, a full backup can take 3 or 4 hours, incremental can take ~30mins at most. I have a lot of family photos and music I have purchased over the past 20 years. So its a chore..

Using rsync avoids most of these issues.  It only copies files that have changed.

---

### Post by sanderella on 2012-06-11
When I change computers...

and I use Ubuntu One now. ;)

---

### Post by Redblade20XX on 2012-06-11
> **Irihapeti said:**
> Just because it's a separate partition doesn't mean it's immune to failure.

Yes...but the probability that a modern hdd will fail is low for an average user with correct environmental variables. I've got several hdds since 2001 and they are still running....

-Red

---

### Post by CharlesA on 2012-06-11
> **SeijiSensei said:**
> Using rsync avoids most of these issues.  It only copies files that have changed.
Yep Yep.

I do daily backups to external media along with monthly backups to external media.

---

### Post by matthewfelgate on 2012-06-13
All important documents on Google drive.
Other files on a 1TB external drive.

---

### Post by HappinessNow on 2012-06-13
Everything is stored automagically on the cloud, and my primary computer is a Google Chromebook (CR-48).

---

### Post by Linux_junkie on 2012-06-13
Reading through all the comments I think I must be the only one who uses Archive Manager to backup.  I backup everything on my home partition to a USB flash drive (memory stick).  Things I leave out are iso files and other compressed archives that maybe sitting in my home partition.

I tend to only backup though when I remember, but then I don't have a lot of personal files on computer anyway.

I'll have to look in to rsync though, sounds like a better app for backing up.

On second thoughts just looked at help screen for rsync and looks too complicated to setup. :-o

---

### Post by scouser73 on 2012-06-13
I backup files to Ubuntu One and have my film, tv & music libraries backed up to various externals.

---

### Post by Brimwylf on 2012-06-13
I am probably one of the few that, at this point, has nothing (really, nothing) backed up. I never went beyond having an 80GB HDD, never needed it. I watch movies on my DVD or go to the cinema, and I stream TV series. All the music I need is on Youtube but I also go to concerts quite frequently.
It's been this way for years, and it came crashing down on me about 2 months ago. I lost many years of my life (a lot of configs, code and of course years of personal pictures) to a HDD failure. I always moved everything from one HDD to the next, without any extra backup. This time, I had no chance. I managed to recover some back, but not nearly enough. 

I was actually in the search of a good setup idea combining an external HDD and a cloud-type service (need to research a bit more on the privacy issues with these though) when I saw this thread, so thanks for all the nice ideas :)

---

### Post by mikeruss on 2012-06-13
I back up regularly (well what I consider to be regular) every few weeks... I probably don't need to, but I lost some pictures and videos once.

---

