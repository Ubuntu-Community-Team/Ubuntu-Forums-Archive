---
title: "trying to reset mysql root password"
date: 2010-10-14
forum: Server Platforms
---

### Post by tbobker on 2010-10-14
I have forgotton my root password for mysql.  I followed some instructions on a website and now I am not sure what i have done?

Basically, when I now try and start mysql I get a notification that i have converted the init script to an upstart. I dont know what this means.

> 
root@server:/home# /etc/init.d/mysql start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start mysql
mysql start/running, process 20301


Can anyone help me on this?

---

### Post by Ryan Dwyer on 2010-10-14
Running /etc/init.d/mysql start isn't the way to do it any more. The preferred method is service mysql start. However, the init.d method still works.

---

