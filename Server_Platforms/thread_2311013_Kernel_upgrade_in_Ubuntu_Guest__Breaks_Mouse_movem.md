---
title: "Kernel upgrade in Ubuntu Guest  Breaks Mouse movement in VMWare Vsphere 6 Console"
date: 2016-01-23
forum: Server Platforms
---

### Post by mattlach on 2016-01-23
Hey all,

I've been running on the 3.13 branch of th ekernel on my Ubuntu servers since launch, but recently had a reason to upgrade the kernel.   I went with the kernel offered through the [LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) by installing as follows:
```

sudo apt-get install --install-recommends linux-generic-lts-wily 
```

This upgraded my kernel to 4.2.0-25-generic.

Upon reboot the mouse is almost unusable in the VMWare Vsphere console.

I remedied this by removing the Wily based kernel, and instead installing the 3.19 branch through the linux-generic-lts-vivid package, and everything works again.

Most of my servers are headless, but on both of my two servers with X installed, I observed this identical problem.

Is this a known issue with 4.2 kernels, or is there something I am doing wrong?

Much obliged,
Matt

---

### Post by Ed_Horch on 2016-02-05
Sorry I don't have a solution, but I can confirm the the problem also appears in VMware Workstation 12 and VMware Player 12.

---

### Post by mattlach on 2016-02-05
> **Ed_Horch said:**
> Sorry I don't have a solution, but I can confirm the the problem also appears in VMware Workstation 12 and VMware Player 12.

Well, it is good to know that it is not just me.  This suggests this is a bug, and that we should file a bug report.

I'm terrible with bug reports though.  

I don't know how to figure out if this is a Linux kernel bug, a Ubuntu bug or a VMWare bug  (they are all reported in different places).

Then before filing the bug, I'd have to somehow search to make sure it isn't a duplicate. (I can't imagine we are the only two people who ahve encountered this issue)

Are you good with bug reporting?

---

