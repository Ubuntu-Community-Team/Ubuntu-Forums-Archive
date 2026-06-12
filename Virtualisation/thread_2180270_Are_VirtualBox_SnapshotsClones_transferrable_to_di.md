---
title: "Are VirtualBox Snapshots/Clones transferrable to different machines on the same LAN?"
date: 2013-10-12
forum: Virtualisation
---

### Post by Jeff_Berrian on 2013-10-12
As per the title, can I copy over my VirtualBox snapshots and clone files to different machines connected together within the same LAN?

I am running Windows XP Pro Sp3 as the guest OS and would like to copy over the snapshots and clones over to several different machines on the same LAN. All machines have IDENTICAL specifications, same exact hardware, memory and processors. 

All machines have XP Pro licenses as well.

I want to maintain consistency across all machines while saving a ton of time installing/configuring Windows XP via VirtualBox on each machine...if possible.

All machines (8 total) are running Ubuntu 12.04 Desktop. I would like them all to run Windows XP Pro SP3 as the guest OS via VirtualBox and connect them all together on the network through Windows too.

Any advice to get me on the right track in accomplishing this goal?

Thank you in advance!!!

---

### Post by JKyleOKC on 2013-10-14
Yes, you can simply copy all files from the VM's directory (in vbox 4.x) across the LAN to another machine that has the same version of vbox in place. When you do this, it will be a TOTAL clone (including having the same IP address if you have network settings at "bridged") and the two WinXP VMs may not want to communicate with each other since their virtual NICs will have the same MAC address also. However you can change those settings afterward, which may solve the problem.

I've done this to transfer VMs from one machine to another, then removed the VM from the original machine. Vbox 4.x has something called "teleporting" which apparently does this automatically, while the VM is running even; I've not experimented with it though since the cp command from a terminal works just fine for my needs.

---

