---
title: "Help, log files not rotating (9.10)"
date: 2011-01-10
forum: Server Platforms
---

### Post by dxjones on 2011-01-10
I am running Ubuntu 9.10 server on MediaTemple (ve).
It is very generic -- I have not customized it.

It has been running for several months, and I just realized the log files (e.g., /var/log/syslog) are not rotating.  The log files just grow larger and larger.

I have checked the "cron" and "anacron" config files and I see "logrotate" in there, but something is not working.

Since I have not fiddled with the cron files, they should still have their default contents.
I am hoping this means this is a well known issue with an easy fix.

Any comments or suggestions welcome,
  David Jones
  [EMAIL="dxjones@gmail.com"]dxjones@gmail.com[/EMAIL]

---

