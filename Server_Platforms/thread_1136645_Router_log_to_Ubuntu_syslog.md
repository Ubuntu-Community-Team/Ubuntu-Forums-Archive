---
title: "Router log to Ubuntu syslog"
date: 2009-04-25
forum: Server Platforms
---

### Post by smeerbartje on 2009-04-25
Hi all,

I have a D-link DIR-655 router which enables me to send the logging to a syslog server. Since my Ubuntu 8.04 LTS server runs a syslog daemon, I thought it would be nice to set this up. So what did I do?

[LIST=1]
[*]In my router, I enables the syslog function, pointing to Ubuntu server: 192.168.1.1
[*]Then I changed /etc/syslog.conf and added the line: System3.* /var/log/router.log
[*]Changed /etc/default/syslogd and made sure the syslog server runs at SYSLOGD="-r" (to enable remote hosts)
[*]Created the file /var/log/router.log
[/LIST]
But unfortunately no entries are written to the router.log file. Am I doing something wrong?

***[edit]***
After checking the /var/log/syslog file, I found out that the router indeed writes logging to Ubuntu, since I found the next line;

```

Apr 25 11:30:52 192.168.1.100 Fri Apr 24 10:30:07 2009 D-Link Systems DIR-655 System Log: Blocked incoming UDP packet from 76.193.168.74:6346 to xxx.xxx.xxx.xxx:45594

```

So the only thing I need to do now is to filter messages from the router and write them to router.log. I thought the line "System3.* /var/log/router.log" would do that, but unfortunately it doesn't. How can I determine the 'facility'-name from the router?

---

### Post by JstSurrender on 2009-04-28
I have a similar issue. I got my  firewall logging to my ubuntu server, however it's logging to /var/log/syslog and I'd like it to log into its own log file. anyone know how to do that?

~Scott

---

### Post by chipyoung on 2010-03-02
Try 

104.info  /var/log/router.log

in your /etc/syslog.conf file. It worked for me with the D-Link DIR-655 router.  My only problem now is that the router log information (router.log) is duplicated in the syslog file.

Any one no how I can fix this problem of duplicating log entries?

Chip

---

### Post by peter3 on 2010-10-31
It would be nice to include something along this line for the new
rsyslogd
since that seems to be the new default.

---

