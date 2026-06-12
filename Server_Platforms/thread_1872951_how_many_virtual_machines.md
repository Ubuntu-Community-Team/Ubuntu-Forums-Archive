---
title: "how many virtual machines ?"
date: 2011-10-31
forum: Server Platforms
---

### Post by jonkiribati on 2011-10-31
Hi everybody,

I have a question about how to know how many VMs can a Server handle ?

---

### Post by Devi1903 on 2011-10-31
Depends on hardware. VMs use CPU and RAM to run. The more CPU and RAM you have the more VMs you can run.

It is also very dependent on what operations these VMs would be performing and what they would actually be. As each OS and operation would use a different amount of resources.

---

### Post by jonkiribati on 2011-10-31
Yep but isn't there any one to calculate that approximately ?

---

### Post by Devi1903 on 2011-10-31
Possibly, but none i am aware of without knowing the exactly OSs and tasks each would perform and check the hardware usages of each.

I would probably just run some testing. Get something setup install a server monitor like munin and get your vms running and see what the performance is like.

Or are you requiring to purchase some new hardware that is required to run a specific amount of vms and you need to know before hand what hardware to get?

---

### Post by jonkiribati on 2011-11-02
Yep I'm planning to buy a server and I'm trying to know how can I size it to know how many VMs it can handle.

---

