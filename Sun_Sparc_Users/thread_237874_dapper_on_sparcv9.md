---
title: "dapper on sparcv9"
date: 2006-08-16
forum: Sun Sparc Users
---

### Post by jharr on 2006-08-16
Hi guys. I have a solaris install on a sunfire v240. I downloaded the sparc ISO, but I can't seem to boot into it. SILO loads fine, starts to boot the kernel, and it spits out "Illegal Instruction"

```

# psrinfo -v
Status of virtual processor 0 as of: 08/16/2006 19:40:56
  on-line since 08/16/2006 19:39:26.
  The sparcv9 processor operates at 1503 MHz,
        and has a sparcv9 floating point processor.
Status of virtual processor 1 as of: 08/16/2006 19:40:56
  on-line since 08/16/2006 19:39:24.
  The sparcv9 processor operates at 1503 MHz,
        and has a sparcv9 floating point processor.

```

Are there any good resources you can point me to? I checked around the forum a bit and din't find anything that fixed my problem. I just ran 'boot cdrom' at the ok ? prompt. SILO comes up fine. The little "welcome to ubuntu dapper" message comes up fine.

at the boot: prompt I hit enter (I've tried rescue, and server too), and it says:
```

boot:
Allocated 8 Megs of memory at 0x40000000 for kernel
Loading kernel version 2.6.15
Loading initial reamdisk (4861231 bytes at 0x103F802000 phys, 0x40C00000 virt) ...

Illegal Instruction
{1} ok 

```

and that's as far as I get. I have an install of Solaris 10 on there currently. The ISO I got says it was built on 20060811.1.

Thanks,
James

---

### Post by jharr on 2006-08-16
I think I've fixed it, so far. I read the forum here.

[https://launchpad.net/distros/ubuntu/+source/silo/+bug/40119](https://launchpad.net/distros/ubuntu/+source/silo/+bug/40119)

I powered off my system completely and booted. It worked perfectly. I couldn't get the system to boot using the graphics card. So I'm left installing over the serial console, which is painful to say the least.

Thanks :)

---

