---
title: "Apache Syslog"
date: 2009-11-03
forum: Server Platforms
---

### Post by sparks13 on 2009-11-03
I am having a problem with Apache writing logs to syslog. Everything I have seen says you can simply set "ErrorLog syslog:local1" or another syslog facility in your /etc/apache2/apache.conf file. I restart the apache and to no avail. This is after specifying "local1.* -/var/log/local1_test" in /etc/syslog.conf and restarting syslog with "sudo /etc/init.d/sysklogd restart". I have no idea how to debug this or what the problem may be. Everything online claims it is as simple as that, but I have had no luck. "logger -p local1.info testing..." logs to my syslog file just fine. Any ideas what may be the problem?

---

