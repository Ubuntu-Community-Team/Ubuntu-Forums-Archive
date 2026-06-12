---
title: "debian-sys-maint@localhost - mysql error"
date: 2006-07-30
forum: Server Platforms
---

### Post by califdon on 2006-07-30
I'm installing Ubuntu 6.06 server on a new box, to replace an existing (old) server.  I've stumbled through most everything, but in the process of transferring all my (old) MySQL data from the old server, I stupidly copied over the mysql control tables and now, on boot-up, I get an access denied error for "debian-sys-maint@localhost".  I realize what happened, but what's the best way to recover?  Is there a way to recover the mysql data file from the installation CDROM and save it under a different name, then join it with the mysql control tables?  Any help will be appreciated.

Don

---

### Post by chaag on 2006-07-30
I must be misunderstanding your installation process, but why not remove and reinstall mysql. Then use mysqldump to xfer just the database(s) you need? You'll likely still have to mess with the mysql.users table (granting privileges, etc) but this should avoid the issues with the users debian sets up.

---

### Post by califdon on 2006-07-30
Thanks, chaag.  That's probably what I'll have to do.  I was hoping there might be a quicker way, since I have quite a few MySQL databases and MySQL users.  I wrongly thought it would be an easy way to just copy the whole mysql directory over, but I learned my lesson.

---

### Post by chaag on 2006-07-30
One more thought:

Do the remove (re) install. Use mysqldump to dump all databases. Then hand edit the resulting file to remove the debian specific users. I _suspect_ that would work, apologies in advance if I force you into another reinstall.

(if only _everything_ were truly file based ;-)

---

### Post by califdon on 2006-07-30
Hey! It was easier than I thought! I uninstalled, then reinstalled MySQL right from the Ubuntu CDROM, checked the user table in mysql...and Lo and Behold! it retained all the previous users and added the Debian user!  So I didn't need to mysqldump or anything--everything was left untouched.  I did a little pruning and reset my mysql root password, and that's all I had to do!  Sometimes things work like you want them to.  :D

---

