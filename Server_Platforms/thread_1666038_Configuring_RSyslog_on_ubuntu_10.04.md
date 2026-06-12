---
title: "Configuring RSyslog on ubuntu 10.04"
date: 2011-01-13
forum: Server Platforms
---

### Post by Farrukhjon on 2011-01-13
[SIZE=3][B][FONT=Arial]Hi, friends
Have any detail configuring RSyslog on ubuntu 10.04?[/FONT] with web interface view[/B][/SIZE]

---

### Post by wongo888 on 2011-01-13
You can use Webmin to view rsyslogd files. You will have to configure the System Logs module to use rsyslog rather than the defaults which search for the non-existent 'syslog'.

```

Path to syslog config file:
/etc/rsyslog.conf

Syslog PID file
/var/run/rsyslogd.pid

Path to syslog server
/usr/sbin/rsyslogd

Command to start syslog
service rsyslog start

Command to apply changes
service rsyslog reload

Command to re-open log files
service rsyslog restart

```

---

### Post by internalkernel on 2011-09-20
I just came across this... if you're still looking for a solution that is.

[http://www.linuxjournal.com/content/centralized-logging-web-interface](http://www.linuxjournal.com/content/centralized-logging-web-interface)

---

