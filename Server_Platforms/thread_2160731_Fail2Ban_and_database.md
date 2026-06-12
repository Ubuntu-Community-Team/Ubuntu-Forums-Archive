---
title: "Fail2Ban and database"
date: 2013-07-08
forum: Server Platforms
---

### Post by alfirdaous on 2013-07-08
Hello everybody,

Is there a way that if fail2ban banned an IP address I can insert that one into MySQL database??

Thx in advance

---

### Post by Habitual on 2013-07-08
Are you looking to have some software do it for you, or looking for a green light to write such code, or procedure?
It is definitely do-able, but would require *you* parsing /etc/hosts.deny and once the IP is found stick that in an "insert" statement so mysql will accept it.

[csv file import is possible]("https://dev.mysql.com/doc/refman/5.1/en/load-data.html"), if you further parse /etc/hosts.deny and then doing a data import using the .csv file as the source.
the interval would also have to be programmed (how will it 'run'?), and I'd suggest a cron job for that schedule.

HTH.

---

### Post by alfirdaous on 2013-07-08
I think we can read the log file, I checked the iptables:

```

# iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
fail2ban-ssh  tcp  --  anywhere             anywhere             multiport dports ssh
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:1213
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:domain
ACCEPT     udp  --  anywhere             anywhere             udp dpt:domain
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:https
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:8443
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ftp-data
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ftp
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:smtp
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:pop3
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:imap2
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:pop3s
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:1215
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:webmin
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:9091
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:51413

Chain FORWARD (policy DROP)
target     prot opt source               destination         

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:1213
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:domain
ACCEPT     udp  --  anywhere             anywhere             udp dpt:domain
ACCEPT     udp  --  anywhere             anywhere             udp dpt:ntp
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:https
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ftp
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ftp-data
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:smtp
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:pop3
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:imap2
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:pop3s
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:9091
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:51413

Chain fail2ban-ssh (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            


```

eventhough I tried to connect to SSH with wrong information, I was not banned, are the information above correct??

in my fail2ban log, I found this line:

```

2013-07-08 14:12:50,045 fail2ban.actions.action: ERROR  iptables -D INPUT -p tcp -m multiport --dports ssh -j fail2ban-ssh
iptables -F fail2ban-ssh

```

---

### Post by Habitual on 2013-07-09
> **alfirdaous said:**
> eventhough I tried to connect to SSH with wrong information, I was not banned
How many times did you try wrong information?

---

### Post by alfirdaous on 2013-07-10
more than 6 times

---

### Post by Habitual on 2013-07-10
then I'd check the settings in /etc/fail2ban/jail.conf
paying particular attention to entries like

```
ignoreip = 127.0.0.1
bantime  = 600
maxretry = 3
```

if you tried it *from* the same host as where it is installed, then an "ignoreip = 127.0.0.1" setting would account for that behavior.
Also check logtarget using ```
grep -i logtarget /etc/fail2ban/fail2ban.conf
```
  
and report the output here.
I am not sure what /var/log/* file fail2ban logs to on Ubuntu, sorry.

Please let us know...

---

### Post by alfirdaous on 2013-07-10
I tried from different host

---

### Post by Habitual on 2013-07-11
check the settings in /etc/fail2ban/jail.conf and 

/etc/fail2ban/fail2ban.conf

---

### Post by alfirdaous on 2013-07-12
I renamed jail.conf to jail.conf.local, I tried with error 404:

```

[apache-404]
enabled = true
port = http
filter = apache-404
logpath = /var/log/apache*/error*.log
maxretry = 3

```

and this the file apache-404:

```

# Fail2Ban configuration file
#
# Author: Cyril Jaquier
#
# $Revision: 471 $
#
[Definition]
# Option: failregex
# Notes.: regex to match the password failure messages in the logfile. The
# host must be matched by a group named "host". The tag "" can
# be used for standard IP/hostname matching.
# Values: TEXT
# [client x.x.x.x] File does not exist: /home/www/admin/admin,
failregex = [[]client []] File does not exist: .*
#
# Option: ignoreregex
# Notes.: regex to ignore. If this regex matches, the line is ignored.
# Values: TEXT
#
ignoreregex =

```

---

