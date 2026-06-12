---
title: "Making Ubuntu faster/Vector Linux"
date: 2006-12-04
forum: The Cafe
---

### Post by Dafydd on 2006-12-04
Hi,
I like Ubuntu Linux (6.10) but how can I make it work faster? After using my computer for several hours, opening word docs, listening to radio online, pdf, firefox etc, it works slooooow (I have 512 mb of ram).

Are there any tricks to speed it up? Perhaps a simple profile with only the basics?

I also just started using Vector Linux which is much lighter and faster. The only problem is that I'm not sure how to customize it and the glsapt (synaptic equivalent) doesn't have reliable repositories (so far)...

Any ideas

Dafydd

---

### Post by renzokuken on 2006-12-04
i guess one way to speed it up would be to use a lightweight desktop manager like fluxbox or IceWM.

another way is to use the correct kernel for your processor. let us know what your processor is and we can tell you how to get the correct one.

do you have a grafix card? if so, the correct drivers will speed up desktop animations and such.

apart from that there isnt a HUGE amount you can do, just little tweaks here and there ..... from what i understand anyway

---

### Post by greggh on 2006-12-04
> **renzokuken said:**
> 
another way is to use the correct kernel for your processor. let us know what your processor is and we can tell you how to get the correct one.

I thought I read that starting with 6.10 Ubuntu has moved away from using different kernel versions. I read somewhere that they're using just one patched 386 kernel and calling it "generic".

---

### Post by renzokuken on 2006-12-04
really?? that sucks.

surely other kernels are available in the repos. i dont know personally cos im using dapper and so i was easily able to get the k7 kernel.

oh well, i suppose the way to find out Dafydd is to fire up synaptic and search for other linux kernels and see what comes up.

EDIT: greggh is spot on, my mistake, there is only one kernel for edgy and it already has optimisations for smp and k7 and the rest,

---

### Post by PrinceArithon on 2006-12-04
I thought there was 2.  Mine sure isn't the generic one, but I could set it up if I want through synaptic.

Anyway when you talk about the computer being slow, do you mean the whole system or just the internet??

---

### Post by angkor on 2006-12-04
I didn't do a fresh install of Edgy so I don't know what the default is but as far as I can tell there are still two different types of kernels available:

```
 apt-cache search linux-image
alsa-base - ALSA driver configuration files
linux-image-2.6.17-10-386 - Linux kernel image for version 2.6.17 on i386
linux-image-2.6.17-10-generic - Linux kernel image for version 2.6.17 on x86/x86_64
linux-image-2.6.17-10-server - Linux kernel image for version 2.6.17 on x86/x86_64
linux-image-2.6.17-10-server-bigiron - Linux kernel image for version 2.6.17 on BigIron Server Equipment
**linux-image-386 - Linux kernel image on 386.**
linux-image-686 - Obsoleted by: linux-image-generic
linux-image-debug-2.6.17-10-386 - Linux kernel debug image for version 2.6.17 on i386
linux-image-debug-2.6.17-10-generic - Linux kernel debug image for version 2.6.17 on x86/x86_64
linux-image-debug-2.6.17-10-server - Linux kernel debug image for version 2.6.17 on x86/x86_64
linux-image-debug-2.6.17-10-server-bigiron - Linux kernel debug image for version 2.6.17 on BigIron Server Equipment
**linux-image-generic - Generic Linux kernel image**
linux-image-k7 - Obsoleted by: linux-image-generic
linux-image-server - Linux kernel image on Server Equipment.
linux-image-server-bigiron - Linux kernel image on BigIron Server Equipment.
linux-686-smp - Obsoleted by: linux-image-generic
linux-image-kdump - Linux Kernel Crash Dump Image.
```

---

### Post by shining on 2006-12-04
> **Dafydd said:**
> Hi,
I like Ubuntu Linux (6.10) but how can I make it work faster? After using my computer for several hours, opening word docs, listening to radio online, pdf, firefox etc, it works slooooow (I have 512 mb of ram).

Are there any tricks to speed it up? Perhaps a simple profile with only the basics?

I also just started using Vector Linux which is much lighter and faster. The only problem is that I'm not sure how to customize it and the glsapt (synaptic equivalent) doesn't have reliable repositories (so far)...

Any ideas

Dafydd

Which desktop environment do you use in Vector, and which one in Ubuntu?

---

### Post by Engnome on 2006-12-04
```
jerry@edgy5:~$ uname -a
Linux edgy5 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 **i686** GNU/Linux
```

The generic kernel is the 686 kernel.

---

### Post by mips on 2006-12-04
What desktop manager do you use in vector linux ?

