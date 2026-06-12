---
title: "General Questions Concerning Virtualization Software"
date: 2009-01-11
forum: Virtualisation
---

### Post by pontifikas on 2009-01-11
I'm trying to conduct a series of benchmarks over various virtualization  managers. I will be using VMWare, VirtualBox, QEMU,KVM.
I have followed the instructions in this forum and installed the required software.
Since I am new to virtualization, I have a few questions about using this software.

a)Is it possible for these managers to Share the same virtual machine?

b)How can I avoid to perform multiple installations of the same OS if I want to use multiple instances of the same OS?

Thank you in advance

---

### Post by Dedoimedo on 2009-01-11
Hello,

Answer: maybe.

1) It is possible to convert the file formats rather easily. Some programs might support other formats, but then you might not get native performance.

I recommend you do create several separate, but identical machines, or at least create one and then copy it.

2) Which brings us to issue 2; virtual machines are files. Just copy them. Check the md5 hash or alike to make sure nothing got wrong during the copy process. If you must, you can use the dd utility and try the clone feature that some of these programs have.

Dedoimedo

---

### Post by HermanAB on 2009-01-11
You can only run one virtualizer on one physical machine.

If you want to compare systems, then you either need multiple identical machines, or you need to re-install the system before you try a new virtualizer.  That makes it rather difficult to compare VMware with Virtualbox for example.

Cheers,

Herman

---

### Post by thomasr on 2009-01-11
Actually, with virtualbox, copying is not a good idea. The file almost always is corrupted. Either use th  VBox Clobne utility or zip the file before copying.

---

### Post by Shazaam on 2009-01-11
> **HermanAB said:**
> You can only run one virtualizer on one physical machine.

If you want to compare systems, then you either need multiple identical machines, or you need to re-install the system before you try a new virtualizer.  That makes it rather difficult to compare VMware with Virtualbox for example.

Cheers,

Herman

I may have misunderstood your post but as an experiment I have Ubuntu 8.10 running as the host, Ubuntu 8.10 vmx/vmdk running using VMware Player, and the exact same Ubuntu 8.10 vmx/vmdk running in Virtualbox at the same time. They are rather slow with the combined memory hit but they are usable.

---

### Post by pontifikas on 2009-01-12
> **Shazaam said:**
> I may have misunderstood your post but as an experiment I have Ubuntu 8.10 running as the host, Ubuntu 8.10 vmx/vmdk running using VMware Player, and the exact same Ubuntu 8.10 vmx/vmdk running in Virtualbox at the same time. They are rather slow with the combined memory hit but they are usable.

You are running them at the same time and is slow or running a vmware machine in VBox is slow?

Anyway indeed vmware machines can be copied-pasted, and VMware tolerates this. It even changes the UUID when it detects the identical hard drives :D. Unfortunately that UUID is the problem with VBox :(.

---

### Post by Shazaam on 2009-01-15
All at the same time slow; equal slowness between VMware and VBox.

---

