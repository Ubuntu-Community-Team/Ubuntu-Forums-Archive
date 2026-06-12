---
title: "Using Ubuntu to backup Windows Network PC's"
date: 2006-02-22
forum: Server Platforms
---

### Post by DieselD on 2006-02-22
Hi,

I'm not keen on spending a fortune on any Windows softare for a simple backup server.
This is what I had in mind.
1. Install Ubuntu on a decent x386 PC
2. Pack it full of HDD's
3. Setup networking so it see's all the Windows PC's on the LAN
4. Install "XXX" backup software (please advise which would do the trick)
5. Run "mirror" type backups of specific shared folders of the Window PC's on the network.

I know this does not really sound like the best backup solution, but we need quick and easy access to the files if any of the PC's on the network fall over. So cannot really spend a lot of time uncompressing etc. (I would however like to learn to do this the correct way - incremental backups etc...)

If anyone has any suggestions, tips, links to software, ideas... anything - It would be highly appreciated!

Thanks

---

### Post by zac1333 on 2006-02-22
I'm pretty sure you will have to configure Samba and/or NFS on the Ubuntu machine to accomplish what you want.  Someone else here with a little more expertise will have to guide you through that.

As far as the backup software that runs on the windows pc's, I would suggest SyncBack Freeware v3.2.9 is a great software that will allow you to copy all of the files from the window's machines to specific directories on the Ubuntu box, without creating a compressed backup file.

Good luck with your efforts.

---

### Post by uopjohnson on 2006-02-22
I've got a very similiar setup here.  What I did was use samba to create seperate $HOME shares for every computer and then mapped the samba share as a network drive on the windows machines.  We then use the backup utility that comes with XP to do the actual backup to the network drive.  
Samba has stellar documentation on their website and some great examples.

Another possible option is to install cygwin on all of the windows boxes and then create a cron job which uses rsync to do the backup.  This is how I backup my wifes XP laptop at home.  

Speed is going to become a factor here if you have a lot of machines.  If you are not using some sort of incremental backup system you will have to copy everything all the time which is going to get pretty bad if you have a lot of machines.

---

### Post by firecat53 on 2006-02-22
Not sure if it's the best way, but I'm using a 'pull' type of backup, where the server is controlling the backups. I set up my Ubuntu server so that it could mount the XP computer(s) "My Documents" folder via samba. Once I got that worked out, I just set up a small script/cron job that mounts the XP drive and does an 'rsync --delete' operation. This is fairly fast after the first time, and keeps a mirror of the My Documents folder.  One thing to be careful of....make sure to test if the XP drive is mounted or not first, otherwise you sync an empty directory (e.g. /mnt/windows) to your backup folder.....aka you get an empty backup folder!  Some lessons are just learned the hard way.....

Good luck!

Scott

---

### Post by dickohead on 2006-02-22
rsync is a good way to synchronize your files at set intervals via the crontab, you could also use unison or just a simple crontab script to run a copy command on the stuff you want.

You'de be best using rsync/unison though, do a little reading on some man pages (man unison/man rsync or tldp.org).

At the moment I've setup network shares for everyone in my house, which I will then set to synchronise with an external hard drive using unison, I'm also going to get it to synchronise a couple of folders on my laptop so when I'm out and about my data will be the same when I plug in at home and can continue to work from my desktop.

---

### Post by breezyfox on 2006-02-23
[QUOTE=DieselD]Hi,

I'm not keen on spending a fortune on any Windows softare for a simple backup server.
This is what I had in mind.
1. Install Ubuntu on a decent x386 PC
2. Pack it full of HDD's
3. Setup networking so it see's all the Windows PC's on the LAN
4. Install "XXX" backup software (please advise which would do the trick)
5. Run "mirror" type backups of specific shared folders of the Window PC's on the network.


Thanks[/QUOTE]
Hi 
I think you can try sbackup or backuppc. both are available through repository and back ports.
check this link for sbackup
[http://www.linux.com/article.pl?sid=05/11/22/2110251](http://www.linux.com/article.pl?sid=05/11/22/2110251) and for backuppc just google it.

hope that will work
bz

---

