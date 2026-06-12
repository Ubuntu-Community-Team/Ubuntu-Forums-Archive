---
title: "how to change kernel boot parameters in systemd or refind"
date: 2021-12-07
forum: Ubuntu/Debian BASED
---

### Post by hellwraiz on 2021-12-07
I am new to Linux and very confused.

 
I need to change the i915.enable_psr and i915.enable_guc parameters  or modules or whatever they are called to prevent my laptop from being  in a constant state of agony, but I only recently found out that pop!_os  instead of grub uses systemd or refind to boot or something and I  genuinely can't find the alternative to the GRUB_CMDLINE_LINUX_DEFAULT  from grub, can anyone help me?

 
And could anyone be kind enough to tell me what the difference  between systemd or refind is? Or one better, what do they even mean?

 
P.S. In case it matters this whole ordeal started because of this:

i915 Atomic update failure on pipe A  And no, moving to a different os didn't solve the problem.

 
Sincerely,

 
One hell of a confused Linux noob.

---

### Post by yancek on 2021-12-08
rEFInd is a boot manager available with most Linux systems, explained at the link below.

[https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/)

And systemd:  [https://en.wikipedia.org/wiki/Systemd](https://en.wikipedia.org/wiki/Systemd)

---

### Post by KBar on 2021-12-08
Here, take a look at [this]("https://wiki.archlinux.org/title/kernel_parameters#systemd-boot") article.

---

