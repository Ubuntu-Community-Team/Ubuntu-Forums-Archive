---
title: "Backuppc Over FTP?"
date: 2007-08-27
forum: Server Platforms
---

### Post by teeds on 2007-08-27
Long time lurker first time poster.

I am currently running backuppc on my ubuntu server box to back up my vista ([DeltaCopy]("http://www.aboutmyip.com/AboutMyXApp/DeltaCopy.jsp")) and ubuntu systems. I would like to use it to back up a hosted webserver however no shell access rules out ssh rsync tunnel.  The only way I can think of is over ftp.  

Any options/thoughts?

---

### Post by wirelessmonkey on 2007-08-27
It's my understanding, though I'm not absolutely certain, that backuppc cannot use a normal ftp connection.

EDIT:  [http://backuppc.sourceforge.net/faq/roadMap.html](http://backuppc.sourceforge.net/faq/roadMap.html)    tells us that FTP is not yet a valid method, but it is on the roadmap!


Good Luck!

---

### Post by teeds on 2007-08-27
Yea read that, was thinking there maybe a way through tar but didn't hold much hope.

Thanks for the reply

---

### Post by Mebus on 2008-04-27
Well, you can backup FTP-Servers, by mounting your FTP-site using curlftps into a users local filesystem.

Simply add another user for instance ftpbackup. Mount your FTP-Site into for instance /mnt/ftpsite.

Add another Host to Backuppc, for instance "ftpsite". Set "ClientNameAlias" to Localhost. Add the authorized_keys2 file to ftpbackups .ssh dir. Let Backuppc login as "ftpbackup". Now you can backup your FTP-site. :rolleyes:

Mebus

---

