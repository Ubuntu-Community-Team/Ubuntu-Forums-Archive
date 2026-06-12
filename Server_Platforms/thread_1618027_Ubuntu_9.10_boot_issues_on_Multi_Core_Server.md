---
title: "Ubuntu 9.10 boot issues on Multi Core Server"
date: 2010-11-10
forum: Server Platforms
---

### Post by tgwoollard on 2010-11-10
Good morning all 

I have an issue with Ubuntu 9.10 running on a HP BL685 G7 Server. This Server has 4x Eight-Core AMD Opteron CPU's and 32GB RAM.

In a nutshell, the system wouldn't install, and won't boot, unless i specify the nolapic option in the boot parameters. With this option Ubuntu 9.10 loads perfectly but the operating system will only see 1 core of 1 CPU.

When i remove this option and restart, the system simply will not boot. The last logged entry at startup is "start_secondary+0xa9/0xab"

Any help or guidance would be greatly appreciated.
Many Thanks in advance

---

