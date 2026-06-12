---
title: "Poor desktop response under CPU load [9.10 Karmic]"
date: 2009-10-29
forum: Testimonials &amp; Experiences
---

### Post by oyvinst on 2009-10-29
Hi,

Karmic's been working pretty well since I installed the RC. But there are some really annoying issues, as always ... One of them is interactivity in the CPU-scheduler/2.6.31-kernel shipped with Karmic. What happened to it and where did it go ? Response goes down the drain totally just by compiling a large Java project. I'm a developer and I constantly compile large Java-projects. Easily reproducible on even a quad-core 8GB 64bit machine and fast graphics card. Something regressed here, since this was never a big problem in Jaunty. I now have to renice Xorg to -20 to get acceptable GUI response if there is load. I thought those sort of work-arounds belonged in the past ? Does anyone else have this problem ? Try starting one or two "perl -e 'while(1){}'" in a couple of terminals and then do stuff with Compiz. It utterly sucks compared to the behaviour and response in Ubuntu Jaunty :(. Linux will conquer the desktop any day, now.

Regards,
Øyvind

---

### Post by jdrodrig on 2009-11-01
just wondering, which graphics card are we talking about? do you know if the driver has changed recently? can you rollback to a previous driver and check?

---

### Post by oyvinst on 2009-11-03
> **jdrodrig said:**
> just wondering, which graphics card are we talking about? do you know if the driver has changed recently? can you rollback to a previous driver and check?

Hi, this probably applies to any graphics card/driver. The problems seems to be that Xorg isn't scheduled aggresively enough by kernel (or it seems to not get any priority advantage). I can reproduce both on a quad-core system with nvidia proprietary driver (GeForce 8600GT) and on my laptop (dual-core), which has an ATI X1400 mobile and using radeon driver.

One can always work around these problems by using nice-values, but I don't want to always nice down all the background jobs I run, that gets old really fast. The kernel should schedule things so interactive processes respond quickly, without the user doing anything special. Otherwise, the desktop experience will suffer. I couldn't care less if a background compilation takes 5 seconds longer, if that means my system remains snappy while it's running.

---

### Post by oyvinst on 2009-11-03
Oh, and I don't just complain, I filed a bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/463894](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/463894) . :p Let's see what happens, maybe the kernel team will respond, and the issue can be resolved..

---

### Post by ukripper on 2009-11-03
So many instances already open for similar issue on launchpad.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/448367](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/448367)
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/407309](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/407309)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati)

I am certain developers are working hard to rectify them. Please be patient.

---

