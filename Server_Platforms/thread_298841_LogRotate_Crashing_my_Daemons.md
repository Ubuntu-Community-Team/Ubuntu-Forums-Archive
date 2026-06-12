---
title: "LogRotate Crashing my Daemons?"
date: 2006-11-13
forum: Server Platforms
---

### Post by Kurdt on 2006-11-13
I have an email server based on postfix, using mysql.
It worked fine for months but, today near 6 AM postfix master daemon crashed with this log information:

> Nov 13 05:44:15 pc009 master[26397]: terminating on signal 11
Nov 13 05:44:15 pc009 master[26397]: fatal: master_sigdeath: kill process group: No such process
Nov 13 05:44:16 pc009 postfix/master[13234]: warning: process /usr/lib/postfix/trivial-rewrite pid 26397 exit status


I suspect from anacron/logrotate, (I had to shut the computer down and ubuntu couldn't close anacron daemon, maybe locked up) How can I get a detailed log about anacron activities? Does anacron even writes some log file?
Any other help will be appreciatted, i looked all over log files and that's is the only thing useful.

Thanks

---

