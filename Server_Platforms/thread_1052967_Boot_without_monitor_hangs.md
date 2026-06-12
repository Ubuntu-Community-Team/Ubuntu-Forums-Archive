---
title: "Boot without monitor hangs"
date: 2009-01-28
forum: Server Platforms
---

### Post by wgcampbell on 2009-01-28
Using Ubuntu 8.10 server edition on a "headless server".  It boots fine with a monitor attached but "hangs" for 35-40 minutes without a monitor.  The BIOS is set to "Halt On - No Errors".  I hangs here:

```
[    0.000000] Detected 498.056 MHz processor.
[ 2157.406302] Console: colour VGA+ 80x25

```

I found several posts that suggested using the "nofb" or "text" boot options - that made no difference.

Further research says I need to rebuild the kernel with the "Enable firmware EDID" option turned off, and remove most of the frame buffer device specific support - this suggestion came for the motherboard manufacturer.  I haven't the expertise to try this (nor the time).

Anyone have any further suggestions?

---

