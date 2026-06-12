---
title: "Why does vmware guest networking fail when zip/unzip to relocate?"
date: 2008-02-16
forum: Virtualisation
---

### Post by mark_k on 2008-02-16
I created a small vmware image, about 4GB worth of disk. I had to copy it to a remote machine, and figured I'd rather deal with 700 Mb worth of zip instead of 4GB worth of raw vmdk.

After it's unpacked on the remote machine, it starts up just fine, but the network on eth0 inside the guest just doesn't start, saying that eth0 isn't configured. However, if I copy over the raw vmware files, things start up just fine.

Why would zip/copy/unzip of a guest screw up its networking?

The guest is ubuntu JeOS, if that matters. Hosts that had problems were windows XP and ubuntu 7.10.

Many thanks in advance.
- Mark (who's using rsync while this gets worked out)

---

