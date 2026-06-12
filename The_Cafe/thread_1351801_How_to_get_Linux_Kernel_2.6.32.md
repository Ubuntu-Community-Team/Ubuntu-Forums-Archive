---
title: "How to get Linux Kernel 2.6.32"
date: 2009-12-10
forum: The Cafe
---

### Post by Shibblet on 2009-12-10
I really want to use this kernel because of the new BFS, Brain F**k Scheduler (Don't ask me, I didn't name it.)  But what it does is amazing.  I use handbrake quite a bit for video transcoding, and it speeds most of my encodes up by almost 80%.

I installed this in my current version of Kubuntu.  But it seems to make my network traffic a little slow.  I understand that this is not something that is supposed to be installed in Ubuntu as of yet...

So my question for you is, could I install this kernel in a different distribution of Linux and get better operation and compatibility?

And... do I smell an Arch discussion coming?

---

### Post by Exodist on 2009-12-10
[www.kernel.org](www.kernel.org)

configure - compile - install - enjoy!

---

### Post by Shibblet on 2009-12-10
> **Exodist said:**
> [www.kernel.org](www.kernel.org)

configure - compile - install - enjoy!

Confused.

---

### Post by Xbehave on 2009-12-10
BFS is not in the mainline you need to patch the kernel yourself. There are also doubts over weather BFS is actually that good (benchmarks by the mainline team show it to be slower on many loads)

If you install your own kernel you may run into problems which people can't help much with, I've got zero help with my audio problems because it's hard for others to help when your running a custom setup.

If you want to run your own kernel with bfs
1) download the kernel from kernel.org, untar it and cd to the directory
2) patch it with the correct batch from the BFS site (you need a patch for your kernel version)
3) you can either configure the kernel youself with make menuconfig or make localmodconfig or copy the existing kernel from /boot/config-`uname -r` to .config then run make oldconfig
4) once you've configured the kernel run either
```
make && sudo make install && sudo make modules_install && sudo update-initramfs -ck 2.6.32
```
or make deb-pkg (i've not used that but it's listed in make help and gives you a deb which you can add remove more easily and probably avoid problems that i've run into.
5) you need to update grub to find the new kernel (probably just sudo update-grub)

---

### Post by Xbehave on 2009-12-10
alternatively try this ppa [https://launchpad.net/~darxus/+archive/bfsbfq](https://launchpad.net/~darxus/+archive/bfsbfq)

---

### Post by Shibblet on 2009-12-11
Let me start again.  I have installed a generic 2.6.32 kernel, and it's significantly faster.  The only exception is that my network traffic is slower.  

What can I do to get the best of both worlds?  I want the processing speed of the new kernel, but also want my network speed as well.

I had read about the BFS in the handbrake forums.  And then went to research it myself.  I thought it was going to be included in the 2.6.32 kernel.  Am I wrong there too?

---

### Post by mdmarmer on 2009-12-11
As I understand it, BFS is just a scheduler which is optional when you build a kernel.  BFS won't be included in any mainstream kernel -- it's too radical.

Liquorix kernels include BFS and are available here:

[http://techpatterns.com/forums/forum-34.html](http://techpatterns.com/forums/forum-34.html)

Liquorix kernels are based on zen sources [http://rahulthewall.wordpress.com/2009/08/31/zen-sources-the-way-kernels-should-be/](http://rahulthewall.wordpress.com/2009/08/31/zen-sources-the-way-kernels-should-be/)

I have not tried them with Ubuntu.  On Debian, these kernels run fast and very well.  I haven't had any networking problems.  I'm not able to use remastersys with these kernels.  Other than that I think they are excellent.  I do use the future repository which has the newest (i.e. less tested) liquorix kernels.

Mike

---

