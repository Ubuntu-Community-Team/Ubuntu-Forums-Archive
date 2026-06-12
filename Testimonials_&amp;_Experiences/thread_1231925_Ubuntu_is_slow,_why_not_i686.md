---
title: "Ubuntu is slow, why not i686?"
date: 2009-08-05
forum: Testimonials &amp; Experiences
---

### Post by ngsupb on 2009-08-05
Ubuntu is a great distro! I am very happy with it. Works awesome without any problem (almost), but the BIG hidden problem of Ubuntu is i386 optimization.(Someone uses ubuntu on that kind of cpu?? )

After I tried how fast is Arch Linux with the same configuration and applications, I recognized how much Ubuntu losses.

Ubuntu is my first distro, but I can't use it anymore after working on Arch for a few weeks. When I start Ubuntu it appears slower for me. 
DE responds slower...
**Developers should think about it.**

---

### Post by kerry_s on 2009-08-05
you can't compare a full ubuntu to arch, arch is a do it yourself install, you can install ubuntu base & build up from there then you can compare the speed. ubuntu is built for everyone, arch is custom you make it to your needs, do a custom ubuntu install.

---

### Post by jocko on 2009-08-05
> **ngsupb said:**
> Ubuntu is a great distro! I am very happy with it. Works awesome without any problem (almost), but the BIG hidden problem of Ubuntu is i386 optimization.(Someone uses ubuntu on that kind of cpu?? )
What do you mean with i386 optimisation?
The -generic kernel in ubuntu is compiled with run-time detection to detect which cpu it's using and use the relevant optimisations.
32 bit ubuntu has an optional -386 kernel, which is there *only* for those that have Pentium II ("586") / amd k6 or older processors.
So, the -generic kernel is optimised for pentium III ("686") / amd duron (k7) or better processors.

---

### Post by ngsupb on 2009-08-05
kerry_s, I optimized Ubuntu as much as possible. Even compiled my own kernel, disabled all unnecessary deamons, start up applications, prelink, preload. tweaking boot scripts...what else?
Actually spent a lot of time into optimizations, what I didn't with Arch and it works faster.

Do you want to say that applications with i386 optimization can work on the same performance as i686?

---

### Post by ngsupb on 2009-08-05
jocko, it isn't a kernel question, which can be recompilied. 
All other packages are build with i386

---

### Post by jocko on 2009-08-05
> **ngsupb said:**
> jocko, it isn't a kernel question, which can be recompilied. 
All other packages are build with i386
Where do you get that information?
Edit: I've done some research and found that you are right.

But all other packages can be recompiled as well... The sources are in the repos.
And there's even [apt-build]("http://ubuntuforums.org/showthread.php?t=1030272&") for those that want to optimize individual packages (or the entire system).

---

