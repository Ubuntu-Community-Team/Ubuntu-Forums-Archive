---
title: "Qmail Svscanboot hanging and defunct errors"
date: 2011-06-22
forum: Server Platforms
---

### Post by sentinelace on 2011-06-22
root@UBUNTU-SERVER:~# ps -e | grep svscan
5462 ? 00:00:00 svscanboot <defunct>
5556 ? 00:05:35 svscan <defunct>
6688 ? 00:00:00 svscanboot <defunct>
25961 pts/1 00:00:00 svscanboot
25963 pts/1 00:00:00 svscan
 
 
 
I can get mailflow if I keep a terminal open and manually run svscanboot. The above is showing more than one process. Why? Why won't it stop? Been working for 3 years straight with no issues. Any ideas?

---

### Post by sentinelace on 2011-06-23
It appears the parent process is hanging these up.  My is that the parent is init so I have to reboot hopefully to clear these up.  Time to upgrade while I am at it.

---

