---
title: "General questions about personal cloud computing."
date: 2015-03-18
forum: Ubuntu Cloud and Juju
---

### Post by bda714 on 2015-03-18
Hello all, 

      I need some advice on a project i am eager to start, although i have an idea in my head of what i want to do, I'm not sure of what the best way to go about this would be while utilizing what i have to work with in the best way, so here it is...  

Basically i have 5 fully built systems with 2 amd, 8 cores ech (4.7 & 5.0 fx chips) and 3 i5 quad cores.  With not nearly enough room and the mess of cables in my small room becoming ridiculous, i want to consolidate.  My first idea was to just build a server rack with multiple 2u atx cases and put them all in that, until i saw a hak5 episode with virtualization clusters.  Unfortunately it was a few years old and I'm afraid most of the info was outdated.  Now what i want....

All the systems basically in a render farm or beowulf configuration, centrally located, that would allow me to run about 4-6 virtual machines remotely at any given time and location..  (Never more than 1 or 2 at a time though)
  I would like to have probably half windows and half Linux VMs..
I am not trying to really spend any more money because i have a whole lot of hardware already, i just want to utilize it all better than to just having five seperate systems that i can access with RDP...  I will be using this for a wide range of tasks including 3d renders, compiling code, gaming if possible... Bla bla...  I hope i am explaining this right, like i said, the vision is clear in my head but i am still learning and don't even know where to look for answer yet,

Do i need vps, open stack, maas....etc.?  Please advise and thank you very much for any help.

---

### Post by TheFu on 2015-07-07
Cloud computing isn't usually good for anything where graphics is involved. The whole network latency issue, you understand.

if you want a personal "cloud" - think about replacing all those services that are "in the cloud" that you might use today.
[https://github.com/sovereign/sovereign](https://github.com/sovereign/sovereign) should provide some ideas for things to run.

But you posted this in the Juju sub-forum, which is a specific type of deployment model for different parts of the solution. Check out the "charms", assuming you setup a juju compatible infrastructure.

BTW - with 5 relatively powerful machines, you can run 40+ Linux VMs .... or 5 Windows machines. ;)  I run about 10 VMs on a C2D box with 8G of RAM nicely.

---

