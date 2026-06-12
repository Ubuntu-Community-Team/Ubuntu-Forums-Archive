---
title: "More Shorewall Questions"
date: 2007-04-14
forum: Server Platforms
---

### Post by novice1 on 2007-04-14
I have Edgy Server running Shorewall behind a Linksys Wireless Router (WRT54G). The Shorwall Policies and Rules definitely are enforced when I access the Internet either from my Edgy or Windows XP desktop or from my Edgy DNS server. However, my physical network topology is that both the WAN and LAN ethernet cards in the Shorwall machine are connected to the Linksys Router ports and the Linksys Wan port connects to my Cable Modem. Linksys is the gateway to the WAN. These two interfaces are configured to use ARP and all is well. However, this is configuration not recommended for anything except testing the firewall.  What I need is to do is connect the Shorwall WAN Ethernet card directly to the Cable Modem and the Shorwall LAN Ethernet card remain on a LAN port of the Linksys.  When set everything up that way - the Shorewall WAN interface gets a DHCP configuration from my ISP just fine, the LAN interface is Static IP and connects well to the LAN.  From the Shorewall Machine I can ping either the WAN or the LAN and I can Name resolve LAN but not WAN addresses -- MY local DNS server, and my two desktop computers Ethernet cards are set to the Shorewall IP address as the gateway. However, I can not browse, connect to my ISP's mail servers, ping or name resolve anything on the Internet. 

I believe my problem is with the Linksys router. But reading the book tells me very little about how to configure the Linksys to no longer be the gateway to the Internet. I am hoping someone here has some suggestions about how to reconfigure the Linksys. Or if there are yet Shorewall configurations I am overlooking?

---

