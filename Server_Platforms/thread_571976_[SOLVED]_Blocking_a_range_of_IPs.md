---
title: "[SOLVED] Blocking a range of IPs"
date: 2007-10-09
forum: Server Platforms
---

### Post by Megaqwerty on 2007-10-09
Could anyone tell me how to block a range of IPs in hosts.deny? Like, say: 222.168.0.0 - 222.223.255.255 ?

Thanks,

Megaqwerty

---

### Post by HermanAB on 2007-10-10
You can drop a netblock on the floor with iptables:
$ sudo iptables -I INPUT -i eth0 -p tcp -s w.x.y.z/24 -j DROP

Cheers,

H.

---

### Post by GigaVolt on 2007-10-10
Hmmm...
I use this solution:
route add -net  X.Y.Z.0 gw 127.0.0.1 netmask 255.255.255.0

X.Y.Z.0 is bad network

---

### Post by HermanAB on 2007-10-10
Heh, neat routing trick.

---

### Post by GigaVolt on 2007-10-10
Hmmm.. very good trick is:

modprobe dummy
ip address add X.Y.Z.0/24 dev dummy0

---

### Post by MJN on 2007-10-10
> **Megaqwerty said:**
> Could anyone tell me how to block a range of IPs in hosts.deny? Like, say: 222.168.0.0 - 222.223.255.255 ?
 
Thanks,
 
Megaqwerty
 
Sure, but you'll need to learn CIDR/VLSM ([http://en.wikipedia.org/wiki/VLSM](http://en.wikipedia.org/wiki/VLSM)) if you don't want to enter each address in individually. Prepare for a few headaches if you've not done it before! ;)
 
Your range can be broken down into:
 
**222.168.0.0 - 222.175.255.255**
**222.176.0.0 - 222.191.255.255**
**222.192.0.0 - 222.223.255.255**
 
...which, using VLSM, can be represented as:
 
**222.168.0.0/13**
**222.176.0.0/12**
**222.192.0.0/11**
 
You can then enter these into hosts.deny as:
 
**ALL: 222.168.0.0/13, 222.176.0.0/12, 222.192.0.0/11**
 
Mathew

---

### Post by MJN on 2007-10-10
> **GigaVolt said:**
> Hmmm...
I use this solution:
route add -net X.Y.Z.0 gw 127.0.0.1 netmask 255.255.255.0
 
X.Y.Z.0 is bad network
 
That's a bit too broadbrush as whilst it may well cover one requirement it will also steamroller in over a load of others.
 
hosts.deny is used to control *dameon access* e.g. forbidding SSH access to a range of IP addresses but still allowing them HTTP, SMTP access etc. Your blackhole routing would stop all of this and more besides (including all outgoing connections to those addresses) hence it may not be a desirable strategy to take! Always use the right tool for the job - 'sneaky tricks and workarounds' may be fun, but they can all too easily drop you in hot water and/or have undesirable (and known!) consequences! :)
 
Mathew

---

### Post by Megaqwerty on 2007-10-10
Thanks guys. I'm going to use MJN's VLSM method, and use [blackholes.us]("http://www.blackholes.us/zones/countries/countries.rbl")'s country ip database. Finally, I will be able to keep most of those Chinese bruteforce attacks on my SSH server from flooding my logs.

Thanks again guys,

Megaqwerty

---

### Post by MJN on 2007-10-11
Have you looked at the several on-the-fly automated blockers, e.g. fail2ban, denyhosts etc?

Alternatively, HermanAB recently posted a little iptables one-liner ([here]("http://ubuntuforums.org/showthread.php?t=568100")) that effectively rate limits connections which may suffice.

I can't help but feel that keeping up with a blacklist, particularly if it requires any manual intervention, may be more trouble/effort than really necessary.

Mathew

---

