---
title: "CRON problem with bash script"
date: 2012-07-06
forum: Server Platforms
---

### Post by Scripting22 on 2012-07-06
Hello,

I've created a script to check my server for inactivity. When I execute the script manually, it works fine, but when I want to schedule it in CRON it does not run?

I've changed the variable

SHELL=/bin/sh to SHELL=/bin/bash

All paths in the script are absolute and it's placed in the root's crontab because some commands need root priviliges.

However, nothing happens and nothing is written to the log. Am I missing something here?

---

### Post by Toz on 2012-07-06
Anything in syslog?
```
cat /var/log/syslog | grep CRON
```

Would you be willing to post your script so we could have a closer look at it?

---

### Post by rubylaser on 2012-07-06
Also, what is your actual crontab entry for that item?

---

### Post by Scripting22 on 2012-07-06
> **Toz said:**
> Anything in syslog?
```
cat /var/log/syslog | grep CRON
```

Would you be willing to post your script so we could have a closer look at it?

Sure, it's an script made by somebody else which I altered for my own purpose. I've changed the location where the log will be created, the treshold to 100 packets, and the end command from suspend to RAM, to shutdown. Corresponding echo messages I've changed also.

If I run this script every 30 minutes through CRON, will it shut down the system when it should be? The network activity exists merely of one ssh connection. When this connection isn't used, are there more than 100 packets per half an hour generated?

```
#!/bin/bash                                                                                                         
#                                                                                                                   
# This script is scheduled in CRON.  It will run every 30 minutes
# and check for network inactivity.  It compares the RX and TX packets
# from 30 minutes ago to detect if they significantly increased.
# If they haven't, it will force the system to shut down.
#

log=/home/wouter/scripts/poweroff_log

# Extract the RX/TX
rx=`/sbin/ifconfig eth0 | grep -m 1 RX | cut -d: -f2 | sed 's/ //g' | sed 's/errors//g'`
tx=`/sbin/ifconfig eth0 | grep -m 1 TX | cut -d: -f2 | sed 's/ //g' | sed 's/errors//g'`

#Write Date to log
date >> $log
echo "Current Values" >> $log
echo "rx: "$rx >> $log
echo "tx: "$tx >> $log

# Check if RX/TX Files Exist
if [ -f ~/scripts/idle/rx ] || [ -f ~scripts/idle/tx ]; then
        p_rx=`cat ~/scripts/idle/rx`  ## store previous rx value in p_rx
        p_tx=`cat ~/scripts/idle/tx`  ## store previous tx value in p_tx

        echo "Previous Values" >> $log
        echo "p_rx: "$p_rx >> $log
        echo "t_rx: "$p_tx >> $log

        echo $rx > ~/Scripts/idle/rx    ## Write packets to RX file
        echo $tx > ~/Scripts/idle/tx    ## Write packets to TX file

        # Calculate threshold limit
        t_rx=`expr $p_rx + 100`
        t_tx=`expr $p_tx + 100`

        echo "Threshold Values" >> $log
        echo "t_rx: "$t_rx >> $log
        echo "t_tx: "$t_tx >> $log
        echo " " >> $log

        if [ $rx -le $t_rx ] || [ $tx -le $t_tx ]; then  ## If network packets have not changed that much
                echo "Powering off ..." >> $log
                echo " " >> $log
                rm ~/scripts/idle/rx
                rm ~/scripts/idle/tx
                sudo /sbin/shutdown -h now  ## Shut down system
        fi

#Check if RX/TX Files Doesn't Exist
else
        echo $rx > ~/scripts/idle/rx ## Write packets to file
        echo $tx > ~/scripts/idle/tx
        echo " " >> $log
fi
```

The entry I've made in crontab is:

```
1 * * * * /home/wouter/scripts/poweroff.sh
```

For testing purpose I set the time to 1 minute. When it's working correctly I change this to 30 minutes.

---

### Post by Toz on 2012-07-06
> **Scripting22 said:**
> The entry I've made in crontab is:

```
1 * * * * /home/wouter/scripts/poweroff.sh
```

Your crontab entry will only run the script on the 1st minute of every hour of every day, etc. If you want it to run every minute, you should use:
```
* * * * * /home/wouter/scripts/poweroff.sh
```

Every 30 minutes would be:
```
*/30 * * * * /home/wouter/scripts/poweroff.sh
```

---

### Post by Scripting22 on 2012-07-06
Aah! At least I get some output in /var/log/syslog from CRON, it sais:

```
Jul  6 14:02:01 Ubuntu-webserver CRON[1561]: (root) CMD (/home/wouter/scripts/poweroff/poweroff.sh)
Jul  6 14:02:01 Ubuntu-webserver CRON[1560]: (CRON) info (No MTA installed, discarding output)
Jul  6 14:03:01 Ubuntu-webserver CRON[1577]: (root) CMD (/home/wouter/scripts/poweroff/poweroff.sh)
Jul  6 14:03:01 Ubuntu-webserver CRON[1576]: (CRON) info (No MTA installed, discarding output)
```

And yes, the location of the script has changed a little, because I made some changes in the file structure. But that shouldn't be a problem.

Edit: Okay, the cronjob is running every minute now, but there's still a problem. When I run the script manual it generates more output than when cron runs. Below you can see the difference, any clue what causes this?

