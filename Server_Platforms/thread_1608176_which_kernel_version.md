---
title: "which kernel version?"
date: 2010-10-28
forum: Server Platforms
---

### Post by h'bel h'balim on 2010-10-28
My VPS is hosted on a Xen server, so I'm limited to the kernel versions supplied by my hosting company.

I am currently running 9.10 on top of 2.6.30.5.

I wish to upgrade to 10.04. I note lucid ships with 2.6.32.24.25, but my hosting company only offers 2.6.34 and 2.6.35.7.

[LIST]
[*]Which kernels can I use with 10.04?
[*]Should I upgrade to 10.10 and use 2.6.35.7?
[/LIST]

Thanks!

---

### Post by arrrghhh on 2010-10-28
It's probably best to stick with whatever version Ubuntu has with it.  In theory, you should be able to run any kernel version with Ubuntu - but if you expect any sort of support, you're going to have to run one that vanilla Ubuntu uses.

So if 10.10 uses 35.7 and your provider supports 35.7, I'd say go with it.

---

### Post by h'bel h'balim on 2010-10-29
Thanks, @arrrghhh!

I suspected that was the case. According to packages.ubuntu.com, maverick ships with 2.6.35.22, which is the closest match to the hosting company's offerings.

I've had occasional virtual memory errors which leave the box in an unusable state, and one of the pointers I dug up suggested a kernel/ubuntu version mismatch could contribute to that.

---

