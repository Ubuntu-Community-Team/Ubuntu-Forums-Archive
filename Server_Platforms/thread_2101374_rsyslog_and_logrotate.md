---
title: "rsyslog and logrotate"
date: 2013-01-04
forum: Server Platforms
---

### Post by nariub on 2013-01-04
this morning after **logrotate** ran
it created a **syslog.1** file which was cool
but the **syslog** file was empty and had been for over an hour

logging to the **syslog** file started again after 

**sudo service rsyslog restart**

..
it is not the first time
I saw a bug on launchpad about this and 
changed **/etc/logrotate.d/rsyslog**

from
>         postrotate
                reload rsyslog >/dev/null 2>&1 || true
        endscript


to
>         postrotate
                restart rsyslog >/dev/null 2>&1 || true
        endscript



It worked fine for a week
this morning... not so much..

---

### Post by cconstantine on 2013-01-04
Which Ubuntu version and which rsyslog package version?

---

### Post by nariub on 2013-01-05
rsyslog  =  swVersion="5.8.6"

ubuntu   =  12.04.1

~$ uname -a
Linux HOSTNAME 3.2.0-35-generic #55-Ubuntu SMP Wed Dec 5 17:42:16 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by cconstantine on 2013-01-07
...are you certain the logging wasn't simply quiet? Did you happen to use fuser(1) to see if rsyslog had it open for writing?

---

