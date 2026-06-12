---
title: "mysqld goes 100% cpu load and freeze"
date: 2010-08-15
forum: Server Platforms
---

### Post by elianto on 2010-08-15
Hello to all,
as soon as mysqld starts it goes 100% cpu. I can stop it,  there is no mysql_safe running, and I ran
         mysqlcheck -A -a -c -o -g --auto-repair -u root -p
all is ok, syslog shows nothing important but I can't login to any account with
mysql client it just sits there, using php it times out. 
I don't know how to fix the urgent situation...         

Looks like it has been started after a release update to 9.10 or 10.4 (i did it in a row)
I don't know if this bug is related                                         
[https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.0/+bug/105457/](https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.0/+bug/105457/)

please help :confused:

>Release:       mysql-5.1.41-3ubuntu12.6 ((Ubuntu))
and stock config files

---

### Post by tyleruk on 2010-08-16
Have you tired backing up your database and re-installing MySQL?

---

### Post by elianto on 2010-08-16
actually I found out that is postfix causing all the cpu load. unfortunatly mail logs says little

Apr 27 21:10:35 ubuntu amavis[19998]: (19998-07) (!!)TROUBLE in process_request: Error writing a SMTP response to the socket: Broken pipe at (eval 83) line 874, <GEN134> line 57.
Apr 29 10:39:03 mail postfix/trivial-rewrite[372]: fatal: mysql:/etc/postfix/mysql_virtual_domains_maps.cf(0,lock|fold_fix): table lookup problem

several lines like this^^^ up to yesterday
this should be caused by problems with chroot/mysql but I've tried several things and this message doesn't appear anymore however I still have this 100%cpu mysql load as soon as postfix starts.

---

