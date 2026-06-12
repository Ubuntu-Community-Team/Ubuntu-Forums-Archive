---
title: "Recover from a bz2 image"
date: 2009-02-23
forum: Server Platforms
---

### Post by damo12 on 2009-02-23
I run a server for a small business and as part of backup plan I run the following script:

```
tar czf /media/backup/serversystem.bz2 --exclude=/proc --exclude=/lost+found --exclude=/backup.tar.bz2 --exclude=/mnt --exclude=/media --exclude=/sys /
```

This seems to work fine and as far a s I know produces a tarball of the server system.  I hope I never have to use it but should the worse happen and the server fails, how do I restore it from the tarball image?

---

### Post by yoyoned on 2009-02-23
tar jxf /media/backup/serversystem.bz2

---

### Post by hictio on 2009-02-23
Is there any special reason you are creating such a (big) backup file, instead of making backups of the things that actually change on the system?
Have you heard of [Rsnapshot](http://www.rsnapshot.org/)?

I'm really curious :D

---

### Post by damo12 on 2009-02-24
Thanks for the help, the backup is only 282Mb which I didn't think was too big.

I have never heard of Rsnapshot but I will certainly have a look at it.

Thanks again for the advice.

---

