---
title: "OpenVPN errors (same config worked on another machine)"
date: 2008-05-18
forum: Server Platforms
---

### Post by samosamo on 2008-05-18
Since converting my box to ubuntu server I have been unable to get a rather simple installation of OpenVPN working properly.  When googling the error (see below) it seems that this is caused mostly by running IPSec on the same subnet, but I'm not running IPSec or any firewalls.

i used this as a guide: [http://www.thebakershome.net/openvpn_tutorial](http://www.thebakershome.net/openvpn_tutorial)

server.conf
```
port 1194
proto udp
dev tun

ca /etc/openvpn/examples/easy-rsa/2.0/keys/ca.crt
cert /etc/openvpn/examples/easy-rsa/2.0/keys/server.crt
key /etc/openvpn/examples/easy-rsa/2.0/keys/server.key
dh /etc/openvpn/examples/easy-rsa/2.0/keys/dh2048.pem

server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
keepalive 10 120
comp-lzo
persist-key
persist-tun

#tls-auth /etc/openvpn/examples/easy-rsa/2.0/ta.key 0
status  /var/log/openvpn-status.log
log     openvpn.log
verb 3
```

client.conf
```

client

dev tun

proto udp

remote myserver.com 1194

resolv-retry infinite
nobind
persist-key
persist-tun

ca keys/ca.crt
cert keys/sean@myserver.com.crt
key keys/sean@myserver.com.key

ns-cert-type server

comp-lzo

verb 3


```

server log:
```
Sun May 18 20:45:58 2008 OpenVPN 2.1_rc7 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] built on May 14 2008
Sun May 18 20:45:58 2008 /usr/sbin/openssl-vulnkey -q /etc/openvpn/examples/easy-rsa/2.0/keys/server.key
Sun May 18 20:45:59 2008 Diffie-Hellman initialized with 2048 bit key
Sun May 18 20:45:59 2008 TLS-Auth MTU parms [ L:1542 D:138 EF:38 EB:0 ET:0 EL:0 ]
Sun May 18 20:45:59 2008 TUN/TAP device tun0 opened
Sun May 18 20:45:59 2008 TUN/TAP TX queue length set to 100
Sun May 18 20:45:59 2008 ifconfig tun0 10.8.0.1 pointopoint 10.8.0.2 mtu 1500
Sun May 18 20:45:59 2008 route add -net 10.8.0.0 netmask 255.255.255.0 gw 10.8.0.2
Sun May 18 20:45:59 2008 Data Channel MTU parms [ L:1542 D:1450 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
Sun May 18 20:45:59 2008 Socket Buffers: R=[110592->131072] S=[110592->131072]
Sun May 18 20:45:59 2008 UDPv4 link local (bound): [undef]:1194
Sun May 18 20:45:59 2008 UDPv4 link remote: [undef]
Sun May 18 20:45:59 2008 MULTI: multi_init called, r=256 v=256
Sun May 18 20:45:59 2008 IFCONFIG POOL: base=10.8.0.4 size=62
Sun May 18 20:45:59 2008 IFCONFIG POOL LIST
Sun May 18 20:45:59 2008 sean,10.8.0.4
Sun May 18 20:45:59 2008 Initialization Sequence Completed
Sun May 18 20:45:59 2008 MULTI: multi_create_instance called
Sun May 18 20:45:59 2008 xx.xxx.187.134:60961 /usr/sbin/openssl-vulnkey -q /etc/openvpn/examples/easy-rsa/2.0/keys/server.key
Sun May 18 20:45:59 2008 xx.xxx.187.134:60961 Re-using SSL/TLS context
Sun May 18 20:45:59 2008 xx.xxx.187.134:60961 LZO compression initialized
Sun May 18 20:45:59 2008 xx.xxx.187.134:60961 Control Channel MTU parms [ L:1542 D:138 EF:38 EB:0 ET:0 EL:0 ]
Sun May 18 20:45:59 2008 xx.xxx.187.134:60961 Data Channel MTU parms [ L:1542 D:1450 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
Sun May 18 20:45:59 2008 xx.xxx.187.134:60961 Local Options hash (VER=V4): '530fdded'
Sun May 18 20:45:59 2008 xx.xxx.187.134:60961 Expected Remote Options hash (VER=V4): '41690919'
Sun May 18 20:45:59 2008 xx.xxx.187.134:60961 TLS: Initial packet from xx.xxx.187.134:60961, sid=03abc648 e6c4fbc8
Sun May 18 20:46:01 2008 MULTI: multi_create_instance called
Sun May 18 20:46:01 2008 xx.xxx.187.134:60962 /usr/sbin/openssl-vulnkey -q /etc/openvpn/examples/easy-rsa/2.0/keys/server.key
Sun May 18 20:46:01 2008 xx.xxx.187.134:60962 Re-using SSL/TLS context
Sun May 18 20:46:01 2008 xx.xxx.187.134:60962 LZO compression initialized
Sun May 18 20:46:01 2008 xx.xxx.187.134:60962 Control Channel MTU parms [ L:1542 D:138 EF:38 EB:0 ET:0 EL:0 ]
Sun May 18 20:46:01 2008 xx.xxx.187.134:60962 Data Channel MTU parms [ L:1542 D:1450 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
Sun May 18 20:46:01 2008 xx.xxx.187.134:60962 Local Options hash (VER=V4): '530fdded'
Sun May 18 20:46:01 2008 xx.xxx.187.134:60962 Expected Remote Options hash (VER=V4): '41690919'
Sun May 18 20:46:01 2008 xx.xxx.187.134:60962 TLS: Initial packet from xx.xxx.187.134:60962, sid=4f245f76 44a9aaab
...
repeats...
...
...

```

and more after about 60 seconds, where a real error shows:
```

Sun May 18 20:52:18 2008 MULTI: multi_create_instance called
Sun May 18 20:52:18 2008 24.188.187.134:61113 /usr/sbin/openssl-vulnkey -q /etc/openvpn/examples/easy-rsa/2.0/keys/server.key
Sun May 18 20:52:18 2008 24.188.187.134:61113 Re-using SSL/TLS context
Sun May 18 20:52:18 2008 24.188.187.134:61113 LZO compression initialized
Sun May 18 20:52:18 2008 24.188.187.134:61113 Control Channel MTU parms [ L:1542 D:138 EF:38 EB:0 ET:0 EL:0 ]
Sun May 18 20:52:18 2008 24.188.187.134:61113 Data Channel MTU parms [ L:1542 D:1450 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
Sun May 18 20:52:18 2008 24.188.187.134:61113 Local Options hash (VER=V4): '530fdded'
Sun May 18 20:52:18 2008 24.188.187.134:61113 Expected Remote Options hash (VER=V4): '41690919'
Sun May 18 20:52:18 2008 24.188.187.134:61113 TLS: Initial packet from 24.188.187.134:61113, sid=92e73433 c23eb901
[COLOR="Red"][B]Sun May 18 20:52:19 2008 24.188.187.134:61088 TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Sun May 18 20:52:19 2008 24.188.187.134:61088 TLS Error: TLS handshake failed
Sun May 18 20:52:19 2008 24.188.187.134:61088 SIGUSR1[soft,tls-error] received, client-instance restarting
..[/B][/COLOR].
repeats...
...
...

```

client log doesn't really matter, as this log shows up even before any clients connect

---

### Post by sq377 on 2008-05-19
I really don't know all that much about openvpn, but was your certificate generated on a debian based machine before the openssl fiasco?  
metasploit has a good explanation:
[http://www.metasploit.com/users/hdm/tools/debian-openssl/](http://www.metasploit.com/users/hdm/tools/debian-openssl/)

Try to regenerate the certificates and see if it works then.

---

### Post by samosamo on 2008-05-19
it must have been some kind of error with the keys.  i deleted the config and used Webmin to create a new one, i'll be damned if i ever do it again manually.. webmin rocks

---

### Post by papagede on 2012-08-26
I had 41690919 530fdded openvpn errors (remote and local options) not working and switched to tcp  instead of udp and everything started working.  suspect firewall interference maybe - although udp worked before a server upgrade so maybe something with newer version of openvpn.

peace out
gede

---

### Post by sffvba[e0rt on 2012-08-28
[IMG]http://i299.photobucket.com/albums/mm313/Zenzirouj/ThreadNecro.gif[/IMG]


404

---