### Post by ngsupb on 2009-08-05
jocko, [http://mirror.beyondi.org/ubuntu-releases/jaunty/](http://mirror.beyondi.org/ubuntu-releases/jaunty/)
can you find me other installation rather than i386 and amd64? :D

I can't find anything about i686 except of ideas to make it.

Ubuntu isn't intended to copile from sources. I would install Gentoo for that, but it is too much time consuming. That is why I would prefer something prebuild.

---

### Post by ngsupb on 2009-08-05
> **jocko said:**
> 
And there's even [apt-build]("http://ubuntuforums.org/showthread.php?t=1030272&") for those that want to optimize individual packages (or the entire system).

It is interesting thing though
Even if it works... (judging from that post it doesn't )
Recompilation will take a lot of time :(

---

### Post by dmizer on 2009-08-05
> **ngsupb said:**
> Ubuntu is a great distro! I am very happy with it. Works awesome without any problem (almost), but the BIG hidden problem of Ubuntu is i386 optimization.(Someone uses ubuntu on that kind of cpu?? )

After I tried how fast is Arch Linux with the same configuration and applications, I recognized how much Ubuntu losses.

Ubuntu is my first distro, but I can't use it anymore after working on Arch for a few weeks. When I start Ubuntu it appears slower for me. 
DE responds slower...
**Developers should think about it.**

Because then there would be no backward compatibility.

> **PeterJS said:**
> i386 includes everything in the x86 family [down] to and including the Intel 80386 processor, the 80386 was the last Intel processor not to implement any extensions to x86 op codes. i686 is the modern x86 variant designed for Pentium chips that includes mmx, 3dnow, sse, and all those other fun extensions people have come to rely on. i386 code will certainly run on i686 hardware (but obviously not the other way around), a large portion of precompiled binaries are built i386 simply to allow them to run on older hardware.

Also see:
```
uname -m
```

And:
> **az said:**
> By default you get the generic kernel.

The 386 and 686 kernels are packaged and you can install them, but for the past few years there has not been any point.  The generic kernel detects the CPU options at boot time.  Specifying the 386 or 686 CPU type at compile time is not necessary anymore, which is why the generic kernel is used.

Which means that Ubuntu IS optimized for i686, it's just also built with backwards compatibility.

---

### Post by 3rdalbum on 2009-08-05
The 64-bit edition is optimised for more recent processors, as there aren't any ancient x86_86 processors.

---

### Post by ngsupb on 2009-08-05
> **dmizer said:**
> 
Which means that Ubuntu IS optimized for i686, it's just also built with backwards compatibility.

You are talking about the kernel.
I am talking about all packages in Ubuntu.

---

### Post by dmizer on 2009-08-05
No, I was talking about both the kernel AND the packages.

As indicated in the quote by PeterJS, the i386 compile incorporates all the necessary optimizations for i686 as well as i586, i486, and i386 so that the packages are backwards compatible for older hardware. So, when the kernel boots to i686, the i386 compiled packages make 100% use of the i686 extensions.

If the packages were i386 only and the running kernel was i686, then the packages wouldn't run.

---

### Post by kerry_s on 2009-08-05
> **ngsupb said:**
> kerry_s, I optimized Ubuntu as much as possible. Even compiled my own kernel, disabled all unnecessary deamons, start up applications, prelink, preload. tweaking boot scripts...what else?
Actually spent a lot of time into optimizations, what I didn't with Arch and it works faster.

Do you want to say that applications with i386 optimization can work on the same performance as i686?

dude trying to tweak a full install & doing a custom install is totally different. a custom install you would do the same way as you do in arch. you install a base which gives you a cli system, just like arch, then you apt-get what you want, just like arch except theres no manual setup.

i left arch a couple of months to go back to debian, i use a custom debian install on 450mhz 256mb ram & i can tell you there is no really noticeable difference other than after you install something it just works, no manual needed. 

i use the net installer, similar to arch:
[http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/)

at the part where you choose your packages just uncheck desktop & standard, that will give you a base system.
after that you just apt-get what you want.
example:
**apt-get install xorg gdm xfce4**

---

### Post by ngsupb on 2009-08-07
> **dmizer said:**
> No, I was talking about both the kernel AND the packages.

As indicated in the quote by PeterJS, the i386 compile incorporates all the necessary optimizations for i686 as well as i586, i486, and i386 so that the packages are backwards compatible for older hardware. So, when the kernel boots to i686, the i386 compiled packages make 100% use of the i686 extensions.

If the packages were i386 only and the running kernel was i686, then the packages wouldn't run.

So according to your conclusion performance on Ubuntu should be something similar to Arch because Ubuntu is running like i686 optimized. Right?

I think this assumption is wrong.

Even Ubuntu isn't slow from the first look, it works fine in general, but I noticed how it is slow after trying Arch.

Lets see some numbers to confirm my "feeling" from the first post about  the performance difference.
I have ran some tests yesterday on my PC from phoronix-test-suite:

1) kernel compilation, Ubuntu was running on the default one which comes with Ubuntu:
[_Kernel compilatoin Arch - Ubuntu_]("http://global.phoronix-test-suite.com/?k=profile&u=vetala-16535-24518-24993")

I was very surprised to see that:confused:
Nothing was running on Ubuntu and the same for Arch. Just the test after fresh boot.

2) Other tests:

hdd/ram/cpu:
_[http://global.phoronix-test-suite.com/index.php?k=profile&u=vetala-12938-14438-23806](http://global.phoronix-test-suite.com/index.php?k=profile&u=vetala-12938-14438-23806)_


It is just some tests, but you can believe me that DE and other things are faster. With the identical applications and configuration...
 
Well, it is hard to see that Ubuntu is optimized...

**Ubuntu is fast as a snail** :P

---

### Post by dmizer on 2009-08-07
> **ngsupb said:**
> So according to your conclusion performance on Ubuntu should be something similar to Arch because Ubuntu is running like i686 optimized. Right?

I think this assumption is wrong.
I did not say that Ubuntu is or should be as fast as Arch. I am just pointing out that your reasoning is incorrect. Ubuntu is not slower than Arch because Ubuntu programs are not i686. There are many reasons for the difference in speed, but that is not one.

---

### Post by ngsupb on 2009-08-07
> **dmizer said:**
> I did not say that Ubuntu is or should be as fast as Arch. I am just pointing out that your reasoning is incorrect. Ubuntu is not slower than Arch because Ubuntu programs are not i686. There are many reasons for the difference in speed, but that is not one.

Wrong.  It is one of the reason too.

i386 packages just are **compatible (not optimized)** with i686 and  don't include it's features, so they can run on i686. That is how ubuntu is compiled.  


> a large portion of precompiled binaries are built i386 simply to allow them to run on older hardware.

---

### Post by binbash on 2009-08-07
> **ngsupb said:**
> So according to your conclusion performance on Ubuntu should be something similar to Arch because Ubuntu is running like i686 optimized. Right?

I think this assumption is wrong.

Even Ubuntu isn't slow from the first look, it works fine in general, but I noticed how it is slow after trying Arch.

Lets see some numbers to confirm my "feeling" from the first post about  the performance difference.
I have ran some tests yesterday on my PC from phoronix-test-suite:

1) kernel compilation, Ubuntu was running on the default one which comes with Ubuntu:
[_Kernel compilatoin Arch - Ubuntu_]("http://global.phoronix-test-suite.com/?k=profile&u=vetala-16535-24518-24993")

I was very surprised to see that:confused:
Nothing was running on Ubuntu and the same for Arch. Just the test after fresh boot.

2) Other tests:

