---
title: "Virtual Box upgrade broke guest additions"
date: 2010-02-16
forum: Virtualisation
---

### Post by ebjsbjc on 2010-02-16
I am new to Linux (Ubuntu).  I am currently running it in a virtual machine in Sun Virtualbox ver. 3.1.4r57640, Linux Kernal 2.6.31-19-generic Ubuntu 9.10 AMDx64 - I have just updated to the most recent version of virtual box and now the guest additions are not working anymore.  I tried to reinstall the guest additions and I get the following error: "Makefile:23: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again..  Stop."
Read some forum articles and everyone has something different to do, and I am to new to get what they are saying.  Please help, how do I fix this.  I guess one way would be to go back to the previous addition of VBOX, but would like to fix in the new version.  Thank you for any suggestion to fix, thank you.[/

---

### Post by Perryg on 2010-02-16
This is usually caused when the kernel and the headers are out of sync, Or it could have been caused if you upgrade from a previous version like 3.0.x to 3.1.x which requires you to uninstall VirtualBox first.  All you should need to do is an update to the guest to make sure that the kernel and headers match and then run the guest additions install again. If not post back.

---

### Post by ebjsbjc on 2010-02-17
Thanks Perryg, I will try the uninstall and see what happens, thank yor for the reply.  I will let you know what happens.:D

---

### Post by ebjsbjc on 2010-02-17
Yes sure enough it worked, easy to do!  All I had to do was reinstall the guest additions from the terminal again and now everything works like it did before, issue fixed.  Thank you \\:D/

---

