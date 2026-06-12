---
title: "Unable receive emails with postfix/dovecot"
date: 2014-12-24
forum: Server Platforms
---

### Post by astarmathsandphysics on 2014-12-24
I am using postfix anddovecot on ubuntu 12.04
I am able to send messages out to my gmail address but unable to receive messages in.
In system logs messages shows as sent to my inbox but the message isnt there. in /home/vmail/astarmathsandphysics.com/admin/
This is something relevant from /var/log/syslog
```

 postfix/qmgr[3677]: 2B2879414AF: from=<astarmathsandphysics@gmail.com>, size=2373, nrcpt=1 (queue active)
Dec 24 10:09:42 server11362 clamsmtpd: 10121F: from=astarmathsandphysics@gmail.com, to=admin@astarmathsandphysics.com, status=CLEAN
Dec 24 10:09:42 server11362 postfix/smtp[8548]: 157AC94155B: to=<admin@astarmathsandphysics.com>, relay=127.0.0.1[127.0.0.1]:10026, delay=0.26, delays=0.12/0/0.05/0.08, dsn=2.0.0, status=sent (250 2.0.0 Ok: queued as 2B2879414AF)

```
The message doesnt bounce

---