Edit 2: All solved. Path names were relative and due to that some output wasn't written to the logfile. Changed the path names and everything is working like a charm! Thanks for support!

```
vr jul  6 14:21:01 CEST 2012
Current Values
rx: 3344
tx: 3161
 
vr jul  6 14:22:01 CEST 2012
Current Values
rx: 3347
tx: 3161
 
vr jul  6 14:22:34 CEST 2012
Current Values
rx: 3623
tx: 3403
Previous Values
p_rx: 938
t_rx: 511
Threshold Values
t_rx: 1038
t_tx: 611
 
vr jul  6 14:22:35 CEST 2012
Current Values
rx: 3628
tx: 3406
Previous Values
p_rx: 3623
t_rx: 3403
Threshold Values
t_rx: 3723
t_tx: 3503
 
Powering off ...
```

---

### Post by LHammonds on 2012-07-06
I'm glad you got it figured out.

If you include a path along with the shell environment variables, it will cover some of the relative paths used in scripts.

Here are some of my notes regarding crontab schedules:

The crontab schedule can be edited directly by typing "crontab -e" but  that can be a bit dangerous.  It would be safer to edit a file and then  load that file into the schedule. This will allow backups of the  schedule to be made.  If there is ever a problem with the schedule, it  can be re-loaded with a known-good schedule or at least back to the way  it was before the last change.  This requires the person doing the  editing to always work with a copy of the schedule 1st.

Here is an example crontab scheduling file for the root user:

/var/scripts/data/crontab.root
```

########################################
# Name: Crontab Schedule for root user
# Author: LHammonds
############# Update Log ###############
# 2012-05-20 - LTH - Created schedule
########################################

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# Crontab SYNTAX:
# minute(0-59) hour(0-23) day-of-month(1-31) month(1-12) day-of-week(0-6) command-to-execute
#
# Adjust the time clock every hour
#
0 * * * * /usr/sbin/ntpdate ntp.ubuntu.com > /dev/null 2>&1
#
# Backup MySQL Server
#
0 23 * * * /var/scripts/prod/mysql-backup.sh > /dev/null 2>&1
#
# Backup MySQL Database On Demand
#
0-59 * * * * /var/scripts/prod/mysql-db-backup.sh > /dev/null 2>&1
#
# Daily checks for available space
#
0 1 * * * /var/scripts/prod/check-storage.sh root 500 100 > /dev/null 2>&1
15 1 * * * /var/scripts/prod/check-storage.sh home 100 50 > /dev/null 2>&1
30 1 * * * /var/scripts/prod/check-storage.sh tmp 100 50 > /dev/null 2>&1
45 1 * * * /var/scripts/prod/check-storage.sh usr 100 50 > /dev/null 2>&1
0 2 * * * /var/scripts/prod/check-storage.sh var 100 50 > /dev/null 2>&1
15 2 * * * /var/scripts/prod/check-storage.sh srv 100 50 > /dev/null 2>&1
30 2 * * * /var/scripts/prod/check-storage.sh opt 100 50 > /dev/null 2>&1
45 2 * * * /var/scripts/prod/check-storage.sh bak 100 50 > /dev/null 2>&1
#
# Daily software upgrade check
#
0 3 * * * /var/scripts/prod/apt-upgrade.sh > /dev/null 2>&1

```Once the file is created, make sure appropriate permissions are set by typing the following:
```

chown root:root /var/scripts/data/crontab.root
chmod 0600 /var/scripts/data/crontab.root

```To enable the root schedule using this file, type the following:

```
crontab -u root /var/scripts/data/crontab.root
```To disable the root schedule, type the following:
```

touch /tmp/deleteme
crontab -u root /tmp/deleteme
rm /tmp/deleteme

```If you need to modify the schedule, make a backup copy 1st.   For example:

```

cp /var/scripts/data/crontab.root /var/scripts/data/2012-11-28-crontab.root
vi /var/scripts/data/crontab.root (make your changes)
crontab -u root /var/scripts/data/crontab.root

```

---

### Post by Scripting22 on 2012-07-07
@ LHammonds:

Thanks for your explanation and the attached scheduling example file for cron. It's clearifies some things for me.

I've one remaining question however. At the beginning of the file there's the line:

```
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
```

I don't understand how to intepret this line. I can't make any sense of it.. How should I read this?

---

### Post by LHammonds on 2012-07-09
> **Scripting22 said:**
> Thanks for your explanation and the attached scheduling example file for cron. It's clearifies some things for me.You're welcome.
 
> **Scripting22 said:**
> I've one remaining question however. At the beginning of the file there's the line:
 
```
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
```
 
I don't understand how to intepret this line. I can't make any sense of it.. How should I read this?
 It sets the path where Linux will search for programs if you do not specify the full path.
 
For example, if you type "ls", it will find the "ls" command as long as it is in one of the folders in the search path.
 
Having it set at the top of the cron schedule, any scripts that are called will have the path set (so you don't have to set it inside each script).  This allows you to get away without having to type the full path for every command.  It is still preferred to use the full URL in order to make sure you are calling the correct file (if there are more than one) as well as saving a bit of processing time.
 
LHammonds

---

