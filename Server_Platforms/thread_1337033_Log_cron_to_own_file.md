---
title: "Log cron to own file"
date: 2009-11-25
forum: Server Platforms
---

### Post by gencha on 2009-11-25
I am simply trying to get syslog to write cron facility messages to it's own file.
So in the first step I am trying to write them to a file while still keeping the entries in /var/log/syslog.

So I uncommented this line in /etc/syslog.conf
```

cron.*                          /var/log/cron.log

```

Then I created the file /var/log/cron.log, gave ownership to syslog and the group adm and set the access rights to 640.

Then I restarted both syslogd and cron but the file remains empty.
I am all out of ideas.

edit: This is on Ubuntu Server 9.10

---

### Post by gencha on 2009-11-25
Well, it seems like the /etc/syslog.conf that I had has no purpose at all and was possibly left there during an update of Ubtunu.

9.10 uses rsyslogd which stores it's configuration in /etc/rsyslog.d/.

Cheers

---

