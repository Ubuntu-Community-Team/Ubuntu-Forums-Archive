---
title: "IPTables help for www/ftp/ssh server"
date: 2006-04-03
forum: Server Platforms
---

### Post by stein on 2006-04-03
Hey everyone,

I'm setting up a Dapper Drake Ubuntu server that will provide the following:
 - public WWW access
 - public FTP access
 - SSH access for server administration


I currently am using the following IPTABLES entries.
I'm new to Linux and Firewalls. Any suggestions on how to improve my IPTABLES entries would be greatly appreciated. Thanks a million in advance.

Sincerely,

Stein



IPTABLES entries script
==================================================
#!/bin/sh

/sbin/modprobe ip_conntrack_ftp

# Interface to Internet
EXTIF=ppp+

iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD DROP

iptables -F FORWARD
iptables -F INPUT
iptables -F OUTPUT

# Allow SSH, FTP, and HTTP Connections
iptables -A INPUT -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
iptables -A INPUT -p tcp --dport 21 -j ACCEPT
# iptables -A INPUT -p tcp --dport 60000:60100 -j ACCEPT
iptables -I INPUT 1 -m state --state RELATED,ESTABLISHED -j ACCEPT

# Deny TCP and UDP packets to privileged ports
iptables -A INPUT -p udp -i $EXTIF --dport 0:1023 -j LOG
iptables -A INPUT -p tcp -i $EXTIF --dport 0:1023 -j LOG
iptables -A INPUT -p udp -i $EXTIF --dport 0:1023 -j DROP
iptables -A INPUT -p tcp -i $EXTIF --dport 0:1023 -j DROP

# Deny TCP connection attempts
iptables -A INPUT -i $EXTIF -p tcp --syn -j LOG
iptables -A INPUT -i $EXTIF -p tcp --syn -j DROP

# Deny ICMP echo-requests
iptables -A INPUT -i $EXTIF -p icmp --icmp-type echo-request -j DROP

---

