---
title: "Starting vsftpd"
date: 2010-12-22
forum: Server Platforms
---

### Post by Eleeist on 2010-12-22
I cannot start vsftpd.

When I enter:

```
 sudo /etc/init.d/vsftpd start 
```

The following message appears: 

> Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service vsftpd stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop vsftpd


But when I try:

```
stop vsftpd
```

It also does not work.

---

### Post by arrrghhh on 2010-12-22
Hehe, it was tryin to tell you the full command: ```
service vsftpd stop
``` Ubuntu uses a new upstart system since 10.04, so all services should now use this new system.  

Basically: ```
service <name> start/stop/restart/etc
```

---

### Post by Eleeist on 2010-12-22
Thanks.

---

