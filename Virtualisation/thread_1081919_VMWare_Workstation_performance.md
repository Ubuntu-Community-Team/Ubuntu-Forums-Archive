---
title: "VMWare Workstation performance"
date: 2009-02-27
forum: Virtualisation
---

### Post by AnimalMagic on 2009-02-27
Is it better to run a 512k machine or 384k under workstation. I have a machine with 2gig memory and it runs 3 virtual machines, 2 with XP and one with Ubuntu 8.04. The host is Ubuntu 8.04.

With no machines started, but VMware running 572384 is used. 

Starting the first machine with 512k, all of memory is used up. 

Starting it with 384k only 1692976 is used (as reported by top)

Starting subsequent machines doesn't seem to make much difference other than 44980 of swap file being used. Starting the Ubuntu machine seems to make almost no difference to the memory usage...

Running all the machines with 384k seems to be faster, but can this be correct?

---

### Post by HermanAB on 2009-02-27
Yes, adding oodles of RAM to XP doesn't make any difference, unless an application actually needs it - eg Quickbooks with a large company file.

Cheers,

Herman

---

