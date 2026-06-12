---
title: "Trace origin of mysql table check"
date: 2010-09-27
forum: Server Platforms
---

### Post by letharion on 2010-09-27
I have a mysql server which "goes down" every day at 9, because the debian-sys-maint user needs to run a table check, for no particular reason.

I assume it's a cron-job, but I can't find anything related to this. There's the mysqlautobackup script, but that runs at 4 in the morning, which is expected and perfectly acceptable.

Any suggestions on how can I trace the source of this?

---

### Post by Jeroensum on 2010-09-27
Have you checked the default cron files?

vim /etc/crontab

sudo crontab -u debian-sys-maint
sudo crontab -u root

Btw, if it is a cron job you should be able to see it stating so in your logfiles /var/log/messages or /var/log/syslog

---

