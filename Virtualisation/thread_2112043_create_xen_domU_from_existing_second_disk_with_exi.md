---
title: "create xen domU from existing second disk with existing ubuntu install"
date: 2013-02-03
forum: Virtualisation
---

### Post by ckruslicky on 2013-02-03
I have an existing ubuntu 12.04 LTS (desktop) install with a few services running, notably NFS.  I've installed a second hard drive and installed ubuntu-server 12.10 with xen initially setup, at least I can access it and verify it is booting into the hypervisor.  I haven't created any guests yet.

What I'd like to do in the meantime while I learn xen and move individual services to new domUs, is boot into xen and start a domU which just uses the original disk as-is.

It seems like it should be easy to specify the right partition to use so nobody notices any difference when running the original OS as a guest.  I just can't find such an example.  Anything talking about a second disk either talks of using an existing windows partition, or starts with "format the second disk" which it right out!

Thanks in advance.  I have a feeling it'll be something that's easy once I understand how to use xen.  But it's the first step I want to do to avoid downtime while setting up individual domUs on the new disk.

---

