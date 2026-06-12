---
title: "date always outputs UTC"
date: 2011-03-30
forum: Server Platforms
---

### Post by fela on 2011-03-30
My debian server is setup to synch with debian's NTP servers, and it works just fine, /etc/localtime is the right time.

I live in the UK, and therefore half the year local time is UTC, but right now it's BST (UTC+1 / daylight saving time). The server knows this, however when running the date command, it always outputs UTC time (ie. local time minus one hour).

Any way to fix this?

cheers

---

