---
title: "[SOLVED] FTP upload fails using iptables"
date: 2008-08-14
forum: Security
---

### Post by potam on 2008-08-14
Hello guys,

I have a simple firewall script in Ubuntu, and I have no problem with it except for uploading files via ftp. I can connect to the ftp server, list directory, even download files, but upload hangs at 100%. Using wireshark I am getting: FTP-DATA packet from my computer to the server, ICMP packet type destination unreachable from my router to my computer and so on.
I guess I am missing sg from my script, but can't figure out what. Note that turning off the firewall (INPUT and OUTPUT chain to ACCEPT) solves the problem. The computer itself is a client, not a server.

The script:
```

#!/bin/bash
IPTABLES=/sbin/iptables
MODPROBE=/sbin/modprobe
INT_NET=192.168.0.0/255.255.255.0
### load the modules
echo "[+] Loading modules..."
$MODPROBE nf_conntrack
$MODPROBE nf_nat
$MODPROBE nf_conntrack_ftp
$MODPROBE nf_conntrack_ipv4
$MODPROBE nf_nat_ftp

### flush existing rules and set chain policy setting to DROP
echo "[+] Flushing existing iptables rules..."
$IPTABLES -F
$IPTABLES -F -t nat
$IPTABLES -X
$IPTABLES -P INPUT DROP
$IPTABLES -P OUTPUT DROP
$IPTABLES -P FORWARD DROP

###### INPUT chain ######
echo "[+] Setting up INPUT chain..."
### state tracking rules
$IPTABLES -A INPUT -m state --state INVALID -j DROP
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
### anti-spoofing rules
$IPTABLES -A INPUT -i eth0 -s ! $INT_NET -j DROP
### ACCEPT rules
$IPTABLES -A INPUT -i lo -j ACCEPT
$IPTABLES -A INPUT -i eth0 -s $INT_NET -j ACCEPT
$IPTABLES -A INPUT -p icmp --icmp-type echo-request -j ACCEPT
$IPTABLES -A INPUT -j DROP

###### OUTPUT chain ######
echo "[+] Setting up OUTPUT chain..."
### state tracking rules
$IPTABLES -A OUTPUT -m state --state INVALID -j DROP
$IPTABLES -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
### ACCEPT rules for allowing connections out
$IPTABLES -A OUTPUT -o lo -j ACCEPT
$IPTABLES -A OUTPUT -o eth0 -d $INT_NET -j ACCEPT
#FTP
$IPTABLES -A OUTPUT -p tcp --dport 20 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 21 --syn -m state --state NEW -j ACCEPT
#SSH
$IPTABLES -A OUTPUT -p tcp --dport 22 --syn -m state --state NEW -j ACCEPT
#SMTP
$IPTABLES -A OUTPUT -p tcp --dport 25 --syn -m state --state NEW -j ACCEPT
#Whois
$IPTABLES -A OUTPUT -p tcp --dport 43 --syn -m state --state NEW -j ACCEPT
#HTTP
$IPTABLES -A OUTPUT -p tcp --dport 80 --syn -m state --state NEW -j ACCEPT
#HTTPS
$IPTABLES -A OUTPUT -p tcp --dport 443 --syn -m state --state NEW -j ACCEPT
#MSN
$IPTABLES -A OUTPUT -p tcp --dport 1863 --syn -m state --state NEW -j ACCEPT
#RTMP
$IPTABLES -A OUTPUT -p tcp --dport 1935 -m state --state NEW -j ACCEPT
#Google talk
$IPTABLES -A OUTPUT -p tcp --dport 5222 --syn -m state --state NEW -j ACCEPT
#IRC
$IPTABLES -A OUTPUT -p tcp --dport 6667 --syn -m state --state NEW -j ACCEPT
#Skype
$IPTABLES -A OUTPUT -p tcp --dport 23399 --syn -m state --state NEW -j ACCEPT
#DNS
$IPTABLES -A OUTPUT -p udp --dport 53 -m state --state NEW -j ACCEPT
#NTP
$IPTABLES -A OUTPUT -p udp --dport 123 -m state --state NEW -j ACCEPT
#IPP
$IPTABLES -A OUTPUT -p udp --dport 631 -m state --state NEW -j ACCEPT
#RTMP
$IPTABLES -A OUTPUT -p udp --dport 1935 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT
$IPTABLES -A OUTPUT -j DROP

```

