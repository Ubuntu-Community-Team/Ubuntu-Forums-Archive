---
title: "Access to zpool denied"
date: 2011-02-08
forum: Server Platforms
---

### Post by MG2R on 2011-02-08
I've set up Ubuntu Server 10.04 LTS 64-bit. I've set up zfs-fuse and created a zpool named 'data' which contains two 2TB WDC Green HDD's in raid1 (mirror). I've set up an NFS server to share the pool. So far so good.

But now, I want to write to the pool. It has occurred to me that I need to be root to do that. On the server, this is not a problem (sudo cp...) but on my laptop I can not copy anything to the pool because I'm not a superuser.

How do I get past this problem?

---

### Post by samosamo on 2011-02-08
You can set your nfs options via "zfs sharenfs" the same way you would on any NFS server.  You're looking for "root squash" option which looks something like this:


```
zfs sharenfs=rw,root=192.168.1.100 mypool/blahblah
```

Read more here: [http://robinbowes.com/article.php/20080411002106299](http://robinbowes.com/article.php/20080411002106299)

---

