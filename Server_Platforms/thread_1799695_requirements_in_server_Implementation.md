---
title: "requirements in server Implementation"
date: 2011-07-08
forum: Server Platforms
---

### Post by Rakeshvijayan on 2011-07-08
Hi friends 
 
  Now in my environment we have no big server and have only broad band connection connected with more than 100 computers .we are planing to purchace a lease line from bsnl  and server ,  on that time we are planing to secure all system with that server and limit speed and block unwanted site and monitor all activities on my network (dns and dchp should be there ).remaining services that I need to know ....... 

I MEAN REQUIREMENTS OF SERVICE IN A  PERFECT SERVER .

---

### Post by Lars Noodén on 2011-07-09
> **Rakeshvijayan said:**
> ...I MEAN REQUIREMENTS OF SERVICE IN A  PERFECT SERVER .

What tasks and activities do you intend to use the server for?
Those will shape any requirements.

---

### Post by Rakeshvijayan on 2011-07-11
> **Lars Noodén said:**
> What tasks and activities do you intend to use the server for?
Those will shape any requirements.
 planing to secure all system with the server and limit speed and block  unwanted site and monitor all activities on my network (dns and dchp  should be there ).

---

### Post by tgalati4 on 2011-07-11
Sounds like  a simple firewall.  You'll need two high speed network cards.  CPU load is minimal.

---

### Post by Rakeshvijayan on 2011-07-11
> **tgalati4 said:**
> Sounds like  a simple firewall.  You'll need two high speed network cards.  CPU load is minimal.



Is just need a firewall enough. for setting firewall what can I do .....I think am in right place to get solution

---

### Post by Lars Noodén on 2011-07-12
> **Rakeshvijayan said:**
> Is just need a firewall enough. for setting firewall what can I do .....I think am in right place to get solution

The firewall in Ubuntu is UFW, but it is also possible to work directly with IPTables which is under UFW.

---

