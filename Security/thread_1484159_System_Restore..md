---
title: "System Restore."
date: 2010-05-15
forum: Security
---

### Post by ammiedredd on 2010-05-15
Hi!

I am new in Ubuntu.

I wanted to know if there is a System Restore available out there in which is equivalent of RollbackRX ([http://www.rollbackrx.com.au](http://www.rollbackrx.com.au)) freeware or shareware.

RollbackRX used to backup/restore OS system changes.
It is able to backup/restore system in less than 1 minute.
It is able to backup with a little amount of disk size.

Feature Needed:
  Pre-Boot Snapshot Backup
  Pre-Boot Snapshot Restore
  Password Access
  Snapshot Encrypted

I currently used this application in my Windows XP system. And I am happy having it. I used to modify my XP a lot and sometimes forcing myself to restore my system (using rollbackrx) because It is unbootable/freezing/sudden restart. It does save me a lot of time, especially those critical moments.

I am hopeful that there is available variant of this one for Ubuntu.

-am O:)

---

### Post by cariboo on 2010-05-15
Personally I don't feel there is a need for a system restore utility, just keep good backups of important data and configuration files. With a new installation taking 15-20 minutes from the live CD, and depending on the amount of personal data, you should be up and running in about half an hour.

---

### Post by iponeverything on 2010-05-15
I honestly have never missed that kind of fuctionality, but it does seem like a good way to address all of the "updates broke my" wifi, sound etc. etc. etc. problems.

Though more often than not, booting the previous version of the kernel would probably fix the problems for most people..

---

### Post by Rubi1200 on 2010-05-15
You don't mention which version of Ubuntu you are using, but this may help you along the way:

For Karmic:

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#System_Backup_and_Recovery](http://ubuntuguide.org/wiki/Ubuntu:Karmic#System_Backup_and_Recovery)

For Lucid:

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#System_Backup_and_Recovery](http://ubuntuguide.org/wiki/Ubuntu:Lucid#System_Backup_and_Recovery)

I think both are the same, but there may be additional information or links.

Good luck!

---

### Post by ammiedredd on 2010-05-15
> **Rubi1200 said:**
> You don't mention which version of Ubuntu you are using, but this may help you along the way:

For Karmic:

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#System_Backup_and_Recovery](http://ubuntuguide.org/wiki/Ubuntu:Karmic#System_Backup_and_Recovery)

For Lucid:

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#System_Backup_and_Recovery](http://ubuntuguide.org/wiki/Ubuntu:Lucid#System_Backup_and_Recovery)

I think both are the same, but there may be additional information or links.

Good luck!


Hi!

Thank you for a quick reply.
I installed Lucid.
I will try to assessed those.

-am O:)

---

### Post by ammiedredd on 2010-05-15
> **cariboo907 said:**
> Personally I don't feel there is a need for a system restore utility, just keep good backups of important data and configuration files. With a new installation taking 15-20 minutes from the live CD, and depending on the amount of personal data, you should be up and running in about half an hour.


Hi!

In my years of experience as a Windows XP user.
I installed lots of applications on my system.
I copied lots of data on my system.

In Ubuntu I also acknowledge some problems that really required attentions by others because they can't fix it themselves.

And of course I don't want to wait 15 minutes everytime I need to fix my PC.
And it would not 15 minutes only if you have lots of a application to reinstalled and file to recopy.
Plus reconfiguration time if you could remember it.
And sometimes your problem can't be available or hard to find on the internet.
Even in forums/blog sometimes don't give you exact fix.
And for me that doesn't have dedicated internet connection it is quite a big problem.

Imagine I should save the world in 2 minutes.
My PC is unbootable.
The application that would save the world was there.
I do not have internet connection.
No PC replacement.
There is a backup system but required more than 2 minutes to restore.
Then I should say I killed the world because I wasn't able to restore in 2 minutes.


Thanks.

- am O:)

---

### Post by cariboo on 2010-05-15
In most cases, we fix the problems instead of re-installing, it would take a major hosing to warrant a re-isntall, there are various imaging tools, eg: [Remastersys]("http://www.geekconnection.org/remastersys/") and [Clonezilla]("http://www.clonezilla.org/"), that make an exact copy of your system.

The best advice I can give you is to do what you were taught to do when you first started using a computer, make copies of the configuration files before making any changes. It takes just as long to learn how to use a Linux distro as it did to learn all you know about Windows.

---

### Post by ammiedredd on 2010-05-16
> **cariboo907 said:**
> In most cases, we fix the problems instead of re-installing, it would take a major hosing to warrant a re-isntall, there are various imaging tools, eg: [Remastersys]("http://www.geekconnection.org/remastersys/") and [Clonezilla]("http://www.clonezilla.org/"), that make an exact copy of your system.

The best advice I can give you is to do what you were taught to do when you first started using a computer, make copies of the configuration files before making any changes. It takes just as long to learn how to use a Linux distro as it did to learn all you know about Windows.


Hi!

Thank You again for your reply.

-am O:)

---

### Post by Rasa1111 on 2010-05-16
> "It takes just as long to learn how to use a Linux distro as it did to  learn all you know about Windows.  ~Cariboo907

good quote, one we all should remember. <3

---

### Post by MartyBuntu on 2010-05-16
Put me down for full system imaging, as well.

I'd never trust a "system restore" feature.

---

### Post by bayvista on 2010-06-04
The problem with restoring from the 'Live CD' is that you restore to the original distribution. Then you have to download and install 200+ updates which hammers your broadband allowance. I have just suffered my 3rd disk crash in 5 years and really don't want to keep restoring my system.

Surely there must be something in the system which will copy all of '/' and restore using the Live CD?

I have explored TAR, FSArchiver and Remastersys but cannot get any to restore. (They all create a backup).

Any suggestions welcome.

One idea I had was to have a bootable system on a removable drive but I am not sure how to create this and also how do you boot from a removeable drive?

---

### Post by cariboo on 2010-06-05
Have you tried rsync? I use it for backing up my home directory, you could do the same for /. I backup to a server, but an external drive would work just as well.

---

### Post by bayvista on 2010-06-05
What a great idea. I already use Rsync for my data files but did not think of it for '/'. The beauty of Rsync is that it only copies changed files which is so much quicker. Also, you can put the backup job in Cron and automate it.

Many thanks.

---

### Post by bayvista on 2010-06-08
OK. So I did a stupid thing. I included 'delete' in my Rsync of '/'. Not very clever. When I tried to restore, I got a load of weird messages and an unusable system. So I have just done a clean install and upgrade.

I think these are the Rsync commands I need and would appreciate comments.

**Backup: sudo rsync -varuzP --exclude=/proc exclude=/media exclude=/mnt exclude=/sys / /media/storage/backupsys/ **

**Restore: sudo rsync -varuzP /media/storage/backupsys/ /**

---

