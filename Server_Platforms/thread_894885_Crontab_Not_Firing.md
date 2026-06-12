---
title: "Crontab Not Firing"
date: 2008-08-19
forum: Server Platforms
---

### Post by Spiny Norman on 2008-08-19
I have several lamp servers on 6.06 and successfully set up their crontabs to do a daily db check, a dump and compression of the same. I then do an SSH backup pull also on cron to another 6.06 lamp. All multipe crons calling a shell script each, sat under a commented out line describing the functionality.
I decided to set myself up an 8.04 lamp to test and did the same (crontab -e) to setup the cron identically. For some reason this does not fire. Is there a reason for this? Perhaps a change to 8.04? I have checked my work meticulously but can't figure this one out? 
Thanks

P.S. All of my scripts will run on C/L on 8.04 but not on cron.

---

### Post by Ximbiot on 2008-08-19
Is your cron daemon running?  If so, could you post the output of `crontab -l' for the broken user?

---

### Post by fwre01 on 2008-08-19
check your crontab has ```
 MAILTO="" 
``` on the top line of the crontab file. If this isnt here, the crontab wont run, (a little gotcha iv tripped over before!)

---

### Post by Spiny Norman on 2008-08-19
Results of Crontab -l

root@SpareR1:~# crontab -l
MAILTO=""
# m h  dom mon dow   command
01 1 * * * . DbDailyCheck.sh
15 1 * * * . SqlDump.sh
30 1 * * * . DumpComp.sh
45 1 * * * . DumpCompDOW.sh

root@SpareR1:~#

I added the MAILTO="" as suggested and no difference
This is the listings in root

root@SpareR1:~# ls -l
total 16
-rw-r--r-- 1 root root 122 2008-08-17 21:51 DbDailyCheck.sh
-rw-r--r-- 1 root root 176 2008-08-14 20:54 DumpCompDOW.sh
-rw-r--r-- 1 root root 148 2008-04-19 16:03 DumpComp.sh
-rw-r--r-- 1 root root 192 2008-04-06 15:09 SqlDump.sh

I reckon I need to make them executable. I will try this as soon as I get to a location with open ports.

Thanks for your prompt replies

---

### Post by Spiny Norman on 2008-09-15
Yes chmod was required also

1. Added as first line of each script " #! bin/bash " without quotes.

2. used absolute path so crontab entry example would be

01 2 * * * /root/DbDailyCheck.sh

---

### Post by Krupski on 2008-09-15
> **Spiny Norman said:**
> Yes chmod was required also

1. Added as first line of each script " #! bin/bash " without quotes.

2. used absolute path so crontab entry example would be

01 2 * * * /root/DbDailyCheck.sh

It would be handy if little tidbits like this were documented... not buried in some obscure MAN page, but right INSIDE the appropriate file!

For example, here's MY crontab file:

```

#####################################################################
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the 'crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.
#
# => NOTE! Scripts to be placed in /etc/cron.daily, weekly, etc
#          must have '#!/bin/sh' or '#!/bin/bash' as their FIRST
#          line or else they will not work!
#
#
# TIME FIELDS:
#
#       *  *  *  *  *  *  command to execute && next command...
#       -  -  -  -  -  -
#       |  |  |  |  |  |
#       |  |  |  |  |  +--- run command as 'user'
#       |  |  |  |  +------ day of week (0-7) (Sunday=0 or 7)
#       |  |  |  +--------- month (1-12)
#       |  |  +------------ day of month (1-31)
#       |  +--------------- hour (0-23)
#       +------------------ minute (0-59)
#
#
# SPECIAL STRINGS:
#
#       special string  meaning / description
#       ==============  =====================
#
#       @reboot         Run once, at bootup.
#       @yearly         Run once a year  [0 0 1 1 *]
#       @annually       (same as @yearly)
#       @monthly        Run once a month [0 0 1 * *]
#       @weekly         Run once a week  [0 0 * * 0]
#       @daily          Run once a day   [0 0 * * *]
#       @midnight       (same as @daily)
#       @hourly         Run once an hour [0 * * * *]
#
#####################################################################

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# min   hour    day     month   dow     user    command(s)
# ===   ====    ===     =====   ===     ====    ==========

# at bootup
# NOTE: a *new* directory: '/etc/cron.boot' has been created for this one!
  @reboot                               root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.boot )

# hourly at nn15
  15     *       *       *       *      root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.hourly )

# daily at 0525
  25    05       *       *       *      root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )

# weekly at 0435
  35    04       *       *      00      root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )

# monthly at 0345
  45    03      01       *       *      root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )

```


Oh how many hours of grief I would have been spared if a few lines of comment had been in /etc/crontab by default...

---

### Post by directcharitycontribution on 2008-09-29
pathetic, isn't he.

---

### Post by Krupski on 2008-09-29
> **directcharitycontribution said:**
> pathetic, isn't he.

What does that mean? :confused:

---

### Post by directcharitycontribution on 2008-10-03
> **Krupski said:**
> What does that mean? :confused: you know english?

---

### Post by Krupski on 2008-10-03
> **directcharitycontribution said:**
> you know english?

Yes indeed I do. I was wondering who you were calling "pathetic"?

I don't see how name calling helps someone with their computer questions...

---