---

### Post by potam on 2008-08-23
So the problem seems to be that FileZilla does not follow the rules of passive ftp connection 100%. ICMP packets marked with invalid status caused my problem. So moving the input rule 'drop invalid state packages' below 'accept icmp packets' solved the problem.
My current (100% working) firewall script:
```

#!/bin/bash
IPTABLES=/sbin/iptables
MODPROBE=/sbin/modprobe
INT_NET=192.168.0.0/255.255.255.0
### load the modules
echo "[+] Loading modules..."
$MODPROBE nf_conntrack
$MODPROBE nf_nat
$MODPROBE nf_conntrack_ftp
$MODPROBE nf_conntrack_ipv4
$MODPROBE nf_nat_ftp

### flush existing rules and set chain policy setting to DROP
echo "[+] Flushing existing iptables rules..."
$IPTABLES -F
$IPTABLES -F -t nat
$IPTABLES -X
$IPTABLES -P INPUT DROP
$IPTABLES -P OUTPUT DROP
$IPTABLES -P FORWARD DROP

###### INPUT chain ######
echo "[+] Setting up INPUT chain..."
### state tracking rules
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
### ACCEPT rules
$IPTABLES -A INPUT -i lo -j ACCEPT
$IPTABLES -A INPUT -i eth0 -s $INT_NET -j ACCEPT
$IPTABLES -A INPUT -p icmp --icmp-type echo-request -j ACCEPT
### DROP rules
$IPTABLES -A INPUT -m state --state INVALID -j DROP
$IPTABLES -A INPUT -i eth0 -s ! $INT_NET -j DROP
$IPTABLES -A INPUT -j DROP

###### OUTPUT chain ######
echo "[+] Setting up OUTPUT chain..."
### state tracking rules
$IPTABLES -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A OUTPUT -m state --state INVALID -j DROP
### ACCEPT rules for allowing connections out
$IPTABLES -A OUTPUT -o lo -j ACCEPT
$IPTABLES -A OUTPUT -o eth0 -d $INT_NET -j ACCEPT
#FTP
$IPTABLES -A OUTPUT -p tcp --dport 20 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 21 --syn -m state --state NEW -j ACCEPT
#SSH
$IPTABLES -A OUTPUT -p tcp --dport 22 --syn -m state --state NEW -j ACCEPT
#SMTP
$IPTABLES -A OUTPUT -p tcp --dport 25 --syn -m state --state NEW -j ACCEPT
#Whois
$IPTABLES -A OUTPUT -p tcp --dport 43 --syn -m state --state NEW -j ACCEPT
#HTTP
$IPTABLES -A OUTPUT -p tcp --dport 80 --syn -m state --state NEW -j ACCEPT
#HTTPS
$IPTABLES -A OUTPUT -p tcp --dport 443 --syn -m state --state NEW -j ACCEPT
#MSN
$IPTABLES -A OUTPUT -p tcp --dport 1863 --syn -m state --state NEW -j ACCEPT
#RTMP
$IPTABLES -A OUTPUT -p tcp --dport 1935 --syn -m state --state NEW -j ACCEPT
#Google talk
$IPTABLES -A OUTPUT -p tcp --dport 5222 --syn -m state --state NEW -j ACCEPT
#IRC
$IPTABLES -A OUTPUT -p tcp --dport 6667 --syn -m state --state NEW -j ACCEPT
#Skype
$IPTABLES -A OUTPUT -p tcp --dport 23399 --syn -m state --state NEW -j ACCEPT
#DNS
$IPTABLES -A OUTPUT -p udp --dport 53 -m state --state NEW -j ACCEPT
#NTP
$IPTABLES -A OUTPUT -p udp --dport 123 -m state --state NEW -j ACCEPT
#IPP
$IPTABLES -A OUTPUT -p udp --dport 631 -m state --state NEW -j ACCEPT
#RTMP
$IPTABLES -A OUTPUT -p udp --dport 1935 -m state --state NEW -j ACCEPT
#ICMP
$IPTABLES -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT
$IPTABLES -A OUTPUT -j DROP

```

---

