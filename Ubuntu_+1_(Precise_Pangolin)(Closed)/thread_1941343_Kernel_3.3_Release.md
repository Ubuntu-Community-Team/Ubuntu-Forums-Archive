---
title: "Kernel 3.3 Release"
date: 2012-03-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by fjgaude on 2012-03-15
Any chance kernel 3.3 will get into Ubuntu 12.04, either before or at LTS release?

Thanks!

---

### Post by dino99 on 2012-03-15
LTS does not mean bleeding edge :)

but some patches from upstream are continuously included into our custom 3.2 kernel

---

### Post by kaldor on 2012-03-15
Kernels in Ubuntu are not vanilla or official Linux kernels. Canonical works on modifying it to add newer hardware support by backporting features from later kernels.

For example, Ubuntu 11.04 uses a 2.6.38 kernel but has wireless support from kernel 3.0. My wireless card didn't have support until Linux 3.0, so eventually this support was added in an update for me. Ubuntu's kernels get patched throughout their lifespan.

Ever fix a hardware issue on Ubuntu by running an update? This is why :)

---

### Post by fjgaude on 2012-03-15
Thanks for the comments.

The question really is if the details of kernel 3.3 get into 12.04, when?

Likely no one really knows, eh?

---

### Post by dino99 on 2012-03-15
> **fjgaude said:**
> Thanks for the comments.

The question really is if the details of kernel 3.3 get into 12.04, when?

Likely no one really knows, eh?

the kernels changelog into synaptic let you know about them

[https://launchpad.net/ubuntu/+source/linux](https://launchpad.net/ubuntu/+source/linux)

---

### Post by kaldor on 2012-03-15
> **fjgaude said:**
> Thanks for the comments.

The question really is if the details of kernel 3.3 get into 12.04, when?

Likely no one really knows, eh?

I believe some 3.3 things are already present in Precise's 3.2 kernel. Some power management changes, I think.

---

### Post by fjgaude on 2012-03-15
> **kaldor said:**
> I believe some 3.3 things are already present in Precise's 3.2 kernel. Some power management changes, I think.

I'm looking for ACPI fixes that permit suspend/resume with Sandy Bridge chipsets like Z68. I'm sure these will be there by the time Ivy Bridge motherboards come out.

Thanks again for your reply.

---

