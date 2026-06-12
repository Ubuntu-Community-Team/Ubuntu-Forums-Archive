---
title: "System logs missing?"
date: 2011-11-09
forum: Security
---

### Post by PeteAsdf on 2011-11-09
Hi,

I tried to review my system logs yesterday in the KLogviewer (or something like that, I'm not behind my machine now)- sys.log, auth.log, ufw.log. 
I was surprised that it only contained records for one or two days. I then manually opened the logs in /var/log and it was the same.

Should I be worried that someone deleted the logs? Or is it simply that I need to change some setting so the system keeps the logs for longer than 1 day?

Thanks

---

### Post by mikewhatever on 2011-11-09
Check the logs' directory first - **ls /var/log**. Log files don't keep on growing indefinitely, but get rotated instead. This simply means that there should be **syslog.1** and **auth.log.1**, as well as archived logs. By default, the system keeps 30 days worth of logs. Logs older then that are deleted.

---

