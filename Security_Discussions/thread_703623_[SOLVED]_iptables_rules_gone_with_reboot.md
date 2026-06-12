---
title: "[SOLVED] iptables rules gone with reboot"
date: 2008-02-21
forum: Security Discussions
---

### Post by (((X))) on 2008-02-21
Why no firewall after rebooting?

this is script used to configure iptables:
#!/bin/sh
#IPTABLES configuration shell script, hello -- 02-06 --
#Version 999
iptables --flush
iptables --delete-chain
## Basic Settings for Allow ##
iptables -P FORWARD DROP
iptables -P INPUT DROP
iptables -A INPUT -i lo --source 127.0.0.1 --destination 127.0.0.1 -j ACCEPT
iptables -A INPUT -m state --state "ESTABLISHED,RELATED" -j ACCEPT 
iptables -A INPUT -p icmp --icmp-type destination-unreachable -j ACCEPT
iptables -A INPUT -p icmp --icmp-type time-exceeded -j ACCEPT
iptables -A INPUT -p icmp --icmp-type echo-request -j ACCEPT
iptables -A INPUT -p icmp --icmp-type echo-reply -j ACCEPT
## Services and Ports ##
#iptables -A INPUT -p tcp --dport ssh -j ACCEPT
#iptables -A INPUT -p tcp --dport http -j ACCEPT
#iptables -A INPUT -p tcp --dport https -j ACCEPT
## Setup Logging and Drop Forwarding ##
iptables -A INPUT -j LOG -m limit --limit 40/minute
iptables -A INPUT -j DROP
iptables -A OUTPUT -j ACCEPT
iptables -A FORWARD -j DROP
echo "$0: IPTABLES Configuration Complete......"

Here is output of iptables --list right after I do #  ./Firewall.sh or sh Firewall.sh or I create direction in /root Firewall.sh.., tried chmod ixu ./Firewall.sh no differnce.
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     0    --  localhost            localhost           
ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-reply 
LOG        0    --  anywhere             anywhere            limit: avg 40/min burst 5 LOG level warning 
DROP       0    --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
DROP       0    --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     0    --  anywhere             anywhere            

This is what I see after a reboot.
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by mikelygee on 2008-02-21
You'll need to reset your iptables after each reboot. Look at [http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)
for a walk-through on setting up a firewall. You can use your rules instead of the ones from that thread, but prepare the "firewall.bash" and "init.d/firewall" as described.

--mag

---

### Post by (((X))) on 2008-02-21
Thanks man, finally got it to work.
I followed step 3.3-The init.d script
:)
Now I got something similar to firestarter but without gui

---

