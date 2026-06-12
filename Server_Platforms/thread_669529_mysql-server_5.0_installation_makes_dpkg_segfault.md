---
title: "mysql-server 5.0 installation makes dpkg segfault"
date: 2008-01-16
forum: Server Platforms
---

### Post by phatalbert on 2008-01-16
I somehow mucked up my installation of mysql-server.

I'm running 7.10 and already had Apache, PHP, and Python installed and set up. So I ran
```
sudo apt-get install mysql-server
```
and everything goes well until dpkg segfaults.
```
Unpacking replacement mysql-server-5.0 ...
E: Sub-process /usr/bin/dpkg received a segmentation fault.
```

When I try to do it again it makes me run ```
dpkg --configure -a
``` first, and then after another install attempt gives me the same error.

And now when I try to remove everything related to mysql-server it also doesn't work, and I get this error.

```
dpkg: error processing mysql-server-5.0 (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 
dpkg: serious warning: files list file for package `mysql-server-5.0' missing, assuming package has no files currently installed.
135750 files and directories currently installed.)
Removing mysql-client-5.0 ...
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Can anyone help me out?

---

### Post by jingo811 on 2008-01-17
I'm not much of a troubleshooter I usually do things from scratch.  Here is how I made MySQL work.
[http://virtualseafarer.com/renaissance/desktop_lamp/index.html#intro](http://virtualseafarer.com/renaissance/desktop_lamp/index.html#intro)

---

