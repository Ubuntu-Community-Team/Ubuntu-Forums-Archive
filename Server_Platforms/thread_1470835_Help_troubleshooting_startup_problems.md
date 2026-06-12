---
title: "Help troubleshooting startup problems"
date: 2010-05-03
forum: Server Platforms
---

### Post by trancephorm on 2010-05-03
Few days ago, weird things started to happen... Majority of services can't startup automatically after boot. Some are working but majority not, including cron which is very important. Can someone help me on troubleshooting that? I tried to enable /var/log/boot logging, but it can't log anything there says nothing is logged yet...

So I just need to know what's the best way to see what succeeded starting up from /etc/init.d and what are the reasons if something failed...

Thanks!

---

### Post by mysteron on 2010-05-03
install rcconf and run it from a command line, it will show which services should be starting up at boot by marking them with an asterisk *

```
apt-get install rcconf
```

/mysteron

---

### Post by trancephorm on 2010-05-03
sorry but that really wasn't the good help :) anyway, thanks...

---

