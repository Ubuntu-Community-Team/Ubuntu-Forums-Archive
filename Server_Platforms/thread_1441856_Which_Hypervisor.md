---
title: "Which Hypervisor?"
date: 2010-03-29
forum: Server Platforms
---

### Post by steev182 on 2010-03-29
I've been using ESXi for a couple of weeks now and it is actually really nice (apart from the need of having a Windows VM on my little weak netbook to manage it) and it's starting to approach the limit for vSphere. The other problem for me is the inability to use USB drives for storage.

What I'd like to have are the following:

-Preferably low footprint
-Ability to administer vms either over ssh or through a web browser/linux friendly app
-Installabale on just one physical machine
-Can mount and use USB hard drives

Now, I could do this:

Physical server:
Ubuntu 9.10/10.04 Server - NO Window Manager thanks...
-NFS
-MT-DAAP
-uShare
-HellaNZB
-[vm server]
--Mail Server
--Web Server
--Solaris test

But I'm not too sure on the VM server to use.

Does anyone have an idea what I could try?

---

### Post by fang0654 on 2010-03-29
I use VirtualBox, which seems to have a pretty low footprint, and is very stable.  I mainly use it for file servers for satellite offices, where we will have a 1U server with a SATA Raid 1, running two VMs, one is a Windows server for active directory and one for is an Ubuntu server for a Samba file server.

I have another server running in our CoLo facility, running 8 backup domain controller VMs, without any problems.

It is all buildable and administrable through the CLI and SSH.

---

