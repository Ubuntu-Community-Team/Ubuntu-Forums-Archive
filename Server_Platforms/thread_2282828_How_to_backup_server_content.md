---
title: "How to backup server content?"
date: 2015-06-17
forum: Server Platforms
---

### Post by dtommy79 on 2015-06-17
Hi,

I have a vps at DO.

How can I save the content of my server (files, database) to my computer? Is there a way to do it from the command line?

Thanks

---

### Post by TheFu on 2015-06-17
Check the "server" subforum for many answers to this question.  You'll need a solution that quiesces the DB (or dumps it to a compressed file first), then you can use any backup method you prefer. There must be 50 choices for "how" and a nearly infinite choice of "what" to backup for your specific situation.  I don't know how to do this without doing it from the shell. Servers don't have GUIs.

Most VPS vendors provide a built-in backup solution. Usually it isn't very efficient, but it does work. The few backups that I've seen from my webhost just makes an entire tgz file of everything under my account. Meh.

If you have access to the hostOS and it is running LVM, btrfs or zfs, there are some other options.

What will work best for you will depend on the programs running on the VPS. There could be any of 50K different programs running, but these are generally split into 2 types - static files and data bases.  Then the DBs are split into groups by the DBMS used. If backing up postgres using mariaDB or sqlite techniques won't work.  See how we are stuck since enough data hasn't been provided yet?

So, please go do some reading in the Server subforum about this stuff, then provide some basic information about your sw stack - OS, version, applications, DBs, etc .... if you'd like more help.

Right now, the only valid answer is "it depends."

---

### Post by sandyd on 2015-06-17
Moved to *server platforms*

---

### Post by nerdtron on 2015-06-17
How big are your backups?

For mysql, I think a mysqldump during off-peak hours will be enough, then just compress the dump file. For your file, tar the whole folder. Then download the files to your home computer since you have ssh access. This is one way to backup. It really depends on what you want to backup, how big the data and how often you want to backup.

---

### Post by CharlesA on 2015-06-17
> **nerdtron said:**
> How big are your backups?

For mysql, I think a mysqldump during off-peak hours will be enough, then just compress the dump file. For your file, tar the whole folder. Then download the files to your home computer since you have ssh access. This is one way to backup. It really depends on what you want to backup, how big the data and how often you want to backup.

I do that on my owncloud server and then transfer it via rsync. Might not be the best way (due to table locking), but it works for me.

The OP didn't really mention what they were running other than a database, but we might be able to give better advice if they said what they were running.

---

