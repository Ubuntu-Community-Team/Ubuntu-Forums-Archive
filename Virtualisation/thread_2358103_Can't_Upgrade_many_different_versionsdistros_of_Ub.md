---
title: "Can't Upgrade many different versions/distros of Ubuntu"
date: 2017-04-09
forum: Virtualisation
---

### Post by daveomcd on 2017-04-09
I've tried to create a Ubuntu (guest) in VMware Workstation 12 Pro. I've tried the following versions/distros: Ubuntu 16.10, Ubuntu 14.10, Ubuntu Gnome 16.10, and Ubuntu Gnome 16.04. Also for some I've tried 32-bit and 64-bit.  Everytime my guest totally freezes when I get to the point of running 'sudo apt-get upgrade'.  During this process it will get to the same spot and freeze up the system.  To the point where I have to do a hard reset and then the guest won't boot at all.  Here's an image of where it stops.  What can I do to troubleshoot/resolve this issue?  Also I have a Dell XPS 13 laptop running Win 10 on host.

[IMG]https://i.stack.imgur.com/ImvF7.png[/IMG]

---

### Post by deadflowr on 2017-04-09
*Moved to **Virtualization ***

---

### Post by sp40140 on 2017-04-18
Could you provide bit more information? You do not have to run "sudo apt upgrade" to run VM. So, are you able to create a VM successfully and boot into it and after booting you try to upgrade and it fails? Have you installed guest additions? What are your hardware specs and how many resources have you allocated to this VM?
I use VMware Player 12 and I did upgrade to 17.04 without any issue on my guest Ubuntu Gnome.

---

