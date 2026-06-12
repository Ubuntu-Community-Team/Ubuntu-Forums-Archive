---
title: "Sun Fire V210 Problem"
date: 2007-03-30
forum: Sun Sparc Users
---

### Post by btsteve on 2007-03-30
I am trying to install Ubuntu Server 6.06 On a Sun Fire V210 Box with Dual Processors and 2gb of Ram. 
I have Updates the OBP to the latest which is 4.16.6.

This is the Error i am getting
Does anyone have any ideas or solutions
```

boot:
Allocated 8 Megs of memory at 0x40000000 for kernel
Loaded kernel version 2.6.15
Loading initial ramdisk (4861231 bytes at 0x3F802000 phys, 0x40C00000 virt)...
     ERROR: Last Trap: Illegal Instruction

Error -256
     ERROR: Last Trap: Memory Address not Aligned

Error -256
Stack Underflow
{0} ok

```

---

### Post by netztier on 2007-03-30
> **btsteve said:**
> I am trying to install Ubuntu Server 6.06 On a Sun Fire V210 Box with Dual Processors and 2gb of Ram. 
I have Updates the OBP to the latest which is 4.16.6.

This is the Error i am getting
Does anyone have any ideas or solutions
```

boot:
Allocated 8 Megs of memory at 0x40000000 for kernel
Loaded kernel version 2.6.15
Loading initial ramdisk (4861231 bytes at 0x3F802000 phys, 0x40C00000 virt)...
     ERROR: Last Trap: Illegal Instruction

Error -256
     ERROR: Last Trap: Memory Address not Aligned

Error -256
Stack Underflow
{0} ok

```

Search this forum for "Illegal Instruction" and see if it the hints help any.

One is to **cold-boot** the machine before booting from CD-ROM, for example. Others say to pass **mem=512** as kernel parameter when booting from CD, or **physically removing RAM** until there's 512 or less left. 

If you've already done all of this, pointing out that you  actually have helps a lot. For example, answers don't need to be starting with "search the forums, we've had that before", and your question looks a lot less n00bish.


best regards

Marc

---

### Post by btsteve on 2007-03-30
I have Taken the Box down to 512MB of ram that is the smallest set of memory chips i have, and i have tried the cold boot and the mem=512 suggestion and neither worked, i even swapped the memory from a different sun box and put in and still did not work.

---

