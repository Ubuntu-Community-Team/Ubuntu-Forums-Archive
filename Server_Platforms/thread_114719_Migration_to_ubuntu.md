---
title: "Migration to ubuntu?"
date: 2006-01-09
forum: Server Platforms
---

### Post by drakkan on 2006-01-09
Hi, 

I'm evaluating ubuntu for my servers. Actually I have about 30 gentoo servers, and some debian and openbsd firewall. Ubuntu is a debian updated so I can use binary package and updated software so it seems very interesting however there are some things I don't like:

1) suppose you want to build a mail server a my basic setup is postfix-amavisd-clamav-spamassassin-postfixadmin, if I chose to install mysql-4.1 ubuntu install all libmysqlclient from libmysqlclient10.so (mysql-3.23) as dependencies for postfix-mysql to libmysqlclient14.so (mysql-4.1), this isn't a very clean solution and I don't think postfix developers test mysql lookup with that old version

2) why I cannot choice the logger daemon and the cron daemon directly during installation process ?

3) minimal installation install a lot of useless package such as  ppp, evms, etc. I'd like to have a very minimal (not more than 100MB) base system and then add what I need. For example I want lvm2 only if I choice to use lvm.

4) often I have to use apt-source because ubuntu package have't options I needed, for example cyrus-sasl is compiled without authdaemond support, postfix without vda patch and so on

5) you include gfs in your patched kernel version this means you have tested and support GFS?

6) I have several system with emc storage, I use multipath-tools instead of commercial powerpath to manage multipathing, your multipath-tools package is very old, have you ever tested this software?

thanks and sorry for my poor english,
drakkan

---

