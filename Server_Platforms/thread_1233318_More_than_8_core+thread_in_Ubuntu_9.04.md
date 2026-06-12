---
title: "More than 8 core+thread in Ubuntu 9.04"
date: 2009-08-06
forum: Server Platforms
---

### Post by Elv13 on 2009-08-06
Hi, I am having problem using more than 8 of the 16 core+thread of a new dual Quad core Xeon with hyperthreading. cat /proc/cpuinfo shot 8 CPU. If I remove 1 CPU (physically) it also show 8 core so it is not an hardware problem. I use linux-image-server and Ubuntu 9.04 32bit

I tried adding 
cpus=16 maxcpus=16 acpi=bigsmp
to the grub kernel command line with no result. I also compiled a kernel with 
CONFIG_X86_BIGSMP=y
CONFIG_MCORE2=y
CONFIG_SMP=y
CONFIG_NR_CPUS=32
CONFIG_X86_32_SMP=y
CONFIG_X86_HT=y

but it also failed to use all thread, but I saw this line in dmesg
```
SMP: Allowing 16 cpus, 8 hotplug cpus
```

Anyone here have successfully got more than 8 core working with Ubuntu 32bit?

And I CAN'T upgrade to 64bit, don't ask me to upgrade, it is not an option. Linux is able to support 64 CPU in 32bit mode, it is an Ubuntu issue.

---

