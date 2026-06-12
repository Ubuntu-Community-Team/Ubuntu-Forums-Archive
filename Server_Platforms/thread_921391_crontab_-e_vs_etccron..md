---
title: "crontab -e vs /etc/cron.*"
date: 2008-09-16
forum: Server Platforms
---

### Post by rosv on 2008-09-16
Hi,
What is the difference between using crontab -e to add new cron jobs and manually putting shell scripts in, let's say /etc/cron.daily ?

thanx

---

### Post by Krupski on 2008-09-16
> **rosv said:**
> Hi,
What is the difference between using crontab -e to add new cron jobs and manually putting shell scripts in, let's say /etc/cron.daily ?

thanx

The stock Ubuntu crontab file runs scripts in "/etc/cron.daily", "/etc/cron.weekly", etc...

Using "crontab -e" is a means to EDIT the main /etc/crontab file.

Unlike most other crontab files, the Ubuntu version may be edited directly using "nano" or "vi" or whatever editor you like. You DO NOT need "crontab -e" to edit the file.

If you have something that needs to be run at an oddball time, you can put it into /etc/crontab, but normally it's better to put the scripts into the appropriate directory.

If you like, copy and paste this comment block into your crontab file - I find it very helpful - you may also:

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

```


Now, a few hints to save you tons of grief:

(1) The FIRST LINE of any script that you wish to run via crontab MUST be exactly this:

```

#!/bin/sh

```

...or this:

```

#!/bin/bash

```



(2) The execute permissions must be set for the file:

```

sudo chmod 0755 my-cron-script

```


Here's an example of one of my scripts that you can use as a template for yours:

```

root@storage:/etc/cron.boot# cat set-cpu-conservative
#!/bin/sh **[COLOR="Red"]<--- note the first line![/COLOR]**
############
# set cpu governor to conservative
############
/bin/echo conservative > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
/bin/echo conservative > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor

```

Obviously, the comment in red is not part of the script! :)

Notice that this script runs in a NEW directory that I made called "/etc/cron.boot". I run it at bootup by adding the following line to my "/etc/crontab" file:

```

# at bootup
# NOTE: a *new* directory: '/etc/cron.boot' has been created for this one!
  @reboot        root        test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.boot )

```

I think running things at boot time in this manner makes more sense (is more consistent) than putting stuff into "rc.local".

"/etc/cron.boot" is, in my opinion, a logical extension of the "hourly, daily, weekly, monthly" setup we currently have.


Good luck!

-- Roger

---

