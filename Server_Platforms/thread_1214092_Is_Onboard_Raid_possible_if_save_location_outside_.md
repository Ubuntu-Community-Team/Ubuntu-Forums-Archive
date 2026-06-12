---
title: "Is Onboard Raid possible if save location outside virtual machine partition?"
date: 2009-07-15
forum: Server Platforms
---

### Post by photoman355 on 2009-07-15
Hi 

I'm fairly new to the idea of virtual machines and am in the process of working out how to implement this on my HP ML115 server.   I plan to set up Ubuntu Server as the base OS.

The server has an onboard raid controller but no separate raid card.   The onboard controller is not supported by VMware so that rules out using VMware ESXi, however it seems i can use VMware Server but without raid capability.

If I configured my server to use onboard raid with RAID 1 mirroring on say 2 x 1TB disks and configure VMware server to have a guest OS on its own say 20GB partition.  Will data saved from applications running on the guest OS to a location outside its partition still be mirrored?

Many thanks for your help.

---

