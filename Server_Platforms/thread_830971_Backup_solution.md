---
title: "Backup solution?"
date: 2008-06-16
forum: Server Platforms
---

### Post by derdud on 2008-06-16
I'm running 8.04 server (no GUI) and I'm having a hard time finding the best backup solution for my server. My agency uses Symantec BackupExec 10d to backup all of our other servers (which are all Windows machines... bleh) to a tape drive. In any case, it doesn't work with the Ubuntu server (I suspect because it's Linux and not Windows).

The most important things on this particular server are the MySQL databases and the SVN repositories.

So, with that said:

1. Is there a way to get Backup Exec to be able to back up this system?

2. Failing that, what other solutions are most recommended for backing up a Ubuntu machine?

---

### Post by windependence on 2008-06-16
[www.amanda.org](www.amanda.org)

[www.bacula.org](www.bacula.org)


-Tim

---

### Post by TheGameAh on 2008-06-16
Another way is to backup your data to a windows server, which Backupexec would see.  Not great, but it does work.

---

### Post by erwall on 2008-06-16
You could also backup your data to a samba share on your server.  Then configure Backup Exec to backup that share, which it should see/access fine.  For MySQL db's you could schedule a dump to said share.

---

### Post by erwall on 2008-06-16
You could also backup your data to a folder on your server that's shared w/samba.  Then configure Backup Exec to backup that share, which it should see/access fine.  For MySQL db's you could schedule a dump to said share and back it up w/BE.

Sorry for the double post!

---

### Post by tuproxy on 2008-06-16
As someone mentioned in the second post, [Bacula]("http://www.bacula.org/en/") is a great option.  It is the program we use at my company on all the servers and networks we support.  It has gotten great review by Linux journal as well.

---

### Post by windependence on 2008-06-17
> **tuproxy said:**
> As someone mentioned in the second post, [Bacula]("http://www.bacula.org/en/") is a great option.  It is the program we use at my company on all the servers and networks we support.  It has gotten great review by Linux journal as well.

And both Amanda and Bacula will work with Windows and are OSS and free!

It's true you could backup your files to a windows machine or a SAMBA share and then use Backupexec, but why pay the license fees?

-Tim

---

### Post by Bosk22 on 2008-06-25
Currently we run BackupExec 11 to backup our windows and linux system.

Previously we where using BackupExec 10d - You just need to purchase and install the BackupExec agent for Linux and then your Linux systems will show up on the BackupExec Tape Engine.

Backups and restores after that are a piece of cake!!!!

Regards

Bosk

---

