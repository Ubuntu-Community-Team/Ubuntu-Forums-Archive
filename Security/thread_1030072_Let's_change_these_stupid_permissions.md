---
title: "Let's change these stupid permissions"
date: 2009-01-04
forum: Security
---

### Post by g0rd99 on 2009-01-04
I'm at my witts end at this one. It comes up over and over. cp, mv, rsync, etc.  bring up errors like:
cp: failed to preserve ownership for `../temp/tbsync/0/0/5ea52b79-3d58-4deb-b564-b13495dd078e.note': Operation not permitted

This was even though I was root. sudo su. I've struggled, and struggled with this, and am about to say goodbye to Ubuntu if not Linux. The device, /dev/sdh1 is owned by root:disk. When it's mounted, it becomes root:root. Nothing will changed any permissions on it at all.

Please. If someone can help. Lets get the paranoia out of Ubuntu and make it useable. The way it is, it certainly is not.

---

### Post by jpkotta on 2009-01-04
It's not an error, it's a warning.

I will guess that it is a vfat filesystem.  There is absolutely no way to do proper Unix permissions on a vfat fs.  Linux does the next best thing by assigning the same permissions to every file on the fs.  The only way around this is to format the disk with a Unix filesystem.

To make sure that this is indeed the problem, post the output of this command:
```
mount
```

---

### Post by koenn on 2009-01-04
It's not the permissions that are stupid. 
Here's an example of what can happen if you get rid of the permissions.
[http://ubuntuforums.org/showthread.php?t=1028598](http://ubuntuforums.org/showthread.php?t=1028598)
[http://ubuntuforums.org/showthread.php?t=1028592](http://ubuntuforums.org/showthread.php?t=1028592)

---

### Post by scorp123 on 2009-01-04
> **koenn said:**
> It's not the permissions that are stupid. 
Here's an example of what can happen if you get rid of the permissions.
[http://ubuntuforums.org/showthread.php?t=1028598](http://ubuntuforums.org/showthread.php?t=1028598)
[http://ubuntuforums.org/showthread.php?t=1028592](http://ubuntuforums.org/showthread.php?t=1028592) +1 !!!!

As for those threads above .... OMFG ](*,)  ...

---

### Post by hyper_ch on 2009-01-05
you call them only stupid because you don't understand them (yet). Put effort into understanding them and you'll be much happier :)

---

