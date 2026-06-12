---
title: "Need Help with OpenVPN server accepting connections but not allowing traffic"
date: 2019-02-03
forum: Server Platforms
---

### Post by kurval on 2019-02-03
Hello,

I have installed Ubuntu 16.04 on a rooted Android box with Linux Deploy to make it a OpenVPN server. I have diligently followed the guide at [https://nanashi07.blogspot.com/2017/04/build-openvpn-server-on-android-device.html](https://nanashi07.blogspot.com/2017/04/build-openvpn-server-on-android-device.html) and the one at [https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-16-04) and I have used keys and certificates that do work correctly on a Windows server.

The OpenVPN client connects correctly to the server, but at that point it can't go outside. In facts, the only thing I managed to do from the client is ping 10.8.0.6 which is its own IP assigned by the VPN server, can't even ping the server itself. After studying a lot and spending 2 days playing around with  configuration, I have come to the conclusion that I need to ask for some  help. I can't understand what I am doing wrong.

In particular, some things that I did (as I see they are often reason for a problem similar to mine) are:
modifying the /etc/sysctl.conf file, uncommenting
[FONT=courier new]net.ipv4.ip_forward=1[/FONT]

modified /etc/ufw/before.rules with
```
# START OPENVPN RULES
# NAT table rules
*nat
:POSTROUTING ACCEPT [0:0] 
# Allow traffic from OpenVPN client to eth0
-A POSTROUTING -s 10.8.0.0/8 -o eth0 -j MASQUERADE
COMMIT
# END OPENVPN RULES
```

modified the  the /etc/default/ufw with
```
DEFAULT_FORWARD_POLICY="ACCEPT"
``` and I also changed the default input policy to "Accept" for now, this was not required but should not be the cause of my problem.

The openvpn server configuration is 

```
port 1194
proto udp
dev tun
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret
dh dh1024.pem
tls-auth ta.key 0
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS 8.8.8.8"
push "dhcp-option DNS 8.8.4.4"
keepalive 10 120
cipher AES-256-CBC
comp-lzo
persist-key
persist-tun
status openvpn-status.log
verb 3
```

Ifconfig now reads

```
eth0      Link encap:Ethernet  HWaddr c4:2a:fe:48:63:81
          inet addr:192.168.0.174  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::c62a:feff:fe48:6381/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4065 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2351 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:997126 (997.1 KB)  TX bytes:1110696 (1.1 MB)
          Interrupt:56

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00                      -00
          inet addr:10.8.0.1  P-t-P:10.8.0.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:0 (0.0 B)  TX bytes:200 (200.0 B)

```

Can anyone please help me out?

Many Thanks!

---

### Post by TheFu on 2019-02-03
Does the machine have an wlp11s0 interface that you want to use?

---

### Post by kurval on 2019-02-03
No sorry, I copied the code from an old template. The interface is correctly set to eth0 in the before.rules. I edited the post to correct my mistake. Thank you!

---

### Post by darkod on 2019-02-03
Have you tried with plain iptables rules and without using ufw? I have always found ufw unnecessary because it is only a frontend to iptables (and rather confusing frontend if I may add).

Disable ufw and try iptables. It seems you have done what you need. For OpenVPN routing to work you only need the forwarding allowed in sysctl.conf and the masquerade rule in iptables.

Did you reboot to make the sysctl.conf change active?

PS. If you can't even ping 10.8.0.1 (the openvpn server IP) from the client, then the firewall might be blocking you. Or blocking ping requests at least. Even if the openvpn server does not route your traffic to the internet correctly, you should always be able to ping it after successfully connecting to it.

---

