---
title: "Need advice with VMware"
date: 2008-03-22
forum: Virtualisation
---

### Post by smc18 on 2008-03-22
I am about to test out VMware on an XP box with a virtual linux os.  I need some help picking which version of Ubuntu I should use.

The test box has 512mb of ram and a 800mhz cpu.

It is currently running a fresh install of XP and I would like to use Ubuntu but maybe I should use Xubuntu instead because of the low specs.  

Any opinions would be useful, thanks!

---

### Post by Shazaam on 2008-03-22
As long as you don't allocate more than half of your physical ram amount to the vm (you have 512; allocate no more than 256 to the vm) most of them will run. Some slower than others. If you have a fast internet connection you could download a bunch of distro's and try them in a virtual environment.
Xubuntu will run better than a normal Ubuntu install on low-mem systems.
Also, running an operating system in a virtual environment does not mean it will run in a physical install. Vitrualization programs use their own drivers for hardware. For example, damnsmalllinux won't install on my system but runs fantastic as a vm.

---

### Post by smc18 on 2008-03-22
Thank you for the advice.  Sadly I am still learning/experimenting with linux; so for now I may stick with Xubuntu.

Anyone else have any suggestions?

---

### Post by smc18 on 2008-03-23
Alright! I made some progress.  I'm currently using the VMware Workstation trial and I made a Xubuntu and DSL vm.  The DSL runs perfectly. :)  

However when trying to start the Xubuntu vm, it loads grub and says "Starting up... Loading. Please wait..." Then it just hangs at a black screen.  I dont know if i just need to give it some more time or it may be a problem when I made it.  

When I first went to Create a Virtual Machine, I selected Linux>Ubuntu.  Since I'm using Xubuntu 7.10 should I have selected Linux>Other Linux 2.X.X Kernel?

*UPDATE*
I just gave Xubuntu some time and it loaded, however I think I need to install VMware tools now so it will run/look properly.

---

