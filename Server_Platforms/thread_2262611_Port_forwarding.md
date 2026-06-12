---
title: "Port forwarding"
date: 2015-01-26
forum: Server Platforms
---

### Post by Furqan_Khan on 2015-01-26
Hi there,

Please see attach file for the scenario I'm having difficulty.

Thanks,
Furqan

---

### Post by ian77 on 2015-01-26
The 3550 won't know how to reach the 10.0.0.0/16 network as it's a different network to its own. So you will need to install a static route on the switch, pointing it to server 1, to reach 10.0.0.0/16

Your static route:

```

ip route 10.0.0.0 0.0.255.255 10.3.31.11

```

This sets server 1 as the next hop to reach the 10.0.0.0/16 network.

The server will need configuring to accept packets for the 10.0.0.0/16 network on its eth0 interface and forward it appropriately. I believe this can be achieved by setting a secondary IP address on eth0 and configuring iptables to route the data. But this is not something I'm familiar with.

---

### Post by Furqan_Khan on 2015-01-26
Thanks Ian, I will try to insert static route into 3550 in the evening - Secondary IP here means setting up bridge??

---

### Post by Doug S on 2015-01-26
I assume there is some reason why host 1 can not just access server 1 via [http://10.3.31.11:8080?](http://10.3.31.11:8080?)

---

### Post by Furqan_Khan on 2015-01-26
On the contrary, I have installed webmin on server1 and easily access to [http://10.3.31.11:10000](http://10.3.31.11:10000) - but tried 10.3.31.11:8080 no go

---

### Post by Furqan_Khan on 2015-01-26
If I need to do routing how todo that - I have already configured [COLOR=#FF0000]/etc/[/COLOR][COLOR=#FF0000]sysctl.conf equals to 1 - [/COLOR]I have edited [COLOR=#111111][FONT=Consolas]/etc/rc.local to [/FONT][/COLOR][COLOR=#111111][FONT=Consolas]/sbin/iptables -P FORWARD ACCEPT ; [/FONT][/COLOR][COLOR=#111111][FONT=Consolas]/sbin/iptables --table nat -A POSTROUTING -o eth0 -j MASQUERADE - no go[/FONT][/COLOR]

---

### Post by Doug S on 2015-01-26
> **Furqan_Khan said:**
> On the contrary, I have installed webmin on server1 and easily access to [http://10.3.31.11:10000](http://10.3.31.11:10000) - but tried 10.3.31.11:8080 no goThen I would look at the configuration of "webui" and see if it can be made to listen to that address as well as the local side. By default perhaps it doesn't listen to the external address for security reasons (I don't know, am just guessing), but you will have those concerns anyhow, even if you do end up port forwarding.

---

### Post by Furqan_Khan on 2015-01-26
give me 1 hour  - I am going to university then will post it - this webui is for Juniper opencontrail, jut FYI.

---

### Post by ian77 on 2015-01-27
> **Furqan_Khan said:**
> Thanks Ian, I will try to insert static route into 3550 in the evening - Secondary IP here means setting up bridge??

You can set up a virtual Interface on eth0.

For example you can create an interface called eth0.1 and assign it a  seperate IP address etc.
All configurable from /etc/network/interfaces.

---

### Post by TheFu on 2015-01-29
Switches without routing are dumb.

For the systems on different networks to find each other, they need either 
* a router, 
* a routing switch or 
* static routes added to each machine.

Usually it is easier to setup a router to handle all this than to add static routes to that many servers.  If I had to do it, I'd use ansible.

---

