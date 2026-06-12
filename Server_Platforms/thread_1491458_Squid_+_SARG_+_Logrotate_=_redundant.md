---
title: "Squid + SARG + Logrotate = redundant?"
date: 2010-05-23
forum: Server Platforms
---

### Post by OoJoo on 2010-05-23
Hello,

I am trying to set up SARG to provide reporting from a squid proxy server.

After installing Squid & SARG, I am a little confused as to how SARG has configured itself to run.

My logrotate file contains:

```
root@machine:~# cat /etc/logrotate.d/squid
#
#       Logrotate fragment for squid.
#
/var/log/squid/*.log {
        daily
        compress
        delaycompress
        rotate 2
        missingok
        nocreate
        sharedscripts
        prerotate
                test ! -x /usr/sbin/sarg-reports || /usr/sbin/sarg-reports
        endscript
        postrotate
                test ! -e /var/run/squid.pid || /usr/sbin/squid -k rotate
        endscript
}
root@machine:~#

```

Yet, there is also a cron file:
```
root@machine:~# cat /etc/cron.daily/sarg
#!/bin/sh

if [ -x /usr/sbin/sarg-reports ]; then
  /usr/sbin/sarg-reports daily
fi
root@machine:~#
```

Should this conflict?  Or at least create a race condition?

In any event SARG and sarg-reports looks like they have not been updated in a few years...  is there anything better that offers per-user location reporting?


thank you

---

### Post by OoJoo on 2010-05-30
Anybody?

---

