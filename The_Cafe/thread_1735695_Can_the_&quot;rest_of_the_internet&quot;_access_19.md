---
title: "Can the &quot;rest of the internet&quot; access 192.168 addresses?"
date: 2011-04-21
forum: The Cafe
---

### Post by Dustin2128 on 2011-04-21
I'm curious, I got my server setup, and even got a co.cc domain name for it pointed at the ip as delivered by the command ifconfig | grep inet. Will people not on my network be able to view the site? It just seemed... too easy.

---

### Post by jerenept on 2011-04-21
wat?

---

### Post by Dustin2128 on 2011-04-21
> **jerenept said:**
> wat?
I'm thinking that 192.168 consists of local block addresses.

---

### Post by RiceMonster on 2011-04-21
This is the IP of your computer on your local network. If you want people from outside your network to be able to access it, you will have to forward the correct ports on your router, and use the IP address assigned by your ISP. Chances are your IP is assigned via DHCP, which means you cannot count on it to stay the same and mapping a domain name to it is not realistic.


Also, most IPs do not allow website hosting on their home plans, which means you are breaking your agreement with them. If you want to host a website, I would recommended getting a VPS or looking into shared hosting.

---

### Post by undecim on 2011-04-21
192.168 is for local blocks.

For example, my IP on my network right now is 192.168.1.100. The guy sitting next to me has 192.168.1.101... That likely matches the IPs for the first two computers on your network as well if you have a linksys router.

The router has its own IP, which you can view at [http://icanhazip.com/](http://icanhazip.com/) or [http://whatismyip.com/](http://whatismyip.com/). Whenever you connect to the outside network, the router use Network Address Translation to "translate" from your internal IP address (192.168.1.100, in my case) to your internet IP address (67.60.XXX.XXX, in my case). It keeps track of which connections are mapped to your internal address and sends each packet, modified to translate the addresses, to the proper computer.

The only way someone can access a 192.168 ip address on your network is if you set up port forwarding or DMZ. Otherwise, anything sent to your internet IP that doesn't match a connection initiated by a computer on your network is rejected.

---

### Post by Dustin2128 on 2011-04-21
> **RiceMonster said:**
> This is the IP of the your computer on your local network. If you want people from outside your network to be able to access it, you will have to forward the correct ports on your router, and use the IP address assigned by your ISP. Chances are your IP is assigned via DHCP, which means you cannot count on it to stay the same and mapping a domain name to it is not realistic.


Also, most IPs do not allow website hosting on their home plans, which means you are breaking your agreement with them. If you want to host a website, I would recommended getting a VPS or looking into shared hosting.
Well damn. Turns out my ISP charges 14.95$/mo extra for a fixed IP too...

---

### Post by wrtpeeps on 2011-04-21
> **Dustin2128 said:**
> Well damn. Turns out my ISP charges 14.95$/mo extra for a fixed IP too...
Most do that because 95% of home users have no need for a static IP address.

---

### Post by Dustin2128 on 2011-04-21
> **wrtpeeps said:**
> Most do that because 95% of home users have no need for a static IP address.
Ah well. Ricemonster, can you run a local minecraft server in the 192.168 block?

---

### Post by Quadunit404 on 2011-04-21
I can answer that since I played on a Minecraft server before (in fact, one run by an irl friend just a few hours ago :D)

No, you can't. You'll need to type in the ISP-assigned IP address of the server maintainer, not the 192.168.x.xx address.

---

### Post by forrestcupp on 2011-04-21
> **Quadunit404 said:**
> I can answer that since I played on a Minecraft server before (in fact, one run by an irl friend just a few hours ago :D)

No, you can't. You'll need to type in the ISP-assigned IP address of the server maintainer, not the 192.168.x.xx address.

You can't just play the game with computers on your local network?

---

### Post by Dustin2128 on 2011-04-21
> **forrestcupp said:**
> You can't just play the game with computers on your local network? 
That's what I'm talking about doing.

---

### Post by undecim on 2011-04-21
> **Dustin2128 said:**
> That's what I'm talking about doing.

I've never played MC before, but I would say that it's definitely possible for you to run a server for just your local network on the 192.168 block. Just know that only people who also have 192.168 addresses on your network can access it (unless you do port forwarding and keep track of your changing WAN IP address. Usually IP addresses will only change when your router is rebooted, but it depends on your ISP. You could always set up a dynamic DNS service if you want to keep it always updated.)

---

