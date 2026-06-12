---
title: "redirect web traffic through VPN what am I doing wrong?"
date: 2008-08-06
forum: Server Platforms
---

### Post by bekamyn on 2008-08-06
Ubuntu 8.04 server installed
OpenVPN installed and misconfigured

I set up OpenVPN manually with the certificates and keys and all the fun stuff.

WHAT I WANT: to connect to VPN from some place and have all my web traffic routed/tunneled through the VPN and out my home network.

Network
{ DSL }
  |
Router 192.168.254.254
  |
VPN at 192.168.254.134
  handing out 10.8.0.x

So, I can set up a TUN based solution just like I had on my WRT54GS (running openwrt) but it doesn't work the same.

I **CAN** connect from the outside (work) to the VPN and get an IP. I **CAN'T** get anywhere after that. 

my server.conf
```

port 1194
proto udp
dev tun

ca /etc/openvpn/keys/ca.crt
cert /etc/openvpn//keys/server.crt
key /etc/openvpn/keys/server.key  # This file should be kept secret

dh /etc/openvpn/keys/dh1024.pem

server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt

;push "route 192.168.254.254 255.255.255.0"

push "redirect-gateway def1"

push "dhcp-option DNS 192.168.254.254"
keepalive 10 120
tls-auth /etc/openvpn/keys/ta.key 0 # This file is secret

comp-lzo
max-clients 3
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 3
mute 20


```

/etc/sysctl.conf 
```

# default except for
# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1

```

rc.local
```

/sbin/iptables -A POSTROUTING --table nat -o ! tun0 -j MASQUERADE
exit 0

```

So I did a lot reading and been reading my openvpn logs on the client and it complains that 192.168.254.254 isn't in the 255.255.255.0 mask. I don't understand that.
I'm not 100% I've even got Iptables running so let's assume no at this point.

What is the error of my ways?

---

### Post by joebeasley on 2008-08-06
uncomment the push route and change it to 192.168.254.0 255.255.255.0.

---

### Post by bekamyn on 2008-08-07
> **joebeasley said:**
> uncomment the push route and change it to 192.168.254.0 255.255.255.0.

Makes sense but here's what I got in my client log.

[quote=see solution]
Thu Aug 07 11:56:52 2008 us=790 route ADD 192.168.254.0 MASK 255.255.255.0 10.8.0.9
Thu Aug 07 11:56:52 2008 us=56388 ROUTE: route addition failed using CreateIpForwardEntry: One or more arguments are not correct.   [if_index=15][/quote]

Solution: that'a a Vista problem download the latest DEV of openvpn client and run it as administrator 
[http://skriptd.wordpress.com/2007/07/12/openvpn-gui-on-windows-vista/](http://skriptd.wordpress.com/2007/07/12/openvpn-gui-on-windows-vista/)

Now, I connect, I can get to my internal network by 192.168 I can get out, sortof. My DNS address is wrong, I can get to [http://64.233.187.99/](http://64.233.187.99/) but not [http://www.google.com](http://www.google.com). That should be an easy fix

---

### Post by bekamyn on 2008-08-09
The working server.conf

```

port 1194
proto udp

dev tun

ca /etc/openvpn/keys/ca.crt
cert /etc/openvpn//keys/server.crt
key /etc/openvpn/keys/server.key  
dh /etc/openvpn/keys/dh1024.pem

server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt

push "route 192.168.254.0 255.255.255.0"

push "redirect-gateway def1"

push "dhcp-option DNS 192.168.254.254"
keepalive 10 120

tls-auth /etc/openvpn/keys/ta.key 0 # This file is secret

comp-lzo
max-clients 3

user nobody
group nogroup

persist-key
persist-tun
status openvpn-status.log
verb 3
mute 20

```

---

