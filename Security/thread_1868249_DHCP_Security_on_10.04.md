---
title: "DHCP Security on 10.04"
date: 2011-10-24
forum: Security
---

### Post by Sef on 2011-10-24
A nonprofit that I am friendly with is thinking about installing a Linux DHCP server (Ubuntu 10.04 possibly) on its network which has an IT department of one part-time person. For security, what are things that I can do to the server that could prevent rogue DHCP servers and rogue clients from causing problems? I want to keep things as simple as possible in case a new IT person starts in place of the current IT person.

---

### Post by redmk2 on 2011-10-24
> **Sef said:**
> A nonprofit that I am friendly with is thinking about installing a Linux DHCP server (Ubuntu 10.04 possibly) on its network which has an IT department of one part-time person. For security, what are things that I can do to the server that could prevent rogue DHCP servers and rogue clients from causing problems? I want to keep things as simple as possible in case a new IT person starts in place of the current IT person.

I believe that you can't really do anything to prevent rouge DHCP servers on your network other than limiting you DHCP pool addresses and looking for addresses outside of that pool.

A DHCP client initiates the request for an address via broadcast and any DHCP server on that subnet can answer.  The first one to respond and be accepted by the client hands out the address. 

Rouge clients.  Hmmmmm, what employee would allow anyone to plug in a host or provide a wireless access password to your network?  You could manage your DHCP clients by MAC address, but that gets old real fast.

All the normal protection applies: firewall all ports except what you need to have open.

---

