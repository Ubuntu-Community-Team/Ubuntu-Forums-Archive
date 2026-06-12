---
title: "Radiculous number of Root CRON sessions open/close"
date: 2010-03-26
forum: Security
---

### Post by secondstage on 2010-03-26
I have an Ubuntu server that is behind a router with limited port forwarding. A few weeks back, I allowed incoming requests via IMAP, POP3, SMTP, and one other email centric port directly to the server. I have noticed a pickup in the amount of blinking on the router, and checked out /var/log/auth.log to find this.
```
Mar 26 16:30:01 server CRON[26887]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 26 16:30:02 server CRON[26887]: pam_unix(cron:session): session closed for user root
Mar 26 16:39:01 server CRON[26967]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 26 16:39:01 server CRON[26967]: pam_unix(cron:session): session closed for user root
Mar 26 16:40:01 server CRON[27043]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 26 16:40:02 server CRON[27043]: pam_unix(cron:session): session closed for user root
Mar 26 16:50:01 server CRON[27122]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 26 16:50:02 server CRON[27122]: pam_unix(cron:session): session closed for user root
Mar 26 17:00:01 server CRON[27201]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 26 17:00:02 server CRON[27201]: pam_unix(cron:session): session closed for user root
Mar 26 17:09:01 server CRON[27280]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 26 17:09:01 server CRON[27280]: pam_unix(cron:session): session closed for user root
Mar 26 17:10:01 server CRON[27356]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 26 17:10:02 server CRON[27356]: pam_unix(cron:session): session closed for user root
Mar 26 17:17:01 server CRON[27435]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 26 17:17:01 server CRON[27435]: pam_unix(cron:session): session closed for user root
Mar 26 17:20:01 server CRON[27503]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 26 17:20:01 server CRON[27503]: pam_unix(cron:session): session closed for user root
Mar 26 17:30:01 server CRON[27582]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 26 17:30:02 server CRON[27582]: pam_unix(cron:session): session closed for user root
Mar 26 17:39:01 server CRON[27661]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 26 17:39:01 server CRON[27661]: pam_unix(cron:session): session closed for user root
Mar 26 17:40:01 server CRON[27737]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 26 17:40:02 server CRON[27737]: pam_unix(cron:session): session closed for user root
Mar 26 17:50:01 server CRON[27816]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 26 17:50:02 server CRON[27816]: pam_unix(cron:session): session closed for user root
Mar 26 18:00:01 server CRON[27895]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 26 18:00:02 server CRON[27895]: pam_unix(cron:session): session closed for user root
Mar 26 18:09:01 server CRON[27974]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 26 18:09:01 server CRON[27974]: pam_unix(cron:session): session closed for user root
Mar 26 18:10:01 server CRON[28050]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 26 18:10:02 server CRON[28050]: pam_unix(cron:session): session closed for user root
Mar 26 18:17:01 server CRON[28130]: pam_unix(cron:session): session opened for user root by (uid=0)
Mar 26 18:17:01 server CRON[28130]: pam_unix(cron:session): session closed for user root
Mar 26 18:20:01 server CRON[28198]: pam_unix(cron:session): session opened for user root by (uid=0)

```

I looked at all of the crontabs and found nothing. /var/log/mail.log didn't have anything suspicious. 

Is this normal for cron? Or has someone gained access to my system?

---

### Post by jfparis on 2010-03-26
Are you sure you checked all the crontabs?

You have the user crontabs in /var/spool/cron/crontabs
Then you have some system crontabs in /etc/crontab, /etc/cron.d, /etc/cron.daily, /etc/cron.hourly, /etc/cron.weekly and /etc/cron.monthly 

jf

---

### Post by secondstage on 2010-03-26
I checked all of the user crontabs in /var/spool/cron/crontabs but not those system ones you listed.

```
*/10 * * * *    root    [ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null
```

Could explain for the 10s but not the 9s. I'll take a closer look tomorrow and try to find a reason for the 9s. Thanks for the quick response.

---

