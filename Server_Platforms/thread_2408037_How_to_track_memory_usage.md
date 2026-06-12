---
title: "How to track memory usage"
date: 2018-12-12
forum: Server Platforms
---

### Post by fernandoch on 2018-12-12
Hello,

I have a server with 2GB of RAM and from time to time it freezes.

I guess it is because of the RAM as I am running many websites on there and fail2ban.

Is there a way to monitor the memory usage and to check what is the problem.

Thanks

---

### Post by LHammonds on 2018-12-12
There are a great many ways to monitor servers.  I use Nagios because I monitor over 100 servers.

However, if this is the only server you have, you can just type "free" at the prompt and it will show you how much RAM is being consumed and how much swap space is being used.

You typically do not want any swap space being used.  If you find that it is being used a lot, that is an indicator that you need more RAM.  The swap space is only there for emergency use but you can increase the amount of swap space available.

I usually install a utility called "htop" that I can run and let it continuously show me the performance in realtime whenever I want to look at what's going on right now.

Since the system is crashing, you might want to check the system logs.   Maybe even run some diagnostics to make sure the RAM and HD are working  properly.

If you want to see what the server is doing over a long period of time, you could write a simple Bash script to capture the data you are interested in and append it to a log file...maybe once per hour or every 15 minutes or even every minute if you like.

**EDIT:**

I did a search and found [a script](https://stackoverflow.com/questions/1868210/how-to-log-the-memory-consumption-on-linux) by klaus se and modified it to be more suitable for being run via crontab schedule.

Create the script:
```
mkdir -p /var/scripts
touch /var/scripts/logmem.sh
chmod 755 /var/scripts/logmem.sh
vi /var/scripts/logmem.sh
```

```

#!/bin/bash
## Original idea: klaus se
## Modified by: LHammonds
DateString=$(date '+%Y-%m-%d')
LogFile = "/var/log/logmem-${DateString}.log"
if [ ! -f ${LogFile} ]; then
  ## Add header row.
  echo "time       $(free -m | grep total | sed -E 's/^    (.*)/\1/g')" > ${LogFile}
fi
echo "$(date '+%H:%M:%S') $(free -m | grep Mem: | sed 's/Mem://g')" >> ${LogFile}

```

You can then schedule that script to run via crontab.

Every minute:
```
* * * * * /var/scripts/logmem.sh
```

Every 5 minutes:
```
*/5 * * * * /var/scripts/logmem.sh
```

Every hour on the hour:
```
0 * * * * /var/scripts/logmem.sh
```

Example output /var/log/logmem-2018-12-12.log:
```

time                 total        used        free      shared  buff/cache   available
20:00:00             488          95          38           1         354         368
20:05:00             488          95          38           1         354         368
20:10:00             488          95          37           1         354         368
20:15:00             488          95          36           1         354         368
20:20:00             488          95          35           1         354         368

```

Example output /var/log/logmem-2018-12-13.log:
```

time                 total        used        free      shared  buff/cache   available
20:01:00             488          95          38           1         354         368
20:02:00             488          95          38           1         354         368
20:03:00             488          95          38           1         354         368
20:04:00             488          95          38           1         354         368
20:05:00             488          95          37           1         354         368

```

You could also create another script that runs at the same time and shows the top processes that is consuming CPU or RAM or HD activity, etc.

LHammonds

---

### Post by fernandoch on 2018-12-13
Oh great, thanks for this, I will try it.

By the way with Nagios, do you get memory consumption or just if a service is up or down?

---

### Post by LHammonds on 2018-12-13
Nagios has a port listener but doesn't do anything until the Nagios server asks for an update on whatever it is you are monitoring.  You can use built-in checks for the basics or code your own such as making a script to query a web server and see if it responds and is connected to it's DB.  Nagios returns data you can analyze/graph...not just up or down.  This is all configurable.

Nagios isn't the only monitoring system out there but it is free and suited my purpose for monitoring Linux/Windows servers and network equipment.  Network guys that manage Cisco switches and configs will likely prefer SolarWinds but that costs a license for each device added.  Can get rather expensive quickly if you wanted to monitor everything (not just switches).

Took me about a month to figure out Nagios by myself and get setup but now that I have it documented, I can roll it out anywhere pretty quick.  You can use basic configs for each device but you really need to fine-tune it for the specific service if unique.  It is also a great way to track usage over time which helps you plan for future hardware requirements.  For example, I have an imaging system that grows by 50GB each month consistently for the last 2 years.  I can easily predict how much I will at least need for each year I am planning out in the future...assuming no additional loads are added.

LHammonds

---

### Post by fernandoch on 2018-12-13
Still not clear if nagios can monitor memory.

---

### Post by LHammonds on 2018-12-14
> **fernandoch said:**
> Still not clear if nagios can monitor memory.
You can configure Nagios to monitor anything you write a script for.  So yes, it can monitor memory usage and even email you alerts when thresholds are passed...warnings or alerts.

Here is a list of built-in programs/checks that can be utilized immediately:

```

# ls /usr/local/nagios/libexec
check_apt               check_imap      check_real
check_apt_motd.sh       check_ircd      check_rpc
check_breeze            check_jabber    check_sensors
check_by_ssh            check_load      check_simap
check_clamd             check_log       check_smtp
check_cluster           check_mailq     check_snmp_IBM_Bladecenter.pl
check_dhcp              check_mrtg      check_spop
check_dig               check_mrtgtraf  check_ssh
check_disk              check_nagios    check_ssmtp
check_disk_by_size.sh   check_nntp      check_swap
check_disk_smb          check_nntps     check_tcp
check_dns               check_nrpe      check_time
check_dummy             check_nt        check_udp
check_esxi_hardware.py  check_ntp       check_ups
check_file_age          check_ntp_peer  check_uptime
check_flexlm            check_ntp_time  check_users
check_ftp               check_nwstat    check_wave
check_http              check_oracle    eventhandlers
check_icmp              check_overcr    negate
check_ide_smart         check_ping      urlize
check_ifoperstatus      check_pop       utils.pm
check_ifstatus          check_procs     utils.sh

```


Here is an image of Nagios in my testing lab that is showing me a list of "problem" services that need my attention:
[IMG]https://i.imgur.com/W6KePsk.jpg[/IMG]

Here is an image of the services I am monitoring on my database server:
[IMG]https://i.imgur.com/wAHdXe6.jpg[/IMG]

Here is an image of an availability report showing "memory usage" over a period of time.  It shows a steady green because the server has been online and memory has never been "overused" but you can mouse-over specific times and see how much memory was available (total) and how much was free at the specific point in time.
[IMG]https://i.imgur.com/yxDf7hp.jpg[/IMG]

Nagios defaults to writing its collected data to log files but you could modify it to write to a database and then make custom queries against that if you have specific reporting needs.

Nagios is not something you setup for just a couple of servers though.  It takes time to get it running which includes designing how it will works.  It is not something you install and walk away from.  It is a shell that you have to mold into something useful.  But once you are finished setting it up, you do not need to "mess with" any more configurations.  You just look at the monitoring web front-end to keep an eye on what needs your attention.

LHammonds

---

