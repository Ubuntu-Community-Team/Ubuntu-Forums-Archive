---
title: "Virtualization for home use"
date: 2009-05-10
forum: Server Platforms
---

### Post by wwbdd on 2009-05-10
I have been a linux user for years now, but I have been unable (despite a valiant effort) to free my family from the death grip that Microsoft has on them.  We have several computers around the house that are used for only the most simplistic tasks, and I would like to install linux on them so that I can harness their power for some scientific computations.

So here's the idea... I install linux as the host on all of the systems I want to convert, and then setup some sort of virtualization, such that whenever the user mom or dad logs in, it start up a lightweight window manager (fluxbox probably), which immediately loads up a virtual machine in full screen mode, so that they are back in their familiar windows environment.  I would like to make this as seemless as possible, not because my family is compute illiterate, but because linux scares the mess out of them (I don't know why).

I have a windows license for all of these machines, so that isn't an issue.  What is the best way to approach something like this?

Thanks

---

### Post by ejschaefer on 2009-05-10
Hello, 

You might want to check out VirtualBox [http://www.virtualbox.org/](http://www.virtualbox.org/)

Looks like it will do what you want. VirtualBox is freely available. 

Otherwise, VMWare Workstation or VMWare Server is the way to go.

---

