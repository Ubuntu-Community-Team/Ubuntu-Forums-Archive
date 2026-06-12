---
title: "Is there such a thing as too much SWAP?"
date: 2009-06-08
forum: Server Platforms
---

### Post by Jekshadow on 2009-06-08
I know that the kernel can support a lot of swap, but would having more swap (10x as much as RAM, 30GB swap to 3GB RAM) negatively affect a server in any way (excluding HD space, which I have plenty of)?

---

### Post by LepeKaname on 2009-06-08
In most of the systems swap is not even used. If you have 3GB RAM maybe 1 more GB is enough. You can dynamically add or remove [swap files]("http://www.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/5/html/Deployment_Guide/s2-swap-creating-file.html") depending on your system load.

Check how much memory is your system using, with for example the "top" command:

```
Mem:   2051936k total,  1711728k used,   340208k free,   309252k buffers
Swap:   979956k total,        0k used,   979956k free,   626464k cached
```

My system is currently using 0k of swap. That means it is not using it. Usually your system will use the swap memory when your physical memory is reaching it maximum and will copy into the swap space the sleeping processes. So, even the process that was using the memory finished, the sleeping processes will remain at the swap space. So anytime you can see if actually your system is using it or not. If is using more than half, then add a little bit more.

---

### Post by Bios Element on 2009-06-08
Yes, there is. But I keep 2gb aside just in case I ever need it. But to be honest, I don't think it's ever actually used.

---

### Post by lensman3 on 2009-06-08
Take a look at the "free" command from a command terminal.  And the pseudo file "/proc/meminfo".  It will tell you the current state of memory.

Recall that the only part of a program that will be written to the swap file is the active data stack.  The program and any read-only data will just be swapped out when not needed and when it is needed again the OS will swap it in from where it resides in on disk.  Only the transient data that is created during execution will use the swap.

---

