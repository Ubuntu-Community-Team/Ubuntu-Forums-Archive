---
title: "ufw - empty logfile"
date: 2015-11-11
forum: Security
---

### Post by Jan_Rohwer on 2015-11-11
Hello,

I have found some threads related to my problem but none of them seems to solve my problem.
UFW ist configured as follows (Result of [FONT=lucida console]ufw status verbose[/FONT]):
```
Status: active
Logging: on (high)
Default: deny (incoming), allow (outgoing), deny (routed)
New profiles: skip


To                         Action      From
--                         ------      ----
80/tcp                     ALLOW IN    Anywhere
443/tcp                    ALLOW IN    Anywhere
22                         ALLOW IN    Anywhere
2000/tcp                   DENY IN     Anywhere
80/tcp (v6)                ALLOW IN    Anywhere (v6)
443/tcp (v6)               ALLOW IN    Anywhere (v6)
22 (v6)                    ALLOW IN    Anywhere (v6)
2000/tcp (v6)              DENY IN     Anywhere (v6)
```

rsyslogd is running ([FONT=lucida console]/etc/init.d/rsyslog status[/FONT]):
```
 * rsyslogd is running
```

Content of /etc/rsyslog.conf: [http://pastebin.com/raw.php?i=mXXZf2SN](http://pastebin.com/raw.php?i=mXXZf2SN)
Content of /etc/rsyslog.d/20-ufw.conf: [http://pastebin.com/raw.php?i=Ys64MUrm](http://pastebin.com/raw.php?i=Ys64MUrm)
Content of /etc/rsyslog.d/50-default.conf: [http://pastebin.com/raw.php?i=YikEuQML](http://pastebin.com/raw.php?i=YikEuQML)

I am running on Ubuntu 14.04 LTS / Strato vServer.

I tried to connect to a netcat-server on Port 2000 to test the deny-rule. So I expect a log-entry in /var/log/ufw.log but this file doesn't exists. Also in other logfiles in /var/log I can't find anything related to ufw.
Can anyone help me out?

---

