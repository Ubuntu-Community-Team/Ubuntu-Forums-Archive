---
title: "Replace /usr/bin, /usr/sbin and /sbin files with the original files"
date: 2009-12-30
forum: Security
---

### Post by flit on 2009-12-30
Hello,

Is there a way to replace /usr/bin, /usr/sbin and /sbin files with the original files in case one gets corrupted? And is there a way to protect these files from corruption? Thanks in advance.

--------------------
Sorry for the icon, this is the fourth time I posted and I made a mistake now I can't change it

---

### Post by cariboo on 2009-12-30
It is far easier to keep the important files in your home directory backed up daily, than it is to worry about corrupted files in /usr and /sbin. After all a reinstall only takes 20 minutes.

If you want to do backups of those directories, there are many backup packages in the repositories. Have a look at SBackup, it is fairly easy to setup.

---

