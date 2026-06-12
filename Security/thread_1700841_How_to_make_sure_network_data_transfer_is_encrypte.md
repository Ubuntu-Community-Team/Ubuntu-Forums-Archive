---
title: "How to make sure network data transfer is encrypted?"
date: 2011-03-05
forum: Security
---

### Post by cgb223 on 2011-03-05
Hey all, I am routing my network stuff through a vpn which claims my data is being encrypted via SSL. How can I check if my network data is in fact encrypted. Like all of it, not just http stuff. If you need specific transfer protocols to answer this then I guess, http, https, and tcp/udp are all active at this time. 

Any ideas?

Thanks in advanced,
Me

---

### Post by wacky_sung on 2011-03-06
> **cgb223 said:**
> Hey all, I am routing my network stuff through a vpn which claims my data is being encrypted via SSL. How can I check if my network data is in fact encrypted. Like all of it, not just http stuff. If you need specific transfer protocols to answer this then I guess, http, https, and tcp/udp are all active at this time. 

Any ideas?

Thanks in advanced,
Me

You need a sniffer to determine your transfer data is encrypted.Apart from that, what type of VPN are you using?Some VPN type are prone to MTM(Man in The Middle attack) or dictionary attack.

[http://en.wikipedia.org/wiki/Point-to-Point_Tunneling_Protocol](http://en.wikipedia.org/wiki/Point-to-Point_Tunneling_Protocol)
[http://en.wikipedia.org/wiki/Virtual_private_network](http://en.wikipedia.org/wiki/Virtual_private_network)

---

### Post by iissmart on 2011-03-08
Wireshark is what you're looking for.

---

