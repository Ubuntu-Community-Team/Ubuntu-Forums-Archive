---
title: "Logrotate does not work with Permission denied"
date: 2015-04-05
forum: Server Platforms
---

### Post by yusui-tomikawa on 2015-04-05
Hello everyone, I have a question about logrotate.
The following errors of daily cron are coming to my email and the logrotation of these logs does not work.

[TABLE="class: outer_border, width: 700"]
[TR]
[TD]/etc/cron.daily/logrotate:
error: failed to rename /var/log/mysql.log to /var/log/mysql.log.1: Permission denied
error: failed to rename /var/log/syslog to /var/log/syslog.1: Permission denied
error: failed to rename /var/log/mail.log to /var/log/mail.log.1: Permission denied
error: failed to rename /var/log/auth.log to /var/log/auth.log.1: Permission denied
run-parts: /etc/cron.daily/logrotate exited with return code 1[/TD]
[/TR]
[/TABLE]



The following are permission of these log files:
[TABLE="class: outer_border, width: 500"]
[TR]
[TD]-rw-r----- 1 mysql adm 0 Jan  1 08:52 /var/log/mysql.log
-rw-r----- 1 syslog adm 3595454 Apr  5 09:39 /var/log/syslog
-rw-r----- 1 syslog adm 2425712 Apr  5 07:00 /var/log/mail.log
-rw-r----- 1 syslog adm 1612982 Apr  5 09:17 /var/log/auth.log[/TD]
[/TR]
[/TABLE]


The following are settings of these log files:
[TABLE="class: outer_border, width: 500"]
[TR]
[TD]**/etc/logrotate.d/mysql-server**[/TD]
[/TR]
[TR]
[TD]/var/log/mysql.log /var/log/mysql/mysql.log /var/log/mysql/mysql-slow.log /var/log/mysql/error.log {
        daily
        rotate 7
        missingok
        create 640 mysql adm
        su mysql adm
        compress
        sharedscripts
        postrotate
                test -x /usr/bin/mysqladmin || exit 0
                # If this fails, check debian.conf!
                MYADMIN="/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf"
                if [ -z "`$MYADMIN ping 2>/dev/null`" ]; then
                  # Really no mysqld or rather a missing debian-sys-maint user?
                  # If this occurs and is not a error please report a bug.
                  #if ps cax | grep -q mysqld; then
                  if killall -q -s0 -umysql mysqld; then
                    exit 1
                  fi
                else
                  $MYADMIN flush-logs
                fi
        endscript
}[/TD]
[/TR]
[/TABLE]

[TABLE="class: outer_border, width: 500"]
[TR]
[TD]**/etc/logrotate.d/rsyslog**[/TD]
[/TR]
[TR]
[TD]/var/log/syslog
{
        rotate 7
        daily
        missingok
        notifempty
        delaycompress
        compress
        size 1000000
        su syslog adm
        postrotate
                reload rsyslog >/dev/null 2>&1 || true
        endscript
}
/var/log/mail.info
/var/log/mail.warn
/var/log/mail.err
/var/log/mail.log
{
        rotate 4
        daily
        missingok
        notifempty
        compress
        size 1000000
        su syslog adm
        delaycompress
        sharedscripts
        postrotate
                reload rsyslog >/dev/null 2>&1 || true
        endscript
}
/var/log/auth.log
{
        rotate 4
        daily
        missingok
        notifempty
        compress
        size 1000000
        su syslog adm
        delaycompress
        sharedscripts
        postrotate
                reload rsyslog >/dev/null 2>&1 || true
        endscript
}[/TD]
[/TR]
[/TABLE]

[TABLE="class: outer_border, width: 500"]
[TR]
[TD]**/etc/logrotate.conf**[/TD]
[/TR]
[TR]
[TD]# see "man logrotate" for details
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


# system-specific logs may be configured here[/TD]
[/TR]
[/TABLE]

What should I do to fix the errors?

---

### Post by SeijiSensei on 2015-04-05
Is there some reason you need to use "su"?  I just let the root user manage all the rotations. The default configuration in /etc/logrotate.d/rsyslog should be all you need:
```

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

```

---

### Post by yusui-tomikawa on 2015-04-05
> **SeijiSensei said:**
> Is there some reason you need to use "su"?  I just let the root user manage all the rotations. The default configuration in /etc/logrotate.d/rsyslog should be all you need:
```

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

```

Does it work without "su"?
When I tried logrotate with "-d" option in the default configuration, errors were displayed like this:
```

root@host:~# **/usr/sbin/logrotate -d /etc/logrotate.d/mysql-server**
reading config file /etc/logrotate.d/mysql-server


Handling 1 logs


rotating pattern: /var/log/mysql.log /var/log/mysql/mysql.log /var/log/mysql/mysql-slow.log /var/log/mysql/error.log after 1 days (7 rotations)
empty log files are rotated, old logs are removed
considering log /var/log/mysql.log
[COLOR=#FF0000]**error: skipping "/var/log/mysql.log" because parent directory has insecure permissions (It's world writable or writable by group which is not "root") Set "su" directive in config file to tell logrotate which user/group should be used for rotation.**[/COLOR]
considering log /var/log/mysql/mysql.log
log /var/log/mysql/mysql.log does not exist -- skipping
considering log /var/log/mysql/mysql-slow.log
log /var/log/mysql/mysql-slow.log does not exist -- skipping
considering log /var/log/mysql/error.log
log does not need rotating
root@host:~#

```

---

### Post by SeijiSensei on 2015-04-07
That error isn't the result of running as root.  It's complaining about the permissions of /var/log which appears to be world writable.  On my default installation /var/log is owned by root and group syslog with 775 permissions.
```

$ ls -l  /var | grep log
drwxrwxr-x 13 root syslog   4096 Apr  6 07:39 log
```

---

### Post by yusui-tomikawa on 2015-04-09
> **SeijiSensei said:**
> That error isn't the result of running as root.  It's complaining about the permissions of /var/log which appears to be world writable.  On my default installation /var/log is owned by root and group syslog with 775 permissions.
```

$ ls -l  /var | grep log
drwxrwxr-x 13 root syslog   4096 Apr  6 07:39 log
```

I am sorry I am late.
As you said, it works after turning back to the default!
Thank you so much for your help!

---

