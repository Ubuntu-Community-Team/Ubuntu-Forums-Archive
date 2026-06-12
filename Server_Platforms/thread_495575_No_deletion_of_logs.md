---
title: "No deletion of logs"
date: 2007-07-08
forum: Server Platforms
---

### Post by kbuntu on 2007-07-08
I want to disable deletion of old logs (in /var/log).

After doing some research, I though this change should do:

Edited /etc/logrotate.conf ...

Earlier:
[FONT="Courier New"]rotate 4[/FONT]

Now:
[FONT="Courier New"]rotate 52178[/FONT]

Apparently, this didn't help. What is the solution?

Thanks.

---

### Post by dreadlord_chris on 2007-07-08
have you rebooted or stopped/restarted the logging daemon since making the changes?

---

### Post by MJN on 2007-07-08
That should've worked - the only reasons I can think of as to why it didn't are i) perhaps the number is out-of-range (remember it's a measure of weeks - even 10 years would only be 520), or ii) the logs you're seeing deleted are managed by syslog (e.g. mail, auth etc).

To solve the first try a smaller (more realistic) number, for the second have a look in /etc/cron.daily/sysklogd and change the -c option in the savelog comand to a larger value (measured in days in this case) - do likewise for /etc/cron.weekly/sysklogd (but this time measured in weeks)[1].

Mathew


[1] The timing difference is because the -c option is actually a measure of *rotations* and hence is depedent on how often the rotation is being called.

---

### Post by kbuntu on 2007-07-08
> **MJN said:**
> That should've worked - the only reasons I can think of as to why it didn't are i) perhaps the number is out-of-range (remember it's a measure of weeks - even 10 years would only be 520), or ii) the logs you're seeing deleted are managed by syslog (e.g. mail, auth etc).

i) it is still keeping 4 weeks of log (for non-syslog maintained ones), so I wonder if it out-of-range (unless there is some default which says 4). anyway, I have changed it to 522 now.
ii) hadn't changed the syslogd command, have done that now. Thanks.

Also, I just noticed that there is a directory, /etc/logrotate.d which is included in logrotate.conf
But that is not being followed either, as /etc/logrotate.d/dpkg has something like:

```
/var/log/dpkg.log {
        monthly
        rotate 12
        compress
        delaycompress
        missingok
        notifempty
        create 640 root adm
}

```

And yes, I had noticed that it is in weeks and had set it to ceiling of 1000 years in weeks. :-)

(dreadlord_chris: yes the (cron) daemon has been restarted because I have rebooted since the change. Tthat shouldn't make a difference though as logrotate is not a daemon. cron runs logrotate periodically)

---

### Post by kbuntu on 2007-07-12
It is NOT an overflow/out-of-range issue. Any other suggestions?

---