[http://www.ubuntuforums.org/showthread.php?t=277090](http://www.ubuntuforums.org/showthread.php?t=277090)
[http://www.ubuntuforums.org/showthread.php?t=298818](http://www.ubuntuforums.org/showthread.php?t=298818)
[http://www.ubuntuforums.org/showthread.php?t=189192](http://www.ubuntuforums.org/showthread.php?t=189192)
[http://ubuntuforums.org/showthread.php?t=197](http://ubuntuforums.org/showthread.php?t=197)
[http://ubuntuforums.org/showthread.php?t=45810](http://ubuntuforums.org/showthread.php?t=45810)

You could also install a lightweight windows manager like Fluxbox, IceWm etc, whichever you prefer.

Prelink, Preload, Profile, hdparm are things you could also look into.

---

### Post by Dafydd on 2006-12-06
thanks,
i'll try a different lightweight windows manager (but gnome is great for being mostly in Welsh!).
how do i find out what processor i have?
my computer actually crashed today! i had too many things going at once.
I like Vector - not sure what windows manager but it is sort of kde-ish but lighter.
i suppose there are things i can do as well (run abiword and not openoffice, change the windows manager, try and find out about tweaks.)

i like the principle of vector. Anyone tried out an ubuntu lite or mini distro?

Dafydd

---

### Post by qalimas on 2006-12-06
That definitely explains why I haven't been able to make my computers faster by installing the 686 kernel.. that sucks, a lot.  If you are willing to change distros (and learn, a lot) you could try Arch.  In my experience, it's the fastest operating system I have ever used.

---

### Post by Dafydd on 2006-12-11
> **qalimas said:**
> That definitely explains why I haven't been able to make my computers faster by installing the 686 kernel.. that sucks, a lot.  If you are willing to change distros (and learn, a lot) you could try Arch.  In my experience, it's the fastest operating system I have ever used.

kernel stuff is too complicated for my brain, but i think the latest vector linux uses the same kernel.

learnt one trick: with openoffice go to options etc choose memory and increase the memory. at least that opens it faster.

i've tried vector linux out a little more and like it. the only thing is that it is more difficult for me to configure - and it is not in welsh. ubuntu is great on localizaion (there's even an esperanto version). the welsh lang support beats windows

dafydd

---

### Post by kerry_s on 2006-12-11
Vector Linux uses xfce4, you can install xubuntu-desktop or just xfce4(base) & the parts you want.

The best way to get speed is to do a custom install,aka: base install build up. That way you control whats installed.

Since you already have a full install, try using synaptic to remove stuff you don't need. Also using lighter alternatives can help it feel faster,like using abiword instead of openoffice.

There are so many options in linux, its just a matter of what fits your needs. I would suggest you try different things till you find what you like. I learned to do the custom installs & i haven't had a full install in like 6 months, i now make the system fit me, instead me trying to learn the system.-> [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by K.Mandla on 2006-12-11
Ditto that. kerry_s is right. If you want to get Ubuntu running the absolute fastest you can, start at the bottom with a server installation (or even less) and work your way up. You'll learn a lot in the process too.

---

### Post by .t. on 2006-12-11
The decision to switch the the generic kernel was based on benchmark data that showed that the processor-specific kernels did not prove much faster, and in some cases slowed the system down.

---

### Post by zgornel on 2006-12-11
> **Engnome said:**
> ```
jerry@edgy5:~$ uname -a
Linux edgy5 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 **i686** GNU/Linux
```

The generic kernel is the 686 kernel.
Actually, that is the architecture of the system the kernel is running onto. The generic kernel is optimized for 586 with smp support. That's what I've seen from the config.

---

### Post by finferflu on 2006-12-13
I'm getting a much faster experience with KDE, I suggest you to try Kubuntu. It runs a lot faster for me. It could be better, but still, way better than before. I still have to install drivers for my ATI card, and see if that improves the speed...

---

### Post by DoctorMO on 2006-12-13
Ubuntu suffered from a memory leak with evolution mail, even though I was using thunderbird. 1GB ram, 700MB used by evolution after 1 week of being switched on and used. Firefox is also known to be a memory hog too, try switching to swiftfox.

512MB should well be enough for an ubuntu machine, unless your going to be opening up massive amounts of things, but sometimes memory problems aren't reported because people have really big machines and tell anyone suffering from problems on lower specified machines to upgrade or use Xfc. :-/

---

### Post by justin whitaker on 2006-12-13
I'm surprised that noone suggested recompiling the kernel for his system, or compiling a stock kernel, or even using the -CK patch. None of these are particularly hard to do, just time consuming, and  fraught with peril and adventure. :mrgreen:

---

### Post by DoctorMO on 2006-12-13
Best thing to do is to use top, and learn how to use top so you can look for processor and memory intensive applications and decide if you need them or not; you can also find problems.

---

### Post by Sef on 2006-12-14
> Firefox is also known to be a memory hog too

Acutally it is not a memory hog.  What is a memory hog is some of the extentions that are added to it.

---

### Post by zgornel on 2006-12-14
> **justin whitaker said:**
> I'm surprised that noone suggested recompiling the kernel for his system, or compiling a stock kernel, or even using the -CK patch. None of these are particularly hard to do, just time consuming, and  fraught with peril and adventure. :mrgreen:
Or better still, the beyond patch ([http://iphitus.loudas.com/beyond.html](http://iphitus.loudas.com/beyond.html)) ;)

---

### Post by shining on 2006-12-14
> **justin whitaker said:**
> I'm surprised that noone suggested recompiling the kernel for his system, or compiling a stock kernel, or even using the -CK patch. None of these are particularly hard to do, just time consuming, and  fraught with peril and adventure. :mrgreen:

Probably because using lighter applications generally has a much bigger impact than just using a different kernel.
The first thing to check before comparing 2 distributions is that you are running the same services and applications. When that's done, it's very likely the differences will be minimal.
These differences may be partly explained by a different kernel. But it's certainly not the first thing to check.

---

