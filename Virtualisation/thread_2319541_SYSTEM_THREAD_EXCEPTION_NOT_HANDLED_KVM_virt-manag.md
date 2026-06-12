---
title: "SYSTEM THREAD EXCEPTION NOT HANDLED KVM virt-manager"
date: 2016-04-05
forum: Virtualisation
---

### Post by wfacedrive on 2016-04-05
I have been playing around with this error in the Windows guest.  I noticed I can create a virtual machine with IDE for the storage or even SATA without a problem and do the 1511 update and perform resets without a problem.  I understand that VIRTIO is faster however so decided to use this instead.  When you go to backup>reset your pc or even when you do the 1511 update from Microsoft you get this SYSTEM_THREAD error as shown in the title.  I also found that currently setting the virtual guest processor as a core2duo fixes the issue.  My question is:

1. Is there a more up-to-date/better fix than this? Will programs that require more than a core2duo run on this? (I have my cores set to 4 and the GHz is well above 2.4)

2. Will this create any problems since my host processor is an AMD?

Thanks

---

### Post by MAFoElffen on 2016-04-06
> **wfacedrive said:**
> 
1. Is there a more up-to-date/better fix than this? Will programs that require more than a core2duo run on this? (I have my cores set to 4 and the GHz is well above 2.4)

In concept, yes this is the fix I do for Recent Windows guests newer than 8.x, to include Win Server 2016 preview. I haven't found a different method yet. But here goes the explanation, and caveat to that while answering your 2nd question.
> **wfacedrive said:**
> 
2. Will this create any problems since my host processor is an AMD?

Yes (but just if you select an Intel Config)... My two KVM servers, each have dual quad-core Xeons (Intel). As I've noted in some of my posts here for using Windows guest, you need to uncover some of the CPU's features for Windows to work right. (because Win digs deep into the hardware). This happens with some of the BSD and Unix based OS'es also. Though, not required with any of the Linux Distro's.

If a problem at boot, I recognize a few errors that are connected with the CPU. First You can copy the host CPU... then test. If not a success, then a lessor CPU. This is not neccsarrily just with the Core2Duo. But that config seems to work with a lot of OS'es.

The caveat, is that will work for an Intel CPU. With an Intel CPU, I cannot say it is an AMD (nor Qualcom, Tegra, etc.), even if lessor. Not the same instruction sets, and it will fail. One of my other VM Host machines is a dual Opteron 6386 SE's (16 cores each)So for an AMD, you cannot use an Intel config. That fails in the same manner, in the same way. Apples and oranges. Comparable on the AMD side to the Intel Core2duo would be using a config for an AMD Athlon 64x2.

I usually allocate 2 cores and 2 threads for a server config. My policy on that is start light, and if not enough, add more. If you overallowcating, it affects any other VM's that are competing for resources.  I usually start with 1-1, but if I know it's going to be taxed, I start out at 2-2. But I have some test VM's that run 3-4 nested layers of VM's.

Virtio tip-- define a second virtual optical drive so that you can have the vrtio device iso in that secondary, while you install from the primary with the win install iso. That way it doesn't even ask where it is... it finds the device files and goes on.

---

### Post by wfacedrive on 2016-04-07
Thanks for the response MAFoElffen.  I have been tinkering with the processor to see which ones throw the SYSTEM THREAD error.  In virt-manager there are only a few solutions I'm finding that work.  I see that the core2duo option works but I also see that kvm64, qemu64, and cpu64-rhel6 work as well.  Is core2duo still my best option?  I'm looking for the best solution as far as performance and functionality with several high-demand software applications.  Thanks!

EDIT:
I also tried passing the host cpu through with the same error as well as host-model and other combinations as shown in the link below.  (AMD FX 8350)
Link: [http://libvirt.org/formatdomain.html#elementsCPU](http://libvirt.org/formatdomain.html#elementsCPU)

---

### Post by MAFoElffen on 2016-04-07
As long as that works for you, then yes. Those other options are lessors than that one. (Less capabilities.)

---

### Post by wfacedrive on 2016-04-08
Thanks for the info MEFoElffen :)  You have been very helpful!  You really know your stuff when it comes to virtualisation.

---

