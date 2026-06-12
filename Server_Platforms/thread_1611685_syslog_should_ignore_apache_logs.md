---
title: "syslog should ignore apache logs"
date: 2010-11-02
forum: Server Platforms
---

### Post by cljoshi on 2010-11-02
Hello,

I am having rsyslog installed on my ubuntu version 10.04. The rsyslogd is working fine with all process logs are getting recorded in /var/log/syslog. It also includes the logs related to apache (i.e. access, error, etc). But, I want to have apache logs to be recorded in the separate file like say /var/log/apache2/access.log and /var/log/apache2/error.log and not to be recorded in /var/log/syslog. I have already configured in the rsyslog conf i.e. /etc/rsyslog.d/50-default.conf file as below :

local6.*    /var/log/apache2/access.log
local7.err    /var/log/apache2/error.log

And, I have also configured in apache conf file as :

ErrorLog syslog:local7.err
CustomLog /var/log/apache2/access.log combined

After doing above settings it is successfully recording the apache access and error log in the above mentioned log file and also it is recording in syslog file too. But, I want that syslog file should not catch or the apache related logs of access/error should not be recorded in syslog file.

Can anyone help me out for this.

Thanks in advance.

---

