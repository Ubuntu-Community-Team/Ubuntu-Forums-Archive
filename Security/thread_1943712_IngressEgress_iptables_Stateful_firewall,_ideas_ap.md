---
title: "Ingress/Egress iptables Stateful firewall, ideas appreciated!"
date: 2012-03-20
forum: Security
---

### Post by dfreer on 2012-03-20
I've just been wanting to share/discuss/improve my knowledge on iptables firewalls, so if you have any comments, critisms, or just ideas please comment.

Basic locked down workstation firewall. Only allows outgoing web browsing and pinging other machines.
```
#!/bin/bash

## First, set default policy and flush existing rules. 
## No point really to set default policy to open other than sometimes it helps when
## working remotely and you don't want to lose your ssh session if there is a typo.
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
iptables -F

## Allow all localhost connections. 
### I still need to test if this is really needed, 
### I'm pretty sure bind talks to itself on the loopback but haven't confirmed.
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

## DNS outgoing queries. 
### I need to craft a request that forces DNS to send the answer as a TCP packet 
### and see if the ESTABLISHED,RELATED traffic will be accepted
iptables -A OUTPUT -p udp --dport 53 -m state --state NEW -j ACCEPT

## HTTP outgoing.
iptables -A OUTPUT -p tcp --dport 80 --syn -m state --state NEW -j ACCEPT

## HTTPS outgoing.
iptables -A OUTPUT -p tcp --dport 443 --syn -m state --state NEW -j ACCEPT

## Allow this machine to ping others, but does not allow incoming pings
iptables -A OUTPUT -p icmp --icmp-type echo-request -m state --state NEW -j ACCEPT

## Drop invalid packets
iptables -A INPUT -m state --state INVALID -j DROP
iptables -A OUTPUT -m state --state INVALID -j DROP

## Allow Established and Related communications in/out
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

## Default Policy
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT DROP

```

HTTP/FTP Server Firewall. Allows incoming FTP Active/Passive connections, does some rate limiting and logging.:
```
#!/bin/bash
## Load kernel module for FTP connection tracking (Debian-based)
modprobe ip_conntrack_ftp

## Load kernel module for FTP connection tracking (Redhat-based)
modprobe nf_conntrack_ftp

## First, set default policy and flush existing rules. 
## No point really to set default policy to open other than sometimes it helps when
## working remotely and you don't want to lose your ssh session if there is a typo.
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
iptables -F

## SYNLIMIT Chain
### Supposedly helps with Syn Flood DoS attacks. I have mixed feelings on
### the effectiveness of this rule.
iptables -N SYNLIMIT
iptables -A SYNLIMIT -m limit --limit 10/second -j LOGNEW

## LOGNEW Chain
### Useful when logging connections.
iptables -N LOGNEW
iptables -A LOGNEW -j LOG --log-prefix "IPT_CONN_NEW: "
iptables -A LOGNEW -j ACCEPT

## Allow all localhost connections. 
### I still need to test if this is really needed, 
### I'm pretty sure bind talks to itself on the loopback but haven't confirmed.
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

## DNS outgoing queries. 
### I need to craft a request that forces DNS to send the answer as a TCP packet 
### and see if the ESTABLISHED,RELATED traffic will be accepted
iptables -A OUTPUT -p udp --dport 53 -m state --state NEW -j ACCEPT

## HTTP/S outgoing.
iptables -A OUTPUT -p tcp --dport 80 --syn -m state --state NEW -j ACCEPT
iptables -A OUTPUT -p tcp --dport 443 --syn -m state --state NEW -j ACCEPT

## HTTP/S incoming.
iptables -A INPUT -p tcp --dport 80 --syn -m state --state NEW -j SYNLIMIT
iptables -A INPUT -p tcp --dport 443 --syn -m state --state NEW -j SYNLIMIT

## FTP/S incoming. Assuming FTPS is using TLS on 21.
### Thanks to connection tracking, this works for both active/passive FTP connections.
iptables -A INPUT -p tcp --dport 21 --syn -m state --state NEW -j SYNLIMIT

## PING in/out
iptables -A INPUT -p icmp --icmp-type echo-request -m state --state NEW -j ACCEPT
iptables -A OUTPUT -p icmp --icmp-type echo-request -m state --state NEW -j ACCEPT

## Drop invalid packets
iptables -A INPUT -m state --state INVALID -j DROP
iptables -A OUTPUT -m state --state INVALID -j DROP

## Allow Established and Related communications in/out
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

## Default Policy
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT DROP
```

