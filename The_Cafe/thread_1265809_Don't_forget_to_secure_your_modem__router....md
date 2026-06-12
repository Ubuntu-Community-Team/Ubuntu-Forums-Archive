---
title: "Don't forget to secure your modem / router..."
date: 2009-09-13
forum: The Cafe
---

### Post by Sporkman on 2009-09-13
> **Worm breeds botnet from home routers, modems**

More than 100,000 hosts invaded

By Dan Goodin in San Francisco 
Posted in Security, 24th March 2009 00:20 GMT

Security researchers have identified a sophisticated piece of malware that corrals consumer routers and DSL modems into a lethal botnet.

The "psyb0t" worm is believed to be the first piece of malware to target home networking gear, according to researchers from DroneBL, which bills itself as a real-time monitor of abusable internet addresses. It has already infiltrated an estimated 100,000 hosts. It has been used to carry out DDoS, or distributed denial of service, attacks and is also believed to use deep-packet inspection to harvest user names and passwords...

[http://www.theregister.co.uk/2009/03/24/psyb0t_home_networking_worm/](http://www.theregister.co.uk/2009/03/24/psyb0t_home_networking_worm/)

---

### Post by Defrector on 2009-09-13
I assume that when they say "any router that... has an administrator interface" they mean a "WAN-accessible administrator interface"

---

### Post by MikeTheC on 2009-09-13
I know DD-WRT's got a patch for their firmware because of an exploit found in it.

---

### Post by pwnst*r on 2009-09-13
> Re: Don't forget to secure your modem / router...

or conversely, don't enable things you're not using.  WEB gui/administration does not come enabled by default on DDWRT

---

### Post by MikeTheC on 2009-09-13
> **pwnst*r said:**
> or conversely, don't enable things you're not using.  WEB gui/administration does not come enabled by default on DDWRT

big 'ole [font=georgia][size=10]**+1**[/size][/font] to that!

---

### Post by Dragonbite on 2009-09-14
> Vulnerable devices include any home router or modem that uses Linux Mipsel, has an administration interface, sshd, or telnet in a DMZ, and employs a weak password. 

Great.. I assume the web interface that just about all of these devices have means they're vulnerable?

I think only my modem is vulnerable, because right off the modem is a box running IPCop and I don't have a DMZ zone set up (just Red/Internet and Green/LAN) on there, or ssh, just the default web interface which is  internal only if I recall.

That should stop it from getting to my wireless router, right?

---

### Post by m3wolf on 2009-09-14
> **Dragonbite said:**
> Great.. I assume the web interface that just about all of these devices have means they're vulnerable?

I think only my modem is vulnerable, because right off the modem is a box running IPCop and I don't have a DMZ zone set up (just Red/Internet and Green/LAN) on there, or ssh, just the default web interface which is  internal only if I recall.

That should stop it from getting to my wireless router, right?

Based on reading the article the major point is that the modem/router is accessible WAN side via telnet or ssh and it relies on users not changing their default password or changing it but giving it a weak password. Come up with a strong admin passwd and disable WAN telnet/ssh if your modem/router has it.

---

### Post by Dragonbite on 2009-09-14
[Another article on this.]("http://www.itworld.com/security/77499/first-linux-botnet")

---

