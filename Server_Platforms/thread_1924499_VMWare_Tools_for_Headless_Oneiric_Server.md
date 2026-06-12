---
title: "VMWare Tools for Headless Oneiric Server"
date: 2012-02-12
forum: Server Platforms
---

### Post by mattlach on 2012-02-12
Hey all,

I am trying to install VMWare tools for ESXi 5.0 in Ubuntu Server 11.10 Oneiric, but I am having some issues.

Has anyone done this?   I am having issues.

I tried following [this guide](https://help.ubuntu.com/community/VMware/Tools) without any success.   It lists three different methods.

**1.) Installing from Ubuntu package open-vm-tools**

This looks like it ought to work, but the dependencies pull all of X11 with it when you try to install it.   The "--no-install-recommends" workaround does not seem to work, as even with this addition it still wants to install a whole lot of X11 stuff.

I'm already tight on RAM on my ESXi server, so adding in any X11 components is out of the question.
 
**2.) Installing from packages.vmware.com**

I followed the [linked guide](http://packages.vmware.com/tools/docs/manuals/osp-esxi-50-install-guide.pdf) but they don't appear to have sources for Oneiric, only Natty and earlier are represented.  I tried using the Natty sources, but then it just failed to get the modules for my kernel, as my uname -r is "3.0.0-12-server".  These apparently don't exist.

**3.) Installing from your VMware host (not recommended)**

I also started attempting this method, but stopped when I realized all the directions were for the GUI.

So has anyone successfully installed VMWare Tools for Oneiric Server?   How did you do it?   Is there a guide I can follows?

It seems kind of ridiculous that Oneiric has been out for 4-5 months and the official VMWare documentation still doesnt cover it.

(Also, VMWare has the worst confusing mess of a webpage and documentation I have ever seen in any major corporation)

Any help would be greatly appreciated!

Thanks,
Matt

---

### Post by amarcionek on 2012-02-24
Wish I could help you, but I'm having the same issue. The installer half works. The tools services are running, but things like the desktop integration that makes the copy/paste work through the vSphere console do not.

I ended up doing the not recommended option 3.

---

### Post by mattlach on 2012-02-28
> **amarcionek said:**
> Wish I could help you, but I'm having the same issue. The installer half works. The tools services are running, but things like the desktop integration that makes the copy/paste work through the vSphere console do not.

I ended up doing the not recommended option 3.

Is your system headless or does it have X installed?

---

