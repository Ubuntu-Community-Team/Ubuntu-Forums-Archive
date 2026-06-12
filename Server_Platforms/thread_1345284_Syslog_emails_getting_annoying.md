---
title: "Syslog emails getting annoying"
date: 2009-12-03
forum: Server Platforms
---

### Post by flyinggreg on 2009-12-03
I have a crontab.hourly running on a 8.04 Server and I get an email along with it getting logged to a file EVERY hour that the script was run.  I really don't want the syslog emails anymore and would rather they just went to the log file ONLY.

I know this is simple and its late at night so I can't remember clearly...but, how do you switch off the emails????

Thanks!

---

### Post by sgosnell on 2009-12-03
6. Disable Email
____________

By default cron jobs sends a email to the user account executing the cronjob. If this is not needed put the following command At the end of the cron job line .

>/dev/null 2>&1

---

