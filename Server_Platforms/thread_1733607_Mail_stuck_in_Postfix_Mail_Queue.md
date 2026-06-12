---
title: "Mail stuck in Postfix Mail Queue"
date: 2011-04-19
forum: Server Platforms
---

### Post by dalitso on 2011-04-19
I have an Ubuntu 10.04-2 remote server running Postfix and it gets mail using fetchmail. Everything has been fine for the past 5 months til this morning. Emails are not being delivered to the users. Emails are stuck in Mail Queue.

I have restarted postfix and even flushed the Mail Queue, mails still stuck
```
/usr/sbin/postqueue -c /etc/postfix -f
```

```
tail -f /var/log/mail.log
Apr 19 16:40:02 cyclone postfix/qmgr[8256]: E7F79100418: from=<root@cyclone.thunzic.local>, size=696, nrcpt=1 (queue active)
```

I cannot find anything useful in the other log files.

Please help

---

### Post by dalitso on 2011-04-25
A reboot sorted the emails out. They got delivered to the users.
Ofcourse, I first made a backup of /var/spool/postfix/ just in case.

---

