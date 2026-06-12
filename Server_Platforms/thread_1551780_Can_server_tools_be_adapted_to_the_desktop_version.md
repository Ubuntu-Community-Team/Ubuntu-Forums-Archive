---
title: "Can server tools be adapted to the desktop version?"
date: 2010-08-12
forum: Server Platforms
---

### Post by website.reader3 on 2010-08-12
Is it possible to install some administrative tools under the System -> Administration tab of the Desktop edition of Ubuntu, so that xinetd, chkconfig, netservices, etc can be controlled?  I am left with an uneasy feeling about my Desktop version, and finding that it is running services that I really do not want to allow.  Apache2 is running for example, but I really am not a web server (yet).  Another service is strigi, the indexer.  I prefer to have it turned off at times.

What administrative tools does Ubuntu offer that can be placed in the sys-admin tab?

(please be kind, I am just starting to use Ubuntu 10.4 having installed the Desktop version)

---

### Post by Bachstelze on 2010-08-12
AFAIK there is none. I think there is a tool you an use to choose which services are started on boot, but none that can start/stop services on the fly.  If that's really a problem for you, other distros have one (OpenSuse comes to mind).

---

### Post by pipemartinm on 2010-08-12
```

sudo apt-get install rcconf
sudo rcconf

```
It's not full GUI but it'll do the trick.

---

