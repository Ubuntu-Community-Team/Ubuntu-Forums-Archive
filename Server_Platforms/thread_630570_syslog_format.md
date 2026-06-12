---
title: "syslog format"
date: 2007-12-03
forum: Server Platforms
---

### Post by Tom Y on 2007-12-03
Anyone know how I can change the formatting used by syslog when it writes to text files?  Currently I get stuff like this:

```
$ logger -plocal4.info test
$ tail /var/log/syslog
...
Dec  3 19:46:30 hostname user: test
```

I would like to change the date field (numeric month and include the year) and to include the priority of the event (e.g. "info").  Anyone know if this is configurable, and if so, how?

---

