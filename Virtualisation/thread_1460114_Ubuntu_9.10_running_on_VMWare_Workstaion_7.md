---
title: "Ubuntu 9.10 running on VMWare Workstaion 7"
date: 2010-04-22
forum: Virtualisation
---

### Post by black888diamon on 2010-04-22
Hi guys, i just installed Ubuntu 9.10 Netbook Remix on my laptop. I notice that i am having trouble with my display which sometimes freezes. The first thing that came to my mind is to install my nvidia ion driver.

How can i install the nvidia driver on my Ubuntu running on VVMWare? ( i tried going to administration>hardware&drivers but it doesn't give me any option)

---

### Post by fjgaude on 2010-04-22
You can't install video drivers in a VM. The driver is already embedded within the software and can't be overwritten... that's the way things are now.

---

### Post by black888diamon on 2010-04-22
Thanks man, but can you suggest a solution on my problem? I run system montior and have found my cpu has 100% cpu utilization. Is this a bug on the new Ubuntu 9.10?

---

### Post by jburr51 on 2010-04-23
You don't say what your host O/S is that you are running Workstation 7 on. Need to start there. Also, why did you install Remix instead of the full version? fjgaude is quite right, you can't install drivers into a virtual machine, but it seems to me the problem may be related to the Remix distro. 
 
Have you installed the full version of 9.10 with the same results?

---

