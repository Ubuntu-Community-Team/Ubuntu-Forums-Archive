---
title: "How much RAM to use for WinXP?"
date: 2008-03-31
forum: Virtualisation
---

### Post by Scooter7 on 2008-03-31
Hi,

I'm going to install WinXP in Virtualbox, but I'm not sure how much ram to give it.   My previous installations ran slowly - usually, the virtual WinXP ran fine, but while this runs Ubuntu slows to a crawl.

I have two processors, both Genuine Intel(R) CPU T2300 according to the System Monitor.   Virtualbox recommends 192 MB of RAM for WinXP, but I'm usually using  about 353.8 MB out of 494.4 MB - 71.6% of my RAM, and this is when I'm running Kopete, and Firefox only, aside from the other standard processes.

How much RAM should I allocate to Windows so the virtual installation and Ubuntu can both run smoothly?   And can I increase my available RAM without adding physical hardware?

Thanks in advance,

---

### Post by fjgaude on 2008-03-31
For several years of direct experience you would really need a minimun of one gig of RAM, split half and half. WinXP works in 256M and so does Ubuntu but you will not be able to have many apps loaded at once... you want to avoid swapping to disk, eh?

I get by with one gig in my laptop okay, but I don't do much heavy graphic design there, only on my main box where I have two gigs.

---

### Post by djbon2112 on 2008-03-31
Depends on (a) how much RAM you have in your host system, and (b) what you're going to be doing with the OS in the VM. For me, I've got 2 GB on my host laptop, and I give XP in VirtualBox 1 GB of that, just to ensure everything is running smoothly. If you're not doing anything intensive, I'd give it 1/4-1/2 of your RAM. If it's something really intensive, go all the way up to 3/4, but never more.

---

