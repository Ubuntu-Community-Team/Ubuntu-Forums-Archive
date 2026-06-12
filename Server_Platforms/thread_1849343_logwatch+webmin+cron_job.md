---
title: "logwatch+webmin+cron job"
date: 2011-09-24
forum: Server Platforms
---

### Post by JACKTE on 2011-09-24
Hi,


I am trying to run a cron job from webmin 1.550. to run logwatch and email me all results.

I am using this command (just for testing)

logwatch --detail 5 --mailto user@server


When I am pressing save and run this command will execute once only.
After the job was completed cron sends email to root mailbox:

/bin/sh: logwatch: not found

Anyone has got any ideas how to fix  it.

Thank you.

---

### Post by CharlesA on 2011-09-24
use the full path.

---

### Post by JACKTE on 2011-09-24
As simple as that.

Thanks it helped. /usr/sbin/logwatch that is the full path in my system

---

### Post by CharlesA on 2011-09-24
Glad you got it working.

Don't forgot to mark the thread as solved from thread tools. :)

---

