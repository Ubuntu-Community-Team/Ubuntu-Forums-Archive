---
title: "logrotate - squid dual instance"
date: 2009-04-30
forum: Server Platforms
---

### Post by edpatterson on 2009-04-30
I am running 2 instances of Squid on one server and I can not get the second instances' logs to rotate.

I have the following file in /etc/logrotate.d
```

#Logrotate fragment for squid2
/var/log/squid2/*.log{
  daily
  compress
  delaycompress
  rotate 2
  missingok
  nocreate
  sharedscripts
  prerotate
    test ! -x /usr/sbin/sarg-maint || /usr/sbin/sarg-maint
  endscript
  postrotate
    test ! -e /var/run/squid2.pid || /usr/sbin/squid -f /etc/squid/squid2.conf -k rotate
  endscript
}

```
The name & path for the pid and conf files is correct.
I tried to manually rotate the logs:
```
 
/usr/sbin/squid -f /etc/squid/squid2.conf -k rotate

```
Nothing.
The log files are being written to in /var/log/squid2, I just can not get them to rotate.

BTW, what is the /sarg-maint line about?
Ideas?
Ed

---

