---
title: "Unable to install mysql server 5.5, DPKG error"
date: 2014-09-30
forum: Server Platforms
---

### Post by alex269 on 2014-09-30
Hey, i've been trying to install the mysql server 5.5 to my Ubuntu 12.04 minimal for a while, and i've been constantly faced with the dpkg, error, i've tried reinstalling the whole OS and nothing has yet to fix it.
```
/var/lib/dpkg/info/mysql-server-5.5.postinst: line 144: logger: command not foundATTENTION: An error has occured. More info is in the syslog!
/var/lib/dpkg/info/mysql-server-5.5.postinst: line 233: logger: command not found
dpkg: error processing mysql-server-5.5 (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 mysql-server-5.5
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

Any help is appreciated.

---

### Post by slickymaster on 2014-09-30
*Moved to the ***Server Platforms*** sub-forum.*

Hi alex269, welcome to the forums.

Maybe these might be of help:
[How to deal with a package failing to be configured properly due to its init script misbehaving?]("http://superuser.com/questions/618358/how-to-deal-with-a-package-failing-to-be-configured-properly-due-to-its-init-scr")
[Mysql strange installations problems]("http://askubuntu.com/questions/506243/mysql-strange-installations-problems")

---

### Post by alex269 on 2014-09-30
Thanks, for the links, reinstalling bsdutils fixed the problem.

Solved.

---

### Post by slickymaster on 2014-09-30
You're welcome. I'm glad you got it fixed.

---

