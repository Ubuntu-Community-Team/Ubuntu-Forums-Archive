---
title: "IPTABLES and SAMBA behind NAT"
date: 2008-05-28
forum: Server Platforms
---

### Post by admarginem on 2008-05-28
Hi all, 

we have a samba server (windows 2k3) behind the linux box (dapper) running NAT. 

I am trying to configure iptables port forwarding from external network to internal samba server but without success. 

My iptables script is:

```
#!/bin/bash
echo 1 > /proc/sys/net/ipv4/ip_forward

IF_EXT="eth1"
IF_INT1="eth0"

NT_EXT="EXTERNAL IP"
NT_INT1="192.168.1.0/24"

PINKSTAR="192.168.1.3"

IPTABLES="/sbin/iptables"

# Clear all
$IPTABLES -F
$IPTABLES -X
$IPTABLES -Z
$IPTABLES -F -t nat
$IPTABLES -X -t nat
$IPTABLES -Z -t nat

$IPTABLES -A INPUT -i lo -j ACCEPT
$IPTABLES -A OUTPUT -o lo -j ACCEPT

# Default policy: accept all
$IPTABLES -P INPUT ACCEPT
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -A FORWARD -p tcp -m multiport --dport 554,1755 -j DROP
$IPTABLES -P FORWARD ACCEPT

$IPTABLES -A FORWARD -i $IF_INT1 -j ACCEPT

# Masquarade
$IPTABLES -t nat -A POSTROUTING -o $IF_EXT -j SNAT --to-source $NT_EXT

# SAMBA 
$IPTABLES -t nat -A PREROUTING -p udp -i $IF_EXT -d $NT_EXT -m multiport --dport 137,138 -j DNAT --to $PINKSTAR
$IPTABLES -t nat -A PREROUTING -p tcp -i $IF_EXT -d $NT_EXT -m multiport --dport 139,445 -j DNAT --to $PINKSTAR
```

Thank you

---

### Post by NateMan on 2008-05-28
Please explain in greater detail what you mean by your running samba on a windows box? that's a linux program. Do you mean you have windows file shares available off of that machine?

---

### Post by admarginem on 2008-05-30
yes, I mean windows share

---

