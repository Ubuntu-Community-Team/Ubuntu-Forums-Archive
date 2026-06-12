---
title: "What's rotating the mail logs?"
date: 2007-04-24
forum: Server Platforms
---

### Post by lkagan on 2007-04-24
I'm trying to change the default group ownership of newly created mail log files and rotated files.  I went over to the /etc/logrotate.d/ directory to find the config file for postfix and uh.... it's not there.  Okay, so maybe  it's configured in /etc/logrotate.conf..... no such luck.  Does anyone have any idea what is rotating the mail log files?   

Thanks

Larry

---

### Post by jtc on 2007-04-24
Mail logs are usually handled by syslog. Take a look at /etc/cron.daily/sysklogd and /etc/cron.weekly/sysklogd

By Ubuntu default your mail.log would be rotated by the weekly one.

---

### Post by lkagan on 2007-04-24
That's exactly what I needed.  Thank you.

---