hdd/ram/cpu:
_[http://global.phoronix-test-suite.com/index.php?k=profile&u=vetala-12938-14438-23806](http://global.phoronix-test-suite.com/index.php?k=profile&u=vetala-12938-14438-23806)_


It is just some tests, but you can believe me that DE and other things are faster. With the identical applications and configuration...
 
Well, it is hard to see that Ubuntu is optimized...

**Ubuntu is fast as a snail** :P


Dmizer made a well explanation to the situation.And believe me gentoo is 3x faster than Arch Linux if you know optimization.But this is not the thread title.You are ruining the title.

---

### Post by ngsupb on 2009-08-07
> **binbash said:**
> And believe me gentoo is 3x faster than Arch Linux if you know optimization. 
Not 3x faster, much less, but faster. And it doesn't worth to spend so much time into it.

After all, I just wish that the developers pay some attention into it to make Ubuntu performance better. 

It won't happen if don't talk about it :P

---

### Post by dmizer on 2009-08-07
> **ngsupb said:**
> After all, I just wish that the developers pay some attention into it to make Ubuntu performance better.

If you are interested in performance, Ubuntu can be made to perform very well. It takes quite a bit of effort, but it's not like you can't compile a custom kernel for Ubuntu. Ubuntu developers are interested in making Ubuntu usable for a wide and generally non-technical user base. Why should Ubuntu developers concentrate on making Ubuntu as fast as Arch ... when Arch does that perfectly well on its own?

Besides, Ubuntu doesn't have to be as fast as Arch, it just needs to be faster than Vista. ;)

---

### Post by moster on 2009-08-08
> **ngsupb said:**
> 
1) kernel compilation, Ubuntu was running on the default one which comes with Ubuntu:
[_Kernel compilatoin Arch - Ubuntu_]("http://global.phoronix-test-suite.com/?k=profile&u=vetala-16535-24518-24993")

I was very surprised to see that:confused:
Nothing was running on Ubuntu and the same for Arch. Just the test after fresh boot.

2) Other tests:

hdd/ram/cpu:
_[http://global.phoronix-test-suite.com/index.php?k=profile&u=vetala-12938-14438-23806](http://global.phoronix-test-suite.com/index.php?k=profile&u=vetala-12938-14438-23806)_
[/B] :P
You cannot compare apples with pears. You compare different kernel and different GCC compilers. Ubuntu is not rolling distro. Arch will always be faster, well, maybe not if some regression in kernel occur.

It would be interesting if you have will, to test it against Ubuntu 9.10 alpha :)

---

