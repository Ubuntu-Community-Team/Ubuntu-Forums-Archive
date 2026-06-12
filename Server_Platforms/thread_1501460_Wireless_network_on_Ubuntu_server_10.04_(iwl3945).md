---
title: "Wireless network on Ubuntu server 10.04 (iwl3945)"
date: 2010-06-04
forum: Server Platforms
---

### Post by feo_ on 2010-06-04
Hello!

I just installed Ubuntu Server on a laptop (HP Pavillion dv6332ea), but I am having trouble getting the the wireless connection to work.

lscpi | grep Network returned:
```
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```

According to the [list of supported network cards]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel") it appears to be supported. Are these cards supported by Ubuntu Server too? And is the list up to date?

When I do *lsmod*, I can see there is a module by the name of iwl3945 running.

I tried to insert the correct information (ESSID, channel and mode managed) into /etc/network/interfaces and reset both network and computer, but to no avail.


I'm not bothering with encryption at the moment, I just want it to actually be able to connect! :)

I'm a bit of an Ubuntu noob, so if anyone could give any advice as to what steps to take to find out what to do/if it can be done.

/feo


EDIT:
Okay I have fixed the issue myself... It was a simple matter of me being an idiot and entering wrong information in /etc/network/interfaces

(The channel was wrong, causing the adapter to scan the wrong frequency ... or something like that :P)

---

### Post by phillustine on 2011-11-13
Can you please post your interfaces set up, because I'm having the same problem.

---

