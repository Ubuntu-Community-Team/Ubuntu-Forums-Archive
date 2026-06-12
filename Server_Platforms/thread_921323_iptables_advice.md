---
title: "iptables advice"
date: 2008-09-16
forum: Server Platforms
---

### Post by chrno2004 on 2008-09-16
My setup:

Vmware Host (eth0) --- iptables (NAT) --- Vmware GuestOS (vmnet1 :: 192.168.101.0/24)


My iptables config:


```

# Masquerade all traffic (allow NAT traffic through VM Guest)
# vmnet1 --- host-only network --- 192.168.101.0/255.255.255.0

iptables --table nat -A POSTROUTING --out-interface eth0 -j MASQUERADE
iptables -A FORWARD --in-interface vmnet1 -j ACCEPT
iptables -A INPUT -i vmnet1 -s 192.168.101.0/24 -d $SERVER_IP -j ACCEPT

```

I would like to access SAMBA (this sits on the Vmware Host) from within Vmware GuestOS.
e.g. \\192.168.101.1\SAMBA


I'm at a lost at how to configure the iptables to grant this access from the Vmware GuestOS.

Any help or recommendations will be kindly appreciated. :)



chrno

---

### Post by kamaji792 on 2008-09-16
Samba needs the following ports

137 udp
138 udp
139 tcp
445 tcp

Hope that helps.

---

