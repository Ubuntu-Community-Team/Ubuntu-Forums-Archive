---
title: "Concept possible? Could Ubuntu run across multiple CPUs, one x86, the other ARM?"
date: 2013-03-07
forum: The Cafe
---

### Post by Omen_20 on 2013-03-07
[My reason for asking.]("http://www.theverge.com/2013/3/7/4074288/asus-transformer-aio-us-release-date-price-specifications-pictures-video")

I think it would be cool if maybe the kernel+OS+DE(Unity) always ran off the tablet and when docked applications would run on the x86 and discrete graphics. I know I've seen tablets go from integrated to discrete graphics when docked. I also know there are distros that can do parallel computing with Beowulf clusters.

My first question: If it were two x86 or two ARM processers, could the work be divided where only applications ran on the second, with everything else running on the first?

Second question: If the above scenario is possible, would it be feasible when pairing the differing architectures?

---

### Post by Paqman on 2013-03-07
> **Omen_20 said:**
> 
My first question: If it were two x86 or two ARM processers, could the work be divided where only applications ran on the second, with everything else running on the first?

Processors with more than one core already do this. Linux has supported multiple cores and multiple CPUs for years. Servers with multiple physical CPUs used to be reasonably common. Linux is able to seamlessly divide up workloads between them as needed.

> 
Second question: If the above scenario is possible, would it be feasible when pairing the differing architectures?

I don't think it would be possible for a single kernel to run simultaneously on two separate architectures. The device you link to uses two completely separate OSes. What might be possible would be to create a device which was able to quickly suspend one OS and resume the other. The trick would be providing some continuity of experience during the transition. Switching from an ARM build to an x86 build of the same distro should be possible, as all of the user's session and data could be in a shared home folder. I'm not saying it would be easy, but it's not a completely mad idea.

---

### Post by MaxIBoy on 2013-03-07
There's a car maker in Sweden called Koenigesgg. Its boss is famous for saying, "if you pay us enough money, we'll build you a helicopter."

This is probably similar. It's probably possible, but at a certain point it stops being customization and turns into a complete rewrite.

On the other hand, your OS probably already does this to a degree, running some tasks on a GPU and other tasks on a main CPU.

---

### Post by ssam on 2013-03-08
The closest that currently exists is ARMs big.LITTLE [https://lwn.net/Articles/481055/](https://lwn.net/Articles/481055/) that uses different core types (A15 and A7), but running the same instruction set. I guess in theory it might be possible to do something similar with i7 and atom cores, as long as you restricted yourself to instructions that existed on both (i dont think any atoms support SSE4 or AVX).

For a general solution you need to share memory between the processors. This means you need your binaries to look identical (same instructions), and your in memory data to be identical. i can't see how you would achieve that with a 64bit x86 and a 32bit arm. Also the memory needs a very fast connection to the CPU, so it would be difficult for example to have the ARM in the tablet, and the x86 in the dock.

You could probably have something that appeared to move seamlessly from the ARM to x86 for specially crafted programs. for example you could make a web browser that could keep its tabs and session synced between to instances running on different CPUs.

personally i think that the effort should be spend on CPUs and GPUs that can work at different power profiles. ie while on battery the CPU knows it can only use 0.5W, so it might switch off some cores, and down clock to achieve that. then you plug it in, and tell it that it has 10W or 50W to play with, and it steps up. Most modern CPUs do something like this, but maybe not over such a big range.

---

### Post by tgalati4 on 2013-03-08
You could write a script:

When docked, open an ssh -2 -Y connection to your powerful desktop machine and open the desktop panel.  It might not be usable on a tablet--icon size, font size, and overall layout.  

When undocked, the ssh connection would break and the desktop panel would/should shut down automatically, leaving you with the tablet environment.  You would have to create some clever file mounts or save your files to the cloud (say UbuntuOne) otherwise they would be on the desktop machine and not accessable to the tablet when you are undocked.

This assumes that your tablet is running some sort of X-Windows client.  The current trend is to get rid of X using Wayland or Mir or something else--so this capability will go away.

---

