---
title: "Request: mysql-query-browser 1.1.7"
date: 2005-05-22
forum: Ubuntu Backports
---

### Post by mat on 2005-05-22
Ubuntu's mysql-query-browser is 1.1.4 (it's in universe/misc).
[Debian unstable has 1.1.7](http://packages.debian.org/unstable/misc/mysql-query-browser). It's not the latest upstream's version, but it seems to be working much better (I had numerous crashes with 1.1.4)

It's divided into 2 packages (mysql-query-browser and mysql-query-browser-common), but this shouldn't be too hard to backport.

---

### Post by jdong on 2005-05-22
Uploaded.

---

### Post by mat on 2005-05-22
Thanks for the quick reaction! 

It works better for me than the 1.1.4 package in universe. I did found some crashes in this version too, but it seems to be upstream bugs, and at least I can browse tables and such, which I couldn't do properly with the 1.1.4 package.

I'll do more tests tomorrow.

---

