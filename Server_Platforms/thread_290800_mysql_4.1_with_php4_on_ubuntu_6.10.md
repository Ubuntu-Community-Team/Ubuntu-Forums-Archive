---
title: "mysql 4.1 with php4 on ubuntu 6.10"
date: 2006-11-01
forum: Server Platforms
---

### Post by jsamort on 2006-11-01
Hi All,

I've just installed 6.10 and intend to use it as a testing server for web development, etc.  I am trying to mimic a production server as closely as possible, and am running into some headaches.  The production server uses PHP 4.4.4 and MySQL 4.0.27 (yes, very old, but beyond my control).  It appears that the closest I can get on Ubuntu is PHP 4.4.2 and MySQL 4.1.x.  Good enough, although if anyone could point me to the exact packages that would be great.  However, I can't seem to pull in php4-mysql without libmysqlclient15off (which is MySQL 5.0.x, correct?)  Could anyone lend me a hand with this?  I can install libmysqlclient14 (which I believe is the version I'm looking for), but it still seems to favour MySQL 5.  Any assistance would be greatly appreciated!

Best,
Scott

---

### Post by Joe_CoT on 2006-11-01
That can be done with:

```
sudo apt-get install php4 mysql-server-4.1 php4-mysql
```

FYI: The version of the mysql client does not matter; the only thing that matters is the server's version. If you're unsure, do '\s' from the mysql console after you install it, and you'll see it's indeed mysql 4. So even though the mysql5 client might be installed, you're fine. I run a ubuntu php4 mysql4 testbed setup like this.

---

### Post by Abhi Kalyan on 2006-11-04
Following on the Thread Mate!!!!

---

