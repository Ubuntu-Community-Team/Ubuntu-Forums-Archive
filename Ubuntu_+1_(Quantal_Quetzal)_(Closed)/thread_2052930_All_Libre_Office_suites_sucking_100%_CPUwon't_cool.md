---
title: "All Libre Office suites sucking 100% CPU/won't cool down."
date: 2012-09-04
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-09-04
I had seen the other thread but I thought I would put this up here. If it is duplicate then please merge.

  Libre suites are pulling 100% cpu slice. This machine , Intel64bit 2.9GHz/1.2GBddr. 200GB SATA.

---

### Post by Harry33 on 2012-09-04
> **ventrical said:**
> I had seen the other thread but I thought I would put this up here. If it is duplicate then please merge.

  Libre suites are pulling 100% cpu slice. This machine , Intel64bit 2.9GHz/1.2GBddr. 200GB SATA.

Which LO version you are using?

This says it has been fixed:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1041354](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1041354)

---

### Post by dino99 on 2012-09-04
latest version has solved that issue on my i386 quantal

---

### Post by philinux on 2012-09-04
> **ventrical said:**
> I had seen the other thread but I thought I would put this up here. If it is duplicate then please merge.

  Libre suites are pulling 100% cpu slice. This machine , Intel64bit 2.9GHz/1.2GBddr. 200GB SATA.

Not here. Acer 1410. Intel 1.3gHz 64bit 2gig mem.

Not sure what to suggest either.

---

### Post by ventrical on 2012-09-04
> **Harry33 said:**
> Which LO version you are using?

This says it has been fixed:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1041354](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1041354)


3.6.0.2, Build 102

I'll update yet again.

---

### Post by effenberg0x0 on 2012-09-04
Hi Ventrical, the best diagnostic method is to start something like calc and immediately run top in a gnome-terminal. If you still see unity-panel-service CPU% growing fast and consistently (it goes up indefinitely causing the stall) it is the same bug. If you run sudo killall -9 unity-panel-service it frees your CPU and calc / desktop becomes usable again.

Regards,
Effenberg

---

### Post by ventrical on 2012-09-04
> **effenberg0x0 said:**
> Hi Ventrical, the best diagnostic method is to start something like calc and immediately run top in a gnome-terminal. If you still see unity-panel-service CPU% growing fast and consistently (it goes up indefinitely causing the stall) it is the same bug. If you run sudo killall -9 unity-panel-service it frees your CPU and calc / desktop becomes usable again.

Regards,
Effenberg


Thanks for your reply. I think I have to apologize to all here. I updated and that solved the problem as which was reported by harry33. I should know better to update  first before creating a new thread but I just didn't think that the update would be that fast.

---

