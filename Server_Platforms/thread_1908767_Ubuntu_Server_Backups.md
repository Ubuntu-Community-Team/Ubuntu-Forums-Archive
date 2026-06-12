---
title: "Ubuntu Server Backups"
date: 2012-01-14
forum: Server Platforms
---

### Post by bubylou on 2012-01-14
Im looking for a way to backup some files on my server to another Windows 7 machine and keep in sync so that my data can be protected. Does anyone know what i should use to accomplish this. i have looked at bacula, backuppc, and script. Im just looking for a simple way to protect the data on my server. and raid is not an option at this point but would be awesome.

---

### Post by volkswagner on 2012-01-14
First, RAID is _not_ a backup solution.


You can create a shared folder on your Win7 machine.  Use SAMBA client on your server to [mount the share]("https://help.ubuntu.com/community/MountWindowsSharesPermanently").  Then use [rsync]("https://help.ubuntu.com/community/rsync") (from the server) to sync the Server files to your Win7 machine.

---

### Post by bubylou on 2012-01-14
thanks for the advice i will definitely take a look at rsync, sounds just like what im looking for. and i know raid isn't a backup but its serves the same purpose which is protection against hard drive failure since this is a very old machine.

---

