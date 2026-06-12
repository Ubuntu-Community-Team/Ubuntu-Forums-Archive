---
title: "realtime kernel not loading"
date: 2010-07-08
forum: Ubuntu Studio
---

### Post by GhostofJohnToad on 2010-07-08
Did a fresh install of Ubuntu 10.04.  Then installed packages for Ubuntu Studio.  I then installed the realtime kernel, well at least I thought I did.  It shows in synaptic as if it is installed but when I do [PHP]uname -r[/PHP] I get the generic/vanilla kernel listed.  Should I assume it did install but is just default booting to the vanilla kernel?  If so how do I change the default?  

I can't remember the kernel versions off the top of my head, I'm not at that box.

---

### Post by cchhrriiss121212 on 2010-07-08
> **GhostofJohnToad said:**
>   Should I assume it did install but is just default booting to the vanilla kernel?  If so how do I change the default?
Yes that's the problem. You can press shift to select a kernel to boot from using the GRUB menu when booting up. Or you can download startup manager to select the default kernel to the rt version you have installed, as well as other settings.
It's a good idea to keep the generic kernel around in case the rt starts trouble with your install.

---

### Post by GhostofJohnToad on 2010-07-08
Very good, thanks! So with startup manager can I dictate how many kernels I wish retained?

---

