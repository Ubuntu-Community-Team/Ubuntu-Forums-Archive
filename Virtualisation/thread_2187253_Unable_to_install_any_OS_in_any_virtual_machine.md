---
title: "Unable to install any OS in any virtual machine"
date: 2013-11-11
forum: Virtualisation
---

### Post by underdog512 on 2013-11-11
I am running Ubuntu GNOME 13.10 64-bit on a Dell Laptop with an Intel Core Duo and 2 gigs of RAM. 

I have a rather odd issue where I cannot install any guest OS on my system.  I am booting from an ISO and usually I get to a where I have the option to select "install."  After I select the install option, the virtual machine usually freezes at a black screen.  No CD drive, HDD, or CPU activity at all, just a black screen.

Here is the interesting part.  I have tried two different versions of VirtualBox (version 4 and the version before that one) and I have also tried using QEMU.  The same exact thing happens in both.

I have tried installing 64-bit and 32-bit versions of CentOS, as well as 32-bit versions of Fedora and Ubuntu Server.  All display the same exact issue.  

At one point, I was about to boot to the Live Desktop of CentOS, which took forever to come up and ran very slowly, and then ran the graphical install.  it errored out at the very end.  I apologize for not jotting down the error but suffice to say, the install was unsuccessful. 

In all these cases, I have given 1 gig of RAM and 20 GB of HDD to each guest OS.  

Before I did a fresh install of Ubuntu GNOME on my host machine, I was running Ubuntu 13.04 with GNOME Shell and was not having any issues with Virtualization.

I have been using Virtual Machines since before it was cool and I have never ran accross an issue quite like this.  I hope someone has some ideas.

---

### Post by SeijiSensei on 2013-11-11
If you're installing an Ubuntu guest, try hitting F6 at the initial menu screen and picking nomodeset.  That can help resolve some display issues.

---

### Post by underdog512 on 2013-11-11
> **SeijiSensei said:**
> If you're installing an Ubuntu guest, try hitting F6 at the initial menu screen and picking nomodeset.  That can help resolve some display issues.

My preference would be to install CentOS for what I am trying to do.   I wonder why this is happening with Multiple OSes on two different virtualization platforms.

---

### Post by underdog512 on 2013-11-12
It turns out that the issue is not what I originally thought.  I was able to actually get CentOS installed. It just runs EXTREMELY slow.  I think I might open a new thread for that issue if need be.

---

### Post by SeijiSensei on 2013-11-13
A Core Duo with just 2 GB of memory is pretty underpowered for running virtual machines.  More memory might help, but the processor is still going to have to work hard to run VMs.

Out of curiosity, what do you see in terms of memory, load average, and swap usage if you run "top" on the host (not the guest)?

---

### Post by ibjsb4 on 2013-11-13
I have vBox set up on a core2duo w/2G ram and find its enough to run my bare bone systems, but a full blown desktop is just asking for too much.

---

