---
title: "Ubuntu office server.. not quite newbie questions!?"
date: 2006-11-07
forum: Server Platforms
---

### Post by a.d.gardiner on 2006-11-07
Hey all,

my first post here.

Sometimes it sucks being me. lol.

Work have asked me to network our printer to their small office network of 8 machines and to get something done about internet filtering. Sure I hear you, why don't they pay somebody to do it! Bottom line.. they won't/can't afford it and as the guy who knows most in the building about this kind of stuff.. they asked if i had any idea!? Soooo... I had a ponder and thought it might be quite an interesting project. (Guy who knows most.. lol... they must be delusional).

Anyway, it seems sensible to go with linux because of the free liscence etc, and the ubuntu distro because itspretty easy to get around and add things to.

Anyways, I have an old ish pentium 4 machine spare, with 2 ethernet ports and a gig of memory and thought that I might have a crack at this.

I have some very basic experience with using 6.06 on a couple of desktop machines.. as much as getting the graphics working alright, and compiling/installing drivers for a nasty unsupported boardcom wireless card.

The services we are going to require from the machine are acting as some kind of router for our internet connection (running our 1 port adsl router into one NIC and sharing it out of the other to our network swtich), in conjunction I read running squid proxy/squid guard could limit access to the internet for certain users on the network, I'd like to also install apache with php and lastly get some kind of print server going. We have a usb HP inkjet printer which ideally needs sharing to every machine on the network.

Any pointers or suggestions would be dead useful. I understand this is going to be a lot of work.. but if anybody has an pointers or advice..

much appreciated.

cheers,

alex

---

### Post by Antonlacon on 2006-11-08
> **a.d.gardiner said:**
> The services we are going to require from the machine are acting as some kind of router for our internet connection (running our 1 port adsl router into one NIC and sharing it out of the other to our network swtich),
iptables, part of the kernel.

> lastly get some kind of print server going. We have a usb HP inkjet printer which ideally needs sharing to every machine on the network.


SaMBa + CUPS.

---

### Post by mips on 2006-11-08
[http://www.ubuntuforums.org/showthread.php?t=111972](http://www.ubuntuforums.org/showthread.php?t=111972)  could be part of your solution.

---

### Post by a.d.gardiner on 2006-11-08
:D cheers guys.. gonna go read through that now

---

