---
title: "iptables firewall problem"
date: 2010-10-22
forum: Security
---

### Post by toloykhan on 2010-10-22
hello every one , I am facing a little problem with iptables firewall configuration ... the story is that I was created a new script using iptables commands and then move it into the /usr/bin  directory and when I run it from the command line it work successfully but there is little problem is that I permit port 80 for web traffic .. but when I start my browser it didn't work and it seems like the ports is closed ... I used default deny policy for my scrip here is the script .........

#!/bin/bash

modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe ip_conntrack_irc
modprobe ip_conntrack_ftp
modprobe iptable_filter
modprobe iptable_nat
modprobe ipt_recent

# Remove all rules
iptables -F
iptables -X
# first set the default behaviour => drop connections
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP


# allowing established sessions
iptables -A INPUT   -m state --state ESTABLISHED,RELATED -j ACCEPT 
iptables -A OUTPUT  -m state --state ESTABLISHED,RELATED -j ACCEPT 
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

# allowing loopack traffic
iptables -N LO
iptables -A INPUT  -i lo   -m state --state NEW  -j ACCEPT
iptables -A OUTPUT  -o lo   -m state --state NEW  -j ACCEPT
iptables -A LO -j ACCEPT
 

# allowing http (www) connecting incoming and outgoing
iptables -A INPUT -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -p udp --dport 80 -j ACCEPT

# End message
echo " [Project Firewall Activated ...]"

regards 
Toloykhan

---

### Post by johnkills on 2010-10-22
> **toloykhan said:**
> 
iptables -A INPUT -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -p udp --dport 80 -j ACCEPT



I think you should add the line 

iptables -A **OUTPUT** -p tcp --dport 80 -j ACCEPT

EDIT: Something else, I think you should allow port 53 for DNS. I think if you use wireshark and view traffic before and after you load your iptables, you get it working.

I think I said I think way too much.. I am sure!

---

### Post by toloykhan on 2010-10-22
i try to add that line but it still didn't work unless I made the policy default accept

---

### Post by toloykhan on 2010-10-22
I am now downloading wireshark I will use it and post my result here again 

Thank you for helping man...

Toloykha

---

### Post by johnkills on 2010-10-22
I am new to iptables too, try with wireshark and let us know. If you still cant get it working, I will try it later.

---

### Post by toloykhan on 2010-10-22
So we have a meeting point , 
I had downloaded the wireshark and use it, the result for ppp0 interface was fully of analyzed packets before executing the firewall script 
and when I enable the firewall the page was blank .. and no any result .. I think that mean there was no packets sent or received during enabling and opening google.com  , may I am right?

what to do then ...

regards 
Toloykhan

---

