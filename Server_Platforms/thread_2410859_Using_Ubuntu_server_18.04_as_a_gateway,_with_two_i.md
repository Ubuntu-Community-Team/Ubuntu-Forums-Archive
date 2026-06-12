---
title: "Using Ubuntu server 18.04 as a gateway, with two interfaces."
date: 2019-01-21
forum: Server Platforms
---

### Post by MrMe01 on 2019-01-21
[COLOR=#000000]Hi folks,[/COLOR]

[COLOR=#000000]Here's my current setup, I think it might help to explain how I have things set up.[/COLOR]
[COLOR=#000000]ISP router that serves DNS and DHCP to the household (192.168.*.*), connected via ethernet is an Ubuntu server 18.04 box with two interfaces, on this machine I run Pi-hole and Zentyal.[/COLOR]


[COLOR=#000000]I currently use Zentyal to act as an administration tool, but I wish to move away from it. I use it to set the interface addresses and other details, and use the DNS and DHCP services of Pi-hole. It also allows traffic to move between one interface and the other. Is this bridging, and if so, what packages does Zentyal use, I'd prefer to drop all the configs where required.[/COLOR]

[COLOR=#000000]Something worth noting, I do use Webmin on this machine too, can I enable this bridge like functionality from there?[/COLOR]

[COLOR=#000000]What packages should I be using to replace the monstrosity that Zentyal has become?

I have crossposted this, but this seems to be the better forum for this question,mods, please delete the previous post, thank you[/COLOR]

---

### Post by darkod on 2019-01-22
You put too many things at once.

To reply to your thread title, using ubuntu server as gateway is very easy. You have your external NIC connected to the ISP router. And you have your internal NIC connected to different private LAN subnet with some computers in it.

On the server you need to:
1. Edit /etc/sysctl.conf and enable the net.ipv4.ip_forward=1 parameter. Reboot.
2. Add iptables NAT rule so that traffic crossing from one network to the other knows to find its way back:
```
sudo iptables -t nat -A POSTROUTING -o <ext_interface> -j MASQUERADE
```

You need to make the iptables rule permanent, otherwise it gets lost after reboot. You can do that in any way most suitable to your situation.

That is all you need for server to act as gateway/router. You will set up the clients on the internal LAN to use the server internal IP as gateway.

You can completely remove Zentyal and Webmin if you are only using them for the routing. In fact I would recommend removing Webmin for sure. All administration should be done by ssh.

Only you know which other features from Zentyal/Webmin you are using, and decide whether removing them is safe.

---

