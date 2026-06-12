---
title: "Need to change rsyslogd destination &quot;on the fly&quot;"
date: 2010-10-20
forum: Server Platforms
---

### Post by weaver4 on 2010-10-20
I have a web service that needs to change to destination of rsyslogd on the fly.  I have tried this in a bash script and it does not work.

pidrsyslogd='pidof -x rsyslogd'
sudo kill $pidrsyslod
rsyslogd -4 -l $LOGFILEURL

I get the error that rsyslogd is "already running"; as soon as I kill it in the second line it restarts.

What is the best way to do this?

---

### Post by sisco311 on 2010-10-20
Try:
```
sudo initctl stop rsyslog
```

---

### Post by weaver4 on 2010-10-20
First time I execute that command it works fine.  But if I execute a "sudo rsyslogd -4 -l 172.16.23.200"; and then execute "sudo initctl stop rsyslog" a second time I get this error:

initctl: Unknown instance:

---

