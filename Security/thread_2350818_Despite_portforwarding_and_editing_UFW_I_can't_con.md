---
title: "Despite portforwarding and editing UFW I can't connect to my openvpn server."
date: 2017-01-28
forum: Security
---

### Post by martifa on 2017-01-28
Hello,

I've been tearing my hair out trying to solve this problem and I hope that you guys can help me solve it.

I have an Ubuntu 16.10 server on which I tried to install Openvpn by using this guide ([https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-16-04)).
Everyting seemed to go smoothly and with lots of self-confidence, I fired up OpenVPN Connect on my android phone (using the network of the mobile provider) ... to find out that it wasn't working.
I did the portforwarding correctly and I've flushed iptables before setting UFW.


Output of "sudo systemctl status openvpn@server":
```
openvpn@server.service - OpenVPN connection to server
   Loaded: loaded (/lib/systemd/system/openvpn@.service; enabled; vendor preset:
   Active: active (running) since Fri 2017-01-27 18:30:33 CET; 20h ago
     Docs: man:openvpn(8)
           [https://community.openvpn.net/openvpn/wiki/Openvpn23ManPage](https://community.openvpn.net/openvpn/wiki/Openvpn23ManPage)
           [https://community.openvpn.net/openvpn/wiki/HOWTO](https://community.openvpn.net/openvpn/wiki/HOWTO)
 Main PID: 828 (openvpn)
   CGroup: /system.slice/system-openvpn.slice/openvpn@server.service
           &#9492;&#9472;828 /usr/sbin/openvpn --daemon ovpn-server --status /run/openvpn/se
```

=======================================================

Output of "ip addr show tun0"
```

4: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN group default qlen 100
    link/none
    inet 10.8.0.1 peer 10.8.0.2/32 scope global tun0
       valid_lft forever preferred_lft forever
    inet6 fe80::4452:4a7c:6da9:20de/64 scope link flags 800
       valid_lft forever preferred_lft forever
```

=======================================================

Output of "ufw status"

```

To                         Action      From
--                         ------      ----
22                         ALLOW       Anywhere
1194/udp                   ALLOW       Anywhere
21/tcp                     ALLOW       Anywhere
OpenSSH                    ALLOW       Anywhere
1194/udp                   ALLOW       Anywhere
22 (v6)                    ALLOW       Anywhere (v6)
21/tcp (v6)                ALLOW       Anywhere (v6)
OpenSSH (v6)               ALLOW       Anywhere (v6)
```
==================================================

```
server.conf:
;local a.b.c.d
port 1194
;proto tcp
proto udp
;dev tap
dev tun
;dev-node MyTap
ca ca.crt
cert server.crt
key server.key  # This file should be kept secret
dh dh2048.pem
;topology subnet
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
;server-bridge 10.8.0.4 255.255.255.0 10.8.0.50 10.8.0.100
;server-bridge
;push "route 192.168.10.0 255.255.255.0"
;push "route 192.168.20.0 255.255.255.0"
;client-config-dir ccd
;route 192.168.40.128 255.255.255.248
;client-config-dir ccd
;route 10.9.0.0 255.255.255.252
;learn-address ./script
push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS 208.67.222.222"
push "dhcp-option DNS 208.67.220.220"
;client-to-client
;duplicate-cn
keepalive 10 120
tls-auth ta.key 0 # This file is secret
key-direction 0

cipher AES-128-CBC   # AES

auth SHA256
comp-lzo
;max-clients 100
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
;log         openvpn.log
;log-append  openvpn.log
verb 3
;mute 20
```
===========================================

```
base.conf

client
;dev tap
dev tun
;dev-node MyTap
;proto tcp
proto udp
remote xxx.xxx.xxx.xxx 1194 (I use the correct IP in de config file)
;remote my-server-2 1194
;remote-random
resolv-retry infinite
nobind
user nobody
group nogroup
persist-key
persist-tun
;http-proxy-retry # retry on connection failures
;http-proxy [proxy server] [proxy port #]
;mute-replay-warnings
#ca ca.crt
#cert client.crt
#key client.key
cipher AES-128-CBC
auth SHA256
key-direction 1
remote-cert-tls server
;tls-auth ta.key 1
;cipher x
comp-lzo
verb 3
;mute 20
```

================================================

I get this message when I want to connect my phone to the OpenVPN network: Waiting for server;
And this is the log file on my phone:

```
Event: Resolve
Contacting: xxx.xxx.xxx.xxx:1194 via UDP (it is in fact showing my real ip)
Event: wait
Server poll timeout, trying next remote entry
```

And this message repeats itself constantly


Does someone has a solution for this problem?

Thanks in advance!

---

### Post by CharlesA on 2017-01-28
It is possible the mobile provider is blocking the port used for OpenVPN, which by default is UDP 1194.

You can verify the port is exposed by checking at a site like [http://www.canyouseeme.org/](http://www.canyouseeme.org/)

---

### Post by martifa on 2017-01-28
Thank you for your reply.
The mobile provider doesn't block this  port, because I'm able to use my phone to connect to my Raspberry Pi  (which is running PiVPN with default 1194 port). 
I wasn't satisfied  with the speed I was getting by running the vpn service on my raspberry  and therefor I decided to use my server. Naturally, I switched the ip  address of the raspberry with my server in the portforwarding settings  of the router.

---

