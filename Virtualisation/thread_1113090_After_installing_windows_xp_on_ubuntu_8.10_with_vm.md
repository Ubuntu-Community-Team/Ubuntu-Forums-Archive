---
title: "After installing windows xp on ubuntu 8.10 with vmware 2.0, no wireless network adapt"
date: 2009-04-01
forum: Virtualisation
---

### Post by ubantuwannabe on 2009-04-01
Hi after I successfully installed windows xp on ubuntu 8.10 with vmware 2.0,

when I am inside windows xp, the OS could not detect the wireless adapter.

my laptop is nc4400.

I'm a noob. really appreciate if someone could guide me on how to resolve this issue?

thanks

---

### Post by dcstar on 2009-04-02
> **ubantuwannabe said:**
> Hi after I successfully installed windows xp on ubuntu 8.10 with vmware 2.0,

when I am inside windows xp, the OS could not detect the wireless adapter.

my laptop is nc4400.

I'm a noob. really appreciate if someone could guide me on how to resolve this issue?

thanks

Guest VMs use the host networking devices, you may need to manually add that device in the configuration options in the VMWare console.

---

