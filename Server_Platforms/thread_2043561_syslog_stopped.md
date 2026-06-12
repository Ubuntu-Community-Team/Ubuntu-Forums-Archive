---
title: "syslog stopped?"
date: 2012-08-16
forum: Server Platforms
---

### Post by chadk5utc on 2012-08-16
for unknown reason syslog file empty no longer logging? also unable to log iptables and have tried multiple methods
server 12.04Lts 3.2.0-29-generic

---

### Post by LHammonds on 2012-08-17
Make sure your partition(s) did not get full.

```
df -h
```

LHammonds

---

