---
title: "Pam errors, on a server install."
date: 2006-02-12
forum: Server Platforms
---

### Post by HS-L on 2006-02-12
I can see the following errors in /var/log/syslog

```
Feb 12 06:09:01 ctu CRON[29257]: PAM unable to dlopen(/lib/security/pam_foreground.so)
Feb 12 06:09:01 ctu CRON[29257]: PAM [dlerror: /lib/security/pam_foreground.so: cannot open shared object file: No such file or directory]
Feb 12 06:09:01 ctu CRON[29257]: PAM adding faulty module: /lib/security/pam_foreground.so
```

does anybody have a clue what could be the problem?

thx Harold

---

### Post by Glut on 2006-02-12
Check that the file actually exists, you may find that you need to add the module with apt. I don't believe that this module is installed as standard.

---

