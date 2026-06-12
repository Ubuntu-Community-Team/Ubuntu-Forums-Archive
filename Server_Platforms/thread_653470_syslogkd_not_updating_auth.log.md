---
title: "syslogkd not updating auth.log"
date: 2007-12-29
forum: Server Platforms
---

### Post by umattu on 2007-12-29
It seems that my auth.log file is no longer getting entries written to it. 

The permissions are rw-r--r-- and the file is owned by root.

I have restarted the server, as well as sysklogd, via  /etc/init.d/syslogkd restart.

I am just unsure how to begin troubleshooting this. 

I log into my server via ssh and expect to see an entry in auth.log, and I do not. This just confirms that its not working. Where should I look first?

Server is ubuntu 6.06 LAMP

---

### Post by andol on 2007-12-30
I assume syslogkd is working fine otherwise? Logging lots of other stuff?

I guess one place to start would be in /etc/syslog.conf
Do you see any references to auth and/or authpriv?

---

