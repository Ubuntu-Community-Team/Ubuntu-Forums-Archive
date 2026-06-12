---
title: "OpenVPN, weird problem, missing route"
date: 2008-06-10
forum: Server Platforms
---

### Post by samosamo on 2008-06-10
It seems my battle against OpenVPN is coming to an end (I'm winning).  I've spent many hours learning how to configure it for a routed connection but I'm sure it will pay off.  I just have one last question.

When starting the VPN server it deletes the route to my gateway and does not readd it.  I have to readd it manually.  Without doing this, I cannot connect to/from outside the LAN on this machine.  Something wrong with my config?

openvpn and bridge-utils are installed from repos.  I manage the config/keys through Webmin.

Here is a working route without OpenVPN started:
> $ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         tomato          0.0.0.0         UG    100    0        0 eth0

Here is a broken route after starting OpenVPN, and how I fix it:
> 
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 br0

$ route add default gw 192.168.1.1

$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 br0
default         tomato          0.0.0.0         UG    0      0        0 br0


> 
port 1194
proto udp
dev tap0
ca keys/myserver.com/ca.crt
cert keys/myserver.com/myserver.com.crt
key keys/myserver.com/myserver.com.key
dh keys/myserver.com/dh2048.pem
server-bridge 192.168.1.10 255.255.255.0 192.168.1.150 192.168.1.200 #@@ br0 eth0
crl-verify keys/myserver.com/crl.pem
ifconfig-pool-persist servers/myserver.com/logs/ipp.txt
cipher AES-128-CBC
user nobody
group nogroup
status servers/myserver.com/logs/openvpn-status.log
log-append servers/myserver.com/logs/openvpn.log
verb 2
mute 20
max-clients 100
keepalive 10 120
client-config-dir /etc/openvpn/servers/myserver.com/ccd
comp-lzo
persist-key
persist-tun
ccd-exclusive
up servers/myserver.com/bin/myserver.com.up
plugin /usr/lib/openvpn/openvpn-down-root.so "/etc/openvpn/servers/myserver.com/bin/myserver.com.down-root"
push "route 192.168.1.0 255.255.255.0"
push "dhcp-option DNS 192.168.1.1"



and one more thing, anyone know why webmin decides to run 2 openvpn's?  one as root, the other as nobody?  weird..

> $ ps aux | grep openvpn
root 7877 0.0 0.0 3992 460 ? Ss 23:14 0:00 /usr/sbin/openvpn --writepid /var/run/openvpn.myserver.com.pid --daemon ovpn-myserver.com --cd /etc/openvpn --config /etc/openvpn/myserver.com.conf
nobody 7905 0.1 0.1 4580 1908 ? Ss 23:14 0:01 /usr/sbin/openvpn --writepid /var/run/openvpn.myserver.com.pid --daemon ovpn-myserver.com --cd /etc/openvpn --config /etc/openvpn/myserver.com.conf
sean 8071 0.0 0.0 3004 772 pts/2 S+ 23:32 0:00 grep openvpn

$ sudo netstat -anp | grep vpn
udp 0 0 0.0.0.0:1194 0.0.0.0:* 7905/openvpn
unix 3 [ ] DGRAM 19931 7877/openvpn
unix 3 [ ] DGRAM 19930 7905/openvpn 


---

### Post by samosamo on 2008-06-12
Problem solved, the issue is that the webmin OpenVPN module (third party) does not have an option to set a gateway IP.  I had to manually edit the up/down bridge scripts and add the -gw switch.  I notified the developer, maybe it will be fixed in a future release.

---

