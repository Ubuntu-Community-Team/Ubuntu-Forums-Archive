---
title: "Moving data to a new server"
date: 2010-06-14
forum: Server Platforms
---

### Post by Fliggerty on 2010-06-14
Hey all,

I've recently acquired a new server.  I want to replace my old one with this one, but I don't want to go through the process of installing and configuring everything again.  

I installed a fresh 9.10 on the new server, which is what is running on the old one.  It is on the network.

So what is the best way to copy everything over?  I have a lot of apps and utilities installed, not to mention all of the MySQL db's and website files.  

Is RSync the best way to handle this?  If so, how would it best be done?  Which system would I run the commands from?

Thanks!

--Fligg

---

### Post by new_tolinux on 2010-06-14
For the mysql and apache/php parts it should be no problem just to copy files from one computer to another. Assuming that you'll know which rights has to be given to which users/groups to make things work (and how to do that), it will probably work at once.

You will however have to install all things again before copying any data, since many programs have parts residing in different places on your computer and you really don't want to search for all of them.
Afaik users can't be copied and have to be set up again. After the first login on the new computer you can copy their profiles from the old computer.

---

### Post by arrrghhh on 2010-06-14
MySQL needs to be properly backed up.  You can't just 'copy files' when it comes to that, unfortunately.  Read [this](http://www.devshed.com/c/a/MySQL/Backing-up-and-restoring-your-MySQL-Database/) article on backing up MySQL.

The best option would be to image the server - but that can be a lot of work if you're not setup to do it.

With that said, other than MySQL it looks like most of your stuff is pretty plain-jane.  Just copy the files, make sure to grab any config files you modified from /etc.  You're going to need to reinstall all your programs, but if they have configuration files associated with them (they all should in one way or another) you can copy the configs.  I would install the software first, then update the configuration files.

---

### Post by new_tolinux on 2010-06-14
> **arrrghhh said:**
> MySQL needs to be properly backed up.  You can't just 'copy files' when it comes to that, unfortunately.  Read [this]("http://www.devshed.com/c/a/MySQL/Backing-up-and-restoring-your-MySQL-Database/") article on backing up MySQL.

Sorry, but I'll have to disagree. I did some reinstalls on my own server after a point that making a backup wasn't an option anymore and just copying the files to the new install (same distribution/version) worked perfect. The only things I found out the hard way was giving "mysql" privileges as the copied files were owned by root and edit the config-file to set the old password for the debian-user which ubuntu uses to perform certain tasks within mysql.
I did also have mysqldump backups in some occasions, but when I tried to import them it seemed they weren't properly escaped and that lead to very incomplete tables.

---

### Post by arrrghhh on 2010-06-15
> **new_tolinux said:**
> Sorry, but I'll have to disagree. I did some reinstalls on my own server after a point that making a backup wasn't an option anymore and just copying the files to the new install (same distribution/version) worked perfect. The only things I found out the hard way was giving "mysql" privileges as the copied files were owned by root and edit the config-file to set the old password for the debian-user which ubuntu uses to perform certain tasks within mysql.
I did also have mysqldump backups in some occasions, but when I tried to import them it seemed they weren't properly escaped and that lead to very incomplete tables.

Interesting.  I honestly don't have much experience with MySQL backups, but in my experience with databases is you must back them up separate of the database files.  Perhaps someone knowledgeable can chime in?

---

### Post by new_tolinux on 2010-06-15
> **arrrghhh said:**
> Interesting.  I honestly don't have much experience with MySQL backups, but in my experience with databases is you must back them up separate of the database files.  Perhaps someone knowledgeable can chime in?
Probably one thing that can be overlooked easily: the database server (mysql service) was down when I copied the database files. As long as the mysql service/daemon is running, it can corrupt your databases since the files are in use.

---

### Post by Fliggerty on 2010-06-17
Thanks for the comments.

I am quite familiar with MySQL backups (I work for a web host, so we deal with that on a daily basis.)  All tables consist of three files, .frm, .MYI, and .MYD.  They reside in /var/lib/mysql/DATABASE_NAME.  So long as you copy all three of the files over from place to another, you shouldn't have any problems.  The difficult part is, as has been mentioned, the permissions.  MySQL permissions are all stored in the MySQL database, so it's usually a simple matter to either copy that over, or export the users that are needed to access your databases.

As for copying everything else, it is going to be a big job.  I have a lot of users and a lot of applications...many of which took days and days to get working properly.  To be honest, I really don't look forward to doing all of that again.

I am not very familiar with rsync, but a lot of people and various tutorials have led me to believe it would be a good choice...I just haven't yet sorted out the final details on the exact process needed to use it to essentially make a clone of my current system with the exception of the base system files.

---

### Post by new_tolinux on 2010-06-17
> **Fliggerty said:**
> I am not very familiar with rsync, but a lot of people and various tutorials have led me to believe it would be a good choice...I just haven't yet sorted out the final details on the exact process needed to use it to essentially make a clone of my current system with the exception of the base system files.
I can't help you out there, as I only know rsync by name, never used it.
Never had to backup a lot of system-users either, only some mysql-users, which where simply copied by copying the "mysql" database itself (but that's probably no news, since you're familiar with mysql ;)).

---

### Post by The Real Dave on 2010-06-17
If your keeping the same version of Ubuntu, you can simply clone the drive from the old server, to the new one, using [Clonezilla]("http://clonezilla.org/").

---

### Post by paulisdead on 2010-06-17
You can directly copy a mysql database if it's not running.  You can also preserve permissions on files, generally with the -p switch with most programs.  This works for cp, rsync, and tar.

If you're going grab the files yourself using cp, tar, rsync, or anything else similar, you want to exclude certain directories like /proc and /sys, and you may or may not want to backup /mnt and /tmp.

The benefit to just grabbing files like this with rsync, cp, and tar, is that you can do it from a running system.  If you don't want to stop mysql to run the backup, then you'll need to dump the database manually, though.

---

### Post by oldfred on 2010-06-18
You can make a list of installed apps and reinstall them.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

You may want to update sources before running the apps to make sure you have all sources covered.
Check:
sudo cp /etc/apt/sources.list ~/sources.list.backup

---

### Post by Fliggerty on 2010-06-18
Thanks for all the comments guys.

Here's what I finally did, which seems to be working well (still copying the last few directories over.)

1.  Upgraded the distro on the old server.
2.  Installed the same distro version on the new server.
3.  Set SSH keys between the two servers for password-less connections.
4.  From the new server I ran this command:

```
rsync -e ssh -avz root@192.168.1.99:/var/ /
```

I did that command for each of the directories, with the exception of dev, sys, media, mnt, and proc.

Still waiting for the very large /var/ directory to finish right now, it's the last one.  All of the others have worked well so far.  I was able to reboot before I got to /var, and all services seem to work okay so far.

---

