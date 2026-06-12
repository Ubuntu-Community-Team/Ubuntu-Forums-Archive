---
title: "How is VMWare different from Virtualbox?"
date: 2010-03-01
forum: The Cafe
---

### Post by Roasted on 2010-03-01
I ask this question based on one particular situation. My buddy has a Linux class now where they teach Ubuntu, which is basically the distro of his choice anyways. A project came up where they have to pick something other than Ubuntu since Ubuntu is what their entire class is on anyway.

He picked Epidemic Linux, a Brazilian distro that's in the mid 90's on distrowatch.com.

Trick is, it wouldn't boot on Virtualbox - yet it did on VMWare Workstation.

How different are these virtual programs? I'm just trying to understand why Virtualbox has worked for every other distro of Linux I've tried (which has been quite a lot) yet Epidemic Linux in particular failed? (yet worked on VMWare)

---

### Post by mickie.kext on 2010-03-01
That Epidemic Linux probably has very old kernel. Try setting something line Linux 2.4 in virtualBOX.

---

### Post by Roasted on 2010-03-01
According to DistroWatch, Epidemic 3.0 came with Linux Package - 2.6.26, and 3.1 that came out a few days ago came with 2.6.32. I'm assuming the Linux Package is the kernel??

---

### Post by t0p on 2010-03-01
The difference between VMWare and VirtualBox is the fact that they are different applications.

They are both virtualisation packages.  But they are not the same thing.  VMWare, Inc, is a company that produces virtualisation software. Its products are VMWare Server, and VMWare Workstation.  As you might be able to guess from the names, VMWare Server provides server virtualisation, and VMWare Workstation provides workstation virtualisation.

VirtualBox is also a virtualisation solution.  There is an open source version, and also a proprietary version that offers more features (ie the proprietary version has USB connectivity that the open source version lacks).

There is a measure of interoperability between the VMWare product and VirtualBox.  For instance they can both run virtual machines from .vdi format images.  But VMWare is a more commercial product, and accordingly has more features built-in.

If you want to know the nitty-gritty of the differences between each. I suggest you look at [this Wikipedia article]("http://en.wikipedia.org/wiki/Comparison_of_platform_virtual_machines"), which compares many virtualisation platforms: VMWare, VirtualBox, QEMU, Windows virtual PC, and more.   Also check out the appropriate websites: [www.vmware.com]("http://www.vmware.com") and [www.virtualbox.org]("http://www.virtualbox.org").  I would also add that VirtualBox is a free solution: there's the "free as in speech" version, then there's also the "free as in beer" version.

---

### Post by Roasted on 2010-03-02
I guess ultimately I'm trying to understand the differences to figure out why Epidemic doesn't boot on Virtualbox, yet it will on VMWare...

---

### Post by Richard1979 on 2010-03-02
I think VMWare supports more operating systems out of the box than  VirtualBox does - it's in their commercial interests (obviously).
I could not get Windows Server 2008 R2 to install on the newest  VirtualBox but had no issue on VMware.
This was just for, erm, testing you understand (for work)...they want to  implement Active Directory.

---

### Post by swoll1980 on 2010-03-02
From my experience vmware doesn't run as fast.

---

### Post by phrostbyte on 2010-03-02
They are completely different codebases. So there will be different bugs in each one. :)

---

