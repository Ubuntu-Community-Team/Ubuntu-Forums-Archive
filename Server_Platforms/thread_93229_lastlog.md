---
title: "lastlog"
date: 2005-11-21
forum: Server Platforms
---

### Post by lee_connell on 2005-11-21
What events in syslog do i need to forward to /var/logs/lastlog to get the appropriate failed/successful logins?

Is auth.log a replacement for lastlog?

I've got an older redhat system that has /var/log/lastlog and it contains very useful login info that i want on my ubuntu system.

---

### Post by ranf on 2005-11-21
[QUOTE=lee_connell]What events in syslog do i need to forward to /var/logs/lastlog to get the appropriate failed/successful logins?

Is auth.log a replacement for lastlog?

I've got an older redhat system that has /var/log/lastlog and it contains very useful login info that i want on my ubuntu system.[/QUOTE]
I'm not familiar with Redhat. How would the info in lastlog look like?
Have you tried the command `last'?

---

### Post by lee_connell on 2005-11-24
the command last does work good, is there a way to have a log of that type of information, and failed logons?  I want that to be in a log so i can look at previous weeks etc...

---

