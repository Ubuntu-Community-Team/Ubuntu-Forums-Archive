---
title: "Change rotation mail.* from weekly to daily"
date: 2011-11-14
forum: Server Platforms
---

### Post by quinox on 2011-11-14
Hi there,

I'm fairly new to Ubuntu and always worked with RH systems.

On a Ubuntu 10.04 LTS I want to change to logrotation of all the mail.info, mail.warn etc files from weekly to daily. Normally this is a simple task in /etc/logrotate.d....but not in Ubuntu.

How can I set Ubuntu 10.04 LTS to logrotate my maillogs on a daily basis?

Thanks in advanced,

Roland

---

### Post by SeijiSensei on 2011-11-14
Edit /etc/logrotate.d/rsyslog.  It works the same way in Ubuntu as it does in RH-flavored systems.  You could also remove all the mail-related items from that file and place them in a custom definition file in the /etc/logrotate.d directory.

---

### Post by quinox on 2011-11-16
Got it working now.

Thanks,

Greets, Roland

---

### Post by quinox on 2011-11-23
> **quinox said:**
> Got it working now.

Thanks,

Greets, Roland

I do not have this working and i'm confused now.
Let me begin with the beginning ;-)

I want to rotate my mail-logs on a daily basis instead of the default weekly basis.
So I created a new file in /etc/logrotate.d/mail.
In that file I've set the foolowing parameters:

```
/var/log/mail.log /var/log/mail.info {
    compress
    daily
    dateext
    maxage 365
    rotate 7
    missingok
    notifempty
    sharedscripts
    create 640 root root
    postrotate
           reload rsyslog >/dev/null 2>&1 || true
    endscript
}

```

This should rotate the two logfiles on a daily basis. So I checked with this command if the logrotation is working:

```
logrotate -vdf /etc/logrotate.conf
```

I see the verbose output of the logrotation which says:

```
reading config info for /var/log/mail.log /var/log/mail.info 

Handling 1 logs

rotating pattern: /var/log/mail.log /var/log/mail.info  forced from command line (7 rotations)
empty log files are not rotated, old logs are removed
considering log /var/log/mail.log
  log needs rotating
considering log /var/log/mail.info
  log needs rotating
rotating log /var/log/mail.log, log->rotateCount is 7
dateext suffix '-20111123'
glob pattern '-[0-9][0-9][0-9][0-9][0-9][0-9][0-9][0-9]'
glob finding old rotated logs failed
rotating log /var/log/mail.info, log->rotateCount is 7
dateext suffix '-20111123'
glob pattern '-[0-9][0-9][0-9][0-9][0-9][0-9][0-9][0-9]'
glob finding old rotated logs failed
renaming /var/log/mail.log to /var/log/mail.log-20111123
creating new /var/log/mail.log mode = 0640 uid = 0 gid = 0
renaming /var/log/mail.info to /var/log/mail.info-20111123
creating new /var/log/mail.info mode = 0640 uid = 0 gid = 0
running postrotate script
running script (multiple) with arg /var/log/mail.log /var/log/mail.info : "
           reload rsyslog >/dev/null 2>&1 || true
"
compressing log with: /bin/gzip
compressing log with: /bin/gzip

```

I see it's renaming the old logfile etc, but when I check /var/log and grep on mail, I still see the old maillogs and no rotation is done!

I really need this to work. Please help.

Kind regards,

Roland

---

### Post by quinox on 2011-11-23
Damm...after getting headache about this problem I found a solution (or bug just how you see this).

When i say in my /etc/logrotate.d/mail file to restart the rsyslog daemon in the postrotate section, the rotation works!

The rsyslog daemon is running as user and group syslog, set in /etc/rsyslog.conf.

The reload command will be executed by the root user, so rsyslog can't create a new logfile.

By changing the user and group to root in /etc/rsyslog.conf to run the daemon as those users, the logrotate works!

Is this some kind of bug?

i can't hardly imagine this is true in an LTS version.

I saw an old bugreport about this kind: [https://bugs.launchpad.net/rsyslog/+bug/388608]("https://bugs.launchpad.net/rsyslog/+bug/388608")

Kind regards,

Roland

---

