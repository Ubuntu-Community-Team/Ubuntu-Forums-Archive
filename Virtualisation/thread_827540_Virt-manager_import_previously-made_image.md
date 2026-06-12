---
title: "Virt-manager: import previously-made image?"
date: 2008-06-12
forum: Virtualisation
---

### Post by scotters on 2008-06-12
Just did a clean install after checking out another distro's features (but came back!). Got KVM/virt-manager all set up...but how do I bring back previous images for virt-manager to recognize?

---

### Post by grantek on 2008-06-12
I just used the "create VM" wizard, pointed it to the raw disk image file I had (it doesn't reinitialise the file or anything), and gave it a random unrelated ISO I had lying around. After the first boot, it had created the VM definition and was able to boot normally off the disk image.

I agree it's frustrating though :confused:

---

### Post by scotters on 2008-06-12
Thanks--grabbed a quick iso, did that, freaked a bit when I saw it initially boot to that ISO, stopped it, and the VM started right up as before.

Worked beautifully, thanks!:)

---

