---
title: "KVM and VMwareplayer on the same machine"
date: 2010-09-05
forum: Server Platforms
---

### Post by srivo on 2010-09-05
Is it possible that VMware Player and KVM don't like each other? I have some KVM VM working all the time and they where crashing from time to time. I finally discover that they where crashing when I use VMware Player?

Any one having the same problem?

---

### Post by alan8 on 2010-09-06
I haven't tried to run KVM and VMWare at the same time, but as both utilise low level virtualisation extensions found in modern CPUs (VT-x Intel / AMD-V) I can imaging they don't like each other very much.

---

### Post by kevinthecomputerguy on 2010-09-06
I could see that happening. Do you have the vmware tools installed inside the vm's ?
That may help... or hurt :- )
 
-Kev

---

### Post by srivo on 2010-10-10
I will check if the tool are present I don't remember. I will give feed back on this!

---

