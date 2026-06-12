---
title: "syslog  daily restart time"
date: 2011-07-13
forum: Server Platforms
---

### Post by Alan87i on 2011-07-13
Is there a way to force the syslog ie /var/log/messages to restart at say 1:00 am instead of 7:55 or so each morning?

---

### Post by Doug S on 2011-07-13
The file /etc/crontab contains the time of day for execution of the daily stuff. (It also contains day of month and time for monthly stuff, and the minute of the hour for hourly stuff.) Make a copy of the original file and then edit as desired, including "sudo" prefix. I do not know if you will need to restart the cron daemon for the changes to take effect (try it and let us know).

---

### Post by Alan87i on 2011-07-14
The daily was set 25 6 *** so 6:25 
When I look at the message log the first line is usually 7:3x the log was restarted. 
I changed the 6 to a 4 and restarted the computer. Will find out tomorrow if it changed anything.

---

### Post by Alan87i on 2011-07-15
That did nothing so far , it's 6:20 now and the log has not restarted.

---

### Post by Doug S on 2011-07-15
Yes, your posting yesterday saying that the daily time was 06:25, but the file time was 7:3X gave a hint that it might not work as expected. Just as a sanity check, I went to my old server machine and made a similar change to crontab and watched for the results. In my case, the messages log file only rotates weekly, so I used the daily rotated syslog file as the reference log file. My edited crontab file (where the time. 7:05, was selected to be a few minutes after my edit):
```
 
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file.
# This file also has a username field, that none of the other crontabs do.
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
# m h dom mon dow user  command
17 *    * * *   root    run-parts --report /etc/cron.hourly
05 7    * * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
47 6    * * 7   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
52 6    1 * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly
#
 

``` 
My syslog files (and you can see the time change of the closed file (the 1 minute delay is because the computer is very very very old and slow and it took a minute to get to this point in the daily list of stuff to do)):
```

-rw-r----- 1 root adm   335 2011-07-15 07:17 /var/log/syslog
-rw-r----- 1 root adm 18526 2011-07-15 07:06 /var/log/syslog.0
-rw-r----- 1 root adm  1093 2011-07-15 06:26 /var/log/syslog.1.gz
-rw-r----- 1 root adm  1058 2011-07-14 06:26 /var/log/syslog.2.gz
-rw-r----- 1 root adm  1067 2011-07-13 06:26 /var/log/syslog.3.gz
-rw-r----- 1 root adm  1060 2011-07-12 06:26 /var/log/syslog.4.gz
-rw-r----- 1 root adm  1193 2011-07-11 06:26 /var/log/syslog.5.gz
-rw-r----- 1 root adm  1078 2011-07-10 06:26 /var/log/syslog.6.gz
 

```
So, I don't know what is different in your system such that this didn't work for you. Maybe have a look at the /var/log/messages section of /etc/logrotate.d/rsyslog file and/or for something that overides the defaults. I do not have any other suggestions, hopefully someone else will chime in and help further.

---

