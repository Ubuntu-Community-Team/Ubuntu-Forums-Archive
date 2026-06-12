---
title: "Setting up a Debian 7 server"
date: 2013-07-11
forum: Ubuntu, Linux and OS Chat
---

### Post by Jaraxle on 2013-07-11
I have some general questions about setting up a Debian 7 server for home use. I was going to build a server using old hardware but today someone gave me an older Dell Pentium 4 1.8ghz system with 1.5Gb RAM, 80GB hard drive, and 10/100 NIC. I assume this would be enough to run Debian server but I was wondering if there would be any advantage to using something like a dual CPU motherboard. I could also get a case that will hold multiple hard drives should I decide to go with a RAID array.

The main thing I would use the server for would be as a proxy/firewall but I would also like to learn some Apache and MYSQL administration. I won't be using it to do any "real work" but I also don't want it running so slow that it's a pain to use. I don't mind spending a little money if it would make a difference. For instance, I have a basic D-Link broadband router (EBR-2310) that I'll be using to connect another desktop and laptop. Do you think this would be enough or should I purchase a more powerful home router/switch?

I'll also be using this to study for the Linux+ exam and I've heard that there are a lot of questions on the exam about older hardware so I was thinking of going with three or more older SCSI drives just to learn, maybe even SCSI tape drive for backup. For those of you who have taken the exam, do you think this would be a good idea? I would need to install a SCSI card as the Dell motherboard only has IDE. Maybe going with SATA RAID would be suficient?

Also, does anyone know of a good book on Debian administration? I've been searching and so far the only thing that looked good was the O'Reilly book.

---

### Post by Jaraxle on 2013-07-11
Also, I've heard some people say that FreeBSD makes the best proxy/firewall server. What is your opinion? It seems to me that Debian should be able to do anything BSD can do. Maybe FreeBSD is slightly more secure?

Thanks in advance.

---

### Post by mips on 2013-07-11
pFsense

---

### Post by CharlesA on 2013-07-11
> **mips said:**
> pFsense

That's my favorite firewall, but there are others out there.

[http://www.debian-administration.org/](http://www.debian-administration.org/)

---

### Post by Cheesehead on 2013-07-11
> **Jaraxle said:**
> older Dell Pentium 4 1.8ghz system with 1.5Gb RAM, 80GB hard drive, and 10/100 NIC. I assume this would be enough to run Debian server
[...]
The main thing I would use the server for would be as a proxy/firewall

That system is powerful enough for the intended use. That system seems powerful enough for lots of non-GUI uses.
Generally, I recommend a low-power, fanless system for such use. I find the fan noise and extra power consumption annoying. However, free is a very good price....

I also recommend against putting experimental services on a network-essential (proxy/firewall/router/gateway) system. A failure in the experimental service could bring down your network...and without a network how will you look up how to fix the problem? I find I'm much less likely to experiment if I'm worried about bringing down the network.

---

### Post by CharlesA on 2013-07-11
> **Cheesehead said:**
> That system is powerful enough for the intended use. That system seems powerful enough for lots of non-GUI uses.
Generally, I recommend a low-power, fanless system for such use. I find the fan noise and extra power consumption annoying. However, free is a very good price....

I also recommend against putting experimental services on a network-essential (proxy/firewall/router/gateway) system. A failure in the experimental service could bring down your network...and without a network how will you look up how to fix the problem? I find I'm much less likely to experiment if I'm worried about bringing down the network.

+1 to both points. I originally run a Ubuntu 9.04 box with webmin as my router/firewall... it was big, noisy and used a ton of power, so I went back to using a normal router.

If I wanted to do it again, I'd probably run something like a Raspberry Pi (with a USB NIC) or the equivalent.

It is a general rule of thumb to only run essential services on a gateway/router/firewall appliance. Anything more gives you greater attack surface and more potential breakage due to updates.

---

### Post by Jaraxle on 2013-07-11
Thank you all for the advice. The first thing I did was check to see if the fan or hard drive was noisy because that's something that I also hate. Both seem really quite but I think I will install a higher quality third party fan. Was also thinking of trying to load Debian from a USB flash drive but I don't know how well that would work. 

Where would someone find a fanless system? I'm interested but I'm not familiar with that. Would that be a kind of network appliance?

I think if I decide to setup an Apache/MySQL server or something, I will first get another system and try to create a DMZ. Something cheap, but I'm thinking Debian 7 firewall, web server or something expiremental, FreeBSD firewall.

If I may ask another question (before I start reading about Debian administration): would it help to use dual network cards in the server?

---

### Post by cariboo on 2013-07-11
If you are going to use the server for a router/firewall, two NICs is a must.

For fanless systems, you may want to start [here.]("http://www.mini-itx.com/").

As a side note, I'm using an ancient Apple G3 (350Mhz cpu, 384MiB ram) and  running Debian stable as an mp3 player, it automatically mounts the music directory on my server via NFS, and uses mpg321 and randomplay which also starts automatically when the system is turned on.

---

### Post by CharlesA on 2013-07-11
This might help:
[http://www.silentpcreview.com/](http://www.silentpcreview.com/)

---

### Post by lykwydchykyn on 2013-07-11
My server runs Debian 7, and does much more than that on less hardware than that.  Hardware should be fine.

If you're new to this, though, I wouldn't recommend starting out with a firewall machine.  The Internet is full of script kiddies looking for misconfigured Linux boxes to crack; it takes a bit of care and know-how to really lock one down, and that's going to add another layer of confusion to what you're doing.

If you just want a proxy for caching or content filtering, you can do that behind the router just as well (this is what my server does, among other things).

---

### Post by Jaraxle on 2013-07-12
Advice regarding misconfigured linux boxes duly noted and you're right, I am new to this so I decided to go with a rented vps server instance for now.

I mainly wanted to use proxy for anonymous web browsing so I will try to setup OpenVPN on my vps server, which is a Debian 7 server so it also accomplishes my goal of learning more about Debian administration. I'm also reading up on a Squid proxy on the server as an alternative.

I still plan on using the Dell PC to setup a local Debian server behind my router, perhaps just for caching or maybe setup Squid on local server to mask my ip. I'm not sure how to go about accomplishing this and still have a lot to learn.

Thanks again to everyone. I'll go ahead and mark thread solved.

---

