---
title: "Backup Server Data"
date: 2005-11-14
forum: Server Platforms
---

### Post by Rollo Tamasi on 2005-11-14
Hi lads, could someone recommend to me a free application that will backup the data that is contained in the WWW folder on a Ubuntu server automatically periodically.

Thanks

---

### Post by jaddison on 2005-11-14
[QUOTE=Rollo Tamasi]Hi lads, could someone recommend to me a free application that will backup the data that is contained in the WWW folder on a Ubuntu server automatically periodically.

Thanks[/QUOTE]

Using 'cron', 'tar' and a variety of other standard tools, you can create the backups periodically, easily enough.  Transferring them to another machine, that's where the fun begins.  There are a myriad of ways that you can accomplish this, but the most recent fad (and secure as well) is to use scp (secure copy), distributed with OpenSSH.  Basically, if you can ssh from your server machine to the machine you want to store the backups on, then this solution will work for you.

Read [this article on linux.com]("http://www.linux.com/guides/solrhe/Securing-Optimizing-Linux-RH-Edition-v1.3/chap29sec311.shtml") for information on using the 'scp' command.

Read [this article on NewsForge]("http://software.newsforge.com/software/04/03/15/211214.shtml") to set up passwordless access from one machine  to the other.  That said, keep in mind that there are security issues in doing this.  Make sure you set up the passwordless access in the direction that provides the smallest security risk (from backup machine to server or server to backup machine).

That should be a start for you.  Other methods include using NFS, Samba, rsync, ftp... you get the picture - there's a ton of choices.

I hope this helps somewhat,

---

### Post by LordHunter317 on 2005-11-14
Look into using rsync, or rdiff-backup, depending on your exact needs.

---

### Post by nagilum on 2005-11-14
A while ago I found the backup-tool 'flexbackup' which can do backups over the network (local storage is also possible of course). It creates simple tar-archives and supports incremental backups as well. Plus you wouldn't have to setup the remote stuff yourself then. Just run it via cron.

---

