---
title: "Apache2 log files not rotating"
date: 2010-03-29
forum: Server Platforms
---

### Post by osx on 2010-03-29
I can't get my apache2 log files to rotate on an Ubuntu 8.04 64-bit server install.

Does anybody know of logrotate creates an error log somewhere by default?

Here's my /etc/logrotate.d/apache2 file if someone has any insight if I am doing something wrong.

Thanks.

/var/log/apache2/*.log /var/log/apache2/portal/*.log {
	weekly
	missingok
	rotate 52
	nocompress
	notifempty
	create 640 root adm
	sharedscripts
	postrotate
		if [ -f "`. /etc/apache2/envvars ; echo ${APACHE_PID_FILE:-/var/run/apache2.pid}`" ]; then
			/etc/init.d/apache2 reload > /dev/null
		fi
	endscript
}

---

### Post by tr333 on 2010-03-30
I don't know much about logrotate, but the man page says it's run daily via a cronjob at /etc/cron.daily/logrotate.

It looks like cron outputs logs to /var/log/syslog, so you can check that for errors.

```
zgrep 'CRON' /var/log/syslog*
```

---

### Post by osx on 2010-03-30
> **tr333 said:**
> I don't know much about logrotate, but the man page says it's run daily via a cronjob at /etc/cron.daily/logrotate.

It looks like cron outputs logs to /var/log/syslog, so you can check that for errors.

```
zgrep 'CRON' /var/log/syslog*
```

Thanks. Just tried that and still no luck. There are entries related to cron, and I see lots of them for cron.hourly and some for cron.weekly, but they all relate to php5. None are for apache2.

---

### Post by tr333 on 2010-03-30
I just installed apache2 in a VM and looked at the default logrotate file for it.  Can't really see anything in your file that would cause it to fail.

Check /etc/crontab and see if the line for run-parts on /etc/cron.daily is commented out or missing?  That's where the daily crontab files (/etc/cron.daily/*) are run from, alongside the cron.hourly, cron.weekly and cron.monthly files.

Also, check the contents of /var/lib/logrotate/status.  That shows the current state of rotated logs.

If you have edited /etc/logrotate.conf, check if it still has the line "include /etc/logrotate.d" to include all the files in /etc/logrotate.d when doing log rotations.

If none of the above gives anything, try running logrotate manually with debugging:
```
$ sudo logrotate -d /etc/logrotate.conf
```

This will output which logs are being rotated.

---

### Post by osx on 2010-03-30
> **tr333 said:**
> I just installed apache2 in a VM and looked at the default logrotate file for it.  Can't really see anything in your file that would cause it to fail.

Check /etc/crontab and see if the line for run-parts on /etc/cron.daily is commented out or missing?  That's where the daily crontab files (/etc/cron.daily/*) are run from, alongside the cron.hourly, cron.weekly and cron.monthly files.

/etc/crontab seems fine. Nothing commented out.

> **tr333 said:**
> Also, check the contents of /var/lib/logrotate/status.  That shows the current state of rotated logs.

Here is what is in the status file. It seems this would mean it is working, but there are no rotated logs there. Just the originals.

"/var/log/apache2/portal/access.log" 2010-3-30
"/var/log/apache2/portal/error.log" 2010-3-30


> **tr333 said:**
> If you have edited /etc/logrotate.conf, check if it still has the line "include /etc/logrotate.d" to include all the files in /etc/logrotate.d when doing log rotations.

It still has the "include /etc/logrotate.d" line.

> **tr333 said:**
> If none of the above gives anything, try running logrotate manually with debugging:
```
$ sudo logrotate -d /etc/logrotate.conf
```

This will output which logs are being rotated.

Here are the results of running the "sudo logrotate -d /etc/logrotate.conf" command. It says the log does not need rotating. I guess I am confused. I thought the logs would be rotated weekly regardless of size as long as they weren't empty.

considering log /var/log/apache2/access.log
  log does not need rotating
considering log /var/log/apache2/error.log
  log does not need rotating
considering log /var/log/apache2/portal/access.log
  log does not need rotating
considering log /var/log/apache2/portal/error.log
  log does not need rotating
not running shared postrotate script, since no logs were rotated

---

### Post by tr333 on 2010-03-30
I would have thought the same thing.  It must be a configuration issue with the logrotate script.  Do you have multiple backup log files in /var/log/apache (access.log.0, access.log.1.gz), or is it just growing to one giant access.log/error.log file?

---

### Post by jrssystemsnet on 2010-03-30
My advice is not to try to use logrotate at all; instead, have Apache pipe logs through **cronolog**.  It will make your life a LOT easier in the long run, particularly if you have (or want to have) automated webstats analysis packages.

---

### Post by osx on 2010-03-30
> **tr333 said:**
> I would have thought the same thing.  It must be a configuration issue with the logrotate script.  Do you have multiple backup log files in /var/log/apache (access.log.0, access.log.1.gz), or is it just growing to one giant access.log/error.log file?

They are just growing into one giant files.

---

### Post by tr333 on 2010-03-31
Try changing the "/var/log/apache2/*.log /var/log/apache2/portal/*.log {" to just "/var/log/apache2/*.log {" and see if it will rotate just the apache logs.  I don't know what else could be the problem, unless something else in the configuration is incorrect.

---

### Post by osx on 2010-03-31
> **tr333 said:**
> Try changing the "/var/log/apache2/*.log /var/log/apache2/portal/*.log {" to just "/var/log/apache2/*.log {" and see if it will rotate just the apache logs.  I don't know what else could be the problem, unless something else in the configuration is incorrect.

Ok. I did that and changed it from weekly to daily just to see what would happen. This time when I ran the "sudo logrotate -d /etc/logrotate.conf" command I got this output:

> rotating pattern: /var/log/apache2/*.log  after 1 days (52 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/apache2/access.log
  log needs rotating
considering log /var/log/apache2/error.log
  log needs rotating
rotating log /var/log/apache2/access.log, log->rotateCount is 52
renaming /var/log/apache2/access.log.52 to /var/log/apache2/access.log.53 (rotatecount 52, logstart 1, i 52), 
renaming /var/log/apache2/access.log.51 to /var/log/apache2/access.log.52 (rotatecount 52, logstart 1, i 51), 

These messages repeat until access.log.# is access.log.0

At that point, the messages change to:

> renaming /var/log/apache2/access.log to /var/log/apache2/access.log.1
creating new log mode = 0640 uid = 0 gid = 4
removing old log /var/log/apache2/access.log.53
rotating log /var/log/apache2/error.log, log->rotateCount is 52
renaming /var/log/apache2/error.log.52 to /var/log/apache2/error.log.53 (rotatecount 52, logstart 1, i 52),

And proceeds down to:

> renaming /var/log/apache2/error.log to /var/log/apache2/error.log.1
creating new log mode = 0640 uid = 0 gid = 4
removing old log /var/log/apache2/error.log.53
running shared postrotate script
running script with arg /var/log/apache2/*.log : "
		if [ -f "`. /etc/apache2/envvars ; echo ${APACHE_PID_FILE:-/var/run/apache2.pid}`" ]; then
			/etc/init.d/apache2 reload > /dev/null
		fi
"


Then I went back in to the apache2 config file for logrotate and changed it back from daily to weekly. Then I again ran the logrotate command in debug mode and got the same message before about the logs not needing to be rotated.

> rotating pattern: /var/log/apache2/*.log  weekly (52 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/apache2/access.log
  log does not need rotating
considering log /var/log/apache2/error.log
  log does not need rotating
not running shared postrotate script, since no logs were rotated

So, it seems the issue is with it being set to weekly.

Does this sound like a bug in logrotate or do I need to check some other configuration file?

Here are the contents of my crontab file (it's default):

> # /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#


---

### Post by tr333 on 2010-03-31
I've never had any problems with it, so I'm not quite sure whether it's a configuration problem or a bug.  I would file a bug report against logrotate for this problem and see what comes out of it.

---

### Post by wojox on 2010-03-31
Try this:

```

/var/log/apache2/*.log /var/log/apache2/portal/*.log {
weekly
missingok
rotate 5
compress
delaycompress
notifempty
create 640 root adm
sharedscripts
postrotate
if [ -f "`. /etc/apache2/envvars ; echo ${APACHE_PID_FILE:-/var/run/apache2.pid}`" ]; then
/etc/init.d/apache2 reload > /dev/null
fi
endscript
}

```


52 backlogs? At least give'em compression.

---

### Post by osx on 2010-04-01
> **wojox said:**
> 52 backlogs? At least give'em compression.

Don't need compression. The logs are not stored permanently on the system and I have far more storage than needed already. I'm not even using 20% of the drive's capacity with no plans to use much more.

Or, are you saying that I should use compression because you think that may be related to the problem?

Thanks.

---

### Post by volkswagner on 2010-04-03
Have you got this sorted?

Do any of your logs rotate?

No logs on my system rotate except for dmesg.  I just don't know where to start.  I have never had to mess with logrotate in the past....It just seemed to work.

UPDATE: I just wanted to point out that logrotate claims not rotate is necessary.  So I can only guess that logrotate does not "understand" the date ore that the files are not empty.  I checked the system date and is correct.  

Perhaps because the file access date is constantly updated, logrotate thinks they are only hours old, not days old.  I am not sure how to determine file creation date and if logrotate can also.

---

### Post by osx on 2010-04-05
> **volkswagner said:**
> Have you got this sorted?

Do any of your logs rotate?

No logs on my system rotate except for dmesg.  I just don't know where to start.  I have never had to mess with logrotate in the past....It just seemed to work.

It seems that things may be working now. I'm not sure why, but suddenly they did rotate this Sunday. There are only three things I have done differently since my initial post. First, I configured the system to do automatic time synchronization using this tutorial [https://help.ubuntu.com/9.04/serverguide/C/NTP.html](https://help.ubuntu.com/9.04/serverguide/C/NTP.html). Second, I installed the latest tzdata update. Third, I restarted apache2. Not sure why restarting apache2 would matter since I have rebooted the entire system before to see if that would fix it.

Per tr333's suggestion, I did file a but report on it here [https://bugs.launchpad.net/ubuntu/+source/logrotate/+bug/553422](https://bugs.launchpad.net/ubuntu/+source/logrotate/+bug/553422)

I guess I'll just have to keep an eye on it to see if the problem continues. If it goes away, I'll update the bug report.

---

### Post by osx on 2010-04-12
UPDATE: Everything seems to be working still. Not sure why the above changes mattered to weekly cron scheduling when it had no problem with daily schedules.

I'm going to mark the thread as solved.

---

