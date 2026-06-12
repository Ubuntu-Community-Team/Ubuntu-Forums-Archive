---
title: "Cron error /etc/cron.d/php5"
date: 2009-04-20
forum: Server Platforms
---

### Post by botfish on 2009-04-20
Hi,

The root user of my newley setup server is sending me the following email. I haven't touched /etc/cron.d/php5, does anyone know why I am getting these errors?

> 
Subject: Cron <root@example.com>   [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 r

Message body: find: invalid argument `+' to `-cmin'


> 
$ cat /etc/cron.d/php5

# /etc/cron.d/php5: crontab fragment for php5
#  This purges session files older than X, where X is defined in seconds
#  as the largest value of session.gc_maxlifetime from all your php.ini
#  files, or 24 minutes if not defined.  See /usr/lib/php5/maxlifetime

# Look for and purge old sessions every 30 minutes
09,39 *     * * *     root   [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm


---

### Post by botfish on 2009-04-23
I think I was getting this error because my VPS did not have enough memory.

I upgraded my hosting plan and have not received any errors since.

---

