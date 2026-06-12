---
title: "Apache graceful restart every Sunday"
date: 2011-03-14
forum: Server Platforms
---

### Post by elaprendiz on 2011-03-14
Ubuntu server kernel 2.6.32-21-generic. Packages:
- apache2_2.2.14
- php5_5.3.2

Every Sunday at 07:35:01 the apache server does a graceful restart. Looking at /var/log/apache2/error.log we can see:

[Sun Mar 13 07:35:01 2011] [notice] Graceful restart requested, doing restart
[Sun Mar 13 07:35:01 2011] [error] (9)Bad file descriptor: apr_socket_accept: (client socket)
[Sun Mar 13 07:35:01 2011] [warn] The Alias directive in /etc/apache2/apache2.conf at line 240 will probably never match because it overlaps an earlier Alias.
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

And it seems that is related to some crontab configuration. Looking at syslog we can see:

Mar 13 07:35:01 HOLTER anacron[16005]: Job `cron.daily' started
Mar 13 07:35:01 HOLTER anacron[16012]: Updated timestamp for job `cron.daily' to 2011-03-13
Mar 13 07:35:01 HOLTER rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="943" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Mar 13 07:35:01 HOLTER rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="943" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Mar 13 07:35:01 HOLTER anacron[16005]: Job `cron.daily' terminated (mailing output)
Mar 13 07:35:01 HOLTER anacron[16005]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Mar 13 07:35:01 HOLTER anacron[16005]: Normal exit (1 job run)

At same time. Actually, the cron is daily but the issue only happens every Sunday. Furthermore, after the restart I do not why but the server does not work properly until I restart it manually.

Any ideas??

---

### Post by falko on 2011-03-15
I guess you should take a look at the scripts in /etc/cron.daily or /etc/cron.weekly.

It might be a good idea to install monit to automatically start Apache if it is down: [http://www.howtoforge.com/server-monitoring-with-munin-and-monit-on-debian-lenny-p2](http://www.howtoforge.com/server-monitoring-with-munin-and-monit-on-debian-lenny-p2)

---

### Post by RedScourge on 2011-05-03
Note about using /etc/cron.hourly daily weekly monthly, or any other cron situations where you are using run-parts (whether you realize it or not):

I noticed that run-parts on Debian and Ubuntu based systems seems to disallow using anything but lowercase, uppercase, numbers, underscore, dash, and a few other things in script names. IT DOES NOT ALLOW DOTS! I spent many days figuring this one out, because I came from RedHat based systems where this seemingly arbitrary restriction does not exist.

To fix this:

Anywhere you use the run-parts command (such as in /etc/crontab) change run-parts --report to run-parts --report  --regex='(^[a-zA-Z0-9.\ _-]+$)' or so, and that way you can do dots and spaces again. You can increase the complexity of the regex and allow more options, or perhaps go with something not very restrictive at all, such as --regex='(.*)' though I have not tested this.

---

