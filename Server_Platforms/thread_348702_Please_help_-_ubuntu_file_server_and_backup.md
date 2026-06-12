---
title: "Please help - ubuntu file server and backup"
date: 2007-01-29
forum: Server Platforms
---

### Post by Robin_P on 2007-01-29
Hi everyone, and thanks in advance for any help! :D :D :D 

I am relatively new to linux, apart from a brief flurry about 10 years ago, but am a pretty savvy windows user (not that it helps).  I work at a small architecture practise in Newcastle, UK, and we have discussed upgrading our basic file server to run on linux (to avoid buying Micro$oft $erver and licenses).  Our server needs are basic - incorporating basic file storage over a windows LAN only and a scheduled daily file backup to a Maxtor USB harddrive. We'd like to keep the same basic arrangement but with linux for stability and no. of connections reasons.  Since I'm a full time Architect also I have pretty limited time for network maintenance - maybe 1 or 2 hours per week max!  Also since we're small we can't afford to employ outside help! :redface: 

I've been scouring the forums this last week and have read about SAMBA and how this should suit our server needs, but have a couple of questions I'd really appreciate some help with.  Firstly I'm a bit stuck on the backup side of things. Essentially all we need is a piece of software which runs in the background and basically copies all revised files to the USB harddrive once per day. A piece of software with a GUI would be ideal as I'm a visual person! :D   Also I've been searching for information on a good GUI to help with SAMBA but haven't found anything that is quite simple enough to install or setup.

My thanks for any comments:D 

Kind regards

Robin Parsons

---

### Post by kidders on 2007-01-29
Hi there and welcome,

Depending on how you want it to work, backing your stuff up could be quite simple ... Tbh, I wouldn't bother with a nice UI. For instance, say you have one central location where important files are stored, and an external hard disk mounted at /media/backup. Something like the following would do the trick...

```
tar -C /path/to/files -czf /media/backup/backup.tar.gz *
```

The idea would be to set up a cron task, to have a command like that executed daily at, say, 3am. Cron can also mail you in the event of some sort of failure.

If it were me, I would dress the command up a bit...

```
if [ -w /media/backup ]; then
     nice -n 15 tar -C /path/to/files -czf /media/backup/`date +"%Y%m%d"`.tar.gz *
fi
```

