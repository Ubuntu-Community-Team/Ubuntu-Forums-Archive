---
title: "Virtualbox linux host,,, xp or vista bus for child?"
date: 2008-12-13
forum: Virtualisation
---

### Post by pompeyjohn on 2008-12-13
Hello all,

I am running the non OSE version of Virtualbox on a dual core 32bit laptop with 4 gigs of ram.

I have legitimate legal copies of XP and Vista. Which should I install as a child? 

I am proposing on giving the child 1gig of Ram, and 64mb of display memory. The purpose of the child is to run development tools which both OS can run. I may also use it for iphone synchronization.

I expect to use the VM for about 20% of the time I am using the laptop - but would like to have it running at all times.

Is there is any information available about performance comparisons between the two of them when virtualized?

I am looking forward to hearing opinions on this as I am unsure of the way forward and really value the help on here.

Many thanks in advance
John

---

### Post by Dedoimedo on 2008-12-14
Hello,

In general, virtualization like VB and similar will give you about 80% performance compared to native installation, but:

If you place virtual machines on a separate partition, even better a separate hard disk, you'll increase performance, especially for intensive IO tasks.

If you preallocate the hard disk space, you'll improve performance.

Faster hard disks = better, multicore CPU = better.

Seeing this is a hot cake, I'm gonna post a tutorial for vm performance issues, soon :)

Dedoimedo

---

