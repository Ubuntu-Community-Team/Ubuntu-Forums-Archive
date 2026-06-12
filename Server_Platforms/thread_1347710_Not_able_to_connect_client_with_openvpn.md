---
title: "Not able to connect client with openvpn"
date: 2009-12-06
forum: Server Platforms
---

### Post by pawan_lal on 2009-12-06
hi

i had configured openvpn in ubuntu 8.04 lts.



-In my office no firewall is there

-done port forwarding in router (1194 udp)

-Removed iptables (apt-get remove iptables)



now when i am connecting vpn from windows machine i get this error



Connection reset by peer (WSAECONNRESET) (code=10054)



these r server.conf and client.conf



**Server.conf**#local 192.168.1.107
port 1194
proto udp
dev tun

ca /usr/share/doc/openvpn/examples/easy-rsa/2.0/keys/ca.crt
cert /usr/share/doc/openvpn/examples/easy-rsa/2.0/keys/server.crt
key /usr/share/doc/openvpn/examples/easy-rsa/2.0/keys/server.key # This file should be kept secret
dh /usr/share/doc/openvpn/examples/easy-rsa/2.0/keys/dh1024.pem

server 10.8.0.0 255.255.255.0

ifconfig-pool-persist ipp.txt

push "route 192.168.15.0 255.255.255.0"

client-to-client
#push "route ADD 192.168.1.0 MASK 255.255.255.0 10.8.0.1"

keepalive 10 120

user nobody


persist-key 


**Client.conf**

client
float
dev tun
proto udp

remote ipaddress 1194

resolv-retry infinite

nobind

persist-key

persist-tun

ca "C:\\Program Files\\OpenVPN\\config\\oss\\ca.crt"
cert "C:\\Program Files\\OpenVPN\\config\\oss\\client1.crt"
key "C:\\Program Files\\OpenVPN\\config\\oss\\client1.key"

ns-cert-type server

verb 3
mute 20

any help will be highly appreciated

---

