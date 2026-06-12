---
title: "expiring temp folder"
date: 2009-08-05
forum: Server Platforms
---

### Post by anystupidname1 on 2009-08-05
I'd like to know if anybody can help me create an expiring /temp/ folder. I'd like files in said folder to be deleted automagically when they reach a certain age. (lets say a week old)  I generally use /tmp/ now but things get deleted on reboots and I occasionally lose something I want because of that. (I'm skatterbrained) Any assistance would be much appreciated!

---

### Post by HermanAB on 2009-08-05
Put a script in /etc/cron.weekly

---

### Post by anystupidname1 on 2009-09-09
> **HermanAB said:**
> Put a script in /etc/cron.weekly

Thanks, but that will not accomplish what I want / need. Instead, it looks like the following in cron.hourly is more what i'm looking for.

```
/usr/bin/find ~/download -atime +4 -exec /usr/bin/rm {} \;
```

---

