---
title: "Networking with QEMU Guest"
date: 2010-04-03
forum: Server Platforms
---

### Post by gyzer on 2010-04-03
I wanted to play around with QEMU a bit on my server. I have to use QEMU because my hardware doesn't support hardware virtualization.

So I've got a copy of Ubuntu 9.10 running in the QEMU guest, it is working just fine, but I cannot seem to get it working on my network. I first changed it to a static address, but I could not ping my default gateway. Then I did a little research and found that it is set to do dhcp automaticly from the host machine, using an address of 10.0.2.15 and the host has an address of 10.0.2.2. I was able to ping the host machine which is a step in the right direction, but now I don't know how to setup things so I can actually get to the internet from my guest machine, or to just be able to ping the other computers on my network.

Can anyone help me out with this or at least point me to an article? I've done some googling and I was able to find data about the guest, but not about anything I need to do on the host.

---

