---
title: "No output from bash script within Crontab"
date: 2014-01-04
forum: Server Platforms
---

### Post by bdaboy22 on 2014-01-04
Hello,
I have a script that checks if the main DHCP server is alive and if not, will turn on DHCP locally to become the main DHCP server.  When I run the script from command line, it runs fine putting logs into /var/log/syslog.  When I enter the script into Crontab (sudo crontab -e), I only get the followning:
```
Jan  4 15:50:01 cdans001 CRON[10654]: (root) CMD (/home/yinyang/scripts/dhcp/autostart_dhcp.sh)
Jan  4 15:50:01 cdans001 CRON[10653]: (CRON) info (No MTA installed, discarding output)

```
The logs should look something like:
```
Jan  4 13:52:46 cdans001 autostart_dhcp: Site DHCP server (x.x.x.x) is available with (0%) packet loss.
Jan  4 13:52:46 cdans001 autostart_dhcp: No need for local DHCP server preemption...
Jan  4 13:52:46 cdans001 autostart_dhcp: Ensuring DHCP sever is not running locally.  Stopping DHCPD service..
```

Any ideas why my logging within the script does not run while in Crontab?
Thanks

**Environment:**
Ubuntu 12.04.3 with latest patches

**Script:**
```
# !/bin/bash
#
###############################################################################
# Created by: Brandt Winchell
# Date Modified: 01-03-2014
# Version: 1.0
# Script Function>
#       Monitor site connectivity and start DHCP-server, if needed
#       if the ping operation has >="$maxPloss" packet loss,
#       then DHCPD will be started
#       Once the condition is false, DHCPD will be stopped
###############################################################################
# Changelog:
#       1. n/a
###############################################################################
# Variables_Section
maxPloss=50 # Maximum percent packet loss before activation
siteDHCP=192.168.10.10 # Main DHCP server you want to check is operational
#
###############################################################################
# Function_Section
start_dhcp () {
        # Add any commands needed to get dhcpd started
        /etc/init.d/isc-dhcp-server start
}
#
stop_dhcp () {
        # Add any commands needed to stop dhcpd
        /etc/init.d/isc-dhcp-server stop
}
#
###############################################################################
# Action_Section
#
# Set $ploss to a value under $maxPloss incase
# ping is error or $ploss in not set
ploss=$(($maxPloss-1))
# now ping $sireDHCP for 10 seconds and count packet loss
ploss=$(ping -q -w10 "$siteDHCP" | grep -o "[0-9]*%" | tr -d %) > /dev/null 2>&1
#
if [ "$ploss" -ge "$maxPloss" ]; then
        logger -t autostart_dhcp "PROBLEM!!! Site DHCP server ($siteDHCP) is NOT available!!!"
        logger -t autostart_dhcp "Packet loss ($ploss) exceeded $maxPloss%, starting DCHP-server ..."
        start_dhcp
fi
#
        if [ "$ploss" -lt "$maxPloss" ]; then
                logger -t autostart_dhcp "Site DHCP server ($siteDHCP) is available with ($ploss%) packet loss."
                logger -t autostart_dhcp "No need for local DHCP server preemption..."
                logger -t autostart_dhcp "Ensuring DHCP sever is not running locally.  Stopping DHCPD service.."
                stop_dhcp
        fi
exit





```

**Script permissions:**
```
-rwxr-xr-x 1 root root 1.9K Jan  3 15:50 scripts/dhcp/autostart_dhcpd.sh
```

**Crontab:**
```
# Edit this file to introduce tasks to be run by cron.
# 
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
# 
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').# 
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
# 
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
# 
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
# 
# For more information see the manual pages of crontab(5) and cron(8)
# 
# m h  dom mon dow   command
#
# run ~/scripts/dhcp/autostart_dhcp.sh every 5 min
*/5 * * * * /home/user/scripts/dhcp/autostart_dhcp.sh

```

---

### Post by tomearp on 2014-01-04
Your crontab entry refers to autostart_dhcp.sh but your ls listing shows autostart_dhcpd.sh

---

### Post by bdaboy22 on 2014-01-04
Looking for the complex answer to a complicated problem but forgot about syntax.  I should have gotten Hooked on Typing for Christmas.

Works the way is was supposed to now.
Thanks

---

### Post by tomearp on 2014-01-04
No problem, we've all been there.

---

