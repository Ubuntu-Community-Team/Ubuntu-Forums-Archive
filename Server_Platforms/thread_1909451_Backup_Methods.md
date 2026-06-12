---
title: "Backup Methods"
date: 2012-01-15
forum: Server Platforms
---

### Post by DanHorniblow on 2012-01-15
Hi, I am looking to backup all of the following to a different server:

[LIST]
[*]Courier Email Accounts
[*]Users Web Directories in "/var/www/"
[*]All MySQL Databases
[/LIST]

Any suggestions?

Cheers Dan

---

### Post by collisionystm on 2012-01-15
> **DanHorniblow said:**
> Hi, I am looking to backup all of the following to a different server:

[LIST]
[*]Courier Email Accounts
[*]Users Web Directories in "/var/www/"
[*]All MySQL Databases
[/LIST]

Any suggestions?

Cheers Dan

clone the server? or just back it up?

With information like that, I suggest you use rsnapshot and set your backup to 1 week or more.

Make a script that stops SQL and then runs rsnapshot, then starts SQL again. Place it in your crontab.

Rsnapshot will backup over ssh using the rsync protocol. It works fantastically.

---

### Post by DanHorniblow on 2012-01-15
Hi, thanks for your reply.

My VPS is backed up weekly by my ISP "HeartInternet" via snapshots anyway, so that is a good disaster recovery solution.

But I would like a simple little solution that could FTP or SSH all my users email /web directories and maybe even make a SQL dump of all databases.

This is becasue a few of my users have acidentally deleted email, files ect, and restoring small files like that is not worth reverting the whole server to a previous snapshot.

Does anyone know of any applications that can do this?

Cheers Dan

---

### Post by collisionystm on 2012-01-16
> **DanHorniblow said:**
> Hi, thanks for your reply.

My VPS is backed up weekly by my ISP "HeartInternet" via snapshots anyway, so that is a good disaster recovery solution.

But I would like a simple little solution that could FTP or SSH all my users email /web directories and maybe even make a SQL dump of all databases.

This is becasue a few of my users have acidentally deleted email, files ect, and restoring small files like that is not worth reverting the whole server to a previous snapshot.

Does anyone know of any applications that can do this?

Cheers Dan


Maybe I confused you somehow. This is exactly what Rsnapshot does.

It does not perform system images. It just lets you backup whatever you specify and allow you to choose how long you want backups to occur.

If you want to backup /home/user/files and be able to go back a minute, an hour, week, weeks, a year, years....etc..... whatever. Have fun

---

