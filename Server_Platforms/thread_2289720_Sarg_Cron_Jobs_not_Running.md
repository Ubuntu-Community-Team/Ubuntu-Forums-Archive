---
title: "Sarg Cron Jobs not Running"
date: 2015-08-06
forum: Server Platforms
---

### Post by Jonathan_Webb on 2015-08-06
I cant seem to get the sarg-reports script to run on a cron schedule.

Ive installed squid and configured it on Ubuntu Server 14.04 and installed sarg with no problems. If i manually run sarg ```
sarg -x
``` the html report correctly generates. I wanted the reports to run automatically so created a new crontab with this in it, pulled from the [Server manpage]("http://manpages.ubuntu.com/manpages/trusty/man1/sarg-reports.1.html")


```

$sudo crontab -e

*Copy and paste the following in, then save*

       PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
       00 08-18/1 * * * sarg-reports today
       00 00      * * * sarg-reports daily
       00 01      * * 1 sarg-reports weekly
       30 02      1 * * sarg-reports monthly


```

Any suggestions?

---

### Post by SeijiSensei on 2015-08-06
You say "sarg -x" works, but the crontab entry is designed to run the program "sarg-reports".  Does that exist on your system? What if you run "sarg-reports monthly"?  Does that work?  Can we see the contents of /var/spool/cron/root inside [noparse][code][/noparse] tags?

---

### Post by Jonathan_Webb on 2015-08-07
> **SeijiSensei said:**
> You say "sarg -x" works, but the crontab entry is designed to run the program "sarg-reports".  Does that exist on your system? What if you run "sarg-reports monthly"?  Does that work?  Can we see the contents of /var/spool/cron/root inside [noparse][code][/noparse] tags?

Im guessing that sarg-reports is there! I can run sarg-reports weekly and the scripts produce a folder in the html output folder, and there is a sarg-reports.conf file present as well. 

There is no folder/file though in called root in /var/spool/cron

ive got /var/spool/atjobs, var/spool/atspool, var/spool/crontabs

thanks for your help!

---

