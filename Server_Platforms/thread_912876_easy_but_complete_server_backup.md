---
title: "easy but complete server backup"
date: 2008-09-07
forum: Server Platforms
---

### Post by chris.davies on 2008-09-07
Hi,

I have a dedicated server and need to make a backup system that will backup absolutely everything on the server so that every setting can be restored when the backup is recovered.

What is the best way to do this? The server is from a hosting company and comes with Ubuntu and 'Matrix Linux' - i would like all of these settings to be preserved upon server restoration aswell.

---

### Post by Paul Weaver on 2008-09-07
To take a proper "forensic" backup you need
1) A snapshottable file system
or
2) Downtime

The problem is while your backup is running, things will get out of sync. Imagine you started backing up your database, which is spread over multiple files (mysql/myisam for example), it could get out of sync, which is why things like mysqlhotcopy exist -- basically lock the database while the copy is going on.

You probably don't have the ability to take a snapshot of your filesystem, but if you could reboot your machine from a live CD, and mount the hard drive read only, you can easilly use tar.

You could try using rsync, but I've not experience with backing up full systems (all our servers have instructions of how to rebuild, and most of them are automated via preseed files)

---

