---
title: "Missing Secure.log file"
date: 2010-07-11
forum: Security
---

### Post by judoka1113 on 2010-07-11
I seem to be missing a secure.log or security.log file.  I have Ubuntu 10.04 and can't find this file.  I looked in the /var/log and ran a search command to no avail.  Does anyone know where this file is or is it called something else.  I'm looking for a file that logs any change to the security settings of the system.

---

### Post by CharlesA on 2010-07-11
It might be in the system.log. I know authentication attempts are logged in /var/log/auth.log

---

### Post by judoka1113 on 2010-07-11
Here's my auth.log file.  Why is it showing that "session opened/closed by user root on 17:01 0f every hour?  I know I didn't try to log in to the machine.  

> Jul 11 08:17:01 ManOfWar CRON[9777]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 11 08:17:01 ManOfWar CRON[9777]: pam_unix(cron:session): session closed for user root
Jul 11 09:17:01 ManOfWar CRON[10171]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 11 09:17:01 ManOfWar CRON[10171]: pam_unix(cron:session): session closed for user root
Jul 11 10:17:01 ManOfWar CRON[10357]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 11 10:17:01 ManOfWar CRON[10357]: pam_unix(cron:session): session closed for user root
Jul 11 11:17:02 ManOfWar CRON[11281]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 11 11:17:02 ManOfWar CRON[11281]: pam_unix(cron:session): session closed for user root
Jul 11 12:17:02 ManOfWar CRON[11335]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 11 12:17:02 ManOfWar CRON[11335]: pam_unix(cron:session): session closed for user root
Jul 11 13:17:01 ManOfWar CRON[11476]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 11 13:17:01 ManOfWar CRON[11476]: pam_unix(cron:session): session closed for user root
Jul 11 14:17:01 ManOfWar CRON[11531]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 11 14:17:01 ManOfWar CRON[11531]: pam_unix(cron:session): session closed for user root

And what is auth1.log is for, which one should I look at: auth.log or auth1.log?

---

### Post by cariboo on 2010-07-11
Like the output says, it's a cron job that runs hourly, check /etc/cron.hourly to see what cron jobs are running.

> nd what is auth1.log is for, which one should I look at: auth.log or auth1.log?

Logs are rotated after a set amount of time, auth.log.1, is just last weeks log.

Have a look [here]("http://docs.openafs.org/Reference/5/AuthLog.html") for what auth.log does

---

### Post by CharlesA on 2010-07-11
auth.log and auth.log.1 are both log files, auth.log.1 is an older version of the auth.log.

---

### Post by Rubi1200 on 2010-07-11
This provides a more general overview of log files:

[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

This has some tips for how to search in them for specific things:

[http://beginlinux.com/sec_train_m/sec_secure/777-logschecks](http://beginlinux.com/sec_train_m/sec_secure/777-logschecks)

---

### Post by judoka1113 on 2010-07-12
Thanks for all the help, I really appreciate it. :D

---

