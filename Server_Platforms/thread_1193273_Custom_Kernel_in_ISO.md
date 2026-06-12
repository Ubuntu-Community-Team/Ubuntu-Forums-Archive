---
title: "Custom Kernel in ISO"
date: 2009-06-21
forum: Server Platforms
---

### Post by tonemgubz on 2009-06-21
I want to edit/customise the ubuntu server 8.04.2 iso to install with a generic kernel from kernel.org instead of the supplied one. I dont need or want to change anything else in the iso. Is this possible and if so can someone give a quick guide to doing it or a good link on how it may be achieved

I saw this [https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization), but it doesnt really asnwer my question I think.

---

### Post by overdrank on 2009-06-21
Move to Server Platforms as requested by OP

---

### Post by Gen2ly on 2009-06-21
Yes you can use a vanilla kernel tonemgubz but it's configuration file is very very minimal and I doubt that compiling a kernel as such probably wouldn't be able to boot on many systems.  If you are willing to put up the time you'll have to do a good amount of research about the hardware and the kernel to get it set up right.

---

### Post by tonemgubz on 2009-06-21
Perhaps using these [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/). BUt again how do I include it in the iso?

---

### Post by CP1256 on 2009-06-21
I would compile the kernel on one machine, make a deb file and spread it to other machines so you don't have to compile the kernel again. 

You can open the Ubuntu install CD in .iso form and put the new kernel in a new directory, so right after install you can mount the CD and install the new kernel from the CD.

> **Dirk.R.Gently said:**
> Yes you can use a vanilla kernel tonemgubz but it's configuration file is very very minimal and I doubt that compiling a kernel as such probably wouldn't be able to boot on many systems.  If you are willing to put up the time you'll have to do a good amount of research about the hardware and the kernel to get it set up right.

I never had any problems from compiling my own kernels, but though it takes some practice to set them up properly.

---

### Post by tonemgubz on 2009-06-23
[edit]

---

