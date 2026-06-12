---
title: "mod_python seg fault with roundup"
date: 2006-03-10
forum: Server Platforms
---

### Post by Tom Bentley on 2006-03-10
I'm trying to install the issue tracker roundup using mod_python and mysql; I've basically been following the roundup installation notes. 

The problem I'm experiencing seems more to be with mod_python. When I visit the roundup page it's blank. When I look at apache's error.log I see:
"""
[Fri Mar 10 13:53:59 2006] [notice] mod_python: Creating 20 session mutexes based on 20 max processes and 0 max threads.
[Fri Mar 10 13:53:59 2006] [notice] Apache/2.0.54 (Ubuntu) DAV/2 SVN/1.2.0 mod_python/3.1.3 Python/2.4.2 PHP/4.4.0-3ubuntu1 configured -- resuming normal operations
[Fri Mar 10 13:54:37 2006] [notice] child pid 10147 exit signal Segmentation fault (11)
"""
I've got the following packages installed:
 python2.4-mysqldb
 libapache2-mod-python2.4
 python2.4
 mysql-server
 roundup

Anyone got any ideas? Thanks!

Tom

---

### Post by Plagued on 2006-11-06
This just happened to me today ... I was not on an Ubuntu box (alas, I am forced to use Red Hat at work), but I fixed by installing RoundUp through CGI rather than through mod_python. Seemed to solve all of my problems.

---

