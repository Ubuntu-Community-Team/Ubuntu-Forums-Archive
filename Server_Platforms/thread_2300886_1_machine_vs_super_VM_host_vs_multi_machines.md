---
title: "1 machine vs super VM host vs multi machines?"
date: 2015-10-29
forum: Server Platforms
---

### Post by Higgins909 on 2015-10-29
I wonder because one day I want to build a huge ish file server and have some power too, and it may be doing more things.
Tho it does seem its cheaper to build one big server rather then  many small ones... unless its some sort of raspberry PI cluster.
But they won't run a game server or a fast storage server... would be some sort of spread out web server or something...

You have storage, game , proxy, web, etc.


**Would it be better**:
1 machine big enough to run them all
1 big machine with VM host for each or so service
run a bunch or little machines?

Right now I'm doing the VM way as I was having issues with samba and had to reinstall all my stuff... samba proxy drives etc...
If I ever build that huge storage server, I would run it in raid and have the virtual drive files (VM hdd) on it and have whatever VM server, say samba would be on it.
Does such a thing sound alright?  It's kinda what I'm already doing, but with no raid.

Thanks,
****    Higgins909

---

### Post by TheFu on 2015-10-29
A file server doesn't need much "power" - a G3258 can easily provide a blazing-fast NAS with 16TB+ of storage.
File servers and edge routers are the only things I don't virtualize.

Virtualization is a way to separate the different dependencies that each different software service requires. All those different tools can bring strange interrelationships. I like having them separate. Plus if 1 thing fails, all the others aren't impacted.

* VMs decouple the OS from the hardware.
* VMs make HA much easier
* VMs make backups easier
* Using virtualization means not being stuck waiting for HW to try new things out
* Live Migration
* If you virtualize your desktops ... think about how trivial migrating to new-faster HW will be.
* Try a new OS with zero risk
* Read-only OS for security - run from an ISO.

So to do this you need 4 machines.
*  router (pfSense) ($150, tiny x86 box w/ 2 GigE ports); Buy a cheap $20 switch for more.
* G3258 -based for a rockin'  NAS ($150+disks)
* (2) VM host systems  Core i5+ w/ 16G RAM - 8G is plenty for 10+ Linux VMs.  ($350-ish to $25K)

Need 2 VM hosts for minimal redundancy. It 1 box fails, the remaining box should have enough power/RAM to run all the most critical VMs.

You can still have lots of web-virtualhosts on a single VM. It is about separation of security risks, services and software interdependencies. For example, I would never put email on a shared VM. Email always gets a dedicated VM.

RAID is for HA. Backups can solve 1000 issues that RAID cannot. Backups are 1000x more important than RAID.

Just MHO.

---

