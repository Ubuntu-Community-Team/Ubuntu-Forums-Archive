---
title: "Syslog stops working on restart"
date: 2017-02-14
forum: Server Platforms
---

### Post by andrew102 on 2017-02-14
So I made some changes on three servers to the rsyslog configuration. This worked fine on two out of three (upon systemctl restart syslog)

Has anyone seen this issue before?

rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="29351" x-info="http://www.rsyslog.com"] exiting on signal 15.

The PID is still active but seems to be a zombie. Killing it doesn't work.

Now all syslog stuff has stopped working. i.e. that error is the last entry in /var/log/syslog

~$ uname -r
4.4.0-62-generic

~$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04.1 LTS"

~$ apt policy rsyslog
rsyslog:
  Installed: 8.16.0-1ubuntu3
  Candidate: 8.16.0-1ubuntu3

---

