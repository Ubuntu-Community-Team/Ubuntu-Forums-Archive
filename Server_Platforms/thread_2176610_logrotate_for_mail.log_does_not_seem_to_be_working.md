---
title: "logrotate for mail.log does not seem to be working."
date: 2013-09-25
forum: Server Platforms
---

### Post by sefs on 2013-09-25
Hi all,

I want to logrotate /var/log/mail.log in a special way.

crontab looks like this...
```

17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )

```
So every morning at 6:25AM the daily will run.

I have edited /etc/logrotate.conf to look like this..
```

....
....
....
# system-specific logs may be configured here
/var/log/mail.log {
    missingok
    daily
    rotate 7
    create
    compress
    start 0
}

```
What I am trying to do is keep 7 days worth of logs for mail log and to rotate the log daily, and start with the extension of .0

However, I find this is not working.  The log is not being rotated.  Each morning I look after 6:25 has passed and I only see "mail.log" and it contains the logs for multiple days, and only keeps getting bigger.

What am I missing here.

Thanks!

---

### Post by SeijiSensei on 2013-09-25
Try running "sudo logrotate --force" to get things started.  Also you can run "sudo logrotate -d" to get logrotate to examine its configuration and tell you what it would do.  See "man logrotate" for details.

---

### Post by sefs on 2013-09-26
> **SeijiSensei said:**
> Try running "sudo logrotate --force" to get things started.  Also you can run "sudo logrotate -d" to get logrotate to examine its configuration and tell you what it would do.  See "man logrotate" for details.

Thank you.
Now I have to wait until tomorrow to see if it will actually rotate by itself.
I also discovered there was an original rotation setup in /etc/logrotate.d/rsyslog that had mail.log to rotate weekly.  I removed it as I do not know if this too would have been causing logrotate to have some conflict with the two mail.log entries asking to be rotated at different intervals.

I'll report back tomorrow.

---

