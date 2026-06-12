---
title: "Failure to install on Sun Blade 100"
date: 2006-07-05
forum: Sun Sparc Users
---

### Post by g1zmo on 2006-07-05
I'm not able to boot from the CD-ROM.  After hitting ENTER at the SILO prompt I get a few errors about Illegal Instruction and Stack Underflow and get kicked back out to the the ok prompt.  I upgraded my OBP version to the latest (4.17.1) and tried again, but still the same result.  Network booting isn't an option, unfortunately, since this is the only machine I have access to on this network.

Am I just out of luck?

---

### Post by MickyLee on 2006-07-06
Ok, I just found out something interesting installing Ubuntu on a Sun Fire V210 and this may apply to your situation as well. I get an Illegal Instruction right after it starts initial ramdisk when I am using ALL the same vendor memory sticks. For example, Sun Fire V210s ship with certain memory sticks by default, but when I remove one of them and replace it with another vendor memory stick the box will complain about different memory architectures and say its disabling one of the banks, however now Ubuntu will load and I can install. Try swapping out one of your memory sticks if they are all the same and replace it with a different vendor's. Illegal instruction typically would mean to me that its using sparc-specific assembly but Ubuntu is trying to use non-sparc specific instructions and by disabling one of the memory banks somehow it might switch over to generic instructions. That's a total long shot and I may be 100% wrong on it, but it's the only thing I can gather from what's happening.

---

### Post by djcrash1981 on 2006-08-28
I have something similar, i olso update my OBP to the 4.17.1 and when i'm trying to inizializate the instalation it crashes after this message:

Loading initial ramdisk (4861231 bytes at 0x1F802000 phys, 0x40C00000 virt)...
ERROR: Last Trap: Illegal Instruction

Error -256
Error: Last trap: Fast Data Access MMU Mis

Error -256
Stack Underflow

This is a sunblade 150.

If someone have a hint please let me know it.

---

