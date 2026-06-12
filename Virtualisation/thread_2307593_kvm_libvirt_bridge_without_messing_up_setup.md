---
title: "kvm libvirt bridge without messing up setup"
date: 2015-12-26
forum: Virtualisation
---

### Post by ReaperX14 on 2015-12-26
Hello, I have a bit of a unique configuration going with my home network. So before I explain what I want to do, I will give you some information about my setup.

I have a main ubuntu server box which acts as a gateway and handles dns / dhcp and various other network stuffs. The internet interface is usb0 and the lan interface is eth0.

This script is used to turn the box into a gateway through usb0 interface:
```

#!/bin/sh


PATH=/usr/sbin:/sbin:/bin:/usr/bin
iface=usb0
lanface=eth0


#
# delete all existing rules.
#
iptables -F
iptables -t nat -F
iptables -t mangle -F
iptables -X


# Always accept loopback traffic
iptables -A INPUT -i lo -j ACCEPT


# Allow established connections, and those not coming from the outside
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -m state --state NEW ! -i $iface -j ACCEPT
iptables -A FORWARD -i $iface -o $lanface -m state --state ESTABLISHED,RELATED -j ACCEPT


# Allow outgoing connections from the LAN side.
iptables -A FORWARD -i $lanface -o $iface -j ACCEPT


# Don't allow DHCP packets outside our lan
iptables -A FORWARD -i $lanface -o $iface -p tcp --dport 67 -j REJECT


# Masquerade.
iptables -t nat -A POSTROUTING -o $iface -j MASQUERADE


# Don't forward from the outside to the inside.
iptables -A FORWARD -i $iface -o $lanface -j REJECT


# Drop outside traffic except ssh
iptables -A INPUT -p tcp --dport ssh -j ACCEPT -i $iface
iptables -A INPUT -j DROP -p tcp -i $iface


# Enable routing.
echo 1 > /proc/sys/net/ipv4/ip_forward


# Proxy through squid3
iptables -t nat -A PREROUTING -i $lanface -p tcp --dport 80 -j REDIRECT --to-port 3128
iptables -t nat -A OUTPUT -p tcp -m owner ! --uid-owner proxy --dport 80 -j REDIRECT --to-port 3128
iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to 3128

```
My traffic on port 80 has to pass through squid in order for me to remain connected to the internet.

The interface config for eth0 is:
```

allow-hotplug eth0iface eth0 inet static
    address 10.1.1.2
    netmask 255.255.255.0
    dns-nameservers 10.1.1.2, 8.8.8.8

```

I want to be able to create a bridged interface for my virtual machines so I can connect to them via the lan kind of like virtualbox's bridged option however, they also need to have the same rules as above for passing port 80 through squid. If I try and create a br0 interface my iptables setup fails and none filtered net traffic makes it to the internet which is bad in my case.

How do I set it up so that my virtual machines can 'connect' to my lan with internet access (and their owns IPs) and my Ubuntu host still remains the gateway of my network with traffic passing through squid3?

---

