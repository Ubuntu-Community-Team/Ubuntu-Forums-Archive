---
title: "Backup Ubuntu Server"
date: 2008-06-30
forum: Server Platforms
---

### Post by ger_macaco on 2008-06-30
Hi, I have installed Ubuntu Server 8.04 to an amd64 PC with 2 SATA disks in a RAID1.

I have a removable disk drive on which I would like to perform weekly backups of the whole system (so that I just need to replace the disk in case there is a failure). I don't need this removable disk to be part of any RAID.

How should I do this?

Many thanks.

---

### Post by mrpeenut24 on 2008-06-30
cronjob and rsync

```

sudo crontab -e

```insert something like this:

```

0    0    1    *    *    rsync -a --exclude=*path_to_backup_dir* / *path_to_backup_dir*

```This will tell rsync to archive (make a *complete* backup) of the entire machine, except where it's backing up to, on the first of the month, at midnight.  Be forewarned that this will also backup every other hdd that is plugged into the machine.  To add extra excludes, just add an extra exclude option.  i.e

```

rsync -a --exclude=/dev/ --exclude=/media/ / /media/backupdrive

```

---

### Post by ger_macaco on 2008-06-30
Great. That's what I needed.

Thanks a lot!

---

### Post by mrpeenut24 on 2008-06-30
No problem.  :-D

---

### Post by gurkburk on 2008-07-13
So this is a pretty valid way of backing up the server, say, once a week?
I figured id do that, and also everyday(mon-fri) make a backup of the home and data directories on the server (user home's, mysql copies and so-on).

Seems a bit to "easy" to just do a rsync -a and exclude some directories?
What happens when it starts over the next week, will the arcive-option simply make rsync update changes?
How about using the --delete option, and why not use the option --backup-dir ?

---

### Post by fjgaude on 2008-07-13
I use something like this, hourly, manually:

```
rsync -r -t -p -o -g --delete /home/raid/ /media/backup/raid/
```

It all depends on what you are wanting to achieve... I want identical files front to back.

---

### Post by chrislynch8 on 2008-07-16
Just wanting to jump in on this thread, I want to perform backup across the network, would rsync be the best option for this?

---

### Post by mrpeenut24 on 2008-07-18
As far as I know rsync is the best option for backing up across networks.  As they've pointed out, there are a lot of different options for rsync, and different needs for different people so be sure to check out the man page for it, or look online.

---

### Post by anelephant on 2009-03-15
Hey, thanks for the nice info! 

Let's say you back up the whole system onto a portable drive like explained here. How would one go about restoring the system?

Or in more general terms. Is there a way of backing up the whole system on a portable media and then restoring the system (os, boot, configurations and all)? Would I make something like a boot floppy with a script that does the jobb?

---

