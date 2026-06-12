---
title: "Limitting speed on my Ubuntu server"
date: 2014-02-03
forum: Server Platforms
---

### Post by Felhazi_Andrei on 2014-02-03
I have a local network of about 30 computers and i need to limit it to 20Mbps up and 20Mbps down. I want thet limitation to be on the local interface, as well as on the external interface.

I have tried wondershaper and trickle with no luck. Wondershaper limited only the download speeds, while [COLOR=#333333][FONT=UbuntuRegular]trickle did not manage utp connections.

What can I do? I am using ubuntu server 13.10.[/FONT][/COLOR]

---

### Post by tgalati4 on 2014-02-03
What router are you running?  If you load [http://dd-wrt.com](http://dd-wrt.com) or [tomato]("http://www.polarcloud.com/img/ssqosg108.png") firmware you can set Quality of Service (QoS) to very fine detail.

---

### Post by Felhazi_Andrei on 2014-02-03
my ubuntu 13.10 is a router. I do not use any other products except two gigabit switches and a wi-fi router, but that only acts as a wi-fi access point

---

### Post by The Cog on 2014-02-03
[http://tldp.org/HOWTO/Adv-Routing-HOWTO/lartc.ratelimit.single.html](http://tldp.org/HOWTO/Adv-Routing-HOWTO/lartc.ratelimit.single.html)

---

