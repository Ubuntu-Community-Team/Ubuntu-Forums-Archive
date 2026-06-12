---
title: "VMWare Server - VM on External Drive Error"
date: 2008-07-26
forum: Virtualisation
---

### Post by borisborf on 2008-07-26
Here is the scoop: I'm not an intermediate Linux user, but I can't figure this one out.

I have a box running Ubuntu 8.04 and VMWare Server 1.0.6 installed. I found out that, along with the transition from 7.10 to 8.04 breaking VMWare (fixed), the mounted drives have been shifted from the /mnt folder to /media folder.

Now the problem:
I tried creating a virtual machine on an external drive (using a virtual drive) with a path of /media/Lacie/vmbsd/ and, whenever I try to launch the VM, it will go to a black screen like it is POSTing and then throw the VM back into the off state. I don't have this problem when I make a VM on the root HD, but the problem also shows up when I try to run a VM on an internal HD other than the root HD.

Any ideas on how I can correct this issue?

---

