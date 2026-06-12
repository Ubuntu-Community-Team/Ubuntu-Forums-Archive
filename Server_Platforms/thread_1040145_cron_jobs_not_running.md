---
title: "cron jobs not running"
date: 2009-01-15
forum: Server Platforms
---

### Post by Emjx on 2009-01-15
am having difficulty trying to get cron jobs to run. I am running 8.04 and have several cron directories:
[INDENT]/etc/cron.hourly
/etc/cron.daily
/etc/cron.weekly
/etc/cron.monthly[/INDENT]
In the cron.hourly directory I have a simple script (below) that is just supposed to "touch" a file in another directory (the thought behind this being just to test that cron was running.

Script: /etc/cron.hourly/crontest.sh
```
#!/bin/bash

touch /home/administrator/testtouch.txt


```
The permissions of the files are:
crontest.sh - 755
testtouch.txt - 777

If I run the crontest.sh script manually (sh /etc/cron.hourly/crontest.sh), it does work and "touch" the testtouch.txt file so I don't think the issue is permissions.

My crontab file is as follows:
```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
30 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#


```

If anyone could shed any light onto what I am doing wrong or am missing, any help would be appreciated!!

---

### Post by RealPSL on 2009-01-16
You probably want to start your investigation in /var/log/syslog which logs when the jobs are run from cron. This might give you some kind of clue on why it is not working.

---

### Post by sunset_studies on 2009-01-18
what is the output of 

ls -la /etc/cron.hourly/crontest.sh

?

---

