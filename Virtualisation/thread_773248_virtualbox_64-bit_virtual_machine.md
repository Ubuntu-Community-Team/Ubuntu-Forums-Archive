---
title: "virtualbox 64-bit virtual machine"
date: 2008-04-28
forum: Virtualisation
---

### Post by zorkerz on 2008-04-28
I have ubuntu 8.04 64-bit installed. I have been trying virtualbox to run virtual machines. When i try to create a new 64-bit virtual machine i get this error. > This kernel requires an x86-64 CPU, but only detected an i686 CPU. Unable to boot - please use a kernel appropriate for your CPU.

This is the same image I installed ubuntu from so i know my CPU (intel core 2 duo) supports it.

I expect that virtualbox OSE does not yet support 64-bit virtual machines. Is this the case?

If not what else could be going on?

---

### Post by agent8131 on 2008-04-28
Yes, VirtualBox does not support 64-bit guests.  That's why I abandoned it in favor of qemu/kvm and qemulator as of Ubuntu 8.04.  It's too bad because I got a lot of good use from VirtualBox in running my legacy Windows XP machine but I need to be able to run 64-bit systems for testing.

---

### Post by zorkerz on 2008-04-28
thankyou
virtualbox is my first foray into virtualizations and i have been very pleased with it. I don't think i will switch away from it as of yet. Im still just exploring and everything im playing with i can get and use in 32bit.

---

### Post by agent8131 on 2008-04-28
That's a great plan.  VirtualBox is probably the easiest to use virtualization software available (compared to the others I've used: QEMU, KVM, VMware, and Xen).  And it does run most 32-bit OS's just fine for the most part.  It's a great way to start trying the technology.  Perhaps by the time you need 64-bit support VirtualBox will have it.  If not, with the additional experience you'll be able to transition to something else more easily.

---

### Post by dlabutte on 2009-10-18
Hello;

I have a 64bit double/quad intel. Virtualbox comes in a 64bit AMD which works great. The remaining problem is that I have to install Windows Vista 32bit.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

