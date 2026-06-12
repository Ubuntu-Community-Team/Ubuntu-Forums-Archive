---
title: "Does VSFTP delete old log files by itself? If not I've been hacked!"
date: 2015-07-14
forum: Security
---

### Post by dreamspy on 2015-07-14
Hi there

I've recently noticed that my vsftp log files only date back about a month, although the ftp has been running for 2 years. 

My question is, is this normal? Does vsftp erase old logs? All I can see are a few vsftp.log.x files in  /var/log (replace x with a number), but the oldest entry is about a month ago.

If vsftp didn't delete those logs, should I worry about that I've been hacked?

Thanks for all answers! This is regarding a live production company webserver so all answers that can help are welcome!

regards
Frímann

---

### Post by bashiergui on 2015-07-15
Check the config file for log rotation at /etc/logrotate.conf. Mine is set to 4 weeks by default.

---

