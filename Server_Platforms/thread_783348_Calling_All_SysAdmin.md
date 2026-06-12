---
title: "Calling All SysAdmin"
date: 2008-05-05
forum: Server Platforms
---

### Post by TheGeekGuy on 2008-05-05
First, Hello Community, this is my first time posting but I have been reading for a while. I am in the process of moving a Windows based infrastructure to a Linux based one. I have been looking at a few desktop virtualization applications already. I have it narrowed down to Virtuozzo and No Machine. Can the community provide me some feedback on these applications and there interaction with Ubuntu Server.

---

### Post by Eil on 2008-05-05
It would help to know what kinds of applications you use and what your infrastructure is like along with what your reasons are for wanting to switch platforms.

We use Virtuozzo where I work and honestly, it's not that great. For an OS virtualization solution, it seems overly complex and restrictive at the same time. And their tech support leaves a lot to be desired. I'd recommend something like Xen, KVM, (which Ubuntu Hardy ships with), or VMWare ESX.

I haven't used NoMachine so I can't comment on its quality. But depending on the virtualization solution you choose, you might be able to just use VNC or RDP, which have many free implementations.

---

