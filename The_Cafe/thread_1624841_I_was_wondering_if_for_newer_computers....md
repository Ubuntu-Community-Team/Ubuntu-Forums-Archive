---
title: "I was wondering if for newer computers..."
date: 2010-11-18
forum: The Cafe
---

### Post by nolag on 2010-11-18
I was thinking, newer computers that run 32-bit x86 would benifit from the kernel being compiled for i686?  I know that it is compiled for i386, but if the computer is from 95 + it should be compatible (ok for those who did not buy high end 96+).  I understand that adding a new kernel just for this would be silly, but say people (like me) are willing to recompile it to get better speed.

---

### Post by snowpine on 2010-11-18
Can you post the output of the following terminal command please?

```
uname -a
```

---

### Post by forrestcupp on 2010-11-18
I'm pretty sure the general x86 kernels included in Ubuntu are already compiled to be optimized for i686.

---

### Post by Joeb454 on 2010-11-18
An Ubuntu server VM I installed recently has an i686 kernel

```
Linux bespin 2.6.35-22-generic-pae #35-Ubuntu SMP Sat Oct 16 22:16:51 UTC 2010 i686 GNU/Linux
Ubuntu 10.10
```

---

### Post by nolag on 2010-11-18
> **Joeb454 said:**
> An Ubuntu server VM I installed recently has an i686 kernel
 
```
Linux bespin 2.6.35-22-generic-pae #35-Ubuntu SMP Sat Oct 16 22:16:51 UTC 2010 i686 GNU/Linux
Ubuntu 10.10
```
 
I stand corrected.  My appologies, I thought that very old computers could use ubuntu so I guess I assumed that it was i383.  I currently have x64 anyways, but I was just thinking was all.  Out of curiosity I will check what the 32-bit disk has (tomorrow or later today) as it may be different from the VM (since they know the VM will have i686 support).

---

### Post by forrestcupp on 2010-11-18
> **nolag said:**
> I stand corrected.  My appologies, I thought that very old computers could use ubuntu so I guess I assumed that it was i383.  I currently have x64 anyways, but I was just thinking was all.  Out of curiosity I will check what the 32-bit disk has (tomorrow or later today) as it may be different from the VM (since they know the VM will have i686 support).

They still have i386 kernels for old computers, too.  But the generic kernel is optimized.

---

### Post by LowSky on 2010-11-18
If you want a Distro that is strictly i686, you could pick Arch.

---

