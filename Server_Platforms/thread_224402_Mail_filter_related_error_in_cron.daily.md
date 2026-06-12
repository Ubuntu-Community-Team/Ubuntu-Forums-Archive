---
title: "Mail filter related error in cron.daily"
date: 2006-07-27
forum: Server Platforms
---

### Post by cdean on 2006-07-27
Since I dist-upgraded to Dapper, I've had this error in my cron logs:

```
/etc/cron.daily/amavisd-new:
bayes: expire_old_tokens: locker: safe_lock: cannot create tmp lockfile
/etc/spamassassin/bayes.lock.<mydomain>.21717 for /etc/spamassassin/bayes.lock: Permission denied
```

I've tried to track it down, but nothing appears odd. No permissions have changed; no files are in different places (in my mail system...and at least that I can find).

Ideas?

---

