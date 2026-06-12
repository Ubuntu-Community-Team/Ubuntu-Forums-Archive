---
title: "Bridge same subnets with OpenVPN"
date: 2010-07-09
forum: Server Platforms
---

### Post by Frunktz on 2010-07-09
Hi folks!

I've a little problem..I've configured VPN with different subnets and it works perfeclty, but I have a lot of problem using bridge on same subnet..

Situation:

Location: Hollywood :D
Server1: br0: 192.168.0.1
             eth0: promisc
             tap0: promisc
    - under that location I've some machines (192.168.0.2 - 192.168.0.10)

Location: Tokyo
Client2: actually (Win 2K3, for testing purpose, Ubuntu Server will it be installed in future..)
        bridge IP: 192.168.0.254
        bridge with (first adapter [eth0] and TAP device)
    - under that location ìthe machines IP (192.168.0.200 - 192.168.0.210)     


How I can bridge that lan using same subnet?
I've tried a lot of examples but nothing work...
I've a little doubt...is possible doing that?
Example, on Client2, if I ping 192.168.0.2 (pc in Hollywood location), how he can route correctly? How he can know that the pc from 192.168.0.2 to 192.168.0.10 is under TAP device?

Thanks a lot...
Ps: sorry for my worst English

---

### Post by xls on 2010-07-23
existing documentation: [http://openvpn.net/index.php/open-source/documentation/howto.html#scope](http://openvpn.net/index.php/open-source/documentation/howto.html#scope)

the bridge should blend all traffic from the Ethernet adapters in question (your case tap0 and eth0) kinda like a HUB.  this is much lower level then TCP/IP routing.  in theory it should work.  i suspect a firewall config issue, not a VPN issue.

with your network like so
```
192.168.0.2 - 192.168.0.10 <-server1:eth0-> 192.168.0.1 <-server1:tap0-> vpn tunnel (internet) <-client2:tap0-> 192.168.0.254 <-client2:eth0-> 192.168.0.200 - 192.168.0.210
```

to trouble shoot i would try all of the following
[LIST]
[*]192.168.0.2 pings 192.168.0.10: local, no vpn used
[*]192.168.0.2 pings 192.168.0.1: also local, no vpn used
[*]192.168.0.2 pings 192.168.0.254: vpn used, only local server bridge tested
[*]192.168.0.2 pings 192.168.0.200: vpn used, both bridges tested
[/LIST]

and again from the other side
[LIST]
[*]192.168.0.200 pings 192.168.0.210: local, no vpn used
[*]192.168.0.200 pings 192.168.0.254: also local, no vpn used
[*]192.168.0.200 pings 192.168.0.1: vpn used, only local server bridge tested
[*]192.168.0.200 pings 192.168.0.2: vpn used, both bridges tested
[/LIST]

---

### Post by YesWeCan on 2010-07-23
Would you post your server.conf and client.conf files?
Also, what are the IP addresses of the internet gateways on each network?

---

### Post by sfr on 2010-07-23
a traceroute from one side to the other should clear up that its not a routing problem, just in case :)

---

