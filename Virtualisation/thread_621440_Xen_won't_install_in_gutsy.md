---
title: "Xen won't install in gutsy"
date: 2007-11-23
forum: Virtualisation
---

### Post by SimonLyall on 2007-11-23
I recently upgraded one of my boxes to gutsy and tried to install Xen Server on it. However the package dependencies are compltely broken so it won't work.

What happened is that all the Xen packages depend on libc6-xen which right now depends on libc6 via:

Pre-Depends: libc6 (= 2.6.1-1ubuntu9)

However a couple of weeks ago libc6 was upgraded to 2.6.1-1ubuntu10 so the dependence fails. Several other packages are broke the same way. There is a bug in launchpad [https://bugs.launchpad.net/ubuntu/+source/xen-3.1/+bug/161783]("https://bugs.launchpad.net/ubuntu/+source/xen-3.1/+bug/161783") but it's been sitting there for 2 weeks with no sign of being fixed.

Any ideas on how to bypass the problem? (without reinstalling)

---

### Post by peabody on 2007-11-23
Installing via aptitude will offer to automatically downgrade.

---

### Post by SimonLyall on 2007-11-24
Thanks! 

Aptitude worked it out and installed everything.

---

### Post by VorDesigns on 2007-11-25
Hi,

I'm considering starting out with a hypervisor and Xen seems to be the way to go; my question is, do I install a base Linux OS just so that I can load the Xen hypervisor which boots into its own smaller footprint kernel or what?  
I've worked with VMWare but, only in the Win32 evironment.
For this installation, I'm planning on starting from scratch with a fair chunk of server iron to run the hypervisor and at least three other guest OS'.

---

### Post by SimonLyall on 2007-11-27
> **VorDesigns said:**
> Hi,

I'm considering starting out with a hypervisor and Xen seems to be the way to go; my question is, do I install a base Linux OS just so that I can load the Xen hypervisor which boots into its own smaller footprint kernel or what?  
I've worked with VMWare but, only in the Win32 evironment.
For this installation, I'm planning on starting from scratch with a fair chunk of server iron to run the hypervisor and at least three other guest OS'.

The Xen Hypervisor Kernel isn't really "cut down". It is more a full Kernel with Xen added on. 

So you do an install with as much stuff as you want (full desktop or just a minimal server install) add the ubuntu-xen-server or ubuntu-xen-desktop package to install all the Xen stuff and reboot.

---

