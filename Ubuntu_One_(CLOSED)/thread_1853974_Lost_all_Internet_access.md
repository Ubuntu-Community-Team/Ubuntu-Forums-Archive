---
title: "Lost all Internet access"
date: 2011-10-03
forum: Ubuntu One (CLOSED)
---

### Post by D00mM4r1n3 on 2011-10-03
This is bizarre, not sure if it's something the company I work for did or if it was the Ubuntu One 2.0 that did it, but I lost all Internet access while the client was syncing. From the dashboard I clicked on the Devices tab to see what it had to show and within a few seconds of doing that the sync button changed from "Disconnect" to "Connect" to indicate it was no longer connected to the service.

Naturally, my first thought was to Google it so I brought up my web browser and couldn't get to any websites. I checked with other employees around me (that don't use this app) and they were having no problems with the Internet. 

After a little investigation I found the DNS address my Windows 7 machine was trying to use had changed to 192.168.0.1. There are no viruses on my system and nothing else running that would cause such a thing to happen. The only thing I can think of is if the network system here automatically did that if it detected high bandwidth usage from the sync or this software caused it to happen.

Anyways, a quick "ipconfig /renew" fixed it and I was able to finish syncing, very weird thing to happen though.

---

