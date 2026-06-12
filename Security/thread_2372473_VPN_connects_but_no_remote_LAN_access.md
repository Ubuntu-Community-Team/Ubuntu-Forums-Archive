---
title: "VPN connects but no remote LAN access"
date: 2017-09-25
forum: Security
---

### Post by rpgusmao on 2017-09-25
I need to use ssh to access a cluster through a VPN. I am getting connection to VPN but cant access the cluster via ssh and neither ping to other remote ips.

I already searched and think is related to routing, but I had no sucess. Any ideas?

Thanks for the help!


Output of ifconfig -a:
[HTML]
enp3s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500   
ether 84:7b:eb:e6:94:48  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B) 
       RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Loopback Local)
        RX packets 405  bytes 28332 (28.3 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 405  bytes 28332 (28.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

ppp0: flags=4305<UP,POINTOPOINT,RUNNING,NOARP,MULTICAST>  mtu 1400
        inet 172.23.22.120  netmask 255.255.255.255  destination 172.23.0.5
        ppp  txqueuelen 3  (Protocolo Ponto-a-Ponto)
        RX packets 45  bytes 2864 (2.8 KB) 
       RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 60  bytes 7998 (7.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.15.2  netmask 255.255.255.0  broadcast 192.168.15.255
        inet6 2804:1b1:1181:ac73:3520:988d:48c2:7f1d  prefixlen 64  scopeid 0x0<global>
        inet6 2804:1b1:1181:ac73:b1b4:3639:2b5b:ee81  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::aefb:f867:3897:cfd5  prefixlen 64  scopeid 0x20<link>
        ether 28:56:5a:e9:aa:bf  txqueuelen 1000  (Ethernet)
        RX packets 623546  bytes 815011367 (815.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0 
       TX packets 354679  bytes 52570743 (52.5 MB) 
       TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0[/HTML]


Output of ip route:


[HTML]default via 192.168.15.1 dev wlp2s0 proto static metric 600 
150.161.70.99 via 192.168.15.1 dev wlp2s0 proto static src 
192.168.15.2 169.254.0.0/16 dev wlp2s0 scope link metric 1000 
172.23.0.5 dev ppp0 proto kernel scope link src 172.23.22.120 metric 50 
192.168.15.0/24 dev wlp2s0 proto kernel scope link src 192.168.15.2 metric 600 
192.168.15.1 dev wlp2s0 proto static scope link metric 600 [/HTML]


When I try to ping to 172.23.0.5:
[HTML]PING 172.23.0.5 (172.23.0.5) 56(84) bytes of data.--- 172.23.0.5 

ping statistics ---10 packets transmitted, 0 received, 100% packet loss, time 9199ms[/HTML]

---

### Post by HermanAB on 2017-09-28
Ensure that ppp0 is your default route.

This will tell you what is going on:
$ route

Something like this could fix it:
$ sudo route add default gw 192.168.1.254 ppp0

---

