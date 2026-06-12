---
title: "Xen 4.x on Ubuntu-server 11.10 - Networking issues"
date: 2011-11-22
forum: Server Platforms
---

### Post by bstempi on 2011-11-22
So, I recently installed Ubuntu Server 11.10 onto a server that I had lying around.  I then set up Xen et all.  I then created some VMs and eventually switched from NAT'd networking to bridged networking.  I've notice some strange behavior.

If I cold boot and run *ifconfig*, I don't see *peth0*.  If I reboot, it then appears.

This causes problems when domUs try to resume after a cold boot of the host -- they are unreachable via the network.

Any ideas why this might be happening?

Thanks!

---

