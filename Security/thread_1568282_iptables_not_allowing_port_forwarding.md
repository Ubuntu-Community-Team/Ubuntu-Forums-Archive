---
title: "iptables not allowing port forwarding"
date: 2010-09-05
forum: Security
---

### Post by steve_d on 2010-09-05
I hope someone can clear my befuddled mind of how to get iptables working correctly...

I've got two virtual machines running, the first VM (VM1) has two network interfaces, one bridged with my real lan, one a private subnet. The second VM (VM2) has one nic, only on the private subnet.

I have VM1 acting as a router for VM2, giving access to my real lan for internet access. The problem I'm having is I cannot get VM1 to forward ports 80 (http) or 222 (ssh) to VM2 from my real lan.

Here is the script I've cobbled together from various (foreshadowing!) locations:


```

#!/bin/bash
LAN=eth0
LANNET=192.168.1.0/24
INT=eth1
SERVER=192.168.1.1
WANIP=192.168.10.11

# Configure default policies (-P), meaning default rule to apply if no
# more specific rule below is applicable.  These rules apply if a more specific rule below
# is not applicable.  Defaults are to DROP anything sent to firewall or internal
# network, permit anything going out.
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT

# Flush (-F) all specific rules
iptables -F INPUT 
iptables -F FORWARD 
iptables -F OUTPUT 
iptables -F -t nat

# Forward all packets from eth1 (internal network) to eth0 (the internet).
iptables -A FORWARD -i $LAN -o $INT -j ACCEPT

# Forward packets that are part of existing and related connections from eth0 to eth1.
iptables -A FORWARD -i $INT -o $LAN -m state --state ESTABLISHED,RELATED -j ACCEPT

# Permit packets in to firewall itself that are part of existing and related connections.
iptables -A INPUT -i $INT -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow all inputs to firewall from the internal network and local interfaces
#
iptables -A INPUT -i $LAN -s 0/0 -d 0/0 -j ACCEPT
iptables -A INPUT -i lo -s 0/0 -d 0/0 -j ACCEPT

# Enable SNAT functionality on WAN interface
iptables -A POSTROUTING -t nat -s $LANNET -o $INT -j SNAT --to-source $WANIP

# **************Forward external ports to LAN IP's**************
iptables -A FORWARD -p tcp -s 0/0 -d 192.168.1.2 --destination-port 80 --syn -j ACCEPT
iptables -A FORWARD -p tcp -s 0/0 -d 192.168.1.2 --destination-port 22 --syn -j ACCEPT

# Allow ICMP for all
#iptables -A INPUT -p icmp -j ACCEPT
#iptables -A OUTPUT -p icmp -j ACCEPT
#iptables -A FORWARD -p icmp -j ACCEPT

# Allow all for loopback
iptables -A INPUT -i lo -s 0/0 -d 0/0 -j ACCEPT
iptables -A OUTPUT -o lo -s 0/0 -d 0/0 -j ACCEPT

# Allow all for local network
iptables -A INPUT -i $LAN -s $LANNET -d $LANNET -j ACCEPT
iptables -A OUTPUT -o $LAN -s $LANNET -d $LANNET -j ACCEPT
iptables -A FORWARD -i $LAN -o $LAN -s $LANNET -d $LANNET -j ACCEPT

# Allow incoming established connections from the Internet
iptables -A INPUT -i $INT -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -i $INT -o $LAN -m state --state RELATED,ESTABLISHED -j ACCEPT

# Allow outgoing connections to the Internet
iptables -A OUTPUT -o $INT -j ACCEPT
iptables -A FORWARD -i $LAN -j ACCEPT

```

And #iptables -L
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  192.168.1.0/24       192.168.1.0/24      
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     tcp  --  anywhere             192.168.1.2         tcp dpt:http 
ACCEPT     tcp  --  anywhere             192.168.1.2         tcp dpt:rsh-spx 
ACCEPT     all  --  192.168.1.0/24       192.168.1.0/24      
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  192.168.1.0/24       192.168.1.0/24      
ACCEPT     all  --  anywhere             anywhere     

```

I can browse to port 80, and ssh to port 222 from VM1 to VM2 without issue.

Help!

EDIT: In case anyone ever runs into something similar

Wasn't using DNAT...
so I replaced my port forwarding section with:

# **************Forward external ports to LAN IP's**************
iptables -t nat -A PREROUTING -p tcp -d 192.168.10.11 --destination-port 80 -j DNAT --to 192.168.1.2:80
iptables -t nat -A PREROUTING -p tcp -d 192.168.10.11 --destination-port 222 -j DNAT --to 192.168.1.2:222

---

### Post by BkkBonanza on 2010-09-05
If you're using VirtualBox, and depending on how VM1 has it's interface mode set, you may have to forward ports 22,80 on the host machine to  VM1. 

I see you have the FORWARD rules there but I don't know which IP is which. The matching dest IP needs to be for VM1 and it needs to re-write the dest to VM2. 

eg.

iptables -t nat -A PREROUTING -p tcp -i eth0 -d $VM1_IP \
     --dport 80 --sport 1024:65535 -j DNAT --to $VM2_IP:80
iptables -A FORWARD -p tcp -i eth0 -o eth1 -d $VM2_IP \
    --dport 80 --sport 1024:65535 -m state --state NEW -j ACCEPT

Also you need this, or have it configured somewhere else,

echo "1" > /proc/sys/net/ipv4/ip_forward

---

### Post by hiccupatron on 2012-09-05
> **BkkBonanza said:**
> If you're using VirtualBox, and depending on how VM1 has it's interface mode set, you may have to forward ports 22,80 on the host machine to  VM1. 

I see you have the FORWARD rules there but I don't know which IP is which. The matching dest IP needs to be for VM1 and it needs to re-write the dest to VM2. 

eg.

iptables -t nat -A PREROUTING -p tcp -i eth0 -d $VM1_IP \
     --dport 80 --sport 1024:65535 -j DNAT --to $VM2_IP:80
iptables -A FORWARD -p tcp -i eth0 -o eth1 -d $VM2_IP \
    --dport 80 --sport 1024:65535 -m state --state NEW -j ACCEPT

Also you need this, or have it configured somewhere else,

echo "1" > /proc/sys/net/ipv4/ip_forward


Specifically echo "1" > /proc/sys/net/ipv4/ip_forward

Worked like a charm.  Thanks BkkBonanza!

---

