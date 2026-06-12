---
title: "postfix and courier-maildrop"
date: 2005-02-09
forum: Server Platforms
---

### Post by zcy930 on 2005-02-09
I set /etc/postfix/mainn.cf
"virtua_-transport=maildrop" 
and master.cf
 "maildrop  unix  -       n       n       -       -       pipe
 flags=Rhu user=vmail argv=/usr/local/courier/bin/maildrop -V 10 -w 75 -d ${recipient}
".
When I telnet localhost 25 and input like "yumei@congyu.com",then return "Feb 10 12:39:02 localhost postfix/pipe[30169]: 224052F8F6: to=<yumei@congyu.com>, relay=maildrop, delay=20, status=bounced (user unknown. Command output: Invalid user specified. )".
What can I do?
Thanks very mach!

---

### Post by alfmatos on 2005-09-08
I also have the same problem.
Apparently courier-maildrop is compiled withou mysql support. So the users dont get authenticated correctly. I tried to compile from source, with mysql support, but now i get an error 0x0B from maildrop.

I reverted back to "virtual" instead of maildrop.

Does anyone know how to fix/get_it_working maildrop + postfix + mysql + virtual domains ?

---

### Post by fago on 2005-09-10
have a look at this docu from syscp:
[http://www.syscp.de/docs/installation/debian/sarge/extensionmaildrop/english](http://www.syscp.de/docs/installation/debian/sarge/extensionmaildrop/english)

the syscp configuration uses virtual users out of mysql.
if you get the 0x0B error, have a really close look at your maildropmysql.config file, just one additional space on the wrong place and maildrop says 0x0B...  :grin:

---

### Post by _AA_ on 2006-10-17
> **alfmatos said:**
> Does anyone know how to fix/get_it_working maildrop + postfix + mysql + virtual domains ?

Easy enough to do.

My question is how the hell do I get maildrop installed?
(AMD Athlon(tm) 64 X2 Dual Core Processor 4200+)


root@elvira:/etc/courier# aptitude search courier-maildrop
root@elvira:/etc/courier# aptitude search maildrop        
root@elvira:/etc/courier# 
root@elvira:/etc/courier# apt-get install courier-maildrop
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package courier-maildrop
root@elvira:/etc/courier# 
root@elvira:/etc/courier# apt-get install maildrop
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package maildrop
root@elvira:/etc/courier#

---

