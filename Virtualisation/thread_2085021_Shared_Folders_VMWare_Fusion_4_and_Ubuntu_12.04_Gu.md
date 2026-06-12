---
title: "Shared Folders VMWare Fusion 4 and Ubuntu 12.04 Guest"
date: 2012-11-17
forum: Virtualisation
---

### Post by derekeverett on 2012-11-17
I have recently installed Ubuntu 12.04 in a VMWare Fusion 4 virtual machine on my iMac. I've completed all the required updates that I am aware of.. including the build-essentials and I have installed the VMWare tools. I will note here that I just accepted all the defaults in that installation.

Everything appears to be working well except my shared folders. The "Shared Folders" option in my Fusion settings is on. I do have a /mnt/hgfs folder but it has no contents.

I assume I have to mount my OS X home folder somehow but I'm not clear on how to do this. If I wish to have this folder always mounted (and I do) then I need to modify the fstab file as well correct?

Please advise and I thank you in advance.

---

### Post by derekeverett on 2012-11-18
With help from folks at The VMWare Forums I have solved my issue.

If anybody else has this problem, it is important to restart your Ubuntu installation after you re-build your kernel module and THEN install VMWare Tools. You will probably have to reboot again, but that your shared folders should then be available.

I had originally performed the steps in the correct order, but had not rebooted before installing VMWare tools. I simply had to re-install the tools and reboot.

I will try to help anyone who has a similar issue that replies to this thread in the future.

---

