---
title: "/var/log/kern.log remains empty"
date: 2009-03-04
forum: Security
---

### Post by eentonig on 2009-03-04
Recently, I've noticed that my kern.log remains empty, which isn't normal behaviour.

Kernel logging is pretty important, because my iptables were sending me a lot of info.

What process is responsible for logging kernel messages? I thought it was klogd, but this gets uninstalled when installing syslog-ng.

And even reinstalling klogd, and removing syslog-ng, doesn't solve the problem

---

