---
title: "Where is mysql5 ?"
date: 2005-11-16
forum: Server Platforms
---

### Post by dbee on 2005-11-16
I'm sure I saw someone post a link here for a mysql5 package in the multiverse somewhere. Unfortunately though, I don't seem to be able to track it down ...

Firstly, does it exist ?
If so, where ?

---

### Post by grendelkhan on 2005-11-16
According to the backports forum, mysql5 isn't going to make it into any breezy repositories (except for the backports maybe).  I've looked high and low for deb's and I can't find them anywhere.

---

### Post by dudus on 2005-11-22
I wrote a how to compile mysql5 [here]("http://www.ubuntuforums.org/showthread.php?t=93725&page=1&pp=10").

---

### Post by markc on 2005-12-14
One way to install an uptodate LAMP system on breezy is to drop in the dotdeb.org debs for apache2-mpm-prefork libapache2-mod-php5 php5-mysqli mysql-server-5.0 mysql-client-5.0 using a mirror from [http://dotdeb.org/mirrors](http://dotdeb.org/mirrors). Probably not ideal but "works for me" (amd64) until Ubuntu offer the same level of LAMP support.

---

