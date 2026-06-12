---
title: "VMWare works, KVM does but only half"
date: 2010-12-16
forum: Virtualisation
---

### Post by jevus on 2010-12-16
Hi there. I am running Lucid 64 bit, kernel 2.6.32-21.

I have VMWare Player installed and I have a few VM's and they work without a hitch.

I wanted to try KVM so I installed it and all the packages, including virsh

When I create a new VM (let's say fedora), I specify the name, CPU, RAM and all the other configs. When I start the creation process, I see the boot menu and press Boot, to run the system. 
I wait for the progress bar to complete and goes from blue to white (as it should) but that's where it hangs. It just stays at that screen forever. That happens when I try to install a Win 7 VM as well.

One important thing to note - I checked to see if my CPU supports virtualization using ```
egrep -c '(vmx|svm)' /proc/cpuinfo
``` and I get a 0, meaning that it doesn't support it. However, like I mentioned, I run VMWare VMs without a problem, and I also get the loading screen for Fedora/Win7 using KVM/QEMU.

Does anybody have any clue why I can run VMs in one and not in the other? I've looked online for 2 days now without any luck.

---

### Post by gmargo on 2010-12-17
It's because VMware does not require hardware virtualization support, while KVM does.

---

