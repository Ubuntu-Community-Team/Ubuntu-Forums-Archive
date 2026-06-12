---
title: "rsyslog not moving logs"
date: 2012-06-12
forum: Server Platforms
---

### Post by Xeneth on 2012-06-12
rsyslog is not moving the logs into the correct log file.  It worked up until this past weekend.  They show up in syslog, but not being moved.  Error in syslog:

"Jun 12 10:24:50 server rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]"

There is no /dev/xconsole


Only thing in /etc/rsyslog.d/50-default.conf is:
```
daemon.*;mail.*;\
        news.err;\
        *.=debug;*.=info;\
        *.=notice;*.=warn       |/dev/xconsole
       daemon.*;mail.*;\

```Everything else is commented out.

---

### Post by Xeneth on 2012-06-13
I nixed this option and just made a cron to do what I want.

---

