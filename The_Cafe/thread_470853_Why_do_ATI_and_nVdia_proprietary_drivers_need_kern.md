---
title: "Why do ATI and nVdia proprietary drivers need kernel modules?"
date: 2007-06-11
forum: The Cafe
---

### Post by Extreme Coder on 2007-06-11
As the topic says, I want to know why does fglrx or nvidia driver need a kernel module to work? Isn't the xorg module enough?


Thanks a lot!

---

### Post by prizrak on 2007-06-11
Linux is a monolithic kernel, which means that all the drivers are built into it. That in turn means that any driver that wants to run at any kind of decent speed has to be a part of the kernel. It's basically a performance issue, the driver needs to talk to the kernel on an intimate level in order to work correctly. Since the binary drivers are not allowed in the kernel itself they link to it with basically a translator module that will make system calls for the driver.

---

### Post by Extreme Coder on 2007-06-11
So to achieve decent performance, the proprietary drivers need to be linked to the kernel? What exactly do they need from the kernel that xorg doesnt provide?

Sorry for asking, but it never entered my mind why they were linked to the kernel.

---

### Post by maniacmusician on 2007-06-11
> **Extreme Coder said:**
> So to achieve decent performance, the proprietary drivers need to be linked to the kernel? What exactly do they need from the kernel that xorg doesnt provide?

Sorry for asking, but it never entered my mind why they were linked to the kernel.
Xorg just provides the **drawing** features. Without X.Org, video cards wouldn't be able to draw windows and cool effects and whatnot. But the controlling of the hardware in the video card is done through the kernel...the kernel manipulates the video card. so for that to be done at a reasonable performance, it needs to be linked.

So, xorg draws the screen, but it doesn't control the video card. It just sets limits on what the video card can and cannot do.

---

### Post by Extreme Coder on 2007-06-11
Thanks a lot for clearing it up !

---

