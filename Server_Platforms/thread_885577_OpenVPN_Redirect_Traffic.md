---
title: "OpenVPN Redirect Traffic"
date: 2008-08-10
forum: Server Platforms
---

### Post by BoGs on 2008-08-10
Ubuntu 8.04 server installed
OpenVPN installed and configured I guess

I set up OpenVPN manually with the certificates and keys and all the fun stuff.

what i need to do is to connect to VPN from some place and have all my web traffic routed/tunneled through the VPN and out the vpn network.

192.168.0.100 (Compter)
|
192.168.0.1 (Home Router)
|
{CABLE INTERNET}
|
VPN IP (VPN IP) 255.255.255.255

I can connect to the VPN and it hands me out a 10.8.0.x ip address and I can ping it but nothign after that. This vpn is on a vps.

openvpn.conf (server)
```

dev tun
proto tcp
port (VPNPORT)

ca /etc/openvpn/easy-rsa/keys/ca.crt
cert /etc/openvpn/easy-rsa/keys/server.crt
key /etc/openvpn/easy-rsa/keys/server.key
dh /etc/openvpn/easy-rsa/keys/dh1024.pem
tls-auth /etc/openvpn/easy-rsa/keys/ta.key 0

user nobody
group nogroup
server 10.8.0.0 255.255.255.0

persist-key
persist-tun

keepalive 10 120

status openvpn-status.log
verb 3
client-to-client
max-clients 3

push "route VPNIP(FIRST3).0 255.255.255.0"
push "redirect-gateway def1"

#log-append /var/log/openvpn
comp-lzo 


```

sysctl.conf
```
# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1

```

when I try to run IP tables
```

iptables -A POSTROUTING --table nat -o ! tun0 -j MASQUERADE
iptables: No chain/target/match by that name

```

if anyone would be able to help me that would be great and much appreciated .... thanks

---

### Post by BoGs on 2008-08-10
I am running on VPS - HyperVM and it doesnt do masquerading so I did for anyone that is interested

```

iptables -t nat -A POSTROUTING -i 10.8.0.0/24 -o venet0 -j SNAT --to (venet0 ip)

```

---

