---
title: "MD5's in Ubuntu"
date: 2005-10-04
forum: Server Platforms
---

### Post by kurtis on 2005-10-04
I'm new to ubuntu and I'm just learning my way around package management in ubuntu.  One thing I made use of when using redhat and gentoo based distros was the fact that all installed packages had corresponding md5 checksums so if something on the system  changed it wasn't hard to track down.  This was useful for security purposes and regular sys admin type work.  A user on irc pointed me to debsums for ubuntu and when I ran it, it said that quite a few packages didn't have md5 information which concerned me.  So I'm wondering if this is in fact true that only certain packages have md5 information and if so I guess why this is so .

---

### Post by kurtis on 2005-10-04
Ok, on this one I found a solution to my problem.  With debsums you can go and generate any missing md5sums for your system, however it would be nice if this was done automatically for every package installed.  Anyone know why some have md5s and others don't and if there is a way to enable this to happend automatically?

---

