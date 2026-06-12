---
title: "What's the best hypervisor for Windows 10 Pro and the best for Ubuntu VM"
date: 2015-12-02
forum: Virtualisation
---

### Post by MechaMechanism on 2015-12-02
What is the best hypervisor for running Windows 10 Pro and what is the best for running Ubuntu 14.04 in a VM.  LXC, KVM, Virtualbox etc.

---

### Post by T.J. on 2015-12-03
That's a loaded question.  Ask 5 different people and you will get 5 different answers.  The question you might ask is which hypervisor has the features you need.  For that you should do your own research, as only you can decide what is best for you.  The rest of this post is shameless KVM promotion, based on personal experience with most of the major options.


VirtualBox: VirtualBox, in my opinion, is not even worth consideration. It's absolutely abysmal.  It crashes Linux kernels and has poor overall performance.  I believe one of the Linux kernel developers called its drivers "crap" and my assessment after years of testing and use is that that is exactly accurate. I no longer use it at all. (I switched over to KVM completely. I'll never use VirtualBox again.)

LXC: LXC is technically not a true hypervisor, more like an enhanced chroot - and generally speaking it is only good for Linux servers running instances of Linux servers.  

Microsoft HV: Microsoft Hyper-V deserves an honorable mention, although like VirtualBox, it is not very useful.  It has limited support and can cause software issues.  

VMWare: An okay system, but I avoid it.  It tends to be costly for commercial use.  There are free versions, but some have serious restrictions. There is also the fact that VMware is in the middle of a GPL lawsuit.  
 
Xen: Decent, but not easy to configure.  It has far more hardware limitations than KVM,

KVM/Qemu: Hands down the best Linux virtualization at present.  All major versions of Linux support it and community documentation is extensive. Because KVM is part of the Linux kernel, it is well maintained and updated.  The hardware support is extensive, including x86, ARM and SPARC emulation, as well as the ability to pass-through devices, even video if you have a second video card and IOMMU capable hardware.  This allows KVM to handle DirectX calls natively, sending them directly to the video hardware.  I use Debian, and then KVM  to run all of my Windows applications, including games and development.

---

### Post by Tadaen_Sylvermane on 2015-12-03
> **T.J. said:**
> KVM/Qemu: Hands down the best Linux virtualization at present.  All major versions of Linux support it and community documentation is extensive. Because KVM is part of the Linux kernel, it is well maintained and updated.  The hardware support is extensive, including x86, ARM and SPARC emulation, as well as the ability to pass-through devices, even video if you have a second video card and IOMMU capable hardware.  This allows KVM to handle DirectX calls natively, sending them directly to the video hardware.  I use Debian, and then KVM  to run all of my Windows applications, including games and development.

I've been playing with virtualized servers on my little file server with kvm however I never figured Windows would run well. What is the best way to interface with the vm? I've been using virt-manager but the resolution seems to stick to 1280x1024 or something else real low. Can't get 16:9 out of it which I would prefer.

---

### Post by zexelon2 on 2015-12-04
Personally I have had great success with VirtualBox but only on a Windows Host. I have never really tried it on a Linux host. 

On Linux I have spent the last long time working with Xen. It is relatively easy to configure and set up (at least in Ubuntu). It handles things like passthrough (specifically VGA) moderately well. I am however going to be switching to KVM in the near future due to its method of exposing more advance features for emulation testing.

---

### Post by T.J. on 2015-12-05
> **Tadaen_Sylvermane said:**
> I've been playing with virtualized servers on my little file server with kvm however I never figured Windows would run well. What is the best way to interface with the vm? I've been using virt-manager but the resolution seems to stick to 1280x1024 or something else real low. Can't get 16:9 out of it which I would prefer.

So far, all that virt-manager has done for me is cause Windows to not run properly.  This is not a criticism of virt-manager, just a recognition that it and libvirt tend to deny access to hardware, even when it is set aside for virtualization.  After many wasted hours, I use native KVMs only.  I do not even install virt-manager anymore.  With a second videocard and a proper KVM configuration, I would speculate you can get up to 85%-90% of native speeds.  No matter what you do, there is always some overhead. I can tell you that with an Nvidia GTX 960 attached to the VM, I can play top shelf video games, such as Fallout 4 with no performance problems, even though my processor is only an AMD 1090T, which is a 2010 technology.  I slave 3 of the 6 cores to the VM.

---

### Post by KillerKelvUK on 2015-12-05
> **Tadaen_Sylvermane said:**
> I've been playing with virtualized servers on my little file server with kvm however I never figured Windows would run well. What is the best way to interface with the vm? I've been using virt-manager but the resolution seems to stick to 1280x1024 or something else real low. Can't get 16:9 out of it which I would prefer.

virt-manager is useful for quick creation and management of guests only IMO.  If you have configured the windows guest correctly i.e. using QXL, spice channels etc and have installed the guest tools then you can use virt-viewer to connect to the windows guest and your resolutions problems should go completely away.

I've been running and Ubuntu host with Windows VM now for years and using the above I get excellent graphical and audio performance (office type use NOT game play).

virt-manager and passthrough...I actually don't mind this combination..some people say virt-manager and libvirt are too restrictive.  My experience of pre 15.04 is that virt-manager had quite a few bugs, since 15.04 its been ironed out quite nicely, you just have to know your way around the tricks as passthrough typically needs qemu features that aren't part of the stable libvirt or virt-manager yet.

---

### Post by MechaMechanism on 2015-12-06
A loaded question indeed I have found out.  I decided upon Virtualbox for Windows.  I'm running Windows XP in VBOX right now.  I'll look into LXC for running 14.04.

---

### Post by T.J. on 2015-12-07
Awesome!  Please mark the thread solved.

---

