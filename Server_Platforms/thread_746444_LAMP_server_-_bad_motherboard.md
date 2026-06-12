---
title: "LAMP server - bad motherboard"
date: 2008-04-05
forum: Server Platforms
---

### Post by TheGameAh on 2008-04-05
Hey guys. 

Need some input.  Have a LAMP server running nearly a year.  AMD 64 Athlon, software mirrored drives.  On Friday the motherboard crashed.

Is it just a matter of swapping the motherboard with an AMD Athlon 64 board?  I'm hoping it's as simple as that.  I tried an Intel board, but didn't think it would work, and sure enough it didn't boot.

---

### Post by netlogic on 2008-04-05
> **TheGameAh said:**
> Hey guys. 

Need some input.  Have a LAMP server running nearly a year.  AMD 64 Athlon, software mirrored drives.  On Friday the motherboard crashed.

Is it just a matter of swapping the motherboard with an AMD Athlon 64 board?  I'm hoping it's as simple as that.  I tried an Intel board, but didn't think it would work, and sure enough it didn't boot.

change your kernel to generic kernel for amd 64.
1. grab a live cd 
2. mount your dev drive to the mount point
3. chroot
4. dpkg -i the downloaded package...

---

