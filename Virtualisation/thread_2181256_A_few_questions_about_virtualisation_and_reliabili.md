---
title: "A few questions about virtualisation and reliability"
date: 2013-10-17
forum: Virtualisation
---

### Post by Q7JEscD on 2013-10-17
Hello,

I am new to the virtualisation techniques and have a few questions.

If I have several physical servers, is there a way of creating some kind of redundant VMs, so that if one server fails, the other VM will instantly do all the work of the failed VM?

---

### Post by TheFu on 2013-11-15
You can create clusters with VMs just like you do with regular systems.

---

### Post by houstonbofh on 2013-11-16
There are as many ways to do this are there are systems.  In VMware, they call it vmotion, for example.  Outside of visualization, you can use something like CARP. (You could do it virtually as well)  Some poeple use puppit to monitor and restart a stuck VM, or start a different one.

---

### Post by TheFu on 2013-11-17
> **houstonbofh said:**
> There are as many ways to do this are there are systems.  In VMware, they call it vmotion, for example.  Outside of visualization, you can use something like CARP. (You could do it virtually as well)  Some poeple use puppit to monitor and restart a stuck VM, or start a different one.

Moving VMs between physical hardware has been supported by KVM and Xen for some time too.  To my knowledge, all of them require a SAN/NAS setup for the VMs for this to work ... except extremely recent versions of ESXi which can use local storage on both and migrate VMs (according to their announcement at VM-World a few months ago).

Moving a VM is not the same as clustering, however. If you have a service that is important enough to need clustering then nothing else will probably do.  If a crashed service being restarted in a few minutes is acceptable, then the other alternatives are much easier to administer.

For webservicey things, I like using the sticky DNS methods and having N+1 front-ends, then going to back-end systems with similar setups as much as possible. It really depends on the specific architecture of the solution.

---

