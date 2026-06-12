---
title: "Running many XP guest OS's on laptop."
date: 2010-08-01
forum: Virtualisation
---

### Post by digib on 2010-08-01
Hi 

I want to run many guest XP OS's on my Thinkpad T61 notebook, T4200 dual core, 3GB ram, 7200 RPM HD, Ubuntu 10.04 host OS

I can currently run 2 guest XP at the same time. . Each guest OS has 600 mb of RAM and 26 mb graphics memory allocated. The performance is really bad though. The screen "greys out" now and then. Sometimes the system really locks down. Tried it both with VMware and Virtualbox.

Is it totally unrealistic to run 3 guest OS's on this machine ? And where is the bottleneck, RAM ? Graphics ? I/O ?

What kind of machine do I need to have to run a decent amount of XP guest OS's ( 5 or 6) ? Would love to have an i7 16GB Ram desktop for this but I'd rather use my existing hardware.

Sorry for the vagueness of this question. Guess I'm just looking for some ideas.

---

### Post by DarthScape on 2010-08-01
Looks like the processor you provided, T4200, does not have Intel VT-x (virtualization acceleration). Honestly, I would recommend a new computer, possibly 4GB of memory or more too. Also, do you have the virtual additions installed, could help some.

---

### Post by dcstar on 2010-08-02
> **DarthScape said:**
> Looks like the processor you provided, T4200, does not have Intel VT-x (virtualization acceleration). Honestly, I would recommend a new computer, possibly 4GB of memory or more too. Also, do you have the virtual additions installed, could help some.

Forget the processor, laptop hard drives have woeful performance compared to "proper" drives - and they are designed that way because they are biased towards power saving and size - and will always cause problems when heavily loaded. 5 gets you 10 that the the VMs - along with the host OS - are slamming the drive with IO requests.

Running simultaneous multiple VMs in a laptop - a hardware environment specifically designed to run one OS in the most energy efficient manner possible - is folly.

---

### Post by JustinR on 2010-08-03
Buy an external HDD for your VM's - it won't tax your hard drive out like dcstar said!

There getting pretty cheap.:D

---

### Post by digib on 2010-08-03
Thanks for your input people  Your ideas have been noted. Will try the external HDD version and see how it goes.

---

