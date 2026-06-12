---
title: "Installing a virtual machine that uses my real graphic card"
date: 2016-03-07
forum: Virtualisation
---

### Post by MatTheRat on 2016-03-07
I need to install a windows 10 VM on my ubuntu for gaming. But from my past experiences with virtual machines, they don't use your real graphic card and so the performance is too low for gaming. I was reading more on the subject and stumbled upon this tutorial that apparently allows you to do just that.

[http://linuxlookup.com/windows_gaming_qemukvm_ubuntu_linux_amd_radeon_r9_280](http://linuxlookup.com/windows_gaming_qemukvm_ubuntu_linux_amd_radeon_r9_280)

However it mentions that you need to have 2 graphic cards (I think?). I'm not good with PC hardware and wasn't aware that people had multiple graphic cards.

Specs:
Processor: Intel(R) Core(TM) i5-2400 CPU @ 3.10 GHz (4 CPUs)
Memory: 16384 MB RAM
System Model: h8-1111 (HP)
Graphic card: AMD Radeon R7 200 Series (Chip type: AMD Radeon Graphics Processor (0x6613)) - 10212 MB memory

The games I play currently aren't very demanding, they would be fairly similar to the very old game "Diablo II". If this doesn't work for my system's specs, can someone point me to a different tutorial/solution. This is pretty important to me to the point where I would buy an older/cheaper PC just for this. (would really like to avoid that)

I also read this on reddit:

"you don't need 2 discrete cards, you can use integrated graphics for the host and the discrete card for the guest its a bit of a pain though if you intend to do anything graphical with the host, so i'd just recommend keeping an old card around when you upgrade" 

However I was't able to find any tutorials on how to do this, if someone could help me out I would really appreciate it.

---

### Post by houstonbofh on 2016-03-08
First, what VM system?  Different ones have different abilities.

But the non-free virtualbox supports opencl, and can use hardware acceleration on the virtual graphics card.  Other then that, you are looking at PCI passthrough, and then it is the graphics card for that VM and only that VM.

---

