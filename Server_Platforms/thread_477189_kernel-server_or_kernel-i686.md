---
title: "kernel-server or kernel-i686"
date: 2007-06-18
forum: Server Platforms
---

### Post by technoteen on 2007-06-18
hey
i installed ubuntu 6.06 desktop verison on a server (hp proliant dl360) , as i am always more comfortable to have a GUI at hand
then the changed the kernel to linux-image-686 and the system is working like a charm

now my question was, should i use linux-image-686 or linux-image-server on the system
whts the advantage of one over another nd how much RAM does each support?


ps: i knw tht i could have done a ubuntu server install and then added the ubuntu-desktop package, but wouldnt that result the system in the same state?

---

### Post by carcioni on 2007-06-18
I haven't installed Ubuntu 6.06 anything, but I'll see if I can  make some sense of the packaging. I may not be entirely accurate here, so others may need to correct me where needed.

If I understand the packaging, the '-server' is a pre-configured LAMP environment, with no GUI components. The '-i686' is a subset of this in that it has a kernel, and possibly other components  specifically compiled of '-i686' architectures.  So the '-server' will contain the '-i686' kernel components.

As to how much memory you need or the servers will address is usually handled by the particular kernel configuration and the underlying machine architecture. The limit under 32 bit architectures (i686 et all) is around  4GB  I think (please correct me), and huge (32 or 64 GB)  for 64 bit architectures.

What is better or worse is usually dependant on your situattion, what level of managment you want to have to deal with, and wheather you like command line interfaces or not. MY rule is that if it is working for you and performing the way you want it to, don't get too excited about which particular flavour you use. 'Serve' environments over 'Desktop' environments will have some very different resource demands, so the kernel will be configured differently, but the tools to manage the environment are up to you.

Hope this helps a bit.

Cheers
D

---

### Post by az on 2007-06-18
The 686 kernel no longer exists.  That meta package points back to the generic desktop kernel.

The desktop kernel is 386, but with the 686 optimisations enabled at run time (instead of the good old days when they needed to be done at compile-time)

The server kernel is 686 or better.  It has many optimisations for server-specific tasks (like having a lower base frequency) but may not work well with desktop hardware like wireless cards, proprietary graphics drivers and some other things like certain kinds of mice.

---

