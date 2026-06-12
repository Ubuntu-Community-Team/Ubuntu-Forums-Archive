---
title: "A question on updating kernel &amp; libraries"
date: 2011-12-21
forum: System76 Support
---

### Post by Zvezdica27 on 2011-12-21
Hi,

I'd just like to ask, if I update kernel to a significantly new version (not through repos/synaptic, but completely through downloading debs) and updating libraries and packages, do I have to re-apply System76 restore (drivers) or not?

Specifically, I am playing a lot with new drivers for Sandy bridge graphics (Intel HD3000), new kernels etc. and would like the best performance (new kernel, mesa etc) while keeping trackpad drivers etc... 

Another question is, does the System76 driver modifies default kernel/ubuntu graphics drivers or is pangolin p8 using "default" ubuntu/intel ones? If not, the answer is clear. Or is the System76 driver the best way to go and ignore other options?

(Using 11.04, kernels above 3.0 and various gits, Pangolin p8)

Thanks,

Bla&#382;

---

### Post by isantop on 2011-12-21
Graphics drivers for Intel cards are always provided by Ubuntu.

As for the kernel, if we make any modifications, we always do it through DKMS so that the fix will stick across kernel updates. This system works very well, and we have almost no problems.

---

