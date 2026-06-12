---
title: "Dibbler-server does not send dhcpv6 Advertise packet (DHCPv6 Offer)"
date: 2014-05-09
forum: Server Platforms
---

### Post by andy941111 on 2014-05-09
I have installed dibbler-server and edit /etc/dibbler/server.conf. The below contents is my server.conf[INDENT][COLOR=#0000ff][B]log-level 8
log-mode short
preference 0
iface ppp0 {
 T1 1800
 T2 2700
 prefered-lifetime 3600
 valid-lifetime 7200
 class {
    pool 5000::/48
 }
 pd-class {
     pd-pool 2001:470:8427:000::/56
     pd-length 56
 }
}[/B][/COLOR]

[/INDENT]
I can get the packet of dhcpv6 discovery ( Solicit ) from client, but the server does not send the packet of dhcpv6 offer ( Advertise ). 

Who can help me how to solve this problem? Or can you give me some suggestions???

Thanks a lot!!!!!!


My OS version is Ubuntu Gnome 14.04 LTS x64

---

### Post by andy941111 on 2014-05-09
I try another linux system that is deepin 12.12 i386. The dibbler-server can work normally!! Dibbler-server can send advertise packet to client if the client had send solicit packet to server.
Now I think maybe it just work fine on 32-bit Linux OS.

But, I want it can work normally on 64-bit Linux OS. Who can give me some suggestions??  Many thanks!!!!

---

### Post by andy941111 on 2014-05-09
~"~

I have installed dibbler-server on 32-bit ubuntu 14.04 LTS......But dibbler-server can not work normally.
Client PC send DHCPv6 discovery ( Solicit packet ) to server, but the server did not have any respose to client. dibbler-server did not send DHCPv6 offer ( advertise packet ) to client.

Who can help me  >"<   many thanks!!!!

(I will try it on ubuntu server version.)

---

