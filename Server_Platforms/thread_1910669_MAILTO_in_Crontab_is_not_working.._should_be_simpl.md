---
title: "MAILTO in Crontab is not working.. should be simple"
date: 2012-01-17
forum: Server Platforms
---

### Post by Gizim on 2012-01-17
This is a Zimbra mail server running 10.4 server. I have a few cron jobs that run with backups and a disk space check I would like the output of those to be emailed to me.

This is my crontab -e
MAILTO=name@domain.com
55 9 * * * /etc/webmin/package-updates/update.pl
0 0 * * * /etc/webmin/backup-config/backup.pl 132433623913443
0 * * * * /etc/webmin/bandwidth/rotate.pl
0,5,10,15,20,25,30,35,40,45,50,55 * * * * /etc/webmin/status/monitor.pl
@daily /root/backup12hr.sh
* 4 * * 7 /root/fullbackup.sh
@daily discus #Disk Size Check

Yet when they run I never get an email and I'm not really sure why.

I'm sure I can do this also with sendmail but I am worried that if I install sendmail it will conflict with port 25 and stop Zimbra.

---

### Post by Gizim on 2012-01-17
Bump

---

### Post by jsra on 2012-01-19
Hi, 
you should check mail.log to see whats wrong.

---

