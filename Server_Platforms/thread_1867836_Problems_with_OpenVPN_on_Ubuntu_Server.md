---
title: "Problems with OpenVPN on Ubuntu Server"
date: 2011-10-23
forum: Server Platforms
---

### Post by Eenexe on 2011-10-23
I set up an OpenVPN server a little while ago, and I can connect just fine. Most services works, Spotify, IRC, TeamViewer, etc. What works, works just fine and there's no problems at all, but there are some things that does not work. FTP does not work for one address (eenexe.com), but works for another domain (radiolive.no).

I really don't see the problem with it. None of Google's services works, but some of Yahoo's services works. Yahoo Answers works, but the login is not working. 

This is the configuration file for the server
```
local 192.168.1.11
script-security 3
up "/etc/openvpn/up.sh br0"
down "/etc/openvpn/down.sh br0"
port 80
proto tcp
;proto udp
dev tap0
;dev tun
;dev-node MyTap
ca ca.crt
cert server.crt
key server.key # This file should be kept secret
dh dh1024.pem
;server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
server-bridge 10.8.0.4 255.255.255.0 10.8.0.50 10.8.0.100
;server-bridge
;push "route 192.168.10.0 255.255.255.0"
;push "route 192.168.20.0 255.255.255.0"
;client-config-dir ccd
;route 192.168.40.128 255.255.255.248
;client-config-dir ccd
;route 10.9.0.0 255.255.255.252
;learn-address ./script
;push "redirect-gateway def1 bypass-dhcp"
;push "dhcp-option DNS 208.67.222.222"
;push "dhcp-option DNS 208.67.220.220"
;client-to-client
;duplicate-cn
keepalive 10 120
tls-auth ta.key 0 # This file is secret
;cipher BF-CBC # Blowfish (default)
;cipher AES-128-CBC # AES
;cipher DES-EDE3-CBC # Triple-DES
;comp-lzo
;max-clients 100
;user nobody
;group nogroup
persist-key
persist-tun
status openvpn-status.log
;log openvpn.log
;log-append openvpn.log
verb 3
;mute 20
```

ifconfig result
```
br0       Link encap:Ethernet  HWaddr 00:1c:25:3f:70:14  
          inet addr:192.168.1.11  Bcast:0.0.0.0  Mask:255.255.255.0
          inet6 addr: fe80::21c:25ff:fe3f:7014/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48907 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47869 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5885220 (5.8 MB)  TX bytes:16046607 (16.0 MB)

eth0      Link encap:Ethernet  HWaddr 00:1c:25:3f:70:14  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:56383 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57477 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12750753 (12.7 MB)  TX bytes:17421850 (17.4 MB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tap0      Link encap:Ethernet  HWaddr da:a7:7b:44:96:6b  
          inet6 addr: fe80::d8a7:7bff:fe44:966b/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:332 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2207 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:43974 (43.9 KB)  TX bytes:381231 (381.2 KB)
```

/etc/network/interfaces
```
# The loopback network interface
auto lo br0
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

iface eth0 inet dhcp

#auto br0
iface br0 inet static
        address 192.168.1.11
	netmask 255.255.255.0
	gateway 192.168.1.1
	bridge_ports eth0

```
The client I'm using is Viscosity for Mac.

---

### Post by Eenexe on 2011-10-23
I wouldn't have asked if I hadn't done a whole lot of searches on fore-hand. I've haven't been able to figrue out this issue for 2 days.

---

### Post by Eenexe on 2011-10-23
Okay, I've tried finding out what the issue is. And it seems that I can't connect to IP addresses that starts with a number that is greater than 100. As google.com has the IP address 173.194.32.50, I can not connect to that one, but Yahoo Answers has 66.196.66.157, so that is possible. This is a really strange issue and I think it may be connected with tap0. 

I'm not 100% sure that's the issue, but I've tested my theory with a lot of websites, and it seems like that is the problem. If anyone has had a similar issue, I'd like to know how you fixed it.

EDIT: Executing the command "w3m google.com" from the server opens up google.com just fine.

---

### Post by sc0g on 2011-10-26
When you are connected, run the command **route -n** and post the results. I'm not certain, but it could be a problem with your subnet-mask.

---

