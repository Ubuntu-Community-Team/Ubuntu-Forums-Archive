---
title: "open vpn not pushing default route/gateway"
date: 2010-06-25
forum: Server Platforms
---

### Post by linkshift on 2010-06-25
i have setup an open vpn server and when i connect to it the client pulls an IP and but not default gateway. My goal is to route all web traffic through the VPN... My config file looks like this...

```
dev tun
proto tcp
port 1194
ca /etc/openvpn/easy-rsa/keys/ca.crt
cert /etc/openvpn/easy-rsa/keys/server.crt
key /etc/openvpn/easy-rsa/keys/server.key
dh /etc/openvpn/easy-rsa/keys/dh1024.pem

user nobody
group nogroup
server 10.8.0.0 255.255.255.0

persist-key
persist-tun

#status openvpn-status.log
verb 3
client-to-client

push "route 192.0.2.0 255.255.255.255"
push "route-gateway 192.0.2.1"
push "redirect-gateway def1"

```

its a virtual machine and route -n shows
```
root@linkshift:/etc/openvpn# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.0.2.1       0.0.0.0         255.255.255.255 UH    0      0        0 venet0
10.8.0.2        0.0.0.0         255.255.255.255 UH    0      0        0 tun0
10.8.0.0        10.8.0.2        255.255.255.0   UG    0      0        0 tun0
0.0.0.0         192.0.2.1       0.0.0.0         UG    0      0        0 venet0

```

Networking file "/etc/network/interfaces"
```
auto lo
iface lo inet loopback

auto venet0
iface venet0 inet static
        address 127.0.0.1
        netmask 255.255.255.255
        broadcast 0.0.0.0
        up route add -net 192.0.2.1 netmask 255.255.255.255 dev venet0
        up route add default gw 192.0.2.1
auto venet0:0
iface venet0:0 inet static
        address XXX.93.166.XX
        netmask 255.255.255.255
        broadcast 0.0.0.0

auto venet0:1
iface venet0:1 inet static
        address XXX.93.166.XX
        netmask 255.255.255.255
        broadcast 0.0.0.0

```

and just if anyone's interested, the client config

```
dev tun
client
proto tcp
remote XXX.93.166.XX 1194
ca ca.crt
cert client1.crt
key client1.key
comp-lzo
verb 3
mute 20
resolv-retry infinite
nobind
persist-key
persist-tun
```

---

### Post by linkshift on 2010-06-25
ipconfig on the client windows machine reveals

```

C:\Users\Blue>ipconfig

Windows IP Configuration


Ethernet adapter Local Area Connection 3:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::457c:4c53:636b:b216%20
   IPv4 Address. . . . . . . . . . . : 10.8.0.6
   Subnet Mask . . . . . . . . . . . : 255.255.255.**252**
   Default Gateway . . . . . . . . . :

Wireless LAN adapter Wireless Network Connection 2:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . :
   IPv4 Address. . . . . . . . . . . : 192.168.1.7
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.1.1

```

Why is the Subnet Mask ending in 252? and does that make a diff?

---

### Post by spynappels on 2010-06-26
You cannot push a default gateway that is not on the same subnet, so you need to set 10.8.0.1 as the default gateway for the client and create a static route on your server pushing the traffic to your server's default gateway. 
The subnet mask is showing as 255.255.255.252 because you are creating a P-t-P tunnel, your IP will be 10.8.0.6 on the client and the other side will be 10.8.0.7 on the server. The server will automatically respond to requests on 10.8.0.1 and this is the IP you use to communicate with the server. 

Hope this helps, if you need more answers please ask. 

Stefan.

---

