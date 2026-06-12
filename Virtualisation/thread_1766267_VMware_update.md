---
title: "VMware update"
date: 2011-05-24
forum: Virtualisation
---

### Post by tapi0n on 2011-05-24
Currently there is a machine running ESX Server 3i, 3.5.0 build 158874. On this ESX server there are 7 Virtual Machines running.

Me and a co-IT'er have been asked to upgrade this server to ESXi 4.1 without losing the virtual machines since VMWare is planning on phasing out the ESX structure.

So I strated looking for some info on the subject and ended up with *Veeam Backup & Replication*. found over [here.]("http://www.veeam.com/downloads/")

Now when reading trough the documentation I saw it is possible to replicate to ESXi. So this is perfect for what we want, backup all the vm's on the 3.5 on a local disk. Do an install of the ESXi 4.1 and just throw the vm's back on the new ESXi 4.1

Now when reading trough the [FAQ's]("http://www.veeam.com/forums/viewtopic.php?f=2&t=5304") I noticed this.

```
Q: Is vSphere 4.1 fully supported?
A: Yes.

Q: Is ESXi fully supported?
A: Yes, licensed ESXi is fully supported since version 3.0 released in February 2009.

Q: What about free ESXi, also known as vSphere Hypervisor?
A:  Unlicensed ESXi is not supported, because VMware has vStorage API for  Data Protection and other management APIs locked down on unlicensed  hosts specifically to prevent ISVs from being able to manage such hosts.  

```
So I'm guessing the plan is a no-go since we're sopposed to use the free version.

I kept on looking for some more info but all I could come up with were ways to upgrade from ESX 3.5 to ESX 4. But we want to go to ESXi4.1 (like I said earlier they're getting rid of ESX). 

Does anyone by any chance know a way around this? Or perhaps anyone's got a different method to achieve the same goal?

Cheers,

---

