---
title: "VMware Server 2.0.x -- how many vCPU's to use on a Guest?"
date: 2010-01-31
forum: Virtualisation
---

### Post by joeinbend on 2010-01-31
I havent been able to find a straight answer on this, so I thought I'd open up this discussion (can o worms...)

In VMware Server 2.0.x, running on 9.10 Server 64-bit, on a Phenom II X4 965 CPU: When setting up a Guest, VMware gives you the option of 1 or 2 CPU's (not 4, oddly enough, since it's a quad-core CPU). How does this affect the performance of the Guest and/or the Host? It seems logical that if you added more vCPU's it would give the Guest more available power, and that perhaps if you only had 1 enabled, that it would only use 1 core. when I monitor my CPU's via HTOP, i see that all 4 cores are actively running at significant load when I put the Guest OS's under load.

So, what's the deal?

---

### Post by Krijk on 2010-03-11
> **joeinbend said:**
> I havent been able to find a straight answer on this, so I thought I'd open up this discussion (can o worms...)

In VMware Server 2.0.x, running on 9.10 Server 64-bit, on a Phenom II X4 965 CPU: When setting up a Guest, VMware gives you the option of 1 or 2 CPU's (not 4, oddly enough, since it's a quad-core CPU). How does this affect the performance of the Guest and/or the Host? It seems logical that if you added more vCPU's it would give the Guest more available power, and that perhaps if you only had 1 enabled, that it would only use 1 core. when I monitor my CPU's via HTOP, i see that all 4 cores are actively running at significant load when I put the Guest OS's under load.

So, what's the deal?

I would choose single CPU. I used to do 2 CPU's but when I changed to single the virtual machines claim less resources on the host.

---

### Post by fjgaude on 2010-03-11
One core... the guest will run much faster, in my experience.

---

### Post by dcstar on 2010-03-11
> **fjgaude said:**
> One core... the guest will run much faster, in my experience.

I recall reading somewhere that the VMware code means that if the host is already using all the CPU cores that the VM is allocated then the VM has to wait for **all** those cores to be non-busy before the VM gets a go at them.

If you only allocate one core to the VM then this reduces the potential wait time and give an apparent performance boost.

This could be totally wrong, but it may explain why VMs on mixed host/VM systems perform this way, while on VM only environments (like a big dedicated VM server) it isn't much of an issue.

I'd have to turn off my host BOINC processing to do benchmark tests..... ;)

---

