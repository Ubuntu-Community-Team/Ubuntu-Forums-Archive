---
title: "not able to ping office lan from vpn"
date: 2009-06-18
forum: Server Platforms
---

### Post by pawan_lal on 2009-06-18
hi  every1,
 friend i am not able to get success in getting access of lan from outside through vpn. i am telling u about my office network, its a very small network .
office network    - 192.168.1.0/24
linux machine on  - 192.168.1.107/24
which vpn confi
no firewall in office.
using tcp 1194.

now i had configured vpn on my linux box i.e 192.168.1.107 
and at clients side OS is XP n client is easily able to connect to vpn n receive the ip.
but not able to ping office lan.
below is the server.conf   and  client.conf
Server.conf
########################################
port 1194
proto tcp
dev tun
daemon
ca /etc/openvpn/keys/ca.crt
cert /etc/openvpn/keys/server.crt
key /etc/openvpn/keys/server.key  # This file should be kept secret
dh /etc/openvpn/keys/dh1024.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "route 192.168.1.0 255.255.255.0"
keepalive 10 120
user nobody
group nogroup
persist-key
persist-tun
status /var/log/openvpn-status.log
log         /var/log/openvpn.log
log-append  /var/log/openvpn.log
########################################
client.conf
client
dev tun
proto tcp
remote <your WAN IP> 1194
resolv-retry infinite
nobind
persist-key
persist-tun
ca ca.crt
cert client.crt
key client.key
ns-cert-type server
verb 3
########################################
ill be really thankfull for ur support n guidance

---

