---
title: "Migrated LTS Server from ESXi to ESXi. Network Fails."
date: 2009-10-22
forum: Server Platforms
---

### Post by MaximumFish on 2009-10-22
Hello,

We've been running a fair few Ubuntu LTS server guests in VMWare ESXi for some time now with no issues, however we now need to transfer two of them to an alternate ESXi host.

I used the VMWare converter to copy one of these guests to the target host, which seemed to work just fine. The transferred guest boots properly except that there's no networking.

The guest itself shows the exact same config as when it was on its previous host, right down to the MAC address of the network card being the same but it just doesn't show up in the booted system. Running ifconfig displays only the Local Loopback adapter.

I've been able to teach myself a lot about Ubuntu servers through Googling, but this really has me stumped! I'm really at a loss for what to try.

Any ideas?

Much thanks in advance,

Max

---

### Post by Kolipoki on 2009-10-22
I guess your new host doesn't have the same network configs as the old one. Means you'll probably need to reconfig.```
sudo vi /etc/network/interfaces
```Where "vi" is your editor (change that name with your current, like "nano", etc.

The output of that would be the former configuration, the one brought from previous host. Compare with the network configuration of your new ESXi . Good luck!

EDIT: Also, depending on the location, you might have to review the ESXi's network config. But since I am presuming you are accessing the admin client remotely, you should have most, if not all, of it (ESXi) resolved.

---

### Post by MaximumFish on 2009-10-22
I did look in there but couldn't see anything obvious. It all looks fine, showing the config from that works as it should on the other host.

There's no reference to MAC addresses or any specific hardware, just eth0 and the loopback stuff.

I even tried removing the existing network card from the config and adding a new one, to no avail.

HA! OK, while writing this reply it dawned on me to try changing the eth0 definition to eth1. Restarted networking and we're good to go!

Thanks. I guess just bashing it out with others got my brain thinking in the right way. :)

---

### Post by Kolipoki on 2009-10-22
> **MaximumFish said:**
> HA! OK, while writing this reply it dawned on me to try changing the eth0 definition to eth1. Restarted networking and we're good to go!
Heh, actually I had that exact situation once in one installation of the very own ESXi, but was on the net configs of the host, not on the guest. Cheers...

Oh, you might want to brand this thread as "Solved".

---

