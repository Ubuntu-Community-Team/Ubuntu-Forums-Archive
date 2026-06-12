---
title: "Need Help configuring my firewall."
date: 2009-10-21
forum: Security
---

### Post by ford08 on 2009-10-21
Hey guys,

I need help or assistance in setting up the stateful firewall policy. This is actually a project in class and im stuck. So if you guys could help it would be much appreciated.

my part is to 

1.)Allow outgoing pings requests.
2.)Disallow incoming pings requests.
3.)Log all incoming connections to the port and protocol normally associated with the MyDoom trojan.
4.)Allow incoming Remote Desktop Protocols connections with the SYN flag set incoming from 145.55.55.55 to 152.168.1.11.
5.)Block all connection attempts from 120.7.7.67.

This is what i got so far as for syntax
for #:
1.) 
# iptables -A OUTPUT -p icmp --icmp-type 8 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
# iptables -A INPUT -p icmp --icmp-type 0 -m state --state ESTABLISHED,RELATED -j ACCEPT

2.)
# iptables -A INPUT -p icmp --icmp-type 8 -m state --state NEW,INVALID -j DROP

5.)
# iptables -A INPUT -p ALL -s 120.7.7.67 -m state --state NEW,INVALID -j DROP


I need help on number 3 and 4

this is what i got for number 4 but i dont think the syntax is correct.

# iptables -A INPUT -i eth1 -p rdp -s 145.55.55.55:152.168.1.11 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT


Thanks guys.

---

### Post by cariboo on 2009-10-21
Forum policy is not to help with home work, I'll leave this thread open for an hour, then it will be closed

Edit: the hour is up, this thread is closed.

---

