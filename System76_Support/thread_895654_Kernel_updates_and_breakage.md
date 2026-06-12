---
title: "Kernel updates and breakage"
date: 2008-08-20
forum: System76 Support
---

### Post by imhavoc on 2008-08-20
For years, I have been frustrated with Linux kernel updates breaking things. One thing I've never figured out in three years of Ubuntu usage is "pinning" with apt-get.

When I'm running kernel 2.6.24-19, my VMware install works. If the kernel gets updated, VMware breaks, and more often, the vmware modules cannot be compiled to the new kernel (sources and tools all being installed). To make matters worse, System76 does not officially support kernels after -19.

Right now, I have /boot/grub/menu.lst set to boot the -19 kernel, but a new kernel is showing up in the updates, and I'm putting off the update to avoid messing up my menu.lst.

Is there a simple way to 'pin' my kernel to avoid the continual breakage that comes with kernel updates?

Thanks big!
havoc

---

### Post by thomasaaron on 2008-08-20
That's correct. As of this post, the versions higher then *-19 are still *proposed* updates, which means that, by definition, they are probably buggy.

You can avoid downloading proposed updates by going to System > Administration > Software Sources > Updates and de-select "Pre-released Updates". This will keep the proposed updates from coming down the pike.

Once you've done this, run: sudo apt-get update to clear the proposed stuff from your updates list.

Regarding VMware, you are also correct. It is compiled against the kernel, so when the kernel changes it breaks. Interestingly, this does not happen with VirtualBox's set-up. But, depending on what you need Windows to do, VirtualBox may not be the best fix.

If you wanted to permanently remain on *-19, you could open Synaptic Package Manager and search for linux-generic, which should be at 2.6.24.19.21, highlight it, and then go to Package > Lock Version in the menu.

That might do the trick, but I'm not sure if it will have any repercussions with other downloads later on.

Hope this helps.

---

### Post by imhavoc on 2008-08-21
very nice! I wish I'd known it was that easy two years ago!

---

