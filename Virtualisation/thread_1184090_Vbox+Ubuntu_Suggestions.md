---
title: "Vbox+Ubuntu Suggestions"
date: 2009-06-10
forum: Virtualisation
---

### Post by treyh22com on 2009-06-10
I have a dell poweredge r805 with 2 quad core cpu's and 8 gigs of ram, 64bit.

I am currently running 8.04 server 64bit with virtualbox (puel)

Before starting a VM, the server only uses 200-300mb of ram.

After starting a VM (windows server 2003 32bit) the memory usage jumps to around 1.8g and then slowly but steadily climbs. 

After about 20 minutes there is 32mb of memory free and the rest is in use, swap is still at 0.

The first VM runs slow when the host's memory gets low and if I try to start another VM, the 1st or 2nd VM will get a error (most of the time segmentation fault) and abort.

What am I doing wrong here?

I would prefer to run the VM's headlessly but have also tried running vbox in X, same problems with both.

---

