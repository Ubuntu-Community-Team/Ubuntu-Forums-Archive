---
title: "Server specifications - hardware incompatibility?"
date: 2008-06-27
forum: Server Platforms
---

### Post by CulleyS on 2008-06-27
Hello,

We are considering building a Dell server with the following specs to run Ubuntu Server LTS 8.04:

Dell Poweredge 2900 III
Dual Quad Core Xeon E5405 2 X 6MB Cache, 2.0 GHz, 1333MHz FSB
8 GB 667MHz (2 X 4GB), Dual Ranked DIMMs
Integrated SAS/SATA RAID 10, PERC 6/I integrated RAID CARD
(6) 146 GB 15K RPM SAS 3Gbps 3.5-in Hot Plug Hard Drives
Dual Embedded Broadcom NetXtreme II 5708 Gigabit Ethernet NIC


Just curious if there was anything that jumped out and screamed "Whoah, don't use this, use this instead."  I think most of it is fine, but I'm most concerned about the Integrated RAID Card.

Thanks in advance for your time,

Culley

---

### Post by shad0w_walker on 2008-06-27
I'm by no means an expert on the hardware, but if memory serves, Dell ensures all their server hardware is Linux compatible, so that and not seeing anything that's raising red flags I'd say you're pretty good to go. I would suggest waiting for a more experienced answer, but I can't see any obvious problems.

---

### Post by Uluen on 2008-06-28
If you click the link to the specs on that server you'll see RHEL as an option for preinstalled OS.

---

### Post by CulleyS on 2008-06-30
Yep, I was just following through on something my boss asked me to do.  Which was post here to make sure. :)

Off topic, nice to another Einstürzende Neubauten fan here.  Have a tattoo of Man in Fire on my arm and have been a long-time fan of the band's work. :guitar:  I guess I'm assuming you're an EN fan by your avatar, when you could just be a fan of Toltec cave drawings. :)

---

### Post by John.Klockenkemper on 2008-06-30
We use dell servers here at my place of business and they are great machines. Reliable, inexpensive (in a manner of speaking), and all of their hardware works great with linux. 

Your hardware will run very well with linux. The only thing that you might have trouble with is your raid card.

I would research more on that card and its usage with ubuntu.

---

