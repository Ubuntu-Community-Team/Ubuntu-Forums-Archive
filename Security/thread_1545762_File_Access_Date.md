---
title: "File Access Date"
date: 2010-08-04
forum: Security
---

### Post by xMbx on 2010-08-04
Hallo,

i got a short question. When i replace a drive in a RAID 1 and then resync it, why does th file access date (all the files) on the drive from which i´m syncing not change ?

Shouldn´t the file access date always change when i copy a file ?
Are there ways to overgo this ? Thanks.

---

### Post by uRock on 2010-08-04
> **xMbx said:**
> Hallo,

i got a short question. When i replace a drive in a RAID 1 and then resync it, why does th file access date (all the files) on the drive from which i´m syncing not change ?

Shouldn´t the file access date always change when i copy a file ?
Are there ways to overgo this ? Thanks.
No, because when you copy a file, you are also copying the file's properties. If you really need to update the modification date, run this in a terminal. It will only change the modification date. ```
touch [filename]
```

---

### Post by xMbx on 2010-08-04
> **uRock said:**
> No, because when you copy a file, you are also copying the file's properties. If you really need to update the modification date, run this in a terminal. It will only change the modification date. ```
touch [filename]
```

Well, how to find out, if somebody copied a file ? I thought the access time would be changed then. Not talking about "modification" date.

Sample.

root@ubuntu:/home/user# stat log
  File: `log'
  Size: 322             Blocks: 8          IO Block: 4096   regular file
Device: 900h/2304d      Inode: 12484775    Links: 1
Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2010-08-04 15:35:28.000000000 +0200
Modify: 2010-06-21 01:28:51.000000000 +0200
Change: 2010-06-21 01:28:51.000000000 +0200

---

### Post by uRock on 2010-08-04
Hmm, I never checked that log before. I don't know anything about that, sorry.

---

