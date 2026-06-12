---
title: "Unable to browse websites - port forwarding problem."
date: 2008-07-07
forum: Server Platforms
---

### Post by satimis on 2008-07-07
Hi folks,


Ubuntu LAMP server
IP - 192.168.0.52

Local machine
IP - 192.168.0.10


With following iptables rules up running, website can't be browsed both on Internet and Intranet ```

# INPUT

# Set the default policy to drop
iptables -P INPUT DROP

# Allow existing connections to continue
iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Allow the server to talk to itself
iptables -A INPUT -i lo -j ACCEPT

# Allow ssh from workstation local IPadd allowing incoming mails 20080307

iptables -A INPUT -s 192.168.0.10 -p tcp --dport 2222 -j ACCEPT


iptables -A INPUT -p icmp --icmp-type echo-request -j ACCEPT
iptables -A INPUT -j LOG



# OUTPUT

# Set the default policy to drop
iptables -P OUTPUT ACCEPT

# Allow existing connections to continue
iptables -A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# Allow the server to talk to itself
iptables -A OUTPUT -d 127.0.0.1 -j ACCEPT

# Allow DNS requests out
iptables -A OUTPUT -p udp --dport 53 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 53 -j ACCEPT
iptables -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT

```


After adding following rules under INPUT```

# Allow port forwarding
iptables -t nat -A POSTROUTING -o eth0 -s 192.168.0.10 -p 53 -j MASQUERADE
iptables -t nat -A POSTROUTING -o eth0 -s 192.168.0.10 -p 80 -j MASQUERADE

```

Restart iptables.


it still fails.  Please advise.  TIA


B.R.
satimis

---

