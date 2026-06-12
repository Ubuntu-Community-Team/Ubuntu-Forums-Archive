---
title: "new from FreeBSD"
date: 2008-03-19
forum: Server Platforms
---

### Post by localetc on 2008-03-19
Hi,

I am looking into Ubuntu after 7 years of managing FreeBSD servers.  Everything is working quite well but I am curious about a couple of missing services-- what is the standard replacement, if any?

newsyslog - log rotation facility
periodic - mostly I am interested in the daily email of system statistics.

Any other advice for a FreeBSD guy is appreciated.

mogarlic

---

### Post by Mr. C. on 2008-03-19
logrotate
/etc/cron.{hourly,daily,weekly}

---

