---
title: "what network swicth is best with Ubuntu"
date: 2008-07-28
forum: The Cafe
---

### Post by bigbrovar on 2008-07-28
Last Friday Lighten stroke our IT building .. frying 2 of our network switches .. :( .. we are currently looking for switches to replace them with .. the dead swicthes where DLINKs  and they suck .. so in a way the Lightening just helped us put an end to their miserable live :) . anyway before we buy anything i felt i should ask anybody where which switch is best with an Ubuntu networks .. we need 24 port gigabit switches and right now am thinking NETGEAR OR LINKSYS .. i feel cisco is proprietary so it might not fit our settings ... 

we run Ubuntu servers one of which is our firewall .. so what we need is a switch that would just fit into the arrangement.. thanks in advance

---

### Post by fedex1993 on 2008-07-28
I would defently go with a netgear switch. There very nice. I have a 24 port in my parents closet since our house is wired with cat5e.

---

### Post by lisati on 2008-07-28
I have a Netgear beast with 4 regular ethernet connections which automatically sense the kind of connection (no need to worry about details like whether or not to use a crossover cable), one WAN connection (hooked up to a D-link router/ADSL modem), and wireless (b & g). No problems so far, and it has a good range of browser-based configuration options (including the facility to block websites and send logs by email)

---

### Post by LaRoza on 2008-07-28
I use a Netgear with no problems. They really shouldn't have any issues.

---

### Post by Trail on 2008-07-28
I am sorry but, unless my networks understanding is way off, what does a switch have to do with the OSes that the nodes of the network are running on? A switch is supposed to be software-transparent, isn't it?

Unless you mean things like http access to control it or whatever, for which I guess firefox is enough.

---

### Post by red_Marvin on 2008-07-28
I have a netgear one which works fine, and my parents' level1 works well too. I've never used but have heard good things about linksys, and I've had problems with D-link.
However that is from trying one of each, so it really isn't anything to base reliable statistics on. And I've even managed to get the D-link one working again.

Most if not all routers should be browser configurable (the one's I've tried are) and the os should not matter since network traffic is standardised.

---

### Post by koenn on 2008-07-28
> **Trail said:**
> I am sorry but, unless my networks understanding is way off, what does a switch have to do with the OSes that the nodes of the network are running on? A switch is supposed to be software-transparent, isn't it?

Unless you mean things like http access to control it or whatever, for which I guess firefox is enough.

you're right. 
Switches just move ethernet frames and have no knowledge of the application / operating system they're coming from or going to

applications / operating systems are only aware of the IP address on the network, and have no knowledge of which and how many switches the data pass through to reach an other host.

---

### Post by AbdRahim on 2008-08-09
My new Linksys SD2008 gigabit switch does not work with new versions of Linux (openSuSe 11.0, or Ubuntu 8.04). It worked fine with older versions. Now if I plug either computer into this switch, the lights on the switch do not even light to indicate a connection. I have had to plug both linux boxes back into the router directly. Here they both work fine. WinXP computers pluged into the swicth work fine (including the openSuSe box when running XP). Can't figure this out. I will try a different brand switch if I can find one locally.

Any ideas on this would be greatly appreciated.

---

### Post by pparks1 on 2008-08-09
Like others have said, switches are switches and can be used regardless of the computer and operating systems that you are using.

As far as Cisco being proprietary..I have no idea what you are saying.   Cisco more or less dominates the market as far as switches and routers go.   They are certainly expensive, but well worth the money with regards to features and such.    In order to configure in an enterprise environment, they certainly do take some know-how of Cisco commands...but that's quite a valuable skill to possess in the job market...so it's worth spending a little time and learning.

---

### Post by Parp on 2008-08-09
I would recommend the HP procurve switches (2810), a bit pricey but they do have lifetime warranty. They also have nice features like network-loop detection (you need to manually set it, but it's easy)..

The problems with differing versions of linux and switch connections could be a few things, probably duplex-mismatch or maybe a badly configured switch. Some drivers can be flaky on spanning-tree configs, but again that's usually badly configured topology.

---

