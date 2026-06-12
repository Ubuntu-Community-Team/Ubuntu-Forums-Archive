---
title: "advantages to multiple virtual CPUs"
date: 2009-04-03
forum: Virtualisation
---

### Post by pytheas22 on 2009-04-03
I have a machine with 2 quad-core Xeon processors and 16 gigabytes of memory.  The host operating system is Ubuntu server 8.04, and I'm planning on using VMware and/or KVM to run two virtualized guests: a Linux webserver and a Windows 2003 database and file server.

I'm trying to figure out if there are any performance advantages to creating more than one virtual CPU for each virtual machine.  I've read conflicting information about this--some people suggest that having more than one virtual CPU per machine is the only way to take advantage of all the physical cores in the host, while others write that multiple CPUs on a single guest can degrade performance, because it causes the guest and the host to compete for physical CPUs.

Does anyone have advice based on personal experience regarding what the best approach to virtual CPUs is?

On a related note: any opinions on whether I should go with KVM or VMware?  Both seem equally easy to manage, but I'm interested in what will give the best performance running multiple virtual machines at the same time.

---

### Post by azredwing on 2009-04-03
> **pytheas22 said:**
> 
Does anyone have advice based on personal experience regarding what the best approach to virtual CPUs is?


My personal experience is that single-core is better. I have a quad core machine, and so you'd think giving the VM two cores would yield better performance but it's the complete opposite. Then again, I use my VM for intense applications like CAD, so YMMV.

---

### Post by Blinkiz on 2009-04-04
Hi there
I can only talk for my self and own experience. But I notice a big different between having one or four virtual cores in a virtual machine. 
I usually give more important virtual machines more cores that the ones that can wait and only get one. 

One thing you should know is that giving a machine only one virtual core, does not mean that the host only processes the data on one physical core. Is more sophisticated than that.

---

### Post by veloce on 2009-04-08
Three observations:

With vmware 1.xx there is (was?) an issue with multi-core vms causing severe degradation of performance.

If the application you are running in the vm can use multiple cores then it may be worthwhile. I am intending to experiment with Excel 2007 - which says it can use multiple cores.

Ubuntu's smp is so much better than windoze's.  For almost every application, I have found it better to let vmware split up the vm into threads for the ubuntu host to manage than let windows vms attempt to use multiple cores.

---

