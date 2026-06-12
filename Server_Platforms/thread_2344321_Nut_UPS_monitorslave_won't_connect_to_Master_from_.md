---
title: "Nut UPS monitor/slave won't connect to Master from different network"
date: 2016-11-24
forum: Server Platforms
---

### Post by jonah1980 on 2016-11-24
I have an issue with NUT / upsd which I'm struggling to get anywhere with. I really hope someone can help?

Although I have two servers in the same room and cabinet sharing the same UPS - they're on different networks!

I can get the NUT Master and Slave set up and can even get them communicating together and working when they're on the same LAN for testing.

But I just can't seem to get them to work on different networks. When asking on IRC, the NUT mailing list and on searching Google I can't find any reference anywhere to Nut masters and slaves being on different networks and if this is even possible...

I'd hoped it would be as simple as just adding an external IP address to a config file in uspmon, uspd or nut so that is was allowed access.

I added "allowfrom = " to upsd.users with the IP I needed to give access but that hasn't help. I've also turned off firewalls etc...

Can anyone please help get this to work?

---

