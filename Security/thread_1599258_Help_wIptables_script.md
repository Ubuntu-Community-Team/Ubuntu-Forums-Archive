---
title: "Help w/Iptables script"
date: 2010-10-17
forum: Security
---

### Post by tad1073 on 2010-10-17
I found a iptables script that I need help with modifying. When the script is enabled I can't connect to samba shares or google voice but everything else works as intended. I added samba rules and ftp rules.

```
#!/bin/sh
IPTABLES=/sbin/iptables
MODPROBE=/sbin/modprobe
INT_NET=192.168.1.0/29
SAMBA_SERVER="192.168.1.3"
BROADCAST="192.168.1.7" # Local area network Broadcast Address

#####################################################################
###   Flush existing rules and set chain policy setting to DROP   ###
#####################################################################
echo "[+] Flushing existing iptables rules..."
$IPTABLES -F
$IPTABLES -F -t filter
$IPTABLES -X
$IPTABLES -N PORTSCAN
$IPTABLES -P INPUT DROP
$IPTABLES -P OUTPUT DROP
$IPTABLES -P FORWARD DROP

$IPTABLES -P PORTSCAN DROP
### Load connection-tracking modules
$MODPROBE ip_conntrack

#######################
###   INPUT chain   ###
#######################
echo "[+] Setting up INPUT chain..."
### State tracking rules
$IPTABLES -A INPUT -m state --state INVALID -j LOG --log-prefix "DROP INVALID " --log-ip-options --log-tcp-options
$IPTABLES -A INPUT -m state --state INVALID -j DROP
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
### Anti-spoofing rules
$IPTABLES -A INPUT ! -s $INT_NET -j LOG --log-prefix "SPOOFED PKT " 
$IPTABLES -A INPUT ! -s $INT_NET -j DROP
### ACCEPT/REJECT rules for allowing connections in
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
# Transmission
$IPTABLES -A INPUT -p tcp --sport 51413 -j ACCEPT
$IPTABLES -A INPUT -p udp --sport 51413 -j ACCEPT
# Samba
$IPTABLES -A INPUT -p udp -s $INT_NET -m multiport --dports 137,138 -j ACCEPT
$IPTABLES -A INPUT -p tcp -s $INT_NET -m multiport --dports 139,445 -j ACCEPT
#FTP
$IPTABLES -A INPUT -s $INT_NET -p tcp -m state --state NEW,ESTABLISHED,RELATED -m tcp --dport 21 -j ACCEPT
# SSH
$IPTABLES -A INPUT -p tcp -s $INT_NET --dport 22 --syn -m state --state NEW -j ACCEPT
# Ping
$IPTABLES -A INPUT -p icmp --icmp-type echo-request -j ACCEPT
# Loopback
$IPTABLES -A INPUT -i lo -j ACCEPT
$IPTABLES -A INPUT ! -i lo -d 127.0.0.0/8 -j REJECT
### Default INPUT LOG rule
#$IPTABLES -A INPUT ! -i lo -j LOG --log-prefix "DROP " --log-ip-options --log-tcp-options

########################
###   OUTPUT chain   ###
########################
echo "[+] Setting up OUTPUT chain..."
### State tracking rules
$IPTABLES -A OUTPUT -m state --state INVALID -j LOG --log-prefix "DROP INVALID " --log-ip-options --log-tcp-options
$IPTABLES -A OUTPUT -m state --state INVALID -j DROP
$IPTABLES -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
### ACCEPT rules for allowing connections out
# SSH
$IPTABLES -A OUTPUT -p tcp --dport 22 --syn -m state --state NEW -j ACCEPT
# Whois
$IPTABLES -A OUTPUT -p tcp --dport 43 --syn -m state --state NEW -j ACCEPT
# DNS
$IPTABLES -A OUTPUT -p udp --dport 53 -m state --state NEW -j ACCEPT
# FTP
$IPTABLES -A OUTPUT -p tcp -m state --state NEW -m tcp --dport 21 -j ACCEPT 
# Samba
$IPTABLES -A OUTPUT -p udp -d $SAMBA_SERVER -m multiport --dports 137,138 -j ACCEPT
$IPTABLES -A OUTPUT -p tcp -d $SAMBA_SERVER -m multiport --dports 139,445 -j ACCEPT
# HTTP
$IPTABLES -A OUTPUT -p tcp --dport 80 --syn -m state --state NEW -j ACCEPT
# HTTPS
$IPTABLES -A OUTPUT -p tcp --dport 443 --syn -m state --state NEW -j ACCEPT
# MSN
$IPTABLES -A OUTPUT -p tcp --dport 1863 --syn -m state --state NEW -j ACCEPT
# RWhois
$IPTABLES -A OUTPUT -p tcp --dport 4321 --syn -m state --state NEW -j ACCEPT
# Google Talk
$IPTABLES -A OUTPUT -p tcp --dport 5222 --syn -m state --state NEW -j ACCEPT
# Transmission
$IPTABLES -A OUTPUT -p tcp --dport 51413 -j ACCEPT
$IPTABLES -A OUTPUT -p udp --dport 51413 -j ACCEPT
# Ping
$IPTABLES -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT
### Default OUTPUT LOG rule
#$IPTABLES -A OUTPUT ! -o lo -j LOG --log-prefix "DROP " --log-ip-options --log-tcp-options

#########################
###   FORWARD chain   ###
#########################
echo "[+] Setting up FORWARD chain..."
### State tracking rules
$IPTABLES -A FORWARD -m state --state INVALID -j LOG --log-prefix "DROP INVALID " --log-ip-options --log-tcp-options
$IPTABLES -A FORWARD -m state --state INVALID -j DROP
$IPTABLES -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
### Anti-spoofing rules
$IPTABLES -A FORWARD ! -s $INT_NET -j LOG --log-prefix "SPOOFED PKT "
$IPTABLES -A FORWARD ! -s $INT_NET -j DROP
### Default FORWARD LOG rule
#$IPTABLES -A FORWARD ! -i lo -j LOG --log-prefix "DROP " --log-ip-options --log-tcp-options

######################
###   Forwarding   ###
######################
echo "[+] Enabling IP forwarding..."
echo 1 > /proc/sys/net/ipv4/ip_forward

######################
###   Port Scan   ###
######################
echo "[+] Enabling port scan filter..."
$IPTABLES -A PORTSCAN -m state --state INVALID -j LOG --log-prefix "PORTSCAN " --log-ip-options --log-tcp-options
$IPTABLES -A PORTSCAN -m state --state INVALID -j DROP
$IPTABLES -A PORTSCAN -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK RST -m limit --limit 1/sec -j RETURN
$IPTABLES -A PORTSCAN -j DROP

```

---

### Post by CharlesA on 2010-10-17
I would suggest using iptables-restore and iptables-save for applying iptables rules, not using a shell script.

You really don't need anything in the output chain unless you want to completely lock down the machine. The forwarding chain is only used if you are using the machine as a gateway.

Try only using these rules:

```

#Transmission
-A INPUT -p tcp --sport 51413 -j ACCEPT
-A INPUT -p udp --sport 51413 -j ACCEPT
# Samba
-A INPUT -p udp -m multiport --dports 137,138 -j ACCEPT
-A INPUT -p tcp -m multiport --dports 139,445 -j ACCEPT
#FTP
-A INPUT -p tcp -m tcp --dport 21 -j ACCEPT
# SSH
-A INPUT -p tcp --dport 22 -j ACCEPT
# Ping
-A INPUT -p icmp --icmp-type echo-request -j ACCEPT
# Loopback
-A INPUT -i lo -j ACCEPT

```

---

