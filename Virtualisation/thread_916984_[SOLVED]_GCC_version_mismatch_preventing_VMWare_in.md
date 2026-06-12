---
title: "[SOLVED] GCC version mismatch preventing VMWare installation"
date: 2008-09-11
forum: Virtualisation
---

### Post by ztirffritz on 2008-09-11
I'm running Ubuntu 8.04 64.  I tried to install the latest version of VMWare (1.07) but it says that there is a mismatch in GCC.  The Kernel is compiled using 4.2.3 version but 4.2.4 version is the currently installed version.  I tried to force version 4.2.3 using Synaptic, but it doesn't seem to want to regress.  The GCC-base seems to be the source of the problem.  If I try to force that to the previous version it wants to un-install half of the software on the computer...I don't think that is a good plan.  Apparently I accidentally turned on the Hardy Proposed repository and that is how the newer version was installed.  Does anyone know how to get around this so that I can get VMWware installed again?  It warned me not to do it but I foolishly tried it anyway...now I can't even install the old version.  This may not be the correct space to ask this question, so if the mods want to move it feel free.  

How do I do a GCC version regression, or how do I recompile the kernel using the current version of GCC that I have?

---

### Post by qos on 2008-09-11
I have the same problem. I can't tell you how to fix your regression problem, but between gcc-4.2.3 and gcc-4.2.4 there is not that much difference so i decided to give it a try. I choosed 'yes' instead of 'no' and it compliled flawlessly. Even my VMs are running fine ;)

---

### Post by ztirffritz on 2008-09-11
I am not having the same luck...

---

### Post by ztirffritz on 2008-09-11
stupid me...I forgot to link the files per the instructions on the sticky...duh...case closed...it is working now.

---

