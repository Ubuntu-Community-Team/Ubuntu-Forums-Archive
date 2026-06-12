---
title: "Cron job is sending mail to *wrong* email  address."
date: 2013-08-17
forum: Server Platforms
---

### Post by Andre-D on 2013-08-17
Whever a cron job finishes, it tries to send result to wrong address, andre@odin2
I get this email from the system, because the error of mailing andre@odin2 is forwarded to correct email, we call it [email]adress@gmail.com[/email]

```

To: address@gmail.com
X-Failed-Recipients: andre@odin2
Subject: Delivery Status Notification (Failure)
......................

Delivery to the following recipient failed permanently:

     andre@odin2

Technical details of permanent failure:=20
DNS Error: Domain name not found
```

So the cron job is trying to email me at andre@odin2 (odin2 is the server the script runs on), ignoring aliases file..

I configured /etc/aliases

```
andre@ODIN2:~$ sudo cat /etc/aliases
# See man 5 aliases for format
postmaster:    root
andre:	address@gmail.com
root:	address@gmail.com

```



I've also  tried to add email to /etc/crontab

```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
MAILTO="address@gmail.com"

```



- how do I make the cron job output

---

### Post by Andre-D on 2013-08-17
also, I am using sSMPT , running newaliases returns: 

newaliases: Aliases are not used in sSMTP

---