[LIST]
[*]**if [...** - Don't try to back up unless the external HDD is plugged in.
[*]**nice** - Lower the task priority, so it doesn't interfere with other operations.
[*]**`date ...`** - Label the backup archive with the date.
[/LIST]

What you'd end up with is a hard disk full of compressed archives, called things like "20070129.tar.gz". While incremental backups would of course be far more efficient, the ability to roll back any document to an arbitrary date in the past would probably be worth  sacrificing the space.

One other possibility is a more "real-time" approach. Assuming you're familiar with (or perhaps already using) RAID, you *could* use a protocol called AoE (ATA over Ethernet) to mirror your data in real time on a second PC. Basically, you would set up a RAID 1 array in which the individual hard disks that make it up are actually in different PCs. This might not be quite what you're after though ... it would be a mirror, not a backup.

In the GUI world, there are several backup apps around for KDE, Gnome & others, many of which are basically just front-ends to tools like tar & cron that I mentioned above. One of the advantages in messing with cron yourself, though, is that you can very easily add personal little touches. For instance, you could...

[LIST]
[*]Have your system mail you if the amount of free space on your backup device falls below a certain threshold.
[*]Automatically check that the size of the backup, or the number of files in it, is reasonable.
[*]Temporarily shut down filesharing to stop thing being modified while the backup is in progress.
[*]Auto-delete archives that are over two weeks old.
[*]Etc.
[/LIST]

Tweaks like these are trivial, and might help to eliminate time wasted maintaining your backup regime.

I hope that helps.

---

### Post by Robin_P on 2007-01-29
Thanks for your response Kidders! :D Apologies for not replying earlier - I've had some stuff to deal with this afternoon. I've read some guides on SAMBA and think I'll have a go minus any GUI. However does anyone know of a good backup utility that can easily setup scheduled, incremental backups?  At the moment we use Retrospect 7 on a windows PC so if something similar exists for Linux that'd be great! :D 

Thanks again

Robin

---

### Post by kidders on 2007-01-29
Hey again,

> **Robin_P said:**
> Apologies for not replying earlier - I've had some stuff to deal with this afternoon.Hehe. It's your thread! There's no rush. :-)

> **Robin_P said:**
> I've read some guides on SAMBA and think I'll have a go minus any GUI.Tbh I always find that easier too. Editing smb.conf directly is fast and reasonably straightforward.

> **Robin_P said:**
> However does anyone know of a good backup utility that can easily setup scheduled, incremental backups?  At the moment we use Retrospect 7 on a windows PC so if something similar exists for Linux that'd be great! :DTry looking through the software repositories with something like **apt-cache search backup | grep -i kde** or **apt-cache search backup incremental** or similar. I almost never use actual backup *applications*, so I couldn't say which ones are good. Sorry. :-( Maybe someone else will post a more productive suggestion.

---

### Post by fellgoog on 2007-01-29
If you want to invest as little time as possible, you can set up a RAID 5 for your data. Costs very little (around 3x60 Euros for three 250GB disks), and you have all of your data secured, not only a part of it. This does, of course, not permit recovery of overwritten files, and neither does it save you from total hardware failure (but neither does the USB drive).

Ubuntu has a very nice installer for RAID, and you can also set it up on a live system.

---

### Post by jrock2004 on 2007-01-29
Is there a way in that script to put to skip /data folder?

> **kidders said:**
> Hi there and welcome,

Depending on how you want it to work, backing your stuff up could be quite simple ... Tbh, I wouldn't bother with a nice UI. For instance, say you have one central location where important files are stored, and an external hard disk mounted at /media/backup. Something like the following would do the trick...

```
tar -C /path/to/files -czf /media/backup/backup.tar.gz *
```

The idea would be to set up a cron task, to have a command like that executed daily at, say, 3am. Cron can also mail you in the event of some sort of failure.

If it were me, I would dress the command up a bit...

```
if [ -w /media/backup ]; then
     nice -n 15 tar -C /path/to/files -czf /media/backup/`date +"%Y%m%d"`.tar.gz *
fi
```

[LIST]
[*]**if [...** - Don't try to back up unless the external HDD is plugged in.
[*]**nice** - Lower the task priority, so it doesn't interfere with other operations.
[*]**`date ...`** - Label the backup archive with the date.
[/LIST]

What you'd end up with is a hard disk full of compressed archives, called things like "20070129.tar.gz". While incremental backups would of course be far more efficient, the ability to roll back any document to an arbitrary date in the past would probably be worth  sacrificing the space.

One other possibility is a more "real-time" approach. Assuming you're familiar with (or perhaps already using) RAID, you *could* use a protocol called AoE (ATA over Ethernet) to mirror your data in real time on a second PC. Basically, you would set up a RAID 1 array in which the individual hard disks that make it up are actually in different PCs. This might not be quite what you're after though ... it would be a mirror, not a backup.

In the GUI world, there are several backup apps around for KDE, Gnome & others, many of which are basically just front-ends to tools like tar & cron that I mentioned above. One of the advantages in messing with cron yourself, though, is that you can very easily add personal little touches. For instance, you could...

[LIST]
[*]Have your system mail you if the amount of free space on your backup device falls below a certain threshold.
[*]Automatically check that the size of the backup, or the number of files in it, is reasonable.
[*]Temporarily shut down filesharing to stop thing being modified while the backup is in progress.
[*]Auto-delete archives that are over two weeks old.
[*]Etc.
[/LIST]

Tweaks like these are trivial, and might help to eliminate time wasted maintaining your backup regime.

I hope that helps.

---

### Post by detectiveinspekta on 2007-01-29
There is another way by using rsync. Havn't implemented mine yet but it does the same job but only copys over what files that have been added or changed. Im not entirly sure if the old copys of modified files are kept though.

---

### Post by jtc on 2007-01-30
> **detectiveinspekta said:**
> There is another way by using rsync. Havn't implemented mine yet but it does the same job but only copys over what files that have been added or changed. Im not entirly sure if the old copys of modified files are kept though.
You get that, and some more (hard links, backup rotation, etc), by using [Rsnapshot]("http://www.rsnapshot.org/").

---

### Post by sitedesign on 2007-09-14
I have used the package 'backup-manager' which is very good for the job. It supports rsync, DVD, ftp and many other backup media.
It basically uses tar. Very simple config file.

---

