---
title: "Backup methods on Server 8.04.1"
date: 2008-09-09
forum: Server Platforms
---

### Post by boragora on 2008-09-09
Hi guys,

after converting 4 machines in my office to Ubuntu I've finally taken the plunge to convert the server from Win2003. I've just downloaded Ubuntu Server 8.04.1 and have it ready for a fresh install.

I have two 500gb drives in this 'server' and previously Windows just made two copies of all data written to a data partition on each drive. Is there any way of doing the same thing in Ubuntu?

I know I could use softRAID but this seems more orientated to backing up a whole OS setup and really I just need to protect my data. I don't want to end up having to backup manually every afternoon, especially as one of my applications streams data consistently from scientific equipment and I need exact copies of the information as it comes in.

Basically, if I can get my data recorded in two partitions at the same time, so if one fails I can just extract it from the other, this is all I need. I don't know if there is any software out there either that will monitor both drives and tell me if one is failing..... can anyone make suggestions?

Thanks everyone, really need the help on this one.

---

### Post by schettj on 2008-09-09
That's exactly what raid is for

[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

If you just want your data in a raid, you can build a raid from two (or more) additional drives, mount that raid disk to the directory where the data will be written, and hey presto you're done.

Otherwise, you could rsync the data off regularly to some offsite or different drive via a cron job ([http://everythinglinux.org/rsync/](http://everythinglinux.org/rsync/)), or set up some other automated backup system.

---

### Post by 47_MasoN_47 on 2008-09-09
If you wanted to you could setup a script to just copy the files from one partition to the other.  Download gnome-schedule and run that, make a new job and use the command as something like this:
```
cp /home/user/Desktop/data /media/disk/data-backup
``` and set it to run at whatever frequency you want.

---

### Post by lazyart on 2008-09-09
That's odd... you sound like you want RAID from your explanation, but you say you don't want RAID.

RAID is not so much about a backup than it is about redundancy.  If a drive goes down you keep going because the second drive is a constant mirror.  Then you just drop in a new drive and it will replicate back.  For a server I would expect this is exactly what you want since the process is transparent.

---

### Post by 47_MasoN_47 on 2008-09-10
I'd agree that a RAID is the best thing, but since he doesn't want one I suggested the copy script.  RAID has saved our servers here 3 or 4 times when we've had hard drive failure.

---

### Post by Doby on 2008-10-08
what about none gui server?  At work we have 3 ubuntu box's doing various things for us and our clients.  We need a none gui based app to run a full system install, then run incramentals every so often and a full backup once a week.  I have been using the desktop for a couple years but not to familiar with the none gui based server. Any suggestions?

---

### Post by Doby on 2008-10-08
An app. like "Time Machine" for mac would be perfect.

---

### Post by 47_MasoN_47 on 2008-10-08
You could use dar and schedule it with cron.  It's pretty easy to use.

Here's a sample command for dar.
```
dar -v -c "/media/disk/mybackup" -R "/home/user" -w -D -y -m 150
```
That will basically do everything you need, just replace /media/disk/mybackup with wherever you want to backup to and replace /home/user with what you actually want to backup.  All those switches do different things, you can see all the options for it [here.]("http://dar.linux.free.fr/doc/Features.html")

Using cron is pretty easy too, here's a good explanation a guy gave to me once.
[QUOTE=northern lights]Create a textfile in your /home folder and name it "cronjobs.txt".

Open it and add the line
Code:

0 19 * * * /usr/bin/unison [options]

Then run
Code:

crontab -u USERNAME cronjobs.txt

where USERNAME is your username. Verify with
Code:

crontab -l

The syntax of a cronjob is

minutes(0-59) hours(0-23) day(0-27/28/29/30) month(0-11) weekday(0-6) command

where a * stands for "any value"[/QUOTE]
[Be sure to thank him if it helps you!]("http://ubuntuforums.org/showthread.php?t=869219")

---

