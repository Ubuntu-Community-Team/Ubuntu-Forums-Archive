---
title: "Daisy chaining routers - How to?"
date: 2013-01-21
forum: The Cafe
---

### Post by u-noob-tu on 2013-01-21
Here's my dilemma: I have a nice Vizio Dual band router that I would like to use. My house however has Verizon Internet and they use a coaxial cable to send the internet to their proprietary router (which is not 802.11n). The problem is that there are other things plugged into the Verizon router (the bluray player, the TV, etc.) that my dad doesn't want changed. I first tried a temporary setup by unplugging the TV ethernet cable from the Verizon box and plugged in my router, which worked, until i realized that the Verizon box no longer worked (stopped sending out a signal, even over ethernet). I know i have to configure my Vizio router to disable DHCP so the two routers don't fight each other over IP addresses. I also have a 10/100 ethernet switch that I suspect I will need to make this work. How can I set this up in a way that I can have my router working as well as the Verizon router?

---

### Post by dannyboy79 on 2013-01-21
what is your end goal to use the vizio router for exactly?

---

### Post by u-noob-tu on 2013-01-21
> **dannyboy79 said:**
> what is your end goal to use the vizio router for exactly?

To use the dual band 802.11n wireless.

---

### Post by kurt18947 on 2013-01-21
I'm doing this very thing though for different reasons (WiFi speeds)  I'm not familiar with Vizio,  I'm using a Linksys WRT54GL.  I disabled DHCP server and the firewall.  Connect LAN port to LAN port, do not use the WAN port.  And yes, just as two buildings cannot have the same address - packages would be misdelivered - two devices cannot have the same I.P. address.  Both routers defaulted to  192.168.1. 1.  I just changed the last digit on my second router.   The second router provides both wireless and wired connections.

There is a second trick with FiOS though I haven't tried it.   You can buy ActionTec FiOS routers on Craigslist or Ebay.  There's one on Craigslist near me for $15.   Load a third party firmware and you can use the FiOS router as a  MoCA bridge.  A MoCA bridge connects to any Coax TV connection and can provide both wired and wireless connections.  There's more information on routers and various broadband topics here.

Some info on routers and FiOS:

[https://secure.dslreports.com/faq/verizonfios/3.0_Networking#16077](https://secure.dslreports.com/faq/verizonfios/3.0_Networking#16077)

There is quite a lot of info on that forum.

---

### Post by dannyboy79 on 2013-01-21
> **kurt18947 said:**
> I'm doing this very thing though for different reasons (WiFi speeds)  I'm not familiar with Vizio,  I'm using a Linksys WRT54GL.  I disabled DHCP server and the firewall.  Connect LAN port to LAN port, do not use the WAN port.  And yes, just as two buildings cannot have the same address - packages would be misdelivered - two devices cannot have the same I.P. address.  Both routers defaulted to  192.168.1. 1.  I just changed the last digit on my second router.   The second router provides both wireless and wired connections.

There is a second trick with FiOS though I haven't tried it.   You can buy ActionTec FiOS routers on Craigslist or Ebay.  There's one on Craigslist near me for $15.   Load a third party firmware and you can use the FiOS router as a  MoCA bridge.  A MoCA bridge connects to any Coax TV connection and can provide both wired and wireless connections.  There's more information on routers and various broadband topics here.

Some info on routers and FiOS:

[https://secure.dslreports.com/faq/verizonfios/3.0_Networking#16077](https://secure.dslreports.com/faq/verizonfios/3.0_Networking#16077)

There is quite a lot of info on that forum.great answer here! thanks

---

### Post by cariboo on 2013-01-21
I've done essentially the same as kurt18947, with my setup. but I also have added a 5 port Gigabyte switch in the house, and a older Dlink 8 port switch in my shop. I too set a static ip address on my old SMC Barricade wireless router in the shop. The only problem I really ran into was the need for a crossover cable between the SMC router and the Dlink 8 port switch.

---