DNS Slave/Master Firewall:
```
#!/bin/bash
#### Variables
DNSMASTER=10.60.2.10
DNSSLAVE=10.60.2.11

## First, set default policy and flush existing rules. 
## No point really to set default policy to open other than sometimes it helps when
## working remotely and you don't want to lose your ssh session if there is a typo.
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
iptables -F

## Allow all localhost connections. 
### I still need to test if this is really needed, 
### I'm pretty sure bind talks to itself on the loopback but haven't confirmed.
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

## DNS incoming/outgoing queries. 
### I need to craft a request that forces DNS to send the answer as a TCP packet 
### and see if the ESTABLISHED,RELATED traffic will be accepted
iptables -A INPUT -p udp --dport 53 -m state --state NEW -j ACCEPT
iptables -A OUTPUT -p udp --dport 53 -m state --state NEW -j ACCEPT

## DNS Zone transfer from slave to master
iptables -A OUTPUT -p tcp --dport 53 --syn -d $DNSMASTER -m state --state NEW -j ACCEPT

## DNS Zone transfer from master to slave
iptables -A INPUT -p tcp --dport 53 --syn -s $DNSSLAVE -m state --state NEW -j ACCEPT 

## HTTP outgoing.
iptables -A OUTPUT -p tcp --dport 80 --syn -m state --state NEW -j ACCEPT

## HTTPS outgoing.
iptables -A OUTPUT -p tcp --dport 443 --syn -m state --state NEW -j ACCEPT

## Allow this machine to ping others, but does not allow incoming pings
iptables -A OUTPUT -p icmp --icmp-type echo-request -m state --state NEW -j ACCEPT
## Need a icmp rule for traceroute requests.

## Drop invalid packets
iptables -A INPUT -m state --state INVALID -j DROP
iptables -A OUTPUT -m state --state INVALID -j DROP

## Allow Established and Related communications in/out
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

## Default Policy
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT DROP

```

