---
title: "networking stopping unexpectedly"
date: 2007-11-09
forum: Server Platforms
---

### Post by AndyCanty on 2007-11-09
hi all,

I'm a noob Ubuntu user, but decided to take the plunge and use Gusty Gibbon Server Edition for a webserver.
I have the webserver running sweet no probs, 

but the the only problem i'm now getting is at unexpected intervals the network will drop and i have to run IFCONFIG to reset it.
I've updated /etc/network/interfaces file but stil does it.

I cannot figure it and trawling the web hasn't yeileded any answers yet.

Any one have any ideas?

---

### Post by zvacet on 2007-11-09
Maybe you will find answer here

[http://www.howtoforge.com/perfect_server_ubuntu7.10]("http://www.howtoforge.com/perfect_server_ubuntu7.10")

---

### Post by AndyCanty on 2007-11-09
i'll give it a look i hadnt fond that one, no idea why, as it's exactly what i've been looking for.

Cheers

---

### Post by MJN on 2007-11-09
What do you mean by 'the network drops'?

Is there anything listed in /var/log/syslog around the time of the drop that may hint at what the problem is? Also check the output of dmesg - particularly towards the end following a network drop.

Mathew

---

### Post by zvacet on 2007-11-10
It is 7 pages tutorial.Did you read it all?Can you cannact to that link?I think this is page you are looking for 

[http://www.howtoforge.com/perfect_server_ubuntu7.10_p3]("http://www.howtoforge.com/perfect_server_ubuntu7.10_p3")

---

### Post by AndyCanty on 2007-11-12
> **MJN said:**
> What do you mean by 'the network drops'?

Is there anything listed in /var/log/syslog around the time of the drop that may hint at what the problem is? Also check the output of dmesg - particularly towards the end following a network drop.

Mathew

> **zvacet said:**
> It is 7 pages tutorial.Did you read it all?Can you cannact to that link?I think this is page you are looking for 

[http://www.howtoforge.com/perfect_server_ubuntu7.10_p3]("http://www.howtoforge.com/perfect_server_ubuntu7.10_p3")

@MJN, i mean by for some reason the IP stack "resets" and goes off to find a DHCP host instead of retaining the static IP i set.
Does the IP reload itself after a period of time?

@ZVACET, I've gone through the IP setup, as everything else works fine. I did find an incorrect setting in the /etc/networking/interfaces
so hopefully it will behave now.

Many thanks to you all for your help.

Andy.

---

### Post by MJN on 2007-11-12
The adapter will only request an address via DHCP if it's configured to do so - check your config (although it sounds like you've found something amiss so this was likely it).
 
Mathew

---

### Post by AndyCanty on 2007-11-12
> **MJN said:**
> The adapter will only request an address via DHCP if it's configured to do so - check your config (although it sounds like you've found something amiss so this was likely it).
 
Mathew

Here's hoping it was just me not configuring it correctly, i now run
/etc/init.d/networking restart and the IP address is assigned correctly. so hopefully it was just that.

Cheers
Andy

---

### Post by AndyCanty on 2007-11-16
Just a quick update.
Since finding the error in the config file the box has been stable and working fine every since.
Thankyou for your help.

---

