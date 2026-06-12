---
title: "HELP!!! UDMA Mode Data Corruption on IDE Drives"
date: 2006-10-09
forum: Sun Sparc Users
---

### Post by rimtech on 2006-10-09
I am a recent gentoo convert, that is, i used to use gentoo but no more, now I'm an ubuntu boy... 

So, a while back I was using gentoo and I installed it on my Sub Blade 100... but lo and behold... it simply would not boot with DMA support. Every single boot would have to be appended with ide=nodma. So... after a long time of running in PIO mode only which is very very slow, and after I had recently discovered ubuntu on my desktop, I decided to give it ago on my blade 100... and so i did, but... again, I had to use ide=nodma on each boot...

I came to my own conclusion and from reading various documents on the internet/google that apparently this system has a specific IDE controller.... the ALI15X3, of which there is support in the linux kernel but on sparc64 systems there is data corruption when DMA is enabled. 

More research has yielded me further results:
[http://www.ussg.iu.edu/hypermail/linux/kernel/0307.2/0620.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0307.2/0620.html)

Apparently whoever posted this had discovered a solution for 2.4 kernels..., why hasn't this made it's way into the kernel source tree and WHY oh WHY doesn't ubuntu have this patch for the 2.6 version, and more specifically the sparc64 kernel?

What would be really great is if an avid developer were to read this and decide to modify the ALI15X3 driver for sparc64 kernels to encorporate this change, as it is clearly a kernel defect. This is my dream.

OR...

What would be nice also is if someone would post how i can do it myself, considering i am not a developer and have no idea how to turn a 2.4 kernel patch into a 2.6 kernel patch. 

Kindest regards to whoever reads this....
:)

---

### Post by Delta_Farce on 2006-10-10
Hmm...It would be great if the DMA issues with Sunblade 100 and 150's could be solved with a kernel patch.

I've played around with several OS's on my 150 and it seems that BSD distros (FreeBSD and OpenBSD) do not seem to have the same issues as Linux distros have with DMA.

---

### Post by netztier on 2006-10-10
> **rimtech said:**
> 
What would be nice also is if someone would post how i can do it myself, considering i am not a developer and have no idea how to turn a 2.4 kernel patch into a 2.6 kernel patch. 


Have you tried posting it as a bug on launchpad.net? That's where you can best reach the Ubuntu developers. If it is beyond their scope to fix it, they' at least know exactly where to go "upstream" to ask the right people to fix it.

Make sure you'll include pointers to all the relevant information you have been able to collect, so you can save them quite a bit of research work, and they'll appreciate the effort you have brought into it beforehand.


regards

Marc

---

