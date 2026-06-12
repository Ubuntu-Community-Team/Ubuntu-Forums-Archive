---
title: "Does it make sense to configure an ubuntu box as a gateway friewall?"
date: 2014-05-05
forum: Security
---

### Post by shahin on 2014-05-05
Greetings-
I am sure this question has be asked in one form or other, and I searched, but just can not find the answer that I am after. Would it make sense, financially, time wise, and functionally to want to turn an old pc into a gateway firewall by installing the latest Ubuntu, IPchains, snort, and other goodies and harden it? I want to put a web server behind it. Or shall I just invest in a small Juniper, Cisco or something? 
I know it takes longer to create the Ubuntu. But then again if you know of any already made images that I can use, please let me know. 
I am willing to invest the time in return for learning the wonderful open source security tools. I installed snort a while back. Oh, I also need to be able to monitor the network remotely.

---

### Post by The Cog on 2014-05-05
I would say so, yes it would. The only reason I haven't done so at home is that I can't find cheap hardware with two ethernet ports.

ipchains is old stuff and has been replaced with iptables. iptables is built in, you don't have to install it, just configure it.

---

### Post by SeijiSensei on 2014-05-05
From a cost perspective, a cheap solid-state router is going to cost you much less in electricity costs and be easier to configure out-of-the-box as well.  If you want to go with Linux, you can buy [routers that use or support]("http://www.newegg.com/Product/ProductList.aspx?Description=dd-wrt&submit=ene") the [dd-wrt]("http://www.dd-wrt.com/") version of Linux.  I have a Buffalo with dd-wrt; Linksys (aka Cisco) and Netgear also support dd-wrt these days.

I like [ntop]("http://www.ntop.org/") for network monitoring over the web.  I usually limit access to it by IP address as well as via logins.

---

### Post by shahin on 2014-05-05
This forum is great. Thanks. I found out my Verizon Actiontec is supported:-)

---

### Post by SeijiSensei on 2014-05-05
I have Verizon FiOS, but I have been wary about playing with the settings on their router.  I have another router, the Buffalo with dd-wrt, behind my Acctiontec.  I did set up port forwarding on the Acctiontec, but I left the firmware alone.  If you switch the firmware to dd-wrt, I doubt Verizon will support it.  I prefer to play with routers I own.

---

### Post by HermanAB on 2014-05-05
An old netbook or laptop computer with a small SSD (or running off a USB memory stick or SD card) can make a good gateway.  For the second ethernet port, you can use a USB or cardbus ethernet adaptor.  The advantage is that you have everything under your own control and know exactly what it is doing.  Do enable App Armor or use another distro with SELinux.

---

### Post by ant2ne on 2014-05-06
I've got a small dual nic box setup running iptables for a gateway/firewall. Mainly, I wanted to do something that could do better logging than your off the shelf home router. But I have to admit, I rarely check the logs. I do like the flexibility of iptables and well as security of linux.  (I'm running ubuntu server on it with some cron jobs to auto update etc.) It also has more power. How many routers do you know of with 4 gigs of RAM and 80Gigs of drive space? It also does DHCP, DNS, ddclient (DYNDNS updates) etc. If I had to do it again, I'd get a raspberry pie with a USB ethernet dongle and play with that. That might bring down the cost in hardware as well as electricity burned to near the off the shelf walmart brand.

---

### Post by SeijiSensei on 2014-05-06
The Raspberry Pi is a nice little machine, but it's not cheap.  I spent [around $100]("http://ubuntuforums.org/showthread.php?t=2206309&p=12932884&viewfull=1#post12932884") for one with the needed memory card, wifi adapter, etc.

---

### Post by ant2ne on 2014-05-06
I'm thinking I paid $75 or so for a walmart router. I just bought 2 pi a few months back for my xbmc's. I think with the case, card, power cable and wifi dongle it was right at $80. I did get kind of lucky with the wifi dongles being on sale.

---

### Post by jon43 on 2014-05-06
> **HermanAB said:**
> An old netbook or laptop computer with a small SSD (or running off a USB memory stick or SD card) can make a good gateway.  For the second ethernet port, you can use a USB or cardbus ethernet adaptor.  The advantage is that you have everything under your own control and know exactly what it is doing.  Do enable App Armor or use another distro with SELinux.

I would think an old laptop would be a terrible device to be running 24/7. Few laptops have good cooling, and Linux tends to lack the power saving features Windows offers to keep the temps down...

I do think there is some value to this idea. I have a higher end Asus router and love the performance. Even the security features it offers are pretty good. But it's still proprietary firmware that I'm sure has exploits that can be taken advantage of. I've thought about creating something with PFSense or smoothwall for a while.

---

