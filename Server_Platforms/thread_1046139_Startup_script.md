---
title: "Startup script"
date: 2009-01-21
forum: Server Platforms
---

### Post by adamitj on 2009-01-21
Hi everybody.

This is a persistent question... I need to deploy a script in the Ubuntu server of my company which needs to run only once at every boot.

I'm not trying to create a "rc" service with update-rc.d, because it runs on almost two or three runlevels.

My goal is to execute this script only once, after the scripts of last runlevel execution. Is something like Micro$oft Window$ "autoexec.bat".

What is the best way to do it?

---

### Post by vanadium on 2009-01-21
The file /etc/rc.local is probably what you are looking for.

---

### Post by adamitj on 2009-01-21
Ok, but... what about that comment inside the file:

***"This script is executed at the end of each multiuser runlevel."***

I don't know how many levels are started at each boot... could it run more than once?

---

### Post by vanadium on 2009-01-21
You probably have not the right idea about runlevels. Commands in /etc/rc.local will be run once after every boot.

---

### Post by Krupski on 2009-01-21
> **adamitj said:**
> Hi everybody.

This is a persistent question... I need to deploy a script in the Ubuntu server of my company which needs to run only once at every boot.

I'm not trying to create a "rc" service with update-rc.d, because it runs on almost two or three runlevels.

My goal is to execute this script only once, after the scripts of last runlevel execution. Is something like Micro$oft Window$ "autoexec.bat".

What is the best way to do it?

The "rc.local" file is where one is "supposed" to place startup scripts, but I do it a different way.

Since the "cron" scheduler has directories for "hourly", "daily", etc... scheduled tasks, why not ADD to this common theme by having a "cron.boot" which runs at boot time?

If you like, you can do it. First, CREATE a new directory named "/etc/cron.boot". Copy the ".placeholder" file from one of the other cron.xxx directories into it.

Then, cut-n-paste the following and use it to REPLACE your "/etc/crontab" file:

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
# => NOTE! Scripts must be executable (i.e. chmod 0755)
#
# => NOTE! Scripts must not write to STDOUT, nor require input from STDIN.
#
#
# TIME FIELDS:
#
#  *  *  *  *  *  *  command to execute && next command...
#  -  -  -  -  -  -
#  |  |  |  |  |  |
#  |  |  |  |  |  +--- run command as 'user'
#  |  |  |  |  +------ day of week (0-7) (sunday=0 or 7)
#  |  |  |  +--------- month (1-12)
#  |  |  +------------ day of month (1-31)
#  |  +--------------- hour (0-23)
#  +------------------ minute (0-59)
#
#
# SPECIAL STRINGS:
#
#   special string  meaning / description
#   ==============  =====================
#
#   @reboot         Run once, at bootup.
#   @yearly         Run once a year  [0 0 1 1 *]
#   @annually       (same as @yearly)
#   @monthly        Run once a month [0 0 1 * *]
#   @weekly         Run once a week  [0 0 * * 0]
#   @daily          Run once a day   [0 0 * * *]
#   @midnight       (same as @daily)
#   @hourly         Run once an hour [0 * * * *]
#
#####################################################################

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# min   hour    day     month   dow     user    command(s)
# ===   ====    ===     =====   ===     ====    ==========

# at bootup
  @reboot                               root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.boot )

# hourly at hh:05
  05     *       *       *       *      root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.hourly )

# daily at 05:20
  20    05       *       *       *      root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )

# weekly at 04:35 (0=sunday)
  35    04       *       *      00      root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )

# monthly at 03:50
  50    03      01       *       *      root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )

```


It's the same old crontab file, with comments added and also the "cron.boot" facility added.

Now, just stick any script you like into "/etc/cron.boot" and it will run at startup.

The script must be set executable (chmod 0755) and should have "#!/bin/bash" as it's first line.

Hope this is of some help to you.

-- Roger

---

### Post by adamitj on 2009-01-25
For now rc.local is working fine and I can't use the server to do tests with cron since the server is under a heavy production environment.

I will deploy a new server with VirtualBox and try to create this cron.boot technic ASAP.

Thanks all.

---

### Post by muhammad680 on 2010-07-26
Guy I need some help as well
I installed the latest ver 10.04 on my computer- so after restarting my computer I was bought to cmd looking page asking for username and password-so I entered my username n password - after that nothing happens -can someone plz tell me wa to do?????

---

