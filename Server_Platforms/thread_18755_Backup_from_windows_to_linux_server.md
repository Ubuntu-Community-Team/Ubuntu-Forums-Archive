---
title: "Backup from windows to linux server?"
date: 2005-03-08
forum: Server Platforms
---

### Post by Rohan on 2005-03-08
Hey guys... I'm going to be setting up an old box with ubuntu to use as a basic fileserver, nat, etc. Anyways.. I was just wondering what's the best to do regular automated backups from a windows box to the ubuntu server. I'd like to this from OSX to the linux box as well..

Thanks again...

---

### Post by Jad on 2005-03-08
depends, What are you going to backup, Documents, web files, database, movies .. 
?

---

### Post by Rohan on 2005-03-08
documents... smaller ones at that

---

### Post by Myles3 on 2005-03-08
I am having a similar problem and posted a little bit befor you ([http://ubuntuforums.org/showthread.php?t=18743](http://ubuntuforums.org/showthread.php?t=18743) ). I did some searching and found this article on Linux.com [http://applications.linux.com/article.pl?sid=04/09/15/1931240&tid=13](http://applications.linux.com/article.pl?sid=04/09/15/1931240&tid=13) . I know it says Linux workstations but there is a Windows version of rsync using cygwin that you can use.

The article above many not work but just google around for a better one.

I hope this gave you a starting point.

---

### Post by Jad on 2005-03-08
on your linux box, set up a cron to ftp get files

---

### Post by alastair on 2005-03-08
A simple "rsync" style script might be all you need.

[http://samba.anu.edu.au/rsync/](http://samba.anu.edu.au/rsync/)

It's very useful.

---

### Post by sesquipedality on 2005-03-15
[QUOTE=Rohan]Hey guys... I'm going to be setting up an old box with ubuntu to use as a basic fileserver, nat, etc. Anyways.. I was just wondering what's the best to do regular automated backups from a windows box to the ubuntu server. I'd like to this from OSX to the linux box as well..
.[/QUOTE]

The backuppc package is available in universe.  I use this for backing up a windows system from my server.  (I'm actually using the backuppc package from Debian unstable, since I was using it before switching to ubuntu, and it's more recent than the one in universe.)

I imagine OSX supports rsync, in which case backuppc can back it up, although I have no personal experience with OSX.

---

### Post by cedricthegreat on 2005-03-16
Take a look at Sync2Nas it basically packages Cygwins rsync into a nice Windows tool/frontend that allows you to backup using rsync to a rsync server

[http://sync2nas.sourceforge.net/](http://sync2nas.sourceforge.net/) 

It works well I havn't had any problems with it to date.

 :grin:

---

