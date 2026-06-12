---
title: "running KVM and VirtualBox at same host"
date: 2010-11-10
forum: Virtualisation
---

### Post by billdeng on 2010-11-10
Hi Guys,

It's really funny. I have searched by google and found many issues said that kvm and VB cannot running at the same machine. On one discussing at VB's forum, the answer is "INPOSSIBLE".

But I have two machines now running both of them. The first machine is use AMD 7960 CPU and the second AMD 945. On the first machine, the host is Ubuntu server 10.04, upgraded from 9.10. and it have 5 kvm guest running, 3 ubuntu servers, 2 windows servers. AND, it have a VirtualBox guest running also.  I used one VirtualBox guest because it hve better support for USB devices. The second machine have similar situation. Both machines have been running well for almost a year!

Last month, I bought a new machine. This time, I have a Intel i7 930 CPU. But this time when I try to running both VB and KVM, problem happened as many of people have seen. When I trying to start a VB guest, I got below error:
Error: failed to start machine. Error message: VirtualBox can't operate in VMX root mode. Please disable the KVM kernel extension, recompile your kernel and reboot (VERR_VMX_IN_VMX_ROOT_MODE)

If if remove the kvm_intel module by below command or blacklisted it as boot:
# modprobe -r kvm_intel
The VB guest can start but KVM guest will not!

Someone said to disable the VM support at bios maybe will help. I will try it later. I will let you know the result.

Do you have any lights?

Bill

---

### Post by billdeng on 2010-11-10
Hi Guys,

I find out something close to "why" and the solution. Hope be help for those still struggling.

KVM has two hypervisor mode (or virtualization management). One is qemu and another is KVM. When kvm_intel (or kvm_amd) is not loaded, KVM can still work on QEMU mode. But qemu alone seems much less effective then kvm. In this case, both KVM and VB can run at same time.

But in my previous machines, the kvm_amd module is loaded and VB still running well.

I am really confused.

Bill

---

### Post by dcstar on 2010-11-11
> **billdeng said:**
> Hi Guys,

I find out something close to "why" and the solution. Hope be help for those still struggling.

KVM has two hypervisor mode (or virtualization management). One is qemu and another is KVM. When kvm_intel (or kvm_amd) is not loaded, KVM can still work on QEMU mode. But qemu alone seems much less effective then kvm. In this case, both KVM and VB can run at same time.

But in my previous machines, the kvm_amd module is loaded and VB still running well.

I am really confused.

Bill

So something that works with one CPU family doesn't work with a **different** CPU family - where the CPUs are **different** designs with **different** capabilities and have totally **different** ways of supporting Virtulization.

See the theme here?

---

### Post by billdeng on 2010-11-11
Thanks David, I know the CPU architecture is the main difference here. 

But I am not sure whether it is the only reason to the different results.

---

### Post by dcstar on 2010-11-13
> **billdeng said:**
> Thanks David, I know the CPU architecture is the main difference here. 

But I am not sure whether it is the only reason to the different results.

If you look at the various CPU specs you see a lot of difference in Virtualization support and architecture. The VM platform providers have to use what is available in the CPUs as well as write code to get around what one CPU may do directly versus another CPU where they may have to emulate the functionality and some things may allow more capabilities than others.

The inherent setup of your AMD CPUs may have allowed both modes to run compared to the Intel CPU - and there are various different VM capabilities in different CPU families from each manufacture as well.

Sometime you just gotta accept that things work differently because things are different.

---

