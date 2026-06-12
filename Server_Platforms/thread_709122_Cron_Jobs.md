---
title: "Cron Jobs"
date: 2008-02-27
forum: Server Platforms
---

### Post by dgcarter on 2008-02-27
I set up a cron job via webmin to run a script every hour that updates my DNS.
But every hour when this cron job runs, I get sent an email with the results, how do I stop it from sending me an email every time the cron job runs?

---

### Post by yabbadabbadont on 2008-02-27
Make sure that you redirect the output of the command to /dev/null.

Use "2>&1" to make sure that both stderr and stdout get redirected.

---

### Post by Mr. C. on 2008-02-27
```
*...  job * > /dev/null 2>&1
```

MrC

---

### Post by yabbadabbadont on 2008-02-27
Whoa... dejavu.  :D

---

### Post by dgcarter on 2008-02-27
Praise the Linux guru's!

Thanks

---

