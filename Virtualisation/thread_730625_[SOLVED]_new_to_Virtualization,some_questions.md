---
title: "[SOLVED] new to Virtualization,some questions"
date: 2008-03-21
forum: Virtualisation
---

### Post by StOoZ on 2008-03-21
well I installed the latest vmware.
can a virtual machine harm my native system? (planing on installing solaris as a vm , and my system run ubuntu)
or I can do what ever I want with the vm and nothing can happen to my regular OS/Machine?

(btw im not talking on overclocking etc,only software)

---

### Post by dcstar on 2008-03-21
> **StOoZ said:**
> well I installed the latest vmware.
can a virtual machine harm my native system? (planing on installing solaris as a vm , and my system run ubuntu)
or I can do what ever I want with the vm and nothing can happen to my regular OS/Machine?

(btw im not talking on overclocking etc,only software)

Unless VMware has some evil malware implanted inside of it, then no.

VMs do not have direct access to the "real" machine, only the Virtual Machine environment and the resources the VM manager allows (and requires).

---

### Post by ScatterBrain on 2008-03-21
> **StOoZ said:**
> well I installed the latest vmware.
can a virtual machine harm my native system? (planing on installing solaris as a vm , and my system run ubuntu)
or I can do what ever I want with the vm and nothing can happen to my regular OS/Machine?
 
(btw im not talking on overclocking etc,only software)
 
You can use a "RAW" file system to load the virtual machine's virtual disk on, this is good for a Database Server for example.  But as long as you separate that RAW disk space from the rest of the machine - meaning a separate physical disk or physical partition - then it shouldn't be able to affect the host.
 
By default, vmWare uses a large file (or several, depending on how you go about it) to simulate a hard drive for the virtual machine.  When it's like this, there is a clear separation between the physical and virtual machine.  You can cross those boundaries with networking but the chances of actual damage to the host is pretty slim.

---

