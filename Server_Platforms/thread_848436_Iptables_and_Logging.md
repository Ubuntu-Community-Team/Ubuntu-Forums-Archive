---
title: "Iptables and Logging"
date: 2008-07-03
forum: Server Platforms
---

### Post by larry Gaminde on 2008-07-03
[B]I have been trying to add a log file to Iptables.rules I cannot get any log files to log even if their right out of Iptables HowTo web pages

[/B][LEFT]** I have sites that are trying to relay mail through my server so I block there addresses. this works but I wanted to know if they were still trying, so I tried this**
[/LEFT]
[B]
-A INPUT -s 216.129.0.0/16 -j LOG --log-prefix "Denied Site: " --log-level 7
-A INPUT -s 216.129.0.0/16 -j DROP
I used my own Ip address with no results, nothing I add from any book or web site works

I also put this log file in with no results.
-A LOGNDROP -p tcp -m limit --limit 5/min -j LOG --log-prefix "Denied TCP: " --log-level 7
-A LOGNDROP -p udp -m limit --limit 5/min -j LOG --log-prefix "Denied UDP: " --log-level 7
-A LOGNDROP -p icmp -m limit --limit 5/min -j LOG --log-prefix "Denied ICMP: " --log-level 7
-A LOGNDROP -j DROP[/B]

---

### Post by kevdog on 2008-07-05
I just helped someone out with this last week.  Here is the script I came up with -- take a look at it and modify it as you need.  It logs every packet -- accepted or rejected.  You may not need to log accepted packets only rejected packets.

#!/bin/sh
#

IPTABLES=/sbin/iptables

### flush existing rules and set chain policy setting to DROP
$IPTABLES -F
$IPTABLES -F -t nat
$IPTABLES -X

$IPTABLES -P INPUT DROP
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -P FORWARD DROP

### state tracking rules
$IPTABLES -A INPUT -m state --state INVALID -j DROP
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

### Create a LOGDROP chain to log dropped packets
$IPTABLES -N LOGDROP

### Drop Log Ruleset (Logs all packets not captured above, before dropping)

#Change the Following Parameters to Limit the amount of Logging
LOGLIMIT="2/s"
LOGLIMITBURST="10"

#Log level may be one of the following: debug, info, notice, warning, warn, err, error, crit, alert, emerg, panic
LOGLEVEL=7

$IPTABLES -A LOGDROP -i ! lo -p tcp -j LOG --log-level $LOGLEVEL --log-prefix "TCP DROP: "
$IPTABLES -A LOGDROP -i ! lo -p udp -j LOG --log-level $LOGLEVEL --log-prefix "UDP DROP: "
$IPTABLES -A LOGDROP -i ! lo -p icmp -j LOG --log-level $LOGLEVEL --log-prefix "ICMP DROP: "
#$IPTABLES -A LOGDROP -i ! lo -m limit --limit $LOGLIMIT --limit-burst $LOGLIMITBURST -j LOG --log-level $LOGLEVEL --log-prefix "IPTABLES UNKNOWN-IN: "

### Log All INPUT Network Traffic
$IPTABLES -A INPUT -j LOGDROP

### ACCEPT rules
$IPTABLES -A INPUT -i lo -j ACCEPT
$IPTABLES -A INPUT -p tcp --dport 80 -j ACCEPT
$IPTABLES -A INPUT -p tcp --dport 22 --source 131.0.0.0/8 -j ACCEPT
$IPTABLES -A INPUT -p icmp --icmp-type echo-request -m limit --limit 10/second -j ACCEPT


exit
### EOF ###

---

