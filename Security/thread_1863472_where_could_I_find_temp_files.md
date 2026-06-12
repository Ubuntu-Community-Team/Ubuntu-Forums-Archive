---
title: "where could I find temp files"
date: 2011-10-17
forum: Security
---

### Post by ahmed.cnbd on 2011-10-17
where could I find temp files?

---

### Post by towheedm on 2011-10-17
/tmp

---

### Post by ahmed.cnbd on 2011-10-17
and how you can delete the locked files and folder

---

### Post by towheedm on 2011-10-17
You should not unless you are absolutely sure they are not temporary files related to your current session.  Removing temp files used by the current session can cause serious data loss and even system crash.

These files do not belong to you.  They are owned by different system users.  Want to know who owns the files?  From the terminal:
```

ls -l /tmp
```might give something like:
```
total 64
srwxr-xr-x 1 towheed towheed     0 2011-10-17 19:29 gedit.towheed.3544607005
drwx------ 4 towheed towheed  4096 2011-10-17 20:20 haze-JEnOJz
drwx------ 2 towheed towheed  4096 2011-10-17 19:29 keyring-0D45p1
drwx------ 2 root    root    16384 2011-02-22 20:10 lost+found
drwx------ 2 gdm     gdm      4096 2011-10-17 19:29 orbit-gdm
drwx------ 2 towheed towheed  4096 2011-10-17 21:00 orbit-towheed
drwx------ 2 towheed towheed  4096 2011-10-17 19:31 plugtmp
drwx------ 2 gdm     gdm      4096 2011-10-17 19:29 pulse-PKdhtXMmr18n
drwx------ 2 towheed towheed  4096 2011-10-17 19:29 pulse-x1S3kGHtSknC
drwxrwxrwx 2 towheed towheed  4096 2011-10-17 19:29 screenlets
drwx------ 2 towheed towheed  4096 2011-10-17 19:29 ssh-rLbifV1525
drwx------ 2 towheed towheed  4096 2011-10-17 19:29 virtual-towheed.RNcIwN
drwxrwxrwt 2 root    root     4096 2011-10-17 19:23 VMwareDnD
drwx------ 2 root    root     4096 2011-10-17 19:23 vmware-root
```Or if you use Nautilus, right-click on file, select properties and permissions.

---

### Post by lisati on 2011-10-17
> **ahmed.cnbd said:**
> and how you can delete the locked files and folder

Don't, unless you are absolutely sure you know what you are doing: there could be unintended side effects. 

I wouldn't sweat it too much about the contents of the /tmp directory, it is usually cleaned out at boot time.

---

