---
title: "Separate pam notifications from auth.log"
date: 2008-05-18
forum: Security
---

### Post by Alekc on 2008-05-18
Hello, 
Currently my auth.log is spammed with entries like 
> 
May 18 06:56:01 ubuntu1 CRON[18881]: pam_unix(cron:session): session opened for user www-data by (uid=0)
May 18 06:56:02 ubuntu1 CRON[18881]: pam_unix(cron:session): session closed for user www-data
May 18 06:57:01 ubuntu1 CRON[18894]: pam_unix(cron:session): session opened for user www-data by (uid=0)
May 18 06:57:03 ubuntu1 CRON[18894]: pam_unix(cron:session): session closed for user www-data


since there are some cronjobs which are executed every minute. Is there any way to separate pam_unix cron session notifications from auth.log in (i.e) pam_cron.log?

If not it's realy boring to look through auth.log for seeking data. Thanks

---

### Post by brian_p on 2008-05-18
> **Alekc said:**
> Is there any way to separate pam_unix cron session notifications from auth.log in (i.e) pam_cron.log?

If not it's realy boring to look through auth.log for seeking data. Thanks 

You could see what /etc/syslog.conf has to offer.

---

