---
title: "Can not see the volume in Window instance"
date: 2011-05-02
forum: Ubuntu Cloud and Juju
---

### Post by lemon1707 on 2011-05-02
I had started a Cloud on single machine with Ubuntu 9.10 64 bit. Everything worked good, I attached a volume to window instance running, it changes the status of volume from available to in-use, but when I used RDP to login to instance,Go to Start -> Run and type diskmgmt.msc, I didn't see any new disk at the bottom of the list.
I had found everything on forum and some other but I couldn't find the problem. Please help me to solve that problem !:confused:

---

### Post by kim0 on 2011-05-03
Disk hotplug might not be in KVM for windows guests. Please try powering off the VM, attaching disk, then starting. Also might want to try a newer Ubuntu like 11.04

---

### Post by lemon1707 on 2011-05-04
Hi kim0,
thank for your relpy, I'm trying to solve that problem. I decide to setup cloud on 2 machines. I hope your post help me to fix that problem. I will show the causes later. Any differences situation, let me know.

---

