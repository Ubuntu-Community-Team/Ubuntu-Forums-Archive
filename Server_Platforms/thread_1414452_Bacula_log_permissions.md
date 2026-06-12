---
title: "Bacula log permissions"
date: 2010-02-23
forum: Server Platforms
---

### Post by coryc on 2010-02-23
Hi, 

I have a recently setup my first linux server (hardy) and am having problems with the permissions for a log file being changed.  I believe this is caused by syslogd, but am not sure how to correct it.  Bacula will report it is unable to start a backup because it is unable to open the log file (/var/lib/bacula/log) "permission denied".  After changing the owner from syslog to bacula, the backup will resume.  However, the following day I encounter the same problem because the owner of the log has been changed back to syslog.  I see where the permissions for logs are altered in sysklogd, but I am not certain how to make bacula exempt or if this is the right approach.

Thanks,

---

### Post by coryc on 2010-03-02
It seems I created this problem by adding bacula's log to the list of logs monitored by webmin.  After removing the log from webmin's list last week, I have not encountered the problem again.  Obviously, I didn't fully understand webmin's system log module and made the mistake of assuming it was a quick way to read a log.  Lesson learned the hard way. ](*,):grin:

---

