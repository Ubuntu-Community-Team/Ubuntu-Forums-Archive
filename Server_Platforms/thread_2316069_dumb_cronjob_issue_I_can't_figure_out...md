---
title: "dumb cronjob issue I can't figure out.."
date: 2016-03-04
forum: Server Platforms
---

### Post by taliosfalcon on 2016-03-04
OK I feel really dumb for this but I have a ubuntu 14.04.3 LTS server that I can't get to respect minutes in cronjobs, i.e 30 6,13,14,20 * * *  /blargh will execute whatever blargh is on the hour at 6,13,14,20 and log nothing to /var/log/syslog , what dumb mistake am i making? System time is also dead on.

---

### Post by darkod on 2016-03-04
So, you want to say it ignores the 30 in front? The minutes parameter?

---

### Post by SeijiSensei on 2016-03-04
In which cron file is this entry stored?  If it's in /etc/crontab you need to include a user like this:
```
30 6,13,14,20 * * * root /path/to/some/app
```
If you create files using the "crontab -e" command, they are stored in /var/spool/cron in a file with the same name as the user, e.g., /var/spool/root/evelyn.  Those files have no username field.

---

