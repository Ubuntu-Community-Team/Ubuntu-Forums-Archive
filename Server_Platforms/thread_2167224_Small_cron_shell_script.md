---
title: "Small cron shell script"
date: 2013-08-12
forum: Server Platforms
---

### Post by alfirdaous on 2013-08-12
Hello everybody,

I am trying to test a small script based on cron.daily:

```

find /home/alfirdaous/www/ -type d -exec chmod 751 {} ";"

```

I put this code in a file named chmod, directory is /etc/cron.daily:

```

-rwxr-xr-x 1 root root 527 Aug 12 02:34 chmod

```

Do I need to add something else so the script will run daily??

Thx in advance

---

### Post by ian-weisser on 2013-08-13
> **alfirdaous said:**
> Do I need to add something else so the script will run daily??

No. 
If your script is really in the /etc/cron.daily directory, then cron will try to run it daily as root.
If your system is turned off, anacron will run all cron.daily jobs at next startup.
This assumes that your script is correct, and does locate target(s) to modify.

---

### Post by alfirdaous on 2013-08-13
I took this line and tried it in a command line on the same directory (/etc/cron.daily):

```

find /home/alfirdaous/www/ -type d -exec chmod 751 {} ";"

```

I even tested it as running chmod from commad line:

```

./chmod

```

It works, but it does not work as a cron

---

### Post by hawkmage on 2013-08-13
You may want to use the full path the the find command.  Depending on how cron is setup you may not have a full path defined.

---

### Post by kpothi on 2013-08-13
@alfirdaous

As @hawkmage mentioned, you may include the full path to `find` command. Alternatively, you may set up $PATH value in crontab entry. By default, crontab doesn't know the value of $PATH.

---

### Post by alfirdaous on 2013-08-17
I added #! /bin/bash  on the top of the file, and now it works :)

---

### Post by LHammonds on 2013-08-21
To ensure everything works as expected, I add a search path inside my cron schedule.  If you don't specify the full path to each and every executable used in the script, it might fail...so instead, I use the path variable inside the cron schedule to keep my scripts more flexible.

Here is an example of my crontab schedule for root:

```

########################################
# Name: Crontab Schedule for root user
# Author: LHammonds
############# Update Log ###############
# 2012-05-20 - LTH - Created schedule
########################################

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow command
#
# Adjust the time clock
#
0 1-23 * * * /usr/sbin/ntpdate ntp.ubuntu.com > /dev/null 2>&1
#
# Upgrade the system
#
0 3 * * * /var/scripts/prod/apt-upgrade.sh > /dev/null 2>&1

```

All of my scripts also specify what shell they use.  Here is an example:

```

#!/bin/bash
#############################################
## Name          : apt-upgrade.sh
## Version       : 1.1
## Date          : 2013-01-08
## Author        : LHammonds
## Purpose       : Keep system updated (rather than use unattended-upgrades)
## Compatibility : Verified on Ubuntu Server 12.04.2 LTS
## Requirements  : Sendemail, run as root
## Run Frequency : Recommend once per day.
## Parameters    : None
## Exit Codes    :
##    0 = Success
##    1 = ERROR: Lock file detected.
################ CHANGE LOG #################
## DATE       WHO WHAT WAS CHANGED
## ---------- --- ----------------------------
## 2012-06-01 LTH Created script.
#############################################

## Import standard variables and functions. ##
source /var/scripts/common/standard.conf

etc.

```

---

