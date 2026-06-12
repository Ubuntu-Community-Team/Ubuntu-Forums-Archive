---
title: "security of ubuntu in windows for internet usage"
date: 2008-11-08
forum: Virtualisation
---

### Post by eival on 2008-11-08
im trying to get my mother to use linux since shes not as aware of all the dangers with the internet, but at the same time she loves to play sims. so installing windows as the vm for sims is out of teh question and id like to avoid the need of a dual boot.

so my question is, if i have a vm of linux, and use that for browsing, what/if any risk is there that it can effect the windows os?

and would there be away to disable the network adapter in windows and still allow the vm to connect to the internet(or something to that extent)?

---

### Post by bodhi.zazen on 2008-11-08
Well virtualization keeps the OS as separate as possible. Securing a virtual machine is the same as securing a physical machine (you can not "protect" a windows machine by running it within Ubuntu for example).

---

### Post by eival on 2008-11-09
would any spyware or viruses that are written for windows be able to infect the windows host through an Ubunbu VM?

thats all im really interested in knowing.

---

### Post by bodhi.zazen on 2008-11-09
In theory, no. The guest is as isolated as possible from the host.

In practice, yes if for example you are using some type of file sharing.

---

### Post by Thirtysixway on 2008-11-09
It may be a hassle to start up a vm for linux just to browse the web...

---

### Post by SunnyRabbiera on 2008-11-09
yeh if windows gets infected in VM mode it wont do squat to linux... its safe :D

---

### Post by eival on 2008-11-09
> **Thirtysixway said:**
> It may be a hassle to start up a vm for linux just to browse the web...

i know but im just gonna do this for my mom since she likes to do online banking.

thanks for the info everybody.

---

