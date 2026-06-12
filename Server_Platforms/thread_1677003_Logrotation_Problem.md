---
title: "Logrotation Problem"
date: 2011-01-28
forum: Server Platforms
---

### Post by Artyom7 on 2011-01-28
Hi All,
I am facing a very weird problem. I do not even know where to start looking for a solution.

I have a small lan setup, with about 30 computers running a mix of windows and linux.
I have 1 Ubuntu server acting as a gateway / proxy and a bunch of iptables rules to log packets from each of these systems. This is done to monitor internet access ( not so much to restrict it ).

The resulting log file grows to about 80 - 100Mb on a daily basis.

I tried setting up log logrotate ( through webmin as well as  manually ) to rotate this log file every night at 11:00 pm.
However, the file does not get rotated.
when i run ```
logrotate -d /etc/logrotate.conf 
```
everything goes through fine. i get a message saying that the file qualifies for rotation and no errors. If i manually force the rotation ( through webmin ) it happens. However, on its own, the log file does not get rotated.
I am completely stumped.
I tried replicating the exact same settings that are set for syslog rotation, and still no luck.
All the other log files do get rotated at the appropriate time ( i have checked in the /var/log/ directory ), but this one does not.
I thought it might have been because i had some prerotate and postrotate scripts. Manually forcing rotation did not generate any errors and the scripts ran without any problems. But even then, i removed those scripts, and still no luck.

this is the config file for logrotate ( in /etc/logrotate.d/bcrl )

```

/BCRL/logs/iptables/log.iptables
{
	rotate 10
	compress
	delaycompress
	postrotate
	    reload rsyslog >/dev/null 2>&1 || true
	endscript
}

```


Another problem ( as of today ) is that iptables is not logging the packets anymore for some reason. the last line in the log file is always similar to :
```
Jan 28 12:40:39 bcrl-server kernel: [   30.408153] __ratelimit: 45 callbacks suppressed
Jan 28 12:41:40 bcrl-server kernel: [   91.623471] __ratelimit: 150 callbacks suppressed

```
after which no more logging takes place and the log file does not grow.
I have to restart the system, and even then it logs only a few packets till the __ratelimit thing happens.

I updated the system just one day before this problem ( the second one ) surfaced, but i do not remember what got updated.
is there any way to check?

Thanks..

---

### Post by SeijiSensei on 2011-01-28
Add the parameter "daily" to the logrotate configuration to force daily updates.

---

### Post by Artyom7 on 2011-01-29
thanks for the suggestion. I will try and get back to you with the results.
Cheers!

---

### Post by Artyom7 on 2011-01-29
> **SeijiSensei said:**
> Add the parameter "daily" to the logrotate configuration to force daily updates.

that worked great..
Thanks!

---

