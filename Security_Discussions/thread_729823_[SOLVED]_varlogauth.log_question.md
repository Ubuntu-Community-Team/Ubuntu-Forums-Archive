---
title: "[SOLVED] /var/log/auth.log question"
date: 2008-03-20
forum: Security Discussions
---

### Post by noahclark on 2008-03-20
Hello

```

Mar 13 06:25:04 black CRON[4120]: (pam_unix) session closed for user root
Mar 13 07:17:01 black CRON[4222]: (pam_unix) session opened for user root by (uid=0)
Mar 13 07:17:01 black CRON[4222]: (pam_unix) session closed for user root
Mar 13 08:17:01 black CRON[4224]: (pam_unix) session opened for user root by (uid=0)
Mar 13 08:17:01 black CRON[4224]: (pam_unix) session closed for user root
Mar 13 09:17:01 black CRON[4226]: (pam_unix) session opened for user root by (uid=0)
Mar 13 09:17:01 black CRON[4226]: (pam_unix) session closed for user root
Mar 13 10:17:01 black CRON[4228]: (pam_unix) session opened for user root by (uid=0)
Mar 13 10:17:01 black CRON[4228]: (pam_unix) session closed for user root
Mar 13 11:17:01 black CRON[4230]: (pam_unix) session opened for user root by (uid=0)
Mar 13 11:17:01 black CRON[4230]: (pam_unix) session closed for user root
Mar 13 12:17:01 black CRON[4232]: (pam_unix) session opened for user root by (uid=0)
Mar 13 12:17:01 black CRON[4232]: (pam_unix) session closed for user root
Mar 13 13:17:01 black CRON[4234]: (pam_unix) session opened for user root by (uid=0)
Mar 13 13:17:01 black CRON[4234]: (pam_unix) session closed for user root
Mar 13 14:17:01 black CRON[4236]: (pam_unix) session opened for user root by (uid=0)
Mar 13 14:17:01 black CRON[4236]: (pam_unix) session closed for user root
Mar 13 15:17:01 black CRON[4238]: (pam_unix) session opened for user root by (uid=0)
Mar 13 15:17:02 black CRON[4238]: (pam_unix) session closed for user root
Mar 13 16:17:01 black CRON[4240]: (pam_unix) session opened for user root by (uid=0)
Mar 13 16:17:01 black CRON[4240]: (pam_unix) session closed for user root
Mar 13 17:17:01 black CRON[4242]: (pam_unix) session opened for user root by (uid=0)
Mar 13 17:17:01 black CRON[4242]: (pam_unix) session closed for user root
Mar 13 18:17:01 black CRON[4244]: (pam_unix) session opened for user root by (uid=0)
Mar 13 18:17:01 black CRON[4244]: (pam_unix) session closed for user root
Mar 13 19:17:01 black CRON[4246]: (pam_unix) session opened for user root by (uid=0)
Mar 13 19:17:01 black CRON[4246]: (pam_unix) session closed for user root
Mar 13 20:17:01 black CRON[4248]: (pam_unix) session opened for user root by (uid=0)
Mar 13 20:17:01 black CRON[4248]: (pam_unix) session closed for user root
Mar 13 21:17:01 black CRON[4250]: (pam_unix) session opened for user root by (uid=0)
Mar 13 21:17:01 black CRON[4250]: (pam_unix) session closed for user root
Mar 13 22:17:01 black CRON[4252]: (pam_unix) session opened for user root by (uid=0)
Mar 13 22:17:01 black CRON[4252]: (pam_unix) session closed for user root
Mar 13 23:17:01 black CRON[4254]: (pam_unix) session opened for user root by (uid=0)
Mar 13 23:17:01 black CRON[4254]: (pam_unix) session closed for user root
Mar 14 00:17:01 black CRON[4256]: (pam_unix) session opened for user root by (uid=0)
Mar 14 00:17:01 black CRON[4256]: (pam_unix) session closed for user root
Mar 14 01:17:01 black CRON[4258]: (pam_unix) session opened for user root by (uid=0)
Mar 14 01:17:01 black CRON[4258]: (pam_unix) session closed for user root
Mar 14 02:17:01 black CRON[4260]: (pam_unix) session opened for user root by (uid=0)
Mar 14 02:17:01 black CRON[4260]: (pam_unix) session closed for user root
Mar 14 03:17:01 black CRON[4262]: (pam_unix) session opened for user root by (uid=0)
Mar 14 03:17:01 black CRON[4262]: (pam_unix) session closed for user root
Mar 14 04:17:01 black CRON[4264]: (pam_unix) session opened for user root by (uid=0)
Mar 14 04:17:01 black CRON[4264]: (pam_unix) session closed for user root
Mar 14 05:17:01 black CRON[4266]: (pam_unix) session opened for user root by (uid=0)
Mar 14 05:17:01 black CRON[4266]: (pam_unix) session closed for user root
Mar 14 06:17:01 black CRON[4268]: (pam_unix) session opened for user root by (uid=0)
Mar 14 06:17:01 black CRON[4268]: (pam_unix) session closed for user root
Mar 14 06:25:01 black CRON[4270]: (pam_unix) session opened for user root by (uid=0)
Mar 13 21:17:01 black CRON[4250]: (pam_unix) session opened for user root by (uid=0)
Mar 13 21:17:01 black CRON[4250]: (pam_unix) session closed for user root

```

what is the cause of this?  I checked for hourly cron jobs in /etc/cron.hourly and didn't find anything.  Thanks.

---

### Post by alan34 on 2008-03-20
If you look at /etc/crontab

less /etc/crontab

You will see something like this
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )

So cron is checking /etc/cron.hourly every hour to see it there any jobs that require doing and that is what is showing in the log.

---

