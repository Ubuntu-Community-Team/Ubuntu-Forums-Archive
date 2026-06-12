---
title: "VPN server?"
date: 2023-10-04
forum: Server Platforms
---

### Post by josephchrzempiec on 2023-10-04
Hello, I'm looking to install a new small micro server. Normally I would use openVPN. However I'm al ittle stuck because I have 3 computer and I need to keep them open and login at all times. The problem with openVPN is that only 2 connections at a time and it is free. If I add a third computer connection they will charge me 70 per month for 5 connections.  I don't currently have that much to cover it and I don't need that many connections. 

My question would be is there another vpn server software that will let me do 3 [COLOR=#273139][FONT=Inter]Concurrent connections without costing me that much?

Joseph


[/FONT][/COLOR]

---

### Post by slickymaster on 2023-10-04
*Thread moved to **Server Platforms**.*

---

### Post by The Cog on 2023-10-04
Look at wireguard. It's much easier to configure than OpenVPN and there are no strange licensing restrictions. wireguard is in the repositories.

---

### Post by TheFu on 2023-10-04
openvpn has no built-in limitations, unless you use their front-end tool for configuration.  Don't use that and you can have hundreds of connections, depending on the hardware, for free.

Or use wireguard ... which is pretty easy to setup point-to-point connections, but you'll need to setup pre and post routing rules to access any other systems.

Or use an overlay network which will create an encrypted channel between any number of systems, basically, they would all be on the same subnet, regardless of where they are located around the world.  Nebula is one of these grid networks.  [https://arstechnica.com/gadgets/2019/12/how-to-set-up-your-own-nebula-mesh-vpn-step-by-step/](https://arstechnica.com/gadgets/2019/12/how-to-set-up-your-own-nebula-mesh-vpn-step-by-step/)

---

### Post by SeijiSensei on 2023-10-04
Right now my VPN hub has eight processes that look like this with "ps ax":
```
 1279 ?  Ss  5:42 /usr/sbin/openvpn --daemon --writepid /var/run/openvpn/mail.pid --cd /etc/openvpn --config mail.conf --script-security 2
```
with different configuration files. Each process listens on a unique port. I use static-key implementations because they are easy to support. The server only allows a small number of remote IP addresses to connect.

As TheFu said, I could have hundreds. 

[https://openvpn.net/community-resources/static-key-mini-howto/](https://openvpn.net/community-resources/static-key-mini-howto/)

---

### Post by josephchrzempiec on 2023-10-04
I'm looking at wireguard. Because my router that is at my other place it has openvpn that is what I connect to as a server. Crazy thing about it is that router also has wireguard as well. I have never used it but I will take a look at it. From what I'm reading at the openVPN site it state 2 connections at one time for free then I would need to pay. 

> **The Cog said:**
> Look at wireguard. It's much easier to configure than OpenVPN and there are no strange licensing restrictions. wireguard is in the repositories.

---

### Post by josephchrzempiec on 2023-10-04
Are you sure? I looked at the openVPN site and it states in the license area that only 2 connections at a time after that it say I need to pay. I have 3 computers I use for clients and one server that is across town.


> **TheFu said:**
> openvpn has no built-in limitations, unless you use their front-end tool for configuration.  Don't use that and you can have hundreds of connections, depending on the hardware, for free.

Or use wireguard ... which is pretty easy to setup point-to-point connections, but you'll need to setup pre and post routing rules to access any other systems.

Or use an overlay network which will create an encrypted channel between any number of systems, basically, they would all be on the same subnet, regardless of where they are located around the world.  Nebula is one of these grid networks.  [https://arstechnica.com/gadgets/2019/12/how-to-set-up-your-own-nebula-mesh-vpn-step-by-step/](https://arstechnica.com/gadgets/2019/12/how-to-set-up-your-own-nebula-mesh-vpn-step-by-step/)

---

### Post by josephchrzempiec on 2023-10-04
I will take a look at it thank you.


> **SeijiSensei said:**
> Right now my VPN hub has eight processes that look like this with "ps ax":
```
 1279 ?  Ss  5:42 /usr/sbin/openvpn --daemon --writepid /var/run/openvpn/mail.pid --cd /etc/openvpn --config mail.conf --script-security 2
```
with different configuration files. Each process listens on a unique port. I use static-key implementations because they are easy to support. The server only allows a small number of remote IP addresses to connect.

As TheFu said, I could have hundreds. 

[https://openvpn.net/community-resources/static-key-mini-howto/](https://openvpn.net/community-resources/static-key-mini-howto/)

---

### Post by TheFu on 2023-10-05
> **josephchrzempiec said:**
> Are you sure? I looked at the openVPN site and it states in the license area that only 2 connections at a time after that it say I need to pay. I have 3 computers I use for clients and one server that is across town.

100% certain.  I ran an OpenVPN server for almost a decade.  That site is there to get people who don't know what they are doing to pay.  openvpn is F/LOSS.  That site provides value by making it easy to setup.  If you do the setup manually, it is 100% free.  Because openvpn is so complex, most people don't have the patience to wade through the documentation, nor the understanding about routing, to make it work well.  But there are thousands, if not 100s of thousands of people that have setup openvpn without the paid version.  

OpenVPN is complex because it handles 500 types of connections that most people don't need/want.  If you just need 3 types of connections like most of us, 95% of the openvpn code isn't needed.

```
sudo apt install openvpn
```

Then configure it.  But if you haven't learned openvpn, learning wireguard is easier, simpler, AND faster.  Connections with wireguard push more data too.

Most people need one of these types of connections:
a) connect two LANS, but not allow internet through the VPN.
b) connect 1 system to a LAN, no internet.
c) connect 1 system to a LAN, force internet through the VPN.

a and b are trivial.
c requires adding routing rules through a gateway too by the VPN admin.

Wireguard is UDP only for the connection. I'm talking about the actual VPN node-to-node connections.
OpenVPN supports both UDP and TCP connections. The use of TCP can be used on networks that fully block all UDP traffic or when only HTTPS is allowed, since openvpn servers can be setup on port 443:tcp, just like HTTPS servers.

Youj know, there are a number of github projects to make setting up almost all the different VPN options easier. Wireguard, openvpn, IPSec, Tinc, Nebula, and 10 others.  If you have Apple stuff, IPSec is probably the best.  For Android, wireguard and openvpn are pretty easy to setup. There's actually a wireguard QRCode setup method to setup connections.

I'm not a fan of using a router to also run any VPN server software. There are important security implications, especially with consumer routers.  I patch my router weekly.  Usually, there are updates 2x a month. If your router software isn't maintained by the vendor/updated that often, maybe it isn't being maintained anymore and it is time for new hardware to get 3 more years of support.  My router is a low-power x86 running opnsense, almost 10 yrs old.  OpenWRT would be good as well.  Just because the router supports XYZ capabilities, that doesn't make using them a good idea.

---

