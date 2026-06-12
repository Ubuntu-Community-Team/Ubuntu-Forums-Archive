---
title: "Installing VMware player on Ubuntu 8.10"
date: 2009-07-13
forum: Virtualisation
---

### Post by nosmadar on 2009-07-13
I am trying to follow the instructions from the Ubuntu documentation site:
[https://help.ubuntu.com/community/VMware/Player#Installing%20VMware%20Player%20on%20Ubuntu%208.04%20LTS%20and%20Ubuntu%208.10](https://help.ubuntu.com/community/VMware/Player#Installing%20VMware%20Player%20on%20Ubuntu%208.04%20LTS%20and%20Ubuntu%208.10)

The first step, before even installing VMware player, says to:

sudo aptitude install build-essential linux-kernel-headers linux-kernel-devel

But when I execute this command, Aptitude says:

robert@Kubuntu-Sandbox:~$ sudo aptitude install build-essential linux-kernel-headers linux-kernel-devel
Reading package lists... Done
Building dependency treeReading state information... Done
Reading extended state information
Initializing package states... Done

Couldn't find any package whose name or description matched "linux-kernel-devel"Couldn't find any package whose name or description matched "linux-kernel-devel"The following packages will be REMOVED:  linux-headers-2.6.27-11{u} linux-headers-2.6.27-11-generic{u} linux-headers-2.6.27-7{u}  linux-headers-2.6.27-7-generic{u} portmap{u}[/COLOR]

I did not proceed as I was especially concerned about the listed packages that were going to be removed.

Does any one know if it's OK to do this or if there is a different way to get this done, or if it really needs to be done at all.

Thanks!

---

