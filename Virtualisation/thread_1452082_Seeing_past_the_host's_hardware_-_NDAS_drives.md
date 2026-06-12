---
title: "Seeing past the host's hardware - NDAS drives?"
date: 2010-04-11
forum: Virtualisation
---

### Post by davidpbrown on 2010-04-11
tldr; Is a virtualisation strictly limited to the host's ability to see hardware, even if it's placed on the Ethernet?


NDAS disks, that is 'Network Direct Attached Storage' network disks over Ethernet, need specific drivers created. Fortunately, today for 9.10 I've found [a good working solution]("http://ubuntuforums.org/showthread.php?t=1340028") but if in future Ximeta aren't developing later versions, what can virtualization do for this?

Can I virtualize an earlier version of Ubuntu and access the network drive despite the host OS' inability to see the drive?

I did try this quickly and, knowing nothing about virtualisation, found setting up 8.04 using Qemu simple. However with NDAS drivers installed and working, it couldn't then see the NDAS drive.

Would this be just about using a different than default setting in Qemu's Network[Card 0] setting, so that it can see the network more clearly?? Is Qemu limited in a way that it seems to be for USBs - would I do better with VMware +?

---

