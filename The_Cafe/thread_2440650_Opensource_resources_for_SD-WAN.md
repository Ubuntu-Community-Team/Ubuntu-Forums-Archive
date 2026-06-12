---
title: "Opensource resources for SD-WAN"
date: 2020-04-13
forum: The Cafe
---

### Post by jason.jackal on 2020-04-13
I am reading a great deal about SD-wan recently; however, I am still new to the concepts and solutions. Due to the latter, is there anything Ubuntu or Linux/FeeBSD offers to turn x86 machines into a router like device that can be paired with a central controller, and an orchestra?

Cisco offers a number of items and solutions, products for SD-WAN; however, that would cost some money. At this point I just want to build a lab, and proof of concept, so: support, warranty and licenses is not a main concern... just getting the concepts and proof down.

Thank you

---

### Post by TheFu on 2020-04-13
There are many Linux SD LAN/WAN tools.  Google found a few.  I&#8217;ve not used any.  
[https://www.linux.com/news/5-open-source-software-defined-networking-projects-know/](https://www.linux.com/news/5-open-source-software-defined-networking-projects-know/)

As you can imagine, F/LOSS doesn't have a marketing department going to colleges and pushing their "really great" hardware w/ 15% fees for annual maintenance/patches.

---

### Post by jason.jackal on 2020-04-14
> **TheFu said:**
> There are many Linux SD LAN/WAN tools.  Google found a few.  I’ve not used any.  
[https://www.linux.com/news/5-open-source-software-defined-networking-projects-know/](https://www.linux.com/news/5-open-source-software-defined-networking-projects-know/)

As you can imagine, F/LOSS doesn't have a marketing department going to colleges and pushing their "really great" hardware w/ 15% fees for annual maintenance/patches.

Thank you for the link; however, I did find the same resources, so I should have been more specific. You answered my real question - if you have used any of the opensource SD-WAN controllers.

---

### Post by TheFu on 2020-04-14
> **jason.jackal said:**
> Thank you for the link; however, I did find the same resources, so I should have been more specific. You answered my real question - if you have used any of the opensource SD-WAN controllers.

A client was using an SD-LAN grid tool for some of their container apps.  I never had to touch that aspect.
Suspect you'd be better asking this sort of question on the #ubuntu-server IRC than here.  It is a different crowd there.  These forums are mostly home desktop users with a few web-dev professionals.

And if you are interested in direct experience, put that in the title.  Linux is huge, so nobody knows or has experience with everything.

As for SD-WAN stuff, the closest I've come was asking a network design engineer to connect 13 business locations with thousands of users each to an ATM network redundantly.  ATM networks route around failures.  In my mind, I see a grid network, but really don't have any idea how it is actually accomplished in the hardware.

---

