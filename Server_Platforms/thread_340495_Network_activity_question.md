---
title: "Network activity question"
date: 2007-01-17
forum: Server Platforms
---

### Post by rickt on 2007-01-17
Hello everyone.
I hope this questions aren't too stupid, but I don't know that much about networking and such.
On my ubuntu machine, I am seeing constant activity when I click on Connection Properties eventhough I am not using any webbrower or anything. After a few minutes it's already recieved 1 mb. Is this normal?
When I run the program [Etherape]("http://etherape.sourceforge.net/") and click on view the protocols, I am seeing constant activity on protocols like SMB and Gnutella-svc. Does this mean that those programs are running on my computer because I haven't installed them or can it be that this activity is just people checking those ports in the hope that they are open?
I have no ports open (sudo netstat -tap|grep LISTEN shows nothing) and I also have a firewall (which I guess is useless if I have no ports open, but I installed one anyway out of habit :) ), I get alot of connection attempts blocked in the firewall log.
So, have I been hacked or is all this normal?
- Rickard.

---

### Post by scrooge_74 on 2007-01-17
There are no stupid questions so dont worry.

Your traffic may be norma, since I am no expert I like to see the reports Firestarter has when you have it running.

As for a firewall, your system comes with a firewall in the kernel, when you here about "IP tables" that is your firewall.  When you install a "firewall program" such as Firestarter you are  installing a GUI manager for IP tables

---

### Post by Dertiger on 2007-01-21
I notice the same thing on my computer - lots of SMB traffic within my local network.  I automatically mount a windows server and when Ubuntu is idle, network traffic skyrockets ... I wonder if Beagle is indexing over the network in the background?

---

### Post by scrooge_74 on 2007-01-21
From what I read on samba, it has to keep some traffic to maintain conenections with the other computers in the LAN.  But keep monitoring maybe you will find the reason.

---

