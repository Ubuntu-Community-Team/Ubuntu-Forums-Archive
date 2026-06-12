---
title: "memory allocation/lock failure during Ubuntu install (Virtualbox/win7 host)"
date: 2014-12-04
forum: Virtualisation
---

### Post by ljwobker on 2014-12-04
Apologies for what is sort of a cross post, but it's not at all clear to me how the interaction works between VirtualBox and the Ubuntu installer.  If the problem described in the thread linked here did not occur every time at the same place in the Ubuntu install, I would think it's a VBox thing.  But given the amount of memory on the machine (12GB) it's hard to see how it's a pure availability issue...

The virtualbox log file is in the thread also.  Any thoughts would be appreciated...

[https://forums.virtualbox.org/viewtopic.php?f=6&t=64963](https://forums.virtualbox.org/viewtopic.php?f=6&t=64963)

---

### Post by TheFu on 2014-12-06
Win7 is the host?
Don't give Ubuntu too much RAM or too many CPUs  - 1G is fine and 1 vCPU.
More details on optimized vbox settings: [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox)

The ubuntu installer shouldn't know anything about running inside a virtual machine.

Is there a specific reason to give Ubuntu lots-o-RAM?  In the many years I've been running VMs, I've never needed to allocate more than 1.8G of RAM to a server VM and 1.5G to a desktop. While Ubuntu desktop is fairly bloated, it isn't like that other OS in the realm of bloat.

---

### Post by ljwobker on 2014-12-07
I'm running fairly memory intensive applications in the guest VM (the Ubuntu part).  But that's sort of orthogonal to the question, which is really "why would the Ubuntu installer request a ton of memory from the host OS?"

---

### Post by TheFu on 2014-12-07
> **ljwobker said:**
> I'm running fairly memory intensive applications in the guest VM (the Ubuntu part).  But that's sort of orthogonal to the question, which is really "why would the Ubuntu installer request a ton of memory from the host OS?"

Does the workaround not work for you?  Install with less than 2G of RAM inside the VM, then post-install, up the amount to avoid swapping?

---

### Post by ljwobker on 2014-12-07
No, the workaround is fine - but I'm a curious problem-solver type.  The question is more about WHY it's happening so (in theory) it can be fixed and others won't have to deal with it.  For me it's just an aggravation to do the switcheroo...

---

### Post by TheFu on 2014-12-07
If it is Ubuntu-specific, trying with a different hypervisor should help determine where the problem is - virtualbox+Windows or Ubuntu.
I'll try to test on KVM today with a huge amount of RAM for the installer and report back.
If someone else can test with virtualbox on Ubuntu, that would be helpful too ... wouldn't it?

---

