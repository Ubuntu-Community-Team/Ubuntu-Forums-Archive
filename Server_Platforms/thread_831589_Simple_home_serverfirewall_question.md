---
title: "Simple home server/firewall question"
date: 2008-06-17
forum: Server Platforms
---

### Post by Untame_Zerg on 2008-06-17
Me and my dad have been searching for a decent OS to use for a home network server. Just something to store media and archive various installer files for Windows XP. 

So far, we have Ubuntu 8.04 Hardy Heron on a Dell Optiplex PC that we figured had decent stats to be a server, if not run any fancy programs. It has the desktop edition on it right now, as I haven't heard about running a firewall on the server edition. We've already tried out a firewall called Firestarter, and we may go with that one. 

Onto the questions:
1. Is the server edition of Ubuntu required for home fileserver use? 

2. I read somewhere that 2 hard drives are needed; 1 for the Ubuntu OS and another for data storage. Is this true, or can I just partition the single drive for both applications?

3. Is it even possible to have a server *and* a firewall in one system?

Thanks,
Steve

---

### Post by iskatyel on 2008-06-17
Onto the questions:
1. Is the server edition of Ubuntu required for home fileserver use? 

No.  You can set up samba shares easily within the desktop edition.

2. I read somewhere that 2 hard drives are needed; 1 for the Ubuntu OS and another for data storage. Is this true, or can I just partition the single drive for both applications?

You can partition the drive for both uses.  The only reasons to use a second drive are the obvious ones (size, speed, redundancy)

3. Is it even possible to have a server *and* a firewall in one system?

Absolutely.  You just need to be certain of which ports to leave open for fileserving (139 may be enough for samba or 137-139 and 445 to be safe).

---

### Post by windependence on 2008-06-17
Me and my dad have been searching for a decent OS to use for a home network server. Just something to store media and archive various installer files for Windows XP. 

So far, we have Ubuntu 8.04 Hardy Heron on a Dell Optiplex PC that we figured had decent stats to be a server, if not run any fancy programs. It has the desktop edition on it right now, as I haven't heard about running a firewall on the server edition. We've already tried out a firewall called Firestarter, and we may go with that one. 

Onto the questions:
1. Is the server edition of Ubuntu required for home fileserver use?

As was stated no, BUT the server edition kernel is tuned for this type of thing. 

2. I read somewhere that 2 hard drives are needed; 1 for the Ubuntu OS and another for data storage. Is this true, or can I just partition the single drive for both applications?


This can be done all on one hard drive, no problem. Try not to let anyone tell you to run RAID so that you have a backup. You actually need a REAL backup, preferably off site. Also, running software RAID is not something I recommend.

3. Is it even possible to have a server *and* a firewall in one system?

While indeed you can do this, if someone launches a DDOS attack on your server, they can bring it down by overloading the CPU. IMHO, it's best to use a simple hardware firewall, or put it on a separate box. You can always build a small box using m0n0wall or pfsense, both free and open source and rock solid, or you can just buy one for about $40.

-Tim

---

### Post by freebeer on 2008-06-17
With regards to firewalls, if you already have a router (facing the internet), then you really don't need another firewall inside of a home network.  A properly secured router will block any outside threats.

---

