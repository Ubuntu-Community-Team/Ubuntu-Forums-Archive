---
title: "How to put any program in autstart"
date: 2009-01-15
forum: Server Platforms
---

### Post by rado3105 on 2009-01-15
Hi how to put/remove any program from autostart in ubuntu server.
Also I would like start some program, but with delay(e.g ntp-server), because sometime when there is lost internet connection, it takes a long time server to load cause it is waiting on NTP-server.

---

### Post by Krupski on 2009-01-15
> **rado3105 said:**
> Hi how to put/remove any program from autostart in ubuntu server.
Also I would like start some program, but with delay(e.g ntp-server), because sometime when there is lost internet connection, it takes a long time server to load cause it is waiting on NTP-server.

OK, first of all, here's a tiny, simple script that will check if your internet is working and, if it is, run whatever you like:

```

#!/bin/bash

# ping a server - give up after 3 seconds no matter what
/bin/ping -w3 www.ubuntu.com &> /dev/null

# if ping failed, exit now
if [ ${?} -ne 0 ]; then
{
  exit 0
}
fi

# start / run whatever you want here

```


Next... "autostart" stuff is usually put into "/etc/rc.local", but I prefer to do it differently.

Since cron has a "cron.hourly" and "cron daily" etc... directory to put scripts into, why not have a "cron.boot" which is run at boot time?

What I did was to edit crontab and then CREATE a new directory named "/etc/cron.boot" and put all my startup stuff in there.

First, the "modified" crontab file:

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


cut-n-paste that into your "/etc/crontab" file.

Next, create a new directory named "/etc/cron.boot".

Then, put all your bootup scripts into it.

Note that for the scripts to work, they must:

(1) Be set executable (chmod 0755)
(2) Must have "#!/bin/bash" as their FIRST line
(3) May not write to STDOUT nor require any input from STDIN


Another thing: scripts are run in lexical order. So, if you need / want to force one script to run before or after another, preface it's name with a suitable number or letter like this:

00-i-run-first
50-i-run-next
99-i-run-last-boo-hoo

or...

aa-i-run-first
zz-darn-im-last-again


Good luck! Hope this helps

-- Roger

---

### Post by rado3105 on 2009-01-15
Thanks a looot.

---

