---
title: "My first time ever messing around with virtual anything"
date: 2009-05-24
forum: Virtualisation
---

### Post by moebob24 on 2009-05-24
Ok, I an totally new to running virtual machines and am asking for a step by step on which software is the easiest to use with Ubuntu 9.04, and how do I get the virtual machine going.

First things first:
Can my Linux box handle it?
I have a pretty old desktop with 1GB RAM and an AMD Athlon XP 1500 CPU.

Second: Which virtual computer software is totally free, if there is one, which I'm pretty sure there is.

and third: How do I get a virtual machine running? I think I get the .iso file and use that but I am not sure.

Thanks

---

### Post by LinuxRules1 on 2009-05-24
Virtualbox is easy to setup virtual machines in. You can download virtualbox by going to [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads).

It will depend on what OS you run in your virtual machine. if the OS your loading in the virtual machine requires 512MB or more of memory then i suggtest that you put more memory in the system. the virtual machine will run but your system might run a little slow.

Setting up the virtual machine is easy. once you install virtualbox go to Applications>>System Tools>>Sun Virtualbox. When you first run virtualbox it will ask you if you accept the license agreement. then when virtualbox loads just click on the Button that Says "New" and go through the virtual machine setup wizard.

---

### Post by moebob24 on 2009-05-24
> **LinuxRules1 said:**
> Virtualbox is easy to setup virtual machines in. You can download virtualbox by going to [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads).

It will depend on what OS you run in your virtual machine. if the OS your loading in the virtual machine requires 512MB or more of memory then i suggtest that you put more memory in the system. the virtual machine will run but your system might run a little slow.

Setting up the virtual machine is easy. once you install virtualbox go to Applications>>System Tools>>Sun Virtualbox. When you first run virtualbox it will ask you if you accept the license agreement. then when virtualbox loads just click on the Button that Says "New" and go through the virtual machine setup wizard.


Ok, thank you, I'll try that out.

---

### Post by moebob24 on 2009-05-24
So now that it is installed, where is it. That is one thing that I always have problems with. Once I install something that isn't from the package manager. I can never find it on my computer and run it. It never shows up in the Applications menus. 

Any tips???

EDIT: Never mind, stupid me found it

---

### Post by LinuxRules1 on 2009-05-24
Try restarting your system. For some reason virtualbox doesn't show up in the menu until you reboot the system. if that doesn't work try going into terminal and type this in,

VirtualBox 

The case of the letters does matter for this program, if you type it in with all lowercase letters then it won't run.

---

