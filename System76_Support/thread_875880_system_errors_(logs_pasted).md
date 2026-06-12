---
title: "system errors (logs pasted)"
date: 2008-07-31
forum: System76 Support
---

### Post by justborn on 2008-07-31
please help me 

here r my logs

auth.log
```
Jul 31 03:05:16 appy-desktop sudo:     appy : TTY=unknown ; PWD=/home/appy ; USER=root ; COMMAND=/usr/sbin/startupmanager
Jul 31 03:17:01 appy-desktop CRON[14718]: pam_unix(cron:account): account root has expired (account expired)
Jul 31 03:17:27 appy-desktop sudo:     appy : TTY=unknown ; PWD=/home/appy ; USER=root ; COMMAND=/usr/sbin/startupmanager
Jul 31 03:18:01 appy-desktop CRON[15380]: pam_unix(cron:session): session opened for user amavis by (uid=0)
Jul 31 03:18:05 appy-desktop CRON[15380]: pam_unix(cron:session): session closed for user amavis
Jul 31 03:19:31 appy-desktop sudo:     appy : TTY=unknown ; PWD=/home/appy ; USER=root ; COMMAND=/usr/sbin/startupmanager
Jul 31 03:21:16 appy-desktop sudo:     appy : TTY=unknown ; PWD=/home/appy ; USER=root ; COMMAND=/usr/sbin/startupmanager
Jul 31 03:31:21 appy-desktop sudo:     appy : TTY=unknown ; PWD=/home/appy ; USER=root ; COMMAND=/usr/bin/nautilus --no-desktop  file:///usr/lib/usplash
Jul 31 04:17:02 appy-desktop CRON[27818]: pam_unix(cron:account): account root has expired (account expired)
```

syslog
```
Jul 31 04:17:02 appy-desktop CRON[27818]: User account has expired
Jul 31 04:18:37 appy-desktop gdl_fs_crawler: E 07-31 04:18:36 27451   gdl_fs_crawler run_process_once.cc:99] This binary should be run only once!!!
```


please suggest me what to do.

---

### Post by thomasaaron on 2008-07-31
Whenever you are requesting help on forums, it is a good idea to give as much info as you can to help us troubleshoot it. Just a small section of a log doesn't tell us all that much.

For example:

1. Which System76 model do you have?
2. What symptoms are you experiencing?
3. What steps have you aready taken to try and fix it?

---

