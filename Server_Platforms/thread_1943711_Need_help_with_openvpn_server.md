---
title: "Need help with openvpn server"
date: 2012-03-20
forum: Server Platforms
---

### Post by SakAttak on 2012-03-20
I have a vps with ubuntu 10.04 and openvpn installed and am trying to connect with windows with openvpn installed on my windows machine. I can connect to the vpn and ping both the private vpn ip and the public ip of the vps but I cannot get to the internet once connected to the vpn.

here is the conf of the openvpn server: 

[INDENT]dev tun
port 1194
proto tcp
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
ca ca.crt
cert server.crt
key server.key
dh dh1024.pem
push "route 10.8.0.0 255.255.255.0"
push "redirect-gateway"
comp-lzo
keepalive 10 60
ping-timer-rem
persist-tun
persist-key
daemon
log opnvpn.log[/INDENT]

and here is the config for openvpn on windows client:

[INDENT]client
dev tun
dev-node TAP1
proto tcp
remote [server ip] 1194
persist-key
persist-tun
ca "C:\\Program Files (x86)\\OpenVPN\\config\\ca.crt"
cert "C:\\Program Files (x86)\\OpenVPN\\config\\Sovereign.crt"
key "C:\\Program Files (x86)\\OpenVPN\\config\\Sovereign.key"
ns-cert-type server
dhcp-option DNS 8.8.8.8
comp-lzo
route-delay 2
route-method exe
redirect-gateway def1
verb 3[/INDENT]

---

### Post by RyanRahl on 2012-03-20
Are you trying to route your traffic through the VPN or are you just connecting to the VPN for remote access and using your local internet connection for web access?
I would start by checking your default gateway on your client with
```
ipconfig /all
```
to see if your route is set for the VPN or the local network.
If you ARE trying to route your traffic through the VPN I would check the routing information on the server to see if it is configured to route VPN traffic through the gateway of the VPN.

---

### Post by SeijiSensei on 2012-03-20
Plus, if you are routing traffic over the tunnel, you need to have a specific route in place that tells the machine how to reach the remote OpenVPN host.  If you route **all** the traffic through the tunnel, then there's no way for the two machines to exchange the UDP packets in which the encapsulated data is carried.

I don't know how to set up routing on Windows, but you need to have both a point-to-point route between the public interface of your machine and that of the OpenVPN remote, and a default route that uses the other end of the VPN tunnel as the default gateway.

---

### Post by d4m1r on 2012-03-21
Did you configure the openvpn server to route ipv4 traffic to the internet?

---

