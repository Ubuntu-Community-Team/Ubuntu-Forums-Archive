---
title: "Backup Solutions?"
date: 2012-05-14
forum: Server Platforms
---

### Post by DocHoliday52090 on 2012-05-14
I'm looking for advice on how to backup my systems. I'm that guy that never backed up anything. So I spent a lot of time setting up my ubuntu server and I'd like to keep it in working condition barring drive failures and the like. 

Here's what I have in the household:

Win7 Laptop

Ubuntu Laptop

Macbook Laptop

Ubuntu PC w/ 1 TB drive divided into 2 partitions - 15 gb for / and 485 for /home. The other 500 I designated for backups of the backups I want to make here.

Ubuntu Server w/ 60 gb (system), 160gb (torrents, usenet downloads, movies, etc), and 2 TB (backups and long term media - pictures, home videos)



What I'd like - 

Backup the Win7 + Ubuntu laptops. The Macbook has nothing important on it, and is easily repairable with drive failure so not worried. 

Backup the Ubuntu desktop's system partition for easy restore. I'm thinking imaging for / and file backup from the 485 gb /home.

MOST IMPORTANT - backing up Ubuntu server's 60gb system partition. I spent a lot of time tweaking this that I don't want to repeat. It is running Webmin, if that makes anything easier. The 60gb drive with the system on it is showing age in SMART so I'm very worried. 

I'd like it and all the other computers to backup to the 2 TB drive, and all those backups backed up to the 500gb media partition on the desktop in case the server dies.

What tools should I use? I've seen rsync and bacula recommended, but what about images? Any anecdotes of how others set up their systems is appreciated.

---

### Post by HermanAB on 2012-05-14
Use rsync.  Read the man page. Really.

---

### Post by CharlesA on 2012-05-14
> **HermanAB said:**
> Use rsync.  Read the man page. Really.
+1.

I use robocopy to copy the "my documents" folder from Windows boxes to my server and then rsync that to backup media.

---

### Post by lukeiamyourfather on 2012-05-14
You can use rsync on the Windows machines too with Cygwin.

---

### Post by giowck on 2012-05-14
check out clonezilla: [http://clonezilla.org/](http://clonezilla.org/)

It is basically a live cd to clone the entire hard drive/partitions and/or save it to iso etc...

Restoring is very easy and fast. The only thing is that you need to backup manually, where rsync can be automated with cron etc... /but rsync doesn't bacup mbr, partitions...)

---

### Post by CharlesA on 2012-05-14
> **lukeiamyourfather said:**
> You can use rsync on the Windows machines too with Cygwin.
True, but Robocopy is included by default with Vista and 7. ;)

---

### Post by Gyokuro on 2012-05-14
You can backup all three clients:

Win7 laptop: robocopy was already mentioned and depending on your Win7 release you can use standard windows backup and backup to your samba share on your Ubuntu server

Ubuntu laptop: rsync is your friend 

Macbook laptop: install netatalk on your Ubuntu server (you need to make a Mac share on your Ubuntu server) and use TimeMachine (10.7.3 works) as it is the way how we backup our Mac clients and it works.

---

### Post by LHammonds on 2012-05-14
[Redo Backup and Recovery]("http://redobackup.org/").

Burn the ISO to a CD, attach an external USB HD to whatever system you want backed up, drop in the CD and boot it up.  Redo can backup whatever partitions you want and place them on the external HD.

Doing a complete system restore (for Linux or Windows) is super easy.

Now, if you are just wanting daily backups of data and whatnot more than a complete disaster recovery, rsync will work wonders for you.  You could even setup your Ubuntu server to connect to all your remote machines to perform the backup when they are online.

LHammonds

---

### Post by kgatan on 2012-05-14
Scripted WinSCP is great if you want scheduled backups over ssh on windows.
I have a couple of win 7/xp machines using it and havnt touched them for a year now.

---

### Post by jonnyboysmithy on 2012-05-14
I personally really like luckybackup. Its a Gui for rsync. You can do soo much with it, its great.
Whats also cool is that you can backup to a remote location, with lots and lots of options.
Seriously have a look at luckybackup..

---

### Post by anonymouschief on 2012-05-15
> **CharlesA said:**
> True, but Robocopy is included by default with Vista and 7. ;)

CharlesA, thanks for the Robocopy tip.

---

### Post by trundlenut on 2012-05-15
I use backuppc, which, with a bit of fettling, should cope with a mixture of windows and ubuntu clients.  My backup server at work has been chugging away backing up a windows server for over a year now.

---

