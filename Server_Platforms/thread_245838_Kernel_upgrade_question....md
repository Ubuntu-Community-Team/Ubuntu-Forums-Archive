---
title: "Kernel upgrade question..."
date: 2006-08-28
forum: Server Platforms
---

### Post by chipyoung on 2006-08-28
I just noticed from the security page of Ubuntu that I need to update my kernel to the latest.(linux image-1.6.15-26.46) for the 386 version. My current version is 2.6.15-25.43.  I am running 6.06 LTS.

I have never done a kernel upgrade before.  Can I use the Synaptic Package manager to update to the latest kernel?  Should I worry about anything? Do I need to take any precautionary measures?

Thank you in advance.

Cly

---

### Post by reacocard on 2006-08-28
yep. synaptic will take care of it. install the linux-386 package and it'll automatically upgrade whenever there's a newer one available. or you can do it manually (search for linux-image).

It shouldn't break anything. and if it does, GRUB will let you fall back to the older kernel to fix things.

---

### Post by chipyoung on 2006-08-28
Thank you Reacocard. I'll give it a shot.  I feel much better now.

One more quick question.  If I start adding new kernels then my Grub will probably expand not to mention my disk usage.  What is the best way to remove an old kernel?  Will Synaptic take care of that...Grub and all.

Thanks again,
Cly

---

### Post by reacocard on 2006-08-28
yep. synaptic will automatically remove a kernel from grub when you uninstall it. again, just search for linux-image to get the kernels.

BTW, for a possible performance gain, you could install a kernel optimized for your processor. Use the -686 kernels for intel processors, and -k7 for AMD processors.

---

### Post by chipyoung on 2006-08-28
Thank you again reacocard.  I'm dancing in the rain.  I'll try the k7 kernel for my AMD processor.

Thanks again,
Chip

---

### Post by az on 2006-08-28
> **chipyoung said:**
> Thank you again reacocard.  I'm dancing in the rain.  I'll try the k7 kernel for my AMD processor.

Thanks again,
Chip

Be sure to install the linux-k7 package and not just the linux-image-k7 package.  The former will also install the corresponding linux-restricted-modules package and the latter will not.

And also be sure to boot into your new kernel to make sure it works for you before you delete the old ones.

---

### Post by chipyoung on 2006-08-29
One last question.  Is the linux-k7 package the 64 bit version.  Everything is very stable for me now and I would hate to disrupt that.  I didn't install the 64 bit ubuntu version originally because of the things I have read in the forum trying to get certain programs to run.

Thanks again.....still dancing
Chip

---

### Post by az on 2006-08-29
k7 is 32-bit.

---

