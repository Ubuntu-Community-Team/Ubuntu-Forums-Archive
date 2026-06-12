---
title: "Permissions in /var/log keep changing and 'break' the logging!"
date: 2012-02-13
forum: Server Platforms
---

### Post by SteveGodfrey on 2012-02-13
For some reason (maybe logrotate)the owner of some files in /var/log change. I haven't been able to work out when this happens yet. when this change happens no data is written to the files.

Usually the files are
```
-rw-r-----  1 syslog            adm           1422 2012-02-13 10:27 messages
```

Here's a list of the files that are affected today
```
-rw-r-----  1 root              logadmin         0 2012-02-12 08:01 auth.log
-rw-r-----  1 root              logadmin         0 2012-02-12 08:01 cron.log
-rw-r-----  1 root              logadmin         0 2012-02-12 08:01 daemon.log
-rw-r-----  1 root              logadmin         0 2012-02-11 07:41 mail.err
-rw-r-----  1 root              logadmin         0 2012-02-12 08:01 mail.info
-rw-r-----  1 root              logadmin         0 2012-02-12 08:01 mail.log
-rw-r-----  1 root              logadmin         0 2012-02-11 07:41 mail.warn
-rw-r-----  1 root              logadmin      1168 2012-02-03 21:16 pm-powersave.log
-rw-r-----  1 root              logadmin      5879 2012-01-29 15:02 pm-powersave.log.1
-rw-r-----  1 root              logadmin       422 2012-01-01 11:01 pm-powersave.log.2.gz
-rw-r-----  1 root              logadmin         0 2012-02-06 08:06 syslog
-rw-r-----  1 root              logadmin         0 2012-02-12 08:01 user.log

```

Once I change the owner back to what it should be it all works fine.

Any ideas why the owner information keeps changing?

Thanks

---

