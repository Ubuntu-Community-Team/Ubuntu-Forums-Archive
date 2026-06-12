---
title: "auth.log archives - how often / when, and can i change it?"
date: 2008-12-06
forum: Security
---

### Post by jame86 on 2008-12-06
Hey ):P

I'v been looking at my auth.log files, unsuprisingly there are a large number of failed logins from the far east!

What I want to know is when / how often, the auth.log file is archived (into the auth.log.*.gz files), and if it is possible for me to change this setting.

Thanks all

Jame86  :D

---

### Post by Kai-vana on 2008-12-06
I need to know this to so.

BUMP

---

### Post by lavinog on 2008-12-06
look at /etc/logrotate.conf
and look in /etc/logrotate.d
logrotate.conf will have the defaults for all packages
the files in /etc/logrotate.d override the defaults
you can use man logrotate for more info, but it is pretty easy to figure out

---

### Post by lavinog on 2008-12-06
Example
My /etc/logrotate.conf
```

# see "man logrotate" for details
# rotate log files weekly
weekly

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

```
to change the default for auth
/etc/logrotate.d/auth
```

/var/log/auth.log {
	monthly
	rotate 12
}

```
this will give me a year of logs grouped by month

---

### Post by jame86 on 2008-12-07
Hey,

So the following will give me weekly log, over a period of 4 weeks??

/var/log/auth.log {
	weekly
	rotate 4
}


Thanks for the help

---

