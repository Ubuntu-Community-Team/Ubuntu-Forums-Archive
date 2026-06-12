---
title: "Setting KVM but problem on assigning storage space ??"
date: 2008-04-27
forum: Virtualisation
---

### Post by mshu on 2008-04-27
I have been using Ubuntu for quiet a while and finally able to install Ubuntu 8.04 Desktop on my Inspiron 6400. 
I am always interest in Virtual Machines and heard of the new KVM on 8.04, thus trying to install the KVM.
Everything works fine except when I try to assign storage space, the virt-manager just would not go on. I saw a post regarding on this issue ([http://ubuntuforums.org/showthread.php?t=765712](http://ubuntuforums.org/showthread.php?t=765712)) and once I un-check the kernel/hardware acceleration then the virt-manager will pass the assign storage space phase.

I have noticed that there is a bug been placed ([https://bugs.launchpad.net/ubuntu/hardy/+source/virt-manager/+bug/221746](https://bugs.launchpad.net/ubuntu/hardy/+source/virt-manager/+bug/221746)) but would like to know anyone came across this problem and able to by-pass the assign storage phase WITH kernel/hardware acceleration enable. 

Many thanks!:)

---

### Post by mshu on 2008-04-27
I just did some additional testing this morning and found out that the Virtual Machine Manager (GUI) only stall if you choose the OS type = Windows && Kernel/hardware acceleration check box is checked. If I choose to install Linux as my VM OS type instead, the Virtual Machine Manager lets me create my VM fine.

Any idea / methods that will allow VM to be created as Windows type and enable Kernel / hardware acceleration ?

Cheers

---

