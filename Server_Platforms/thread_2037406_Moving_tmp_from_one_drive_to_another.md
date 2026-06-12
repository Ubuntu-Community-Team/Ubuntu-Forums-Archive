---
title: "Moving /tmp from one drive to another"
date: 2012-08-04
forum: Server Platforms
---

### Post by schworak on 2012-08-04
URGENT HELP

My boot drive has a /tmp folder on it and I have been mounting a secondary small drive in place of the /tmp folder using /etc/fstab

I want to do away with that and just use the /tmp folder that is on the boot disk. Is this possible/recommended or should I keep it on a separate partition?????

My first attempt to use the boot drive was to simply comment out the mount point in the /etc/fstab file but then mysql couldn't start because it couldn't create temp files. As soon as I uncommented the mount line and remounted mysql started working again.

So is it not possible to use the actual /tmp folder? Does it have to be its own partition?

---

### Post by schworak on 2012-08-04
OH MY GOSH!

I am such an idiot some times. I forgot to change the permissions on the /tmp folder. It was one quick "chmod" and it is working.

---

### Post by steeldriver on 2012-08-04
what did you change the permissions to btw? they should be 1777 (rather than plain 777) I think

```
$ ls -ld /tmp
drwxrwxrwt 10 root root 4096 Aug  4 14:17 /tmp
```

---

