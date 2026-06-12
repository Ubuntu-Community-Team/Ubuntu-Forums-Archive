---
title: "Can't update Ubuntu server 14.04 - statoverride file is missing final newline"
date: 2016-01-15
forum: Server Platforms
---

### Post by toshko3 on 2016-01-15
Hi, when I do a
```
apt-get update ; apt-get dist-upgrade --yes
```

this is what comes as an error:
```
...
Fetched 111 MB in 54s (2,047 kB/s)                                             
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: unrecoverable fatal error, aborting:
 statoverride file is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Didn't find absolutely anything about this particular error in Google. 
Thanks!

---

### Post by v3.xx on 2016-01-15
Whats your statoverride file look like?

/var/lib/dpkg/statoverride

---

### Post by toshko3 on 2016-01-16
The contents of /var/lib/dpkg/statoverride file are these:
```
root postdrop 2555 /usr/sbin/postdrop
root lp 775 /var/log/hp/tmp
root postdrop 2555 /usr/sbin/postqueue
root mlocate 2755 /usr/bin/mlocate
postfix postdrop 2710 /var/spool/postfix/public
hplip root 755 /var/run/hplip
root ssl-cert 710 /etc/ssl/private
root crontab 2755 /usr/bin/crontab
```

---

