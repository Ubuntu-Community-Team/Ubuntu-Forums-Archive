---
title: "Ubuntu randomly restarts"
date: 2013-12-10
forum: Server Platforms
---

### Post by peeta123456 on 2013-12-10
Hi,

I rent an OpenVZ vps and every so often, seemingly at random times my instance will restart.

I've checked the syslog (and the other log files in /var/log) and nothing seems out of the ordinary before or after the restart, please see below:

```
Dec 10 09:07:01 vm-nl-02 CRON[22043]: (root) CMD (cd / && run-parts --report /etc/cron.hourly)
Dec 10 09:20:01 vm-nl-02 CRON[22148]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 10 09:34:40 vm-nl-02 -- MARK --
Dec 10 09:40:01 vm-nl-02 CRON[22312]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 10 09:54:40 vm-nl-02 -- MARK --
Dec 10 10:00:01 vm-nl-02 CRON[22480]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 10 10:07:01 vm-nl-02 CRON[22544]: (root) CMD (cd / && run-parts --report /etc/cron.hourly)
Dec 10 10:48:17 vm-nl-02 syslogd 1.5.0#6.2ubuntu1: restart.

```

Any guidance on where I should look next is greatly appreciated!

Many thanks,
Pete

---

### Post by cariboo on 2013-12-11
Does the system actually restart, as the log file only indicates that the syslogd daemon is restarting, which doesn't indicate a complete restart. If this is all you are seeing in the logs, you have nothing to worry about.

You can check to see if the system is actually restarting by using the uptime command:

```
uptime
```

the result should look something similar to this:

```
uptime
 20:59:33 up 91 days,  1:39,  1 user,  load average: 0.00, 0.01, 0.05
```

---

### Post by peeta123456 on 2013-12-12
Hi, 

Thanks for your reply.

The syslogd restart message it is followed by log entries for a few other services starting as well, mainly named and xinetd.

The uptime matches the point at which these messages appeared.
```
root@vm:~# uptime
 11:27:24 up 2 days, 39 min,  1 user,  load average: 0.04, 0.03, 0.00
```

Pete

---

