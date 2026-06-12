---
title: "Network backup server"
date: 2011-03-17
forum: Server Platforms
---

### Post by root911911 on 2011-03-17
Hi 
I am looking for a way to setup a network backup server, so clients can backup their files over the Internet to the server (windows, Apple and Ubuntu clients).

Is there any one that could point me in the right direction?

Thanks
Root

---

### Post by falko on 2011-03-17
You could try BackupPC: [http://backuppc.sourceforge.net/](http://backuppc.sourceforge.net/)

---

### Post by Lars Noodén on 2011-03-17
> **root911911 said:**
> Hi 
I am looking for a way to setup a network backup server, so clients can backup their files over the Internet to the server (windows, Apple and Ubuntu clients)...


[bacula](http://packages.ubuntu.com/maverick/bacula) is one option.  radmind might be another.

---

### Post by hawk2010 on 2011-03-18
Or you can use Duplicity :-)

---

### Post by SeijiSensei on 2011-03-18
Do you need to manage these backups centrally on an automated basis, or are you just looking to set up a server where people can dump files they wish to back up?  

If the latter is all you need, you can accomplish this by running Samba on an Ubuntu server.  If you create accounts on the box for each user, then they'd get private access to their home directories.  A Windows user, for instance, could map drive H: to \\server\username; on Ubuntu you'd use smb://server/username.  If you want to insure good security between users, make sure that all the /home/username directories have 0700 permissions making them totally private to the user in question.

---

