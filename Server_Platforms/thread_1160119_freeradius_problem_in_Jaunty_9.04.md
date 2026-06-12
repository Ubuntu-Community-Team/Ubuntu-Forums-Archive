---
title: "freeradius problem in Jaunty 9.04"
date: 2009-05-15
forum: Server Platforms
---

### Post by MatsB on 2009-05-15
A fresh apt-get update & apt-get install freeradius gives me this error when I run in debug mode:

Unable to open file "/etc/freeradius/sql/mysql/dialup.conf": No such file or directory
Errors reading /etc/freeradius/radiusd.conf

Yes the radiusd.conf points to the right directory now, which it didn't do in earlier versions.

```

run_dir = ${localstatedir}/run/freeradius
pidfile = ${run_dir}/freeradius.pid

```

---

### Post by formatC'vt on 2009-05-27
Hi, try this
```
apt-get install freeradius-mysql
```

---

