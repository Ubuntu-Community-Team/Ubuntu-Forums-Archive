---
title: "Kernel IP logging"
date: 2010-01-04
forum: Security
---

### Post by Belizeian on 2010-01-04
Currently all ip traffic is going to syslog, is there any way to move it to it's own log file?  Ie put less entries in the main log.

---

### Post by kiranmurari on 2010-01-04
[SIZE=2]Assuming that you are using iptables netfilter framework for logging, you can make following changes to syslog.conf file to log desired IP traffic to a separate file (say firewall.log)
[/SIZE] [SIZE=2]
Open your /etc/syslog.conf file:[/SIZE][SIZE=2]
```
# vi /etc/syslog.conf       
```[/SIZE][SIZE=2]Append following line
```
 kern.warning /var/log/firewall.log
```       [/SIZE][SIZE=2]Save and close the file.
[/SIZE] [SIZE=2]   Restart the syslogd[/SIZE][SIZE=2]
```
# /etc/init.d/syslogd restart
```[/SIZE][SIZE=2]Make sure you pass the log-level 4 option with log-prefix to iptables. 
```

iptables -A INPUT -j LOG --log-level 4
iptables -A INPUT -j DROP       
```[/SIZE][SIZE=2]For example, drop and log all connections from IP address A.B.C.D to your
/var/log/firewall.log file:
```
iptables -A INPUT -s A.B.C.D -m limit --limit 5/m --limit-burst 7 -j LOG --log-prefix '** FIREWALL **' --log-level 4
iptables -A INPUT -s A.B.C.D -j DROP

```[/SIZE][SIZE=2]Where, 
--log-level 4: is level of logging (4 is for warning) 
--log-prefix '*** FIREWALL ***': Prefix log messages with the specified prefix (FIREWALL); useful for distinguishing messages in the logs.
[/SIZE] [SIZE=2]
As all logs with the kern facility get logged to firewall.log, you can search with the log prefix for all ip traffic messages.

[/SIZE]  [SIZE=2]Regards,
[/SIZE] [SIZE=2]Kiran
[/SIZE]

---

### Post by Belizeian on 2010-01-04
Thanks alot big help.

---

