---
title: "Controlling How Far Back My Logs Archive"
date: 2015-02-19
forum: Server Platforms
---

### Post by moebob24 on 2015-02-19
I look in /var/logs and see my auth logs. I also see where it archives a couple days. I want to increase the number of days these types of logs archive.

Not like the number of days per log but how many logs are kept.

Am I thinking about this correctly.

---

### Post by Habitual on 2015-02-19
logrotate is what you're after I believe. Check /etc/logrotate.d/ for current logrotate scripts.

[PHP]rotate count 
Log files are rotated count times before being removed or mailed to the address specified in a mail directive. \
If count is 0, old versions are removed rather than rotated.[/PHP]

---

### Post by Doug S on 2015-02-19
By default the /var/log/auth.log files should be 1 week each, keeping 4 past weeks. You can edit /etc/logrotate.conf and change the default to whatever you want. Look at this area:```
# keep 4 weeks worth of backlogs
rotate 4
```Note that other specifics are in the /etc/logrotate.d directory

---

### Post by moebob24 on 2015-02-19
So my current logrotate.conf looks like this:

[HTML]
# see "man logrotate" for details
# rotate log files weekly
weekly

# use the syslog group by default, since this is the owning group
# of /var/log/syslog.
su root syslog

# keep 4 weeks worth of backlogs
rotate 4

# create new (empty) log files after rotating old ones
create

# uncomment this if you want your log files compressed
#compress

# packages drop log rotation information into this directory
include /etc/logrotate.d

# no packages own wtmp, or btmp -- we'll rotate them here
/var/log/wtmp {
    missingok
    monthly
    create 0664 root utmp
    rotate 1
}

/var/log/btmp {
    missingok
    monthly
    create 0660 root utmp
    rotate 1
}

# system-specific logs may be configured here
[/HTML]

I can add something like:

[HTML]
/var/log/auth {
   rotate 8
}
[/HTML]

---

### Post by Doug S on 2015-02-19
I made a mistake in my earlier posting. /var/log/auth.log log files are controlled by /etc/logrotate.d/rsyslog. Take it out of there and add a section to deal with it. I am saying take this:```
doug@s15:~$ [COLOR=#ff0000]cat /etc/logrotate.d/rsyslog[/COLOR]
/var/log/syslog
{
        rotate 7
        daily
        missingok
        notifempty
        delaycompress
        compress
        postrotate
                reload rsyslog >/dev/null 2>&1 || true
        endscript
}

/var/log/mail.info
/var/log/mail.warn
/var/log/mail.err
/var/log/mail.log
/var/log/daemon.log
/var/log/kern.log
[COLOR=#ff0000]/var/log/auth.log[/COLOR]
/var/log/user.log
/var/log/lpr.log
/var/log/cron.log
/var/log/debug
/var/log/messages
{
        rotate 4
        weekly
        missingok
        notifempty
        compress
        delaycompress
        sharedscripts
        postrotate
                reload rsyslog >/dev/null 2>&1 || true
        endscript
}
``` and make it this:```
/var/log/syslog
{
        rotate 7
        daily
        missingok
        notifempty
        delaycompress
        compress
        postrotate
                reload rsyslog >/dev/null 2>&1 || true
        endscript
}

/var/log/mail.info
/var/log/mail.warn
/var/log/mail.err
/var/log/mail.log
/var/log/daemon.log
/var/log/kern.log
/var/log/user.log
/var/log/lpr.log
/var/log/cron.log
/var/log/debug
/var/log/messages
{
        rotate 4
        weekly
        missingok
        notifempty
        compress
        delaycompress
        sharedscripts
        postrotate
                reload rsyslog >/dev/null 2>&1 || true
        endscript
}

[COLOR=#ff0000]/var/log/auth.log[/COLOR]
{
        rotate 8
        weekly
        missingok
        notifempty
        compress
        delaycompress
        sharedscripts
        postrotate
                reload rsyslog >/dev/null 2>&1 || true
        endscript
}
```

---

### Post by moebob24 on 2015-02-20
Aww I see!

Thank you friend!

---

### Post by mörgæs on 2015-02-20
If this solves your problem please mark the thread so.

---

