---
title: "Restore server from tar archive"
date: 2010-09-15
forum: Server Platforms
---

### Post by dtech on 2010-09-15
Hi

Because of [this](http://ubuntuforums.org/showthread.php?t=1563467) problem I want to format the servers harddrives and then restore the server from a tar archive.

Is this safe or are there any problems I might run into? (except maybe that I have to change /etc/fstab)

---

### Post by CharlesA on 2010-09-15
I would suggest trying it in a VM first, just to make sure it'll work.

I can't think of any reason why it wouldn't work (outside is fstab)

---

### Post by dtech on 2010-09-16
But wouldn't it be unlikely to work in a VM because of the changed HW?

---

### Post by BkkBonanza on 2010-09-16
Did you ever check the hidden mounts? /home /media
That still seems like the most likely reason. Having data in there before you mounted new drives on top of them.

Also running an fsck to make sure no low level corruption is a good idea.

As far as recovering from a tar that shouldn't be a problem. There are certain paths that should be excluded. These come to mind,

--exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/dev

and mkdir those ones after. 

See here for more detailed info,
[https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

---

### Post by dtech on 2010-09-16
Ah thanks you, that answers my question.

I haven't found a good day to do downtime (yet), but before restoring I'll check /home and /media/sde1 for files on the wrong disks. Especially since those files would be removed on formatting.

---

### Post by psusi on 2010-09-16
Assuming that you created the tar properly and it has everything you need, then you just boot from a livecd, format, untar, then re-install grub and you're back up and running.

---

