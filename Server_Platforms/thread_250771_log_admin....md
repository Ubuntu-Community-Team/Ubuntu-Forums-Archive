---
title: "log admin..."
date: 2006-09-04
forum: Server Platforms
---

### Post by chipyoung on 2006-09-04
I am new to running a lamp server.

I noticed my log files are growing in leaps and bounds.  Maybe someone could suggest a way to manage these growing files.  Do I really need two months of logs if everything is running fine.  I thought maybe a cron job that would remove old data in these files.

Any suggestions would be greatly appreciated.

Thank you,
CLY

---

### Post by Uluen on 2006-09-04
Isn't *logrotate* installed?
```
$ man logrotate
```

---

### Post by chipyoung on 2006-09-05
Thanks.  Yes I do have logrotate. I'll take a look at it.  Sounds like this should do it.

Cly

---

