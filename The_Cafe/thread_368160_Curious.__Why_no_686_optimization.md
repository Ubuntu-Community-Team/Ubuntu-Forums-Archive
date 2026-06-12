---
title: "Curious.  Why no 686 optimization?"
date: 2007-02-22
forum: The Cafe
---

### Post by darweth on 2007-02-22
Please don't take this the wrong way.  I love Ubuntu and will continue to use it.  I am just curious. :) 

I understand why there is a 386 build.  To be as compatible with as much of the world as possible.  But why isn't there also a 686 build?  I would think the Ubuntu community is large enough to support all possible desires.  I have used Arch Linux and other distros and the speed advantage is no illusion.

---

### Post by ComplexNumber on 2007-02-22
probably to cater to the lowest common denominator.

---

### Post by ice60 on 2007-02-22
i love ubuntu to be as fast as arch, if i knew what i was doing with linux i'd do it.

---

### Post by MetalMusicAddict on 2007-02-22
This was always weird to me as well. Ive seen the threads about it but what Im still fuzzy on is how it would adversely effect users on the lower end? :-k 

I just started to play with [Foresight Linux]("http://www.foresightlinux.org/") and it defiantly "snappier" than Ubuntu. Nothing insane but defiantly noticeable. Its 686 optimized.

---

### Post by russell.h on 2007-02-22
[http://www.ubuntuforums.org/showthread.php?t=353128](http://www.ubuntuforums.org/showthread.php?t=353128)

---

### Post by Jucato on 2007-02-23
From the Ubuntu IRC:
> Background to the decision to replace -686, k7 and -smp kernels with -generic can be found here [https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html](https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html) (the -386 kernel is still available if needed)


[https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html](https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html)

---

### Post by 3rdalbum on 2007-02-23
I doubt it's the 686 optimisation that makes the other distros faster. It's probably because Ubuntu enables a lot of local services by default that most people don't need.

---

### Post by The Noble on 2007-02-23
The generic kernel is modular, so that means that the kernel will detect what it can use, and use it.  In essence, you are using something equivalent to a custom kernel once you boot. Boot time may suffer a little, but your overall speed should be comparable to a custom kernel. You are getting the idea that arch is fast because it has so few services to run. With some serious hacking, you could get ubuntu just as fast as arch, but i mean _serious_. Also, it is important to note that arch is using a much more up to date kernel, and with progress comes speed boosts. 

By the way, if you want to actually use the 686 optimizations, you may have to recompile gnome, firefox, Xserver, and almost everything you will ever use to even see the speed differences.

---

### Post by picpak on 2007-02-23
lol, I've had the exact opposite happen with me. With the exception of Java, I think Ubuntu is faster than Arch. It even starts up faster.

---

### Post by prizrak on 2007-02-23
CPU optimizations (save for 64bit and SMP) are pretty much useless, distro's vary in speed for many reasons and architecture optimizations don't even figure into it. I for one have used both 386, K7 and 686 kernels on previous Ubuntu releases and seen no noticeable difference. The only difference I have ever seen was installing a 686 onto a Pentium M which decreased the performance considerably compared to 386. 

If you really want to test speed differences get Gentoo and do a full 386 build and then a full 686 build on the same machine and see if there is any difference. 

The biggest absolute performance boost that you will see in any distro is changing your WM. Ubuntu with Gnome will always be slower than Ubuntu with XFCE or Fluxbox.

---