Email Server Firewall. Pretty much as everything else in it as well. Allows Incoming/Outgoing SMTP, Incoming POP3/S and IMAP/S connections, and webmail connections. Authenticates with external MySQL database and uses winbind to authenticate users against Windows AD. Drops a variety of "bad" packets:
```
#!/bin/bash
#### Variables for use with MySQL and AD  
SQLSERVERIP=10.60.20.5
ADPRIMARY=10.60.20.20

## Set default policy and flush current rules
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
iptables -F

## SYNLIMIT Chain # Limit Essential Services like HTTP/FTP
iptables -N SYNLIMIT
iptables -A SYNLIMIT -p tcp &#8211;-syn -m limit --limit 10/second -j LOGNEW

## LOGNEW CHAIN # Track New Connections Inbound
iptables -N LOGNEW
iptables -A LOGNEW -j LOG &#8211;-log-prefix &#8220;IPT_CONN_NEW: &#8221;
iptables -A LOGNEW -j ACCEPT

## LOGNDROP Chain
iptables -N LOGNDROP
iptables -A LOGNDROP -j LOG &#8211;-log-prefix &#8220;IPT_CONN_DROP: &#8221;
iptables -A LOGNDROP -j ACCEPT

## Allow loopback connections
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

## DNS Queries # UDP 53
iptables -A OUTPUT -p udp --dport 53 -m state --state NEW -j ACCEPT

## HTTP/S Outgoing # TCP 80, TCP 443 for SSL
iptables -A OUTPUT -p tcp --dport 80 --syn -m state --state NEW -j ACCEPT
#iptables -A OUTPUT -p tcp --dport 443 --syn -m state --state NEW -j ACCEPT

## MySQL Outgoing (if not localhost) # TCP 3306
#iptables -A OUTPUT -p tcp --dport 3306 -d $SQLSERVERIP --syn -m state --state NEW -j LOGNEW

## SMTP IN/OUT # TCP 25, TCP 465 for SSL
iptables -A INPUT -p tcp &#8211;-dport 25 &#8211;-syn -m state &#8211;-state NEW -j SYNLIMIT
iptables -A OUTPUT -p tcp &#8211;-dport 25 &#8211;-syn -m state &#8211;-state NEW -j SYNLIMIT 

## HTTP/S Incoming # TCP 80, TCP 443 for SSL
#iptables -A INPUT -p tcp --dport 80 --syn -m state --state NEW -j SYNLIMIT
#iptables -A INPUT -p tcp --dport 443 --syn -m state --state NEW -j SYNLIMIT

## POP3/S Incoming # TCP 110, TCP 995 for SSL
iptables -A INPUT -p tcp -&#8211;dport 110 -&#8211;syn -m state -&#8211;state NEW -j SYNLIMIT
iptables -A INPUT -p tcp -&#8211;dport 995 -&#8211;syn -m state -&#8211;state NEW -j SYNLIMIT

## IMAP/S Incoming # TCP 143, TCP 993 for SSL
iptables -A INPUT -p tcp -&#8211;dport 143 -&#8211;syn -m state -&#8211;state NEW -j SYNLIMIT
iptables -A INPUT -p tcp -&#8211;dport 993 -&#8211;syn -m state -&#8211;state NEW -j SYNLIMIT

## WINBIND Outgoing Ports. I can't remember what ports I enabled, this really needs some narrowing down
iptables -A OUTPUT -p tcp --dport 445 --syn -d $ADPRIMARY -m state --state NEW -j LOGNEW
iptables -A OUTPUT -p tcp --dport 389 --syn -d $ADPRIMARY -m state --state NEW -j LOGNEW
iptables -A OUTPUT -p tcp --dport 113 --syn -d $ADPRIMARY -m state --state NEW -j LOGNEW
iptables -A OUTPUT -p tcp --dport 88 --syn -d $ADPRIMARY -m state --state NEW -j LOGNEW
iptables -A OUTPUT -p udp --dport 88 -d $ADPRIMARY -m state --state NEW -j LOGNEW

## NTP outbound as winbind relies heavily on correct time *well kerberos maybe*
iptables -A OUTPUT -p udp --dport 123 -d $ADPRIMARY -m state --state NEW -j ACCEPT

## ICMP REQUEST IN/OUT
iptables -A INPUT -p icmp --icmp-type echo-request -m state &#8211;-state NEW -j ACCEPT
#iptables -A OUTPUT -p icmp --icmp-type echo-request -m state &#8211;-state NEW -j ACCEPT

##Drop invalid/malformed/evil packets
iptables -A INPUT -m state --state INVALID -j LOGNDROP
iptables -A OUTPUT -m state --state INVALID -j LOGNDROP
#iptables -A INPUT -p tcp -m tcp UNCLEAN -j LOGNDROP # Doesn't seem to work
iptables -A INPUT -p tcp -m tcp --tcp-flags ALL NONE -j LOGNDROP # No flags set in packet
iptables -A INPUT -p tcp -m tcp --tcp-flags ALL ALL -j LOGNDROP # All flags set in packet
iptables -A INPUT -p tcp -m tcp --tcp-flags FIN FIN -j LOGNDROP # Never see a FIN packet set by itself
iptables -A INPUT -p tcp -m tcp --tcp-flags FIN,SYN FIN,SYN -j LOGNDROP #Open and Close
iptables -A INPUT -p tcp -m tcp --tcp-flags SYN,RST SYN,RST -j LOGNDROP #Open and reset
iptables -A INPUT -p tcp -m tcp --tcp-flags FIN,RST FIN,RST -j LOGNDROP #Finish and reset
iptables -A INPUT -p tcp -m tcp --tcp-flags ALL FIN,URG,PSH -j LOGNDROP #Nmap XMAS Flags
iptables -A INPUT -p tcp -m tcp --tcp-flags ALL SYN,RST,ACK,FIN,URG -j LOGNDROP #Merry Xmas Flags
#iptables -A INPUT -p tcp -m tcp --tcp-flags FIN,ACK FIN -j LOGNDROP # DON'T KNOW?


## Allow Established,Relate IN/OUT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

## Log all outgoing connections we missed to ensure that WinBIND works
iptables -A OUTPUT -j LOGNDROP

iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT DROP
```

---

