---
title: "Iommu"
date: 2015-03-04
forum: Virtualisation
---

### Post by marseille2 on 2015-03-04
Does IOMMU need to be enabled (for hardware acceleration) if only using 1 video card? 


----

Note: motherboard --Asrock 970 Extreme4 -- has no onboard video). Currently using VB 4.3.22 r98236, but thinking about switching brands.


PS: Sorry for spelling error... forgot my glasses!

---

### Post by TheFu on 2015-03-04
No, but a VM doesn't see the physical video card anyway.  For video accel, you probably need the proprietary GPU drivers installed and working on the hostOS.  Again, that won't help much for any VM graphics.

---

### Post by marseille2 on 2015-03-05
Thank-you!

---

