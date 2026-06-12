---
title: "RM Permission denied ????"
date: 2010-07-01
forum: Server Platforms
---

### Post by cjleonard on 2010-07-01
> root@box:/mnt/Backup# ll
drwxrwxr-x  1 cjl    sambashare     4096 2010-07-01 18:56 test/

root@box:/mnt/Backup# rm -r test/
rm: cannot remove directory `test/My Music': Permission denied

Can anyone please explain to me why I cannot remove these stupid empty folders????

---

### Post by -humanaut- on 2010-07-01
It looks like your trying to remove a directory you could try with extreme caution sudo rm -rf /carefully

---

### Post by cjleonard on 2010-07-01
Tried.

> root@box:/mnt/Backup# rm -rf test/
rm: cannot remove directory `test/My Music': Permission denied
rm: cannot remove directory `test/My Pictures': Permission denied
rm: cannot remove directory `test/My Videos': Permission denied


---

### Post by cjleonard on 2010-07-01
WTF!!!

> cjl@box:/mnt/Backup$ chmod -R u+rwx test/
cjl@box:/mnt/Backup$ rm -rf test/
cjl@box:/mnt/Backup$ ll

It's gone! Appearently I had to give access to myself in order to remove the directory...?

---

