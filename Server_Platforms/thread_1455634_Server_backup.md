---
title: "Server backup"
date: 2010-04-16
forum: Server Platforms
---

### Post by bazman79 on 2010-04-16
Hi,

I have major problems with backup, and I can't seem to find a solution that works (a Google search produced too many results, and I am not sure how to proceed).

I have tried using rsync over ssh and rdiff-backup with very (too) limited success. The backups usually fail (although seem to work when started manually instead of by cron).

Setup (main server):
-----------------------------------------------------------------
Ubuntu 9.04 (64-bit)
3 directories being backed up.

directories have mostly very small files, and one directory contains around 50GB data (other two about a third of that each)

Connection: ADSL 2+

Backup server:
Also runs 9.04 and same version software (regularly updated) and same connection.
-----------------------------------------------------------------
(The servers are not at the same location and require Internet based backup)

Main server is used daily and networked with windows machines and macs. Backup server does nothing except contact main server and download data.

I have tried "fixing" the problems with suggestions found through Google (nice, ssh settings), with no success. The main issue seems to be the unreliable connection (although that seems to contradict that it usually works when started manually).

I would like backup software that keeps trying (not an infinite number of times, but at least a few times) to re-connect with the server if the connection fails and perhaps waits a bit between attempts, and at the same time doesn't start all over (e.g. rdiff-backup).

Is there any such solution/software (secure connection is also a requirement)?

It would also be nice if it was easy to setup, as this has already taken too much of my time.

Thank you in advance for your much appreciated advice.

---

### Post by bazman79 on 2010-05-05
Hi again,

Any ideas, perhaps a solution to rdiff-problem?

Thank you

---

### Post by geraldbrandt on 2010-05-05
I use backuppc with it's rsync protocol.  BackupPC is in the repos, and using the rsync helps with the bandwidth needed.

I've been using it for years.

Gerald

---

### Post by HermanAB on 2010-05-05
Howdy, 

I have found that using the rsync BW parameter to throttle it to a fraction of the supposed bandwidth of the link helps to keep it going on a bad network connection.

---

