---
title: "Cannot Enable 3d Acceleration on 14.04 Host"
date: 2015-03-29
forum: Virtualisation
---

### Post by residualbit on 2015-03-29
Running ubuntu 14.04 with an nvidia 750 ti using driver 346.

When I try to enable 3d accelertation, it shows the invalid settings detected message, then generates a system error:

```
VBoxTestOGL assert failure: ***buffer overflow detected***: /usr/lib/virtualbox/VBoxTestOGL terminated
```

Any ideas?

---

### Post by TheFu on 2015-03-29
Unless you are doing VGA passthru, the actual physical GPU doesn't mean anything in a virtual environment. I don't think virtualbox supports that at all, but I could be wrong.  You will be using the virtualbox video card emulation, nothing else. Using that requires that the **guest additions** be correctly installed into the guestOS.  Have you done that and have you changed the video RAM setting to be 128MB (not the default) for the VM?

[https://www.virtualbox.org/manual/ch09.html#pcipassthrough](https://www.virtualbox.org/manual/ch09.html#pcipassthrough) - notice they show PCI pass thru for non-graphics cards.  To do that, people seem to have the most success using either KVM or Xen systems. Don't know if that nvidia card is known to work or not.  

You might check the VGA Passthru threads here. Setting this stuff up is non-trivial. You will be patching and rebuilding kernels.

---

### Post by residualbit on 2015-03-29
Solved. I should have done some more searching up front. Basically, this is a known bug in the version in the 14.04 repos. Updating to the current version from the website (4.3.26) fixed the issue.

---

### Post by TheFu on 2015-03-29
Are you doing VGA passthru under virtualbox? If so, I bet lots of people would like some help/how-to here!

---

