---
title: "How to update Ubuntu running as Xen-DomU"
date: 2011-01-07
forum: Virtualisation
---

### Post by micxer on 2011-01-07
Hello everybody,

I have a virtual server and since it's a bit outdated running 9.10 I did an upgrade using *do-release-upgrade*. I had to merge some config files, but the rest went fine, except for the bootloader stuff.

First, the updater asked me about a LILO config. I didn't even know that LILO was installed before (must have come with the image my hoster provides). since I didn't want to break things, I skipped writing into the MBR. Later GRUB wanted to do the same. This was weird. Also I only found /dev/sda1 (swap) and /dev/sda2 (root), but no /dev/sda. So even if LILO and GRUB want to write to the MBR, I think they can't, do they? 

So I was wondering, how a Xen guest get's started and how to upgrade my Ubuntu installation. Am I right, that the boot process uses the /vmlinuz to boot the kernel? 

My hoster told me they would provide new images with the current Ubuntu version soon, but I don't want to reinstall everything. So is it possible or do I have no other choice then start from scratch again?

Cheers,
Michael

---

