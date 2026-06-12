---
title: "Checking UFW logs"
date: 2008-05-20
forum: Security
---

### Post by Bale on 2008-05-20
I've installed UFW and enabled logging.  I've looked all over but can't find how to check the logs.  Could someone point me in the right direction please, thanks!

---

### Post by kamaji792 on 2008-05-24
Hi,

I've been having the same problem over the last 2 days.  I think the UFW drops are recorded in the syslog file (/var/log/syslog).

I guess you are looking for entries with [UFW BLOCK xxxx] if my log is anything to go by.

To get the relevant entries try:

   ```
grep UFW /var/log/syslog
```

or

   ```
grep UFW /var/log/syslog | less
```

in a terminal

all the best

---

### Post by Borg6of9 on 2009-11-30
I found log lines in my kern.log.0 file in /var/logs nothing in syslog.  my ufw.conf in /etc/ufwis set to 
 
# set to one of 'off', 'low', 'medium', 'high'
LOGLEVEL=low

---

