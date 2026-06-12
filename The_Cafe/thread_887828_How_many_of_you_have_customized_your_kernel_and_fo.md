---
title: "How many of you have customized your kernel and for what purpose?"
date: 2008-08-12
forum: The Cafe
---

### Post by kernelhaxor on 2008-08-12
I believe that the kernel you get out of the box with Ubuntu is already optimized for the average user .. but I know some of you might have customized it for some specific functionality .. 
Wht is it and how hav u modified the kernel (not the code details but jus a top level description wud be good)?

---

### Post by kernelhaxor on 2008-08-12
Regarding myself, I havent modified the kernel as I never felt the need to

---

### Post by Dr Small on 2008-08-12
I haven't. The only times I ever did, the system wouldn't boot. I think I need to have a spare machine to test it on and play with it before I would try it on my main system :D

---

### Post by FuturePilot on 2008-08-12
I've never touched kernel code before. It works, what more is there to do? :)

---

### Post by Canis familiaris on 2008-08-12
> **FuturePilot said:**
> I've never touched kernel code before. It works, what more is there to do? :)

+1

Though the geek part of me urges on to do so.

---

### Post by Masoris on 2008-08-12
I am not a geek. You should Make your Firefox cute first:
[http://ubuntuforums.org/showthread.php?t=852020](http://ubuntuforums.org/showthread.php?t=852020)

---

### Post by logos34 on 2008-08-12
I compiled my own (from the most recent 2.6.26.2) as a learning exercise.  But I found in addition to graphics card frustrations that the Hardy stock -generic (or in my case -rt-generic ubuntustudio) kernel is pretty good already.  

But it's great to know you can make your own kernel anytime--no more fears about hardware support when you can simply compile a new kernel with the required module support

---

### Post by lukjad on 2008-08-12
I have the kernel from Ubuntu Studio that is pre=adjusted to make sound and video go straight to the processor. Does that count?

---

### Post by cardinals_fan on 2008-08-12
I compiled a custom kernel on my new SliTaz install just this morning :)

---

### Post by logos34 on 2008-08-12
> **lukjad007 said:**
> I have the kernel from Ubuntu Studio that is pre=adjusted to make sound and video go straight to the processor. Does that count?

like me you're running the standard studio kernel--i.e. real-time ('-rt'), low-latency, kernel, which means it's configured so that system-level services can be involuntarily preempted (necessary when doing professional audio recording/editing/mixing and video production).

---

### Post by Barrucadu on 2008-08-12
I did once, it shaved a few seconds off booting as I trimmed out a lot of unrequired modules. I can't be bothered again though.

---

### Post by lukjad on 2008-08-12
OK. So the answer is No then.

---

### Post by Keyper7 on 2008-08-12
Back in the Feisty days, I needed to compile a vanilla 2.6.22 kernel to get proper hibernation.

Then came Gutsy/Hardy and hibernation just worked. :)

---

### Post by spupy on 2008-08-12
Gentoo. Enough said. :)

I now have a vanilla 2.6.24, compiled 2-3 months ago.

---

### Post by ghindo on 2008-08-12
I wouldn't even know how to start customizing a kernel.

---

### Post by K.Mandla on 2008-08-12
I run 2.6.26.2 right now, stripped down to nothing and customized to the machine. I have that on three of the four machines I use. 

Generally speaking I get a considerable improvement in performance, particularly on old machines. The tradeoff is about 20 minutes of my life to compile a kernel (at 1Ghz, longer for slower machines).

To me it's worth it. To others, it's not. The choice is personal.

If you want to do the same thing in Ubuntu, this is a good place to start. ...

[http://ubuntuforums.org/showthread.php?p=5432160#post5432160](http://ubuntuforums.org/showthread.php?p=5432160#post5432160)

Results will vary, but a stock Gnome Ubuntu system performed [much quicker for me]("http://kmandla.wordpress.com/2008/07/29/finally-grub-to-gnome-in-under-a-minute/") when I gave it a custom kernel.

---

### Post by logos34 on 2008-08-12
> **K.Mandla said:**
> The tradeoff is about 20 minutes of my life to compile a kernel (at 1Ghz, longer for slower machines).

Really?  Wow, it takes me up to an hour on mine, 64-bit Sempron 1.6 GHz@2.0 GHz (user time: 45 min; sys time:58 min.).  Must be because I'm using the option 'INSTALL_MOD_STRIP=1' to keep the folder size down...I've also stripped out all unecessary modules and stuff in make xconfig...hmm

---

### Post by jayson.rowe on 2008-08-12
I have a box running VMware Server on Ubuntu Server 6.06 w/ a custom kernel I compiled w/ a 1000Hz Tick rate, and I changed the optimizations from Generic to my specific processor.

Only changes I made, but they make a huge difference in performance (more the 1000Hz w/ VMware than the CPU optimizations).

---

### Post by stmiller on 2008-08-12
Two settings make a drastic improvement for desktop users:

* low-latency desktop
* 1000Hz tick rate

All audio/video playback is much better. DVD playback is smoother. All major audio and video apps work much better.

Why Ubuntu, a 'desktop' oriented distro does not do this by default baffles me...  The default kernel in Ubuntu is configured more for a server.

Edit: BTW: you can apt-get install kernel-rt to install a pre-configured low-latency kernel.

Some newer digital tv tuners, webcams and such are supported in newer kernels. Also there are wifi card improvements as far as hardware support in most every major kernel release.

---

### Post by logos34 on 2008-08-13
> **stmiller said:**
> two settings make a drastic improvement for desktop users:

* low-latency desktop
* 1000hz tick rate

all audio/video playback is much better. Dvd playback is smoother. All major audio and video apps work much better.

Why ubuntu, a 'desktop' oriented distro does not do this by default baffles me...  The default kernel in ubuntu is configured more for a server.


+1

---

### Post by K.Mandla on 2008-08-13
> **logos34 said:**
> Really?  Wow, it takes me up to an hour on mine, 64-bit Sempron 1.6 GHz@2.0 GHz (user time: 45 min; sys time:58 min.).  Must be because I'm using the option 'INSTALL_MOD_STRIP=1' to keep the folder size down...I've also stripped out all unecessary modules and stuff in make xconfig...hmm
Yup, I trim almost everything out that isn't absolutely necessary though.

[http://kmandla.wordpress.com/2008/06/08/howto-16-second-boot-on-550mhz-celeron-with-crux/](http://kmandla.wordpress.com/2008/06/08/howto-16-second-boot-on-550mhz-celeron-with-crux/)

It saves time if I'm not compiling software for hardware I'll never use. :)

---

### Post by kernelhaxor on 2008-08-13
> **K.Mandla said:**
> [..]

Will try to mess in tht direction.  Thanks for the input!

> **stmiller said:**
> Two settings make a drastic improvement for desktop users:

* low-latency desktop
* 1000Hz tick rate

All audio/video playback is much better. DVD playback is smoother. All major audio and video apps work much better.


Interesting.  Will check that out.  Thanks!

---

### Post by ghindo on 2008-08-14
Huh.  I just tried compiling my own kernel using the method K.Mandla linked to and when I rebooted, my wireless didn't work.  :(  Oh well.  Maybe I'll try compiling a vanilla kernel instead of one from the repos.

By the way, could somebody explain low-latency kernels for me?  I understand that it helps with audio and video playback and production, but I don't understand how they do it or better yet why low-latency kernels aren't the default.

---

