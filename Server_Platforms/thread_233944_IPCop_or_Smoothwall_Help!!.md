---
title: "IPCop or Smoothwall Help!!"
date: 2006-08-10
forum: Server Platforms
---

### Post by chrisfay on 2006-08-10
I have been contemplating adding some extra security to my setup and was curious for some input on methods. I am currently running a setup with two computers behind a Linksys wrt54g with integrated firewall. I have one of the computers running a web server, DNS, SSH and Mail server while the other is just a personal pc. I portforward any needed ports directly to my server box and have the rest closed by the Linksys.

My question is whether or not its an added benefit to integrate a third machine that I have laying around as a dedicated firewall and use my router as just a router. I was thinking of creating a Red,Green and Orange type configuration with my server on the oragne dmz interface. When I did some more searching I found that the DMZ zone is pretty much wide open on the net. Can you limit the ports open on the orange DMZ zone in something like IPCop or Smoothwall? Or am I better off just using the Linksys to open a few ports to the server?

I have full remote access to my router for configuration so the motivation to use these alternative software options is less of convenience and more of a desire for better security if neccessary. Does anyone have experience with either software option preferably with ideas for comparing them against a standard linksys firewalled router?

---

### Post by djdicbob on 2006-08-11
If your trying to protect your LAN in a home networking scenario...The Linksys with the right ports open should be just fine.  If your looking to tinker around I would choose IPCOP over Smoothwall.  IPCOP has some nice plugins for the interface e.g OpenVPN plugin.  In my expeirence IPCOP was easier to setup and manage.  The two of them are just interfaces for IPTABLES, so as far as protection..probable 6 of 1, and half a dozen of another!

Just my two cents.........:)

---

### Post by printmkr on 2006-08-11
Might be a good question for the forums over at smoothwall.org. They are real responsive, and though they may be biased to smoothwall, you will get knowledgable answers. I couldn't live without my smoothie! It was the first non-windows box I added to my network. I just checked its status and it has been up and running for 110 days straight. Now this might not seem like much to Linux folks, but coming from a Windows background, this is some kind of miracle!

If you wanted to see the smoothwal docs, (the quick install guide should give you a good overview of features) they are available at [http://smoothwall.org/docs/]("http://smoothwall.org/docs/")

---

### Post by Ozz on 2006-08-11
<biased answer>Smoothwall no questions asked</biased answer>

Ozz.

---

### Post by chrisfay on 2006-08-11
My question is less about which software to use, but rather how would I benefit from using either one over a linksys wrt54g or similar peice of hardware. 

I have been on the Smoothwall forums for a while doing some archival searches which have given me 'some' answers but nothing really concrete. If someone has a good understanding of the pros and cons between using something like smoothwall vs a hardware router/firewall that would really help.

My focus is purely on security and I understand that good network integrity is a combination of multiple defence layers not only focusing on the perimeter. However, I would like to make sure that I'm not missing out on extra security by using my router over something like a dedicated firewall like Smoothwall.

---

### Post by Ozz on 2006-08-11
Well for a proper answer, smoothwall has SPI (stateful packet inspection) which gives better reading of the packets arriving at your firewall, a regular router will not have that. 
There's also logging capabilities and last but not least open source which allows for modifications on the firewall that will custom fit your network/security needs.
On the router side I can only see less impact on your hydro bill but not by much, aesthetics, and space saving.

Ozz.

---

