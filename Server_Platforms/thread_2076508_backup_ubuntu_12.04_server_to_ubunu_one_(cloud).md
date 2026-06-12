---
title: "backup ubuntu 12.04 server to ubunu one (cloud)"
date: 2012-10-26
forum: Server Platforms
---

### Post by bart.a on 2012-10-26
Hi.. I use a headless ubuntu 12.04 server, and it works like a charm. But I have some questions regarding a backup..

I backup the user files daily and make a full backup weekly using tar and crontab. But the backup process relais on yours truly to change removable hardware to ensure success.. Therefore I would like to move the weekly (incremental) backup to ubuntu one..

**My questions are: **
1. Is it possible to backup to ubuntu one from a headless server?
2. Has anyone got some experience with backing up to ubuntu one from a headless server?
3. Is it possible to set up a cron job to automate that process, and how do I do that?

I found how to set up ubuntu one from a headless server [(found it here)]("http://wiki.ubuntu.com/UbuntuOne/Headless"), so thats covered..

Thanks..

---

### Post by LHammonds on 2012-10-26
I don't use Ubuntu cloud.  I prefer to keep my sensitive files on my own hardware.  I happen to have an environment where I have access to a remote site (different city) and simply copy my backups from one server to another.

It is all automated using LVM + Snapshots and FSArchiver for full system backups (most servers don't need this done except just before an OS/App update.  A base OS with level 7 compression is about 1.4 GB for my setup.  If curious about it, I have detailed setup documentation in my signature.

Sorry I can't help you with Ubuntu cloud.  I'm almost curious in how it would work but I just don't have anything I would want going onto a 3rd-party site.

LHammonds

---

### Post by bart.a on 2012-10-27
Hi LHammonds, thanks for your reply..

I understand your concern about that.. I could set up a backup server for myself in another location (home for instance) but in this case it would be to much.. I would consider a dedicated backup server when I had more servers in different locations or more sensitive data that needs frequent backups.. The data is not that sensitive. Sure I don't want it to get public, but it wouldn't mean the end of the world..

So I think a 3rd-party cloud drive would be sufficient and reasonably secure in this case and because ubuntu offers a free cloud drive I want to give it a try and see how it works out..

---

### Post by thnewguy on 2012-10-28
So far as I know Ubuntu One does not work properly without a graphical interface. I've seen some tutorials for getting One to sync on a server, however, all the ones I have tried failed.

There is a package called u1ftp (Ubuntu One FTP) which will set up a proxy FTP server on your local host, connecitng your host to the One service. I tried it on a couple of machines and found it worked sometimes, but not consistently. You are probably better off using a different cloud sync service, like Dropbox, until the Ubuntu One team includes official support for headless machines.

---

### Post by bart.a on 2012-10-28
Hi thnewguy, thanks for your reply..

Unfortunately not what I hoped to hear but I'm glad you shared your experience..
I think I'll take your advise and look for an alternative..

---

### Post by bart.a on 2013-02-04
SOLVED.. Found what I was looking for..

I installed headless Ubuntu One using the guidelines I found and that works perfectly..
Created a new backup folder in my home folder, which is synchronized with Ubuntu One..
Wrote a shell script that makes a backup of the (samba) shared folders which contain all files..
Created a cronjob that starts the shell script daily..

So to answer my own questions:
1. Yes, it's possible
2. Not much, but I got it working
3. Yes it is, with a shell script and a cronjob.. If anyone needs more info or the content of the shell script, please let me know..

---

