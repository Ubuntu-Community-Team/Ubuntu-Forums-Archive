---
title: "Colocation Blindspots"
date: 2007-12-16
forum: Server Platforms
---

### Post by rukuartic on 2007-12-16
I'll be sending a box to a colo sometime this month, or starting next year. Its a little scary, as I've never done this before. I had a few friends point out some things that I'd never have noticed before. 

For example, someone told me that I'd probably never noticed before -- such as needing rails for the rackmount. He said one particular colo he heard of only accepted boxes with a specific brand of rails.

Furthermore, should I invest in a lock for my server of sorts to protect my internals (such as RAM) from data center thieves? Or would this end up being a problem if something internal fails and I need them to pop the case and find out whats happening?

Thats all before I ship the box to the colo... When my box gets there, are they going to have to log in and configure networking by hand? Or should I configure this myself before sending it?

I've seen the Perfect Setup articles on HowToForge... they install BIND9. What would I need DNS for? Do I actually need it, or will I handle everything from my registrar (eg: namecheap, godaddy)?

If anyone in the community has experience they'd like to share, it would be greatly appreciated.

---

### Post by operator207 on 2007-12-16
> **rukuartic said:**
> I'll be sending a box to a colo sometime this month, or starting next year. Its a little scary, as I've never done this before. I had a few friends point out some things that I'd never have noticed before. 

For example, someone told me that I'd probably never noticed before -- such as needing rails for the rackmount. He said one particular colo he heard of only accepted boxes with a specific brand of rails.


No, thats specific TYPE of rails. I seriously doubt they require a specific brand. Unless they bought a bunch of cabinets that can only use their rails. Not a good colo facility if thats the case.

> **rukuartic said:**
> 
Furthermore, should I invest in a lock for my server of sorts to protect my internals (such as RAM) from data center thieves? Or would this end up being a problem if something internal fails and I need them to pop the case and find out whats happening?


Ya, its good to do that, but you would be giving them a key to open it. Unless you want to goto the colo facility to reboot, or fix anything that requires getting into it.

> **rukuartic said:**
> 
Thats all before I ship the box to the colo... When my box gets there, are they going to have to log in and configure networking by hand? Or should I configure this myself before sending it?


Thats up to the colo facility. They may give you IPs to pre-configure, or they may require that they have root access to do this. Call them, they will know, not us.

> **rukuartic said:**
> 
I've seen the Perfect Setup articles on HowToForge... they install BIND9. What would I need DNS for? Do I actually need it, or will I handle everything from my registrar (eg: namecheap, godaddy)?

If you want to run your own DNS server, then yes you will need BIND9 installed and running. I prefer that way. I do not like using others DNS servers. Then again, you may not want to do this. Its a personal requirement, not a requirement for everyone.

> **rukuartic said:**
> 
If anyone in the community has experience they'd like to share, it would be greatly appreciated.

I worked remotely for a company that had colo for customers. I strongly suggest that you get yourself into a colo that you can drive to if at all possible. Most 'techs' that are staffed at a colo facility, either will not know what to do to fix your computer (you will have to diagnose the problem yourself, remotely) or they will simply not help you (TOS against working too much on customer equipment).

---

