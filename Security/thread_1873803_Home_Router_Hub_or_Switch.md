---
title: "Home Router: Hub or Switch?"
date: 2011-11-01
forum: Security
---

### Post by crazyguy510 on 2011-11-01
I've seen quite a few posts on the subject of switches, hubs, and packet sniffing, however none seem to directly answer this kind question. 

So here's the situation, we've changed our router a few times over the last few years. The router previously owned was set up as an unencrypted hotspot where I could directly connect and sniff all LAN traffic without switching my wireless card in monitor mode. I would assume that because I was able to this, it was hub and not a switch. With our newer router, we have finally decided to enable WPA2 encryption. If I connect to the network and sniff like I had done in the past, I would,as expected from a switch, only see my own local traffic. However, if I sniff the traffic in monitor mode, capture the four-way WPA handshake and decrypt the 802.11 traffic, I am once again able to see all network traffic as before.

Now, I've always assumed our newer router was a switch. I've read many, many articles saying that hubs are quite out of date and it is becoming much harder to purchase one. However, I've never been able to tell with absolute certainty. Does sniffing in monitor mode allow you to see all traffic from both switches and hubs, or is there some concept that I'm missing? The router we are currently using is a Linksys E4200 router. Thanks for the help. :)

---

### Post by secret resistor on 2011-11-01
Sniffing on a typical switch is only slightly harder than sniffing a hub (doing it undetected is a different story though). The simplest method involves using ARP poisoning to make all traffic go through you and then you don't even need to be in monitor mode because the Ethernet packets will already be addressed to you. Some sniffers will even do that automatically which may be what's happening in your case.

---

### Post by crazyguy510 on 2011-11-02
I suppose that could be a possibility, however I've experimented with Ettercap and other MITM utilities and I usually start dropping packets and slowing our network down to a crawl. I haven't experienced those kinds problems in this case. 

Also, I've been using Wireshark and that, to my knowledge, does not perform an ARP cache. It does feature promisc. sniffing, but I don't think that would have any affect on a switched router.

Guess I'll head on over to Wikipedia and see if there was some concept that I missed.

---

### Post by emiller12345 on 2011-11-02
monitor mode graps all 802.11 traffic from the area. if you have laptop A and laptop B on your WPA2 Personal wifi network, your going to use the same encryption key.  when you enter the key in wireshark, it should decrypt all of the packets from both A and B. There's nothing physically separating the dot11 packets, so it looks like a 'hub'. when you
> connect to the network and sniff like I had done in the past

I assume your entering in promisc mode, and leaving your card in managed mode, the wifi adapter is only looking at traffic thats addressed to your MAC addr.  This discrimination is handled by your hardware so your computer isn't processing data that isn't directed to it, as it is in normal operation.

---

### Post by crazyguy510 on 2011-11-03
> **emiller12345 said:**
> monitor mode graps all 802.11 traffic from the area. if you have laptop A and laptop B on your WPA2 Personal wifi network, your going to use the same encryption key.  when you enter the key in wireshark, it should decrypt all of the packets from both A and B. There's nothing physically separating the dot11 packets, so it looks like a 'hub'. when you

I assume your entering in promisc mode, and leaving your card in managed mode, the wifi adapter is only looking at traffic thats addressed to your MAC addr.  This discrimination is handled by your hardware so your computer isn't processing data that isn't directed to it, as it is in normal operation.
 You are correct. I have been leaving my main network interface in managed mode. I hadn't realized that my hardware did anything to organize the flow of packets. Does a card in manage mode do this even if the router is a hub, or will wireshark still pick up traffic not addressed to it?

Thanks for the answers!

---

### Post by emiller12345 on 2011-11-03
> **crazyguy510 said:**
> Does a card in manage mode do this even if the router is a hub, or will wireshark still pick up traffic not addressed to it?

In managed mode it will pick up packets from any wifi router or wifi hub within the antenna's range. Basically anything running 802.11 AFAIK.

---

