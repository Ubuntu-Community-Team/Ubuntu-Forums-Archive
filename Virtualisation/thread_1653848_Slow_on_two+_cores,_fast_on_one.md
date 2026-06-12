---
title: "Slow on two+ cores, fast on one"
date: 2010-12-27
forum: Virtualisation
---

### Post by superheavy on 2010-12-27
Hello folks,
  I have a simple question , not really a problem.  I am running Ubuntu on an AMD quad-core ( 64bit OS and hardware ) with a windows vista guest.  I got this computer because virtualized vista was slow on 2 cores.  I set the vm to run using 2 and noticed the system was unusable, then I switched it to 3 cores.  No luck.  I saw in another post, they switched the vm to use one core so I did the same. Voila !  The vm ran MUCH faster than before.

My question is, why would the vm run faster on one core than 2+ cores.  I'm not ragging on anybody, as a programmer myself, I know it must be hard to design software to work on such a "soup" of hardware.

---

### Post by dcstar on 2010-12-27
> **superheavy said:**
> Hello folks,
  I have a simple question , not really a problem.  I am running Ubuntu on an AMD quad-core ( 64bit OS and hardware ) with a windows vista guest.  I got this computer because virtualized vista was slow on 2 cores.  I set the vm to run using 2 and noticed the system was unusable, then I switched it to 3 cores.  No luck.  I saw in another post, they switched the vm to use one core so I did the same. Voila !  The vm ran MUCH faster than before.

My question is, why would the vm run faster on one core than 2+ cores.  I'm not ragging on anybody, as a programmer myself, I know it must be hard to design software to work on such a "soup" of hardware.
(Way simplified explanation based on what I have read previously on this issue):

Because on most VM management systems the guest VM waits until **all** CPUs are available and the host takes priority over any VM.

Using a single CPU allows the VM manager to pick a single available CPU without the logical "AND" of all of them being available to match the quantity allocated to the VM.

If you had a host/hypervisor that did nothing but run VMs then this shouldn't be much of an issue, but if your host uses resources for itself then the VMs just take second (or third....) priority.

---

### Post by supershin on 2010-12-28
So you're saying its better to run VM's on a single core if the host is being used. If the host is just running VM's only then multi-core is an option. 

Is that it?

---

