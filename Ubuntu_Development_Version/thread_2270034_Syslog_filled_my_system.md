---
title: "Syslog filled my system"
date: 2015-03-19
forum: Ubuntu Development Version
---

### Post by wgarcia on 2015-03-19
I don't know if this is new from 15.04 or I already had this and just noticed (this is an upgraded system), but I got a message telling me that my root partition was about to fill, and after investigating, it turned out that /var/log/syslog had 7 Giga. More investigation told me that the logs were not rotating, and then I think I have the following bug:

[https://bugs.launchpad.net/ubuntu/+source/logrotate/+bug/1278193](https://bugs.launchpad.net/ubuntu/+source/logrotate/+bug/1278193)

According to message 3 in that bug report, the file /etc/logrotate.conf) should have this directive:

```

 # use the syslog group by default, since this is the owning group
 # of /var/log/syslog.
 su root syslog

```

since the /var/log directory changed from the root group to the syslog group. My /etc/logrotate.conf file doe not have that directive.

Anybody else has seen this in 15.04?

---

### Post by SeijiSensei on 2015-03-19
More pertinent is the question of why is syslog so large?  What errors does it report?  Syslog won't get that large unless it's logging a persistent error.

---

### Post by wgarcia on 2015-03-20
Thanks SiejiSensei. Or if it hasn't been rotated for months, I would say.

---

### Post by dino99 on 2015-03-20
> **wgarcia said:**
> I don't know if this is new from 15.04 or I already had this and just noticed (this is an upgraded system), but I got a message telling me that my root partition was about to fill, and after investigating, it turned out that /var/log/syslog had 7 Giga. More investigation told me that the logs were not rotating, and then I think I have the following bug:

[https://bugs.launchpad.net/ubuntu/+source/logrotate/+bug/1278193](https://bugs.launchpad.net/ubuntu/+source/logrotate/+bug/1278193)

According to message 3 in that bug report, the file /etc/logrotate.conf) should have this directive:

```

 # use the syslog group by default, since this is the owning group
 # of /var/log/syslog.
 su root syslog

```

since the /var/log directory changed from the root group to the syslog group. My /etc/logrotate.conf file doe not have that directive.

Anybody else has seen this in 15.04?

here is mine, which works as expected on vivid:

```
oem@u32:~$ cat /etc/logrotate.conf
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
```

---

### Post by wgarcia on 2015-03-20
Thanks 9d9, that's the way I have except on one system where the lines that I said above are missing. Maybe it's just something weird that happened in that system, or I was hit by the bug above.

---

