---
title: "getting error message while connecting vpn through windows client"
date: 2009-12-06
forum: Server Platforms
---

### Post by pawan_lal on 2009-12-06
hi,
i had configured openvpn in ubuntu 8.04 lts.
 
-In my office no firewall is there
-done port forwarding in router (1194 udp)
-Removed iptables (apt-get remove iptables)
 
now when i am connecting vpn from windows machine i get this error
 
**Connection reset by peer (WSAECONNRESET) (code=10054)**
 
these r server.conf and client.conf
 
**server.conf**
[FONT=Times New Roman][SIZE=3]#local 192.168.1.107[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]port 1194[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]proto udp[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]dev tun[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ca /usr/share/doc/openvpn/examples/easy-rsa/2.0/keys/ca.crt[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]cert /usr/share/doc/openvpn/examples/easy-rsa/2.0/keys/server.crt[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]key /usr/share/doc/openvpn/examples/easy-rsa/2.0/keys/server.key  # This file should be kept secret[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]dh /usr/share/doc/openvpn/examples/easy-rsa/2.0/keys/dh1024.pem[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]server 10.8.0.0 255.255.255.0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ifconfig-pool-persist ipp.txt[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]push "route 192.168.15.0 255.255.255.0"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]client-to-client[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]#push "route ADD 192.168.1.0 MASK 255.255.255.0 10.8.0.1"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]keepalive 10 120[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]user nobody[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3];group nogroup[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]persist-key[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
**client.conf**

[FONT=Times New Roman][SIZE=3]client[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]float[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]dev tun[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]proto udp[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]remote ipaddress 1194[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]resolv-retry infinite[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]nobind[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]persist-key[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]persist-tun[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ca "C:\\Program Files\\OpenVPN\\config\\oss\\ca.crt"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]cert "C:\\Program Files\\OpenVPN\\config\\oss\\client1.crt"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]key "C:\\Program Files\\OpenVPN\\config\\oss\\client1.key"[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ns-cert-type server[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]verb 3[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]mute 20[/SIZE][/FONT]

---

