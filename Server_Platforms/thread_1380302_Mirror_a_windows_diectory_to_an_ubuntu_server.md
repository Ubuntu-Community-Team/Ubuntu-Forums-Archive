---
title: "Mirror a windows diectory to an ubuntu server"
date: 2010-01-13
forum: Server Platforms
---

### Post by ljungbacka on 2010-01-13
Hi!
 
I am looking for a solution to mirror a directory on my companys computer that runs in windows to an external ubuntu server on the internet.
Can it be done? Help me with this, please.
I do not matter if it is trough ftp or something else. I just want i to work.
/L

---

### Post by noway2 on 2010-01-13
Maybe someone else will have a better idea or can elaborate on this method, but: Normally, one could use RSYNC for synchronizing between two systems.  But since you want to back up a Windows system, you will need an RSYNC utility that runs on that system.  There are a few of them available.  Try checking out cwrsync.

---

### Post by pirateghost on 2010-01-13
> **noway2 said:**
> Maybe someone else will have a better idea or can elaborate on this method, but: Normally, one could use RSYNC for synchronizing between two systems.  But since you want to back up a Windows system, you will need an RSYNC utility that runs on that system.  There are a few of them available.  Try checking out cwrsync.

i use backuppc (which uses RSYNC) to backup my music collection from my windows 2k8r2 server to a dedicated backuppc machine.  the utility i prefer for windows is deltacopy, as it provides an easy to use GUI without requiring any other packages to make it work.

---

### Post by ljungbacka on 2010-01-14
Having problems....
 
I want to run the rsync daemon on my VPS on an external ipaddress.
Then connect from my windows computers at home from deltacopy.
How do i specify differnt users in rsync?

---

### Post by BkkBonanza on 2010-01-14
Usually you don't want to run the rsync daemon. It's better to use ssh and let it start the rsync program automatically. This is just a change in how rsync is used on the Windows end. If you tell rsync to use the -e option and ssh, then it will not require the daemon on the server. This is more secure and doesn't require any additional user config other than what you have for ssh access.

---

### Post by ljungbacka on 2010-01-14
I am starting over now...
Installing backuppc and starting from the beginning..

---

### Post by ljungbacka on 2010-01-14
How do I specify the host if the host is in my apartment behind a router?
The server with backuppc has an own ip adress 74.xxx.xxx.xxx, my windows has 192.168.0.197 who is connected to a router that has an ip adress 210.xxx.xxx.xxx.
For a while I could connect to the server with deltacopy but not do backups. Then I did a rebuilt on my vps(74.xxx....) and now I can't connect anymore.....
-ARGH, I should be eating icecream and get really fat instead of running my brain through this mixer! ;)

---

### Post by ljungbacka on 2010-01-17
Got it!!
 
Followed this one:
[http://www.gaztronics.net/rsync.php](http://www.gaztronics.net/rsync.php)
 
 
Thank you!:popcorn:

---

