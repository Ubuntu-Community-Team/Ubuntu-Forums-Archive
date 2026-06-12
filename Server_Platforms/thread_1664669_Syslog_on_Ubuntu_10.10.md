---
title: "Syslog on Ubuntu 10.10"
date: 2011-01-11
forum: Server Platforms
---

### Post by sentinelace on 2011-01-11
I have this configured to the best of my knowledge. (did it on my last box no problem) but for some reason I am getting no logs from my cisco router. any thoughts?
 
Edit:
 
I found I didn't have "R" enabled for remote but now when I restart I get this:
 
 
```
root@Qmail:/etc/default# /etc/init.d/sysklogd restart
* Restarting system log daemon... usage: syslogd [-drvh] [-l hostlist] [-m markinterval] [-n] [-p path]
[-s domainlist] [-f conffile] [-u user]
```
 
Edit:
 
Maybe I need to do a syslogd -r and syslogd -h ? This seems to have fixed it. Just curious what changed?

---

