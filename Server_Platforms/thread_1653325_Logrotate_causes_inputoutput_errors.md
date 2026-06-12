---
title: "Logrotate causes input/output errors"
date: 2010-12-26
forum: Server Platforms
---

### Post by jmidgley on 2010-12-26
Hi

I've been having problems with a server becoming unstable - giving input/output errors, claiming the FS is read-only, other disk-related errors. The only way out is to pull the power, which is obviously not great!

After some pretty nifty detective work, I've discovered that the problem is caused by the logrotate script, run each day from the cron.daily directory. I can recreate the issue at will by running this script, or prevent it by moving it. If I run logrotate manually with -v I can capture the messages, but nothing points to "it went wrong here".

Can anyone suggest how to proceed?

Now if you'll excuse me, I have to go and pull the plug from the back of my server again...

Regards
John

---

### Post by robert_pectol on 2010-12-26
Sounds like you have a failing hard disk drive!  Get your important data off it as soon as you can and then replace it.  I'm betting that the logrotate script is merely triggering the problem due to the extra disk activity involved in compressing/moving log files around, etc.  Every time I've seen input/output errors, it's *always* been a failing disk drive.  Good luck.

---

