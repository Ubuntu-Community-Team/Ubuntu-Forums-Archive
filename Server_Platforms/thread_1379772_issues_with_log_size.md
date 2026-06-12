---
title: "issues with log size"
date: 2010-01-12
forum: Server Platforms
---

### Post by guessswh0 on 2010-01-12
Guys,

My logs are getting too large.  They are soon to hit the 100 meg size.  Syslog that is, but others will approach behind it.

I don't know why the logs aren't being cleared.  I've learned logrotate is installed in ubuntu by default.  I checked /etc/cron.daily/ and logrotate has a script in there.  It should be rotating the logs.  It should rotate them weekly, and keep 4 weeks worth.

However, it has never rotated them.  I tried manually calling the logrotate command myself.  It seemed to execute (it just waited at the command line for the next command) however, upon viewing my logs, nothing has changed.  I am in need of some help.

Any ideas?

---

