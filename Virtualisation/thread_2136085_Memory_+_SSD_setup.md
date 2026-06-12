---
title: "Memory + SSD setup"
date: 2013-04-16
forum: Virtualisation
---

### Post by ERRRIMMAD on 2013-04-16
So I want to set up an ubuntu virtualbox on my ubuntu os, I want to do this so I can test apps before I install them to my actual OS, that way if it crashes something I will know not to do it on my main OS.

This is my build, I have 8gb of ddr2, a 256gb crucial M4 SSD, a PCI-E 2.0 MOBO, and a core2 quad processor, I also have an e-GeForce 8600 gts, on the outside chance that should make any difference at all, although I can't see why it would.

My software is Ubuntu 12.04 and the virtualbox version is the latest 4.2 build.

So here comes the million dollar question.

When I installed my ubuntu OS I did not setup a swap drive because you're not suppose to on a SSD with as much memory as I have, in most cases 8gb is sufficient, even pushing my system hard I have never consumed half of that.

So when I install a virtualbox build I can already see the potential problem, if my main OS is keeping 2GB for it's own operation off the top, and I set up a new virtualbox which also does not have swap, and I assign it 2GB, which will not really leave enough memory in case I need it considering no swap will be available on the VM.

I also would want to install other VM's to my computer in the future, so here is the big question.

Should I install the VM on a secondary rotational drive?

Also, when running the VM what are the chances of encountering memory problems if enough virtual machines are open to actually limit the original OS to 2GB.

Just trying to get a full understanding of this kind of setup before I blindly get in trouble, I would appreciate any advice that can be offered by anyone who has encountered a situation similar to what I'm about to attempt.

Thanks.

---

### Post by dcstar on 2013-04-18
Swap on a SSD is not an issue. Run your VMs without swap and if you find that need it, set up swap.

---

