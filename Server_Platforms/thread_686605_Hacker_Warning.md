---
title: "Hacker Warning"
date: 2008-02-03
forum: Server Platforms
---

### Post by Gizkaguy on 2008-02-03
Last night at 23:10:13, someone from ---.--.-.- tried to get into my computer. It was unsuccessful. Are there any ways I can find out where he is?

---

### Post by mnemosyne on 2008-02-03
Do you know how they tried to get into your computer? Do you have any open ports? Are you sure they aren't on your LAN?

---

### Post by edm1 on 2008-02-03
What makes you think they tried to hack your computer? It could well just be a computer on your LAN running a service that is innocently trying to exchange info with your computer. What is you LAN IP? That IP looks like it could be your router.

---

### Post by Gizkaguy on 2008-02-03
I doubt it. I am in a hotel -- yesterday I had networking problems, so I called Tech Support. The guy got my I.P. address and gave me a fake number. I called it - it's a human resource management service. He had just pinged my computer just under 2 hours ago.

---

### Post by Gizkaguy on 2008-02-03
He just did it again.

---

### Post by dynamethod on 2008-02-03
just pull the network cable out from your pc, problem solved

---

### Post by fedex1993 on 2008-02-03
also if your on ubuntu your safe and you dont halff to worry about anything hopefully since there are only 20 known virus and they are not wild

---

### Post by Gizkaguy on 2008-02-03
That'd be great, but I'd like to be on the internet.

---

### Post by Gizkaguy on 2008-02-03
> **fedex1993 said:**
> also if your on ubuntu your safe and you dont halff to worry about anything hopefully since there are only 20 known virus and they are not wild

Yah I know there aren't many viruses, but I'd like to stop him from hacking and I didn't the exact number ... thanks though :-)

---

### Post by kerry_s on 2008-02-03
> **Gizkaguy said:**
> Last night at 23:10:13, someone from 198.18.1.1 tried to get into my computer. It was unsuccessful. Are there any ways I can find out where he is?

198.18.1.1 is a internal router address, for instance if you type that into your browser you will get the router logon. the router sends out a icmp to check if your still there. it's a way of maintaining a connection to the router. other wise your dhcp address would be dropped and you would lose connection.
here-> [http://en.wikipedia.org/wiki/Internet_Control_Message_Protocol](http://en.wikipedia.org/wiki/Internet_Control_Message_Protocol)

---

### Post by fedex1993 on 2008-02-03
yeah that is lol 192.18.1.1 usualyl its 192.168.1.1. its probley there monitoring serice to see what you have download or something. do you half ot pay for the internet at this hotel?

---

### Post by Gizkaguy on 2008-02-03
I just got off the phone with the ISP -- all network traffic is routed through that I.P. address, so there's really nothing anyone can do.

---

### Post by Gizkaguy on 2008-02-03
> **fedex1993 said:**
> yeah that is lol 192.18.1.1 usualyl its 192.168.1.1. its probley there monitoring serice to see what you have download or something. do you half ot pay for the internet at this hotel?

No.

---

### Post by kerry_s on 2008-02-03
> **fedex1993 said:**
> yeah that is lol 192.18.1.1 usualyl its 192.168.1.1. its probley there monitoring serice to see what you have download or something. do you half ot pay for the internet at this hotel?

lol, i didn't even catch that type o. :)

---

### Post by hyperair on 2008-02-03
Either way I doubt there's anything to worry about unless someone who has ill wishes towards your computer has got hold of 192.168.1.1. It's usually the router's internal address anyway.

---

### Post by fedex1993 on 2008-02-03
yeah its probley like a monitoring service that they have or something. I have seen it happen at many hotels. every couple of mins it would say some one would try to portscan and what not since your on linux your safe.

---

### Post by HermanAB on 2008-02-03
Maybe see this: [http://aeronetworks.ca/ssh-kiddies.html](http://aeronetworks.ca/ssh-kiddies.html)

---

### Post by hyperair on 2008-02-03
Awesome. Totally awesome.

---

### Post by Vadi on 2008-02-03
I'd say you're fine. Just don't enable the remove destkop thing (it's disabled by default). I enabled it for a stupid reason once, but thankfully I set it to ask me before allowing a connection - one time in a library someone tried connecting. Kept it off since.

But really, I'd say you're fine.

---

### Post by hyperair on 2008-02-03
I've enabled it on my system, but then again I'm behind a NAT without the VNC port forwarded on my router. I only use SSH tunneling to access my VNC anyway.

---

### Post by Vadi on 2008-02-03
Yes but you seem like a person who knows that are they doing here :)

---

### Post by hyperair on 2008-02-03
Either way VNC has password authentication as well.

---

