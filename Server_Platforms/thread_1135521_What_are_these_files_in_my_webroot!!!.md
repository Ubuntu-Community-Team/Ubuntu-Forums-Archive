---
title: "What are these files in my webroot?!!!"
date: 2009-04-24
forum: Server Platforms
---

### Post by botfish on 2009-04-24
Hi,

My first Ubuntu VPS has been live on the internet for only two weeks.

Today I noticed the following directory tree in /var/www/

I have no idea how it got there or what it's for. I definitely have not installed anything like openwebmail, whatever that is. I have been careful with my sudo commands.

xxx.domain.com and yyy.domain.com are valid domain names on my server.

Does anyone recognise this directory structure so I can perhaps find out where it came from (and fix it)?

I have installed ssh, apache2, postfix, php, mysql, awstats, and phpmyadmin. 

> 
me@domain:/var/www$ ls -Rl ./cgi-bin
./cgi-bin:
total 2
drwxr-xr-x 3 root root 2048 2009-04-22 09:59 openwebmail

./cgi-bin/openwebmail:
total 2
drwxr-xr-x 3 root root 2048 2009-04-22 09:59 etc

./cgi-bin/openwebmail/etc:
total 2
drwxr-xr-x 2 root root 2048 2009-04-22 09:59 sites.conf

./cgi-bin/openwebmail/etc/sites.conf:
total 4
-rw-r--r-- 1 root root 135 2009-04-22 09:59 xxx.domain.com
-rw-r--r-- 1 root root 138 2009-04-22 09:59 yyy.domain.com

[email]me@domain:/var/www/cgi-bin/openwebmail/etc/sites.conf[/email]$ cat xxx.domain.com
mailspooldir	/var/spool/vmail/xxx.domain.com/mail
auth_withdomain	yes
auth_module	auth_pop3_hspc.pl
virtusertable /dev/null

[email]me@domain:/var/www/cgi-bin/openwebmail/etc/sites.conf[/email]$ cat yyy.domain.com
mailspooldir	/var/spool/vmail/yyy.domain.com/mail
auth_withdomain	yes
auth_module	auth_pop3_hspc.pl
virtusertable /dev/null


---

### Post by leifharmsen on 2011-03-31
Bump.

I have the same problem.  This mysterious directory tree in my web root at /var/www/ which gets re-created given some time (how much I'm not sure yet) after I delete it.  The mysterious directory tree starts from  /var/www/cgi-bin/openwebmail and keeps going down.   I don't have openwebmail installed, at least I never installed it and can't find any evidence of it - when I use apt-get remove to remove it the response is that there's no such program installed.  There must be something with root permissions putting these there.  Deleting them makes no difference to how my web or email servers function. 

 :confused:  I thought computers having a mind of their own was a Microsoft/Apple kind of thing.  There's no evidence that my system has been compromised, unless this is it.  Anyone had a problem with this?  I've googled my face off and found only this one post with no solution.

---

