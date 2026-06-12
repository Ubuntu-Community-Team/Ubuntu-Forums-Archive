---
title: "DNS Server Behind Nat Router &amp; Nat Firewall"
date: 2012-03-21
forum: Server Platforms
---

### Post by bsaidus on 2012-03-21
Hello !!
I have the following situation :
 I have a Public IP address, Nat Router and Firewall (pfSense) (as shown in the attached picture).
so my problem is how to publish my DNS Server to the net.
How does the zone files in bind looks like ?
Do i put the PUBLIC IP address in the zones files ?
help me please  .
I have proceded by doing nat of port 53 (tcp and udp) from Router to pfSense Firewall then I did another nat from pfSense(Firewall) to my Server but does not work .

---

### Post by LtPitt on 2012-03-21
I don't want to ruin the thread and I promise I'll disappear immediately but...

What did you use to draw that lovely scheme?

---

### Post by Cheesemill on 2012-03-21
> **LtPitt said:**
> I don't want to ruin the thread and I promise I'll disappear immediately but...

What did you use to draw that lovely scheme?

That would be Microsoft Visio.

---

### Post by bsaidus on 2012-03-22
Microsoft VISIO !! :D

---

### Post by LtPitt on 2012-04-04
[IMG]http://troll.me/images/y-u-no/guess-whut-i-like-cheese111.jpg[/IMG]


ps
Please someone help the guy that opened this thread I feel sorry for hijacking it.

---

### Post by darkod on 2012-04-04
Your router needs to forward port 53 tcp AND udp to the firewall, and the firewall needs to forward (and ALLOW) port 53 also to the DNS server and from the DNS server to the interface towards the router.

So, if the router has no firewall, simply set up port forwarding port 53 both protocols to 192.168.2.20.

On the pfsense firewall, tell it to allow port 53 from 172.24.103.4 towards 192.168.2.20 (if all OUTPUT traffic is allowed you don't need to do this, it will allow 53 by default because it originates from your internal server).
Also in pfsense configure to allow and forward (two separate options) port 53 from 192.168.2.20 towards 172.24.103.4.

That's it.

---

### Post by LtPitt on 2012-04-05
God bless you for freeing my soul, darko :)

---

### Post by haqking on 2012-04-05
I hope that is made up configuration.

posting your network infrastructure including IP addresses is not a good idea ;-)

Peace

---

