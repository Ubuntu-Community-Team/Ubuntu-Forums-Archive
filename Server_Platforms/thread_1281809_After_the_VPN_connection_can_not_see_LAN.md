---
title: "After the VPN connection can not see LAN"
date: 2009-10-03
forum: Server Platforms
---

### Post by redelek on 2009-10-03
Good morning, 
 From a few hours struggling with OpenVPN on Ubuntu-server. I join the server without problems. Unfortunately, the merger can not see any computer on the LAN. 
 Switched off the firewall and still nothing. It seems to me that I have a problem with routing.

Server Configuration
```
dev tun
tun-mtu 1500
port 1194
user nobody
group nogroup
comp-lzo
proto tcp-server
ping 20
ping-restart 120
ping-timer-rem
persist-tun
persist-key
daemon
verb 4
log-append /var/log/openvpn.log
duplicate-cn
ca /etc/openvpn/certyfikat_rootca.pem
cert /etc/openvpn/certyfikat_bramy.pem
key /etc/openvpn/klucz_bramy.pem
tls-server
dh /etc/openvpn/dh1024.pem
mode server
server 10.0.3.0 255.255.255.0
ifconfig-pool-persist /etc/openvpn/ipp.txt
#push "redirect-gateway 10.0.1.1/24"
#push "redirect-gateway def1"
push "route 10.0.1.1 255.255.255.0"
push "dhcp-option DNS 10.0.1.3"
push "dhcp-option DNS 194.204.159.1"
push "dhcp-option DNS 194.204.152.34"
push "ping 20"
push "ping restart 120"
```

Computer Configuration
```
tls-client
dev tun
proto tcp-client
comp-lzo
persist-tun
persist-key
verb 4
ca /etc/openvpn/certyfikat_rootca.pem
cert /etc/openvpn/certyfikat_clickad.pem
key /etc/openvpn/klucz_clickad.pem
remote 195.205.XXX.XXX # My public IP
pull
port 1194
ping 15
```

In iptables I have such entries
  	 	 	 	 	```
#echo "1" >/proc/sys/net/ipv4/ip_forward
#iptables -t nat -A POSTROUTING -s 10.0.3.1/24 -o eth0 -j MASQUERADE

```
I'll be very obliged if you would help or information for what I'm doing wrong. 

 Yours
Redelek

---

