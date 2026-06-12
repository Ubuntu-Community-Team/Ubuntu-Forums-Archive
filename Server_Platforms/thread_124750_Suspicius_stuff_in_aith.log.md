---
title: "Suspicius stuff in aith.log"
date: 2006-02-02
forum: Server Platforms
---

### Post by krusbjorn on 2006-02-02
Hey all.

I recently checked my auth.log file and checked all the cronjobs and stuff like that. Everything seemed okay, except for this :
> 
Feb  2 07:30:02 localhost CRON[12221]: (pam_unix) session opened for user root by (uid=0)
Feb  2 07:30:02 localhost CRON[12223]: (pam_unix) session opened for user root by (uid=0)

This is run daily at that time, and is not explained by:

> # /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file.
# This file also has a username field, that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
47 6    * * 7   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
52 6    1 * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly
#


or:

> johannes@embla:~$ sudo crontab -u root -l
0,10,20,30,40,50 * * * * python /usr/bin/denyhosts.py -c /usr/share/denyhosts/denyhosts.cfg

I also did "crontab -u <user> -l" for all the users that are listed in the "Users and Groups" in Preferences->Administration, but none of them had any. 

Help me beat my paranoia :)
Oh, sorry for the typo in the title.

---

### Post by robert_pectol on 2006-02-02
cat /etc/cron.d/anacron

No worries!  :)

---

### Post by krusbjorn on 2006-02-02
[QUOTE=robert_pectol]cat /etc/cron.d/anacron

No worries!  :)[/QUOTE]

Ahh. Thanks a lot :D

---

### Post by krusbjorn on 2006-06-16
edited

---

