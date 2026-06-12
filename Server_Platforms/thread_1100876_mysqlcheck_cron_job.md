---
title: "mysqlcheck cron job"
date: 2009-03-19
forum: Server Platforms
---

### Post by cfgauss on 2009-03-19
There is some cron job from MySQL that is sending root email. The latest had sujbect "WARNING: mysqlcheck has found corrupt tables". What is evidently true is that debian-sys-maint has some tables open in my databases drupal5 and mysql.

Where is this cron job? I can't find any occurrence of mysql in /etc/cron*/*.

If I find it, can I turn it off (or at least send email to /dev/null?) Is this check necessary?

Thanks.

---

