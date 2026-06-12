---
title: "Rsyslog template"
date: 2019-03-02
forum: Server Platforms
---

### Post by ricardo35 on 2019-03-02
Hi,

I'm trying to setup a syslog server with rsyslog.
It's working and I'm receiving logs, however, I want to change the output layout but I don't know how.

Now it looks like this:
```
2019-03-02T22:12:15+01:00 MT_Halvemaanstraat defconf deassigned 192.168.2.17 from 9C:F4:8E:76:83:DB
2019-03-02T22:17:36+01:00 MT_Halvemaanstraat defconf assigned 192.168.2.17 to 9C:F4:8E:76:83:DB

```
And I would like to see it like this for example:

date time, HOSTNAME, level of log (warning, etc), log message
Sow I can filter easily on WARNING or ERROR for example.

I know I can change this in the template /etc/rsyslog.conf
I have it like this:

```
$template rfc, "/var/log/rfc/%HOSTNAME%/log.log"
*.* ?rfc



```

But I don't know how to change it correctly.

Any help would be super!

---

