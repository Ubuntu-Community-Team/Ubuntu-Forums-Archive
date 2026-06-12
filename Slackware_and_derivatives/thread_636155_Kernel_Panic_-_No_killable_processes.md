---
title: "Kernel Panic - No killable processes"
date: 2007-12-09
forum: Slackware and derivatives
---

### Post by ntowakbh on 2007-12-09
I really want to try Slackware, and I have 2 or 3 spare 10GB partitions, and a swap partition is already set up.

The last time I tried to install Slackware, I was at fist kind of scared of the text only installer, but I got used to it.  I chose the correct partition, and everything needed, I chose not to install a boot loader, as I already have GRUB installed with Ubuntu.  I tell it to install, walk off to play a game for about 30 minutes, and return to see something along the lines of:

> Kernel panic:  Out of memory, no killable processes

What should I do to fix this problem, as I don't think I would be out, seeing as my computer has one gigabyte of RAM.

Any help is greatly appreciated.

---

### Post by angryfirelord on 2008-01-17
Strange. All I can say is do a re-install and add more swap.

---

### Post by kellemes on 2008-01-18
Pretty strange indeed.
I never ran Slackware so only guessing here.. can you select the kernel to use during install? Maybe the default kernel is compiled with all flags up, so it's too demanding for your system?

---

### Post by tommcd on 2008-01-24
When you install Slackware, choose to install the huge-smp kernel. The generic kernels need an initrd created to boot, which you set up manually after you install from one of the huge kernels. Unless your PC is old, you should install from the huge-smp kernel, and then after installation create a initrd as per the readme in the /boot directory and switch to the generic-smp kernel for daily use.
If you tried to install from one of the generic kernels this may be the problem.

---

### Post by ntowakbh on 2008-01-24
I'm sorry that I had almost forgotten about this topic.

> **angryfirelord said:**
> Strange. All I can say is do a re-install and add more swap.

Heh....about that...when I first installed Ubuntu, it was on my 300GB hard drive that i have on my computer...I was to lazy to repartition, so I used one of my smallest blank partitions for swap...that's 10GB.

> **tommcd said:**
> When you install Slackware, choose to install the huge-smp kernel. The generic kernels need an initrd created to boot, which you set up manually after you install from one of the huge kernels. Unless your PC is old, you should install from the huge-smp kernel, and then after installation create a initrd as per the readme in the /boot directory and switch to the generic-smp kernel for daily use.
If you tried to install from one of the generic kernels this may be the problem.

I'll give that a try, as soon as I redownload the first disk's ISO and reburn it...I left it out by mistake, and it got scratched up. o.o

---

