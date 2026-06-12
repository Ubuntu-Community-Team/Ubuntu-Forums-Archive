---
title: "Syslog - monitoring logged in/out users, services, etc."
date: 2008-10-20
forum: Server Platforms
---

### Post by josh6847 on 2008-10-20
I'm using Ubuntu 8.04 Server and was wondering which syslog maintains who has logged in and out of the system, what services are running, and any changes that have been made, etc.

I'm sure the items I named above are in different logs but could someone help push me in the right direction? The most important log I need is who is logging in and out...

Thanks,

Josh

---

### Post by Dr Small on 2008-10-20
The log files are:
```
/var/log/wtmp
/var/log/btmp
```

But they are not readable on my system (example, binary).
You can see the last logged in users by running:
```
last
```

For futher options, see:
```
man last
```

Dr Small

---

