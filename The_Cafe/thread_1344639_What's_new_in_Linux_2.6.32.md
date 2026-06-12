---
title: "What's new in Linux 2.6.32"
date: 2009-12-03
forum: The Cafe
---

### Post by u.b.u.n.t.u on 2009-12-03
This is grand!

"Linus Torvalds has released version 2.6.32 of the Linux kernel. Like it's predecessors, the Linux main development line brings thousands of improvements to the new kernel release such as KMS (kernel-based mode setting), 3D support for series 2000, 3000 and 4000 Radeon graphics card and KSM (Kernel shared memory or kernel samepage merging) which reduces memory use when running identical virtual machines. Devtmpfs allows for booting without Udev and lets the Linux kernel run faster."

[http://www.h-online.com/open/features/What-s-new-in-Linux-2-6-32-872271.html](http://www.h-online.com/open/features/What-s-new-in-Linux-2-6-32-872271.html)

...

"Linux 2.6.32 has been released on December 3rd 2009.

Summary: This version adds virtualization memory de-duplicacion, a rewrite of the writeback code which provides noticeable performance speedups, many important Btrfs improvements and speedups, ATI R600/R700 3D and KMS support and other graphic improvements, a CFQ low latency mode, tracing improvements including a "perf timechart" tool that tries to be a better bootchart, soft limits in the memory controller, support for the S+Core architecture, support for Intel Moorestown and its new firmware interface, run time power management support, and many other improvements and new drivers." 

[http://kernelnewbies.org/Linux_2_6_32](http://kernelnewbies.org/Linux_2_6_32)

---

### Post by Zoot7 on 2009-12-03
The incorporation of Alsa 1.0.21 is the main feature I've had my eye on.

---

### Post by u.b.u.n.t.u on 2009-12-03
> **Zoot7 said:**
> The incorporation of Alsa 1.0.21 is the main feature I've had my eye on.

What does that feature present?

I am very interested in KMS, kernel-based mode setting, getting full 3d functionality for Linux.

---

### Post by Zoot7 on 2009-12-03
> **u.b.u.n.t.u said:**
> What does that feature present?
The Creative X-Fi Alsa driver is the main thing I'm interested in. Granted there's a driver in 2.6.31 too, but I've found the Alsa 1.0.21 variant to be much better.
(I fetched my X-Fi from the Attic after Alsa 1.0.21 came out :) )

---

### Post by u.b.u.n.t.u on 2009-12-03
> **Zoot7 said:**
> The Creative X-Fi Alsa driver is the main thing I'm interested in. Granted there's a driver in 2.6.31 too, but I've found the Alsa 1.0.21 variant to be much better.
(I fetched my X-Fi from the Attic after Alsa 1.0.21 came out :) )

Advanced Linux Sound Architecture, sounds good, pun intended! :lolflag:

---

### Post by Xbehave on 2009-12-03
> **u.b.u.n.t.u said:**
> What does that feature present?

I am very interested in KMS, kernel-based mode setting, getting full 3d functionality for Linux.
Sorry to disappoint, but all KMS does is remove the flicker when you switch to ttys, it paves the way to some interesting features
(advanced power management (dynamic control of clocks etc..) &  running X without root privileges ) but DRI2 / RDR  is what paves the way to full 3D support in linux, they are needed for gallium3D which offers advanced 3D (OpenGL 1.5+, GLSL) via generic Mesa code means driver development will get faster and offers video decode acceleration & OpenCL support.

---

### Post by u.b.u.n.t.u on 2009-12-03
> **Xbehave said:**
> Sorry to disappoint, but all KMS does is remove the flicker when you switch to ttys, it paves the way to some interesting features
(advanced power management (dynamic control of clocks etc..) &  running X without root privileges ) but DRI2 / RDR  is what paves the way to full 3D support in linux, they are needed for gallium3D which offers advanced 3D (OpenGL 1.5+, GLSL) via generic Mesa code means driver development will get faster and offers video decode acceleration & OpenCL support.

KMS isn't the only good news on the graphics front. Quoted from the linked source first post.

"The kernel and its Direct Rendering Manager (DRM) will now offer 3D support and kernel-based mode setting (KMS) for AMD's series R600 and R700 GPUs. These are used in the Radeon series 2000, 3000 and 4000 models – which includes most of the Radeon graphics cards sold in the past couple of years as well as various AMD series 700 motherboard chip-sets. For the 3D support and KMS to function, however, suitable (developer) versions of Libdrm and Mesa 3D as well as Radeon graphics drivers for X.org need to be installed."

---

### Post by gradinaruvasile on 2009-12-03
For those who feel adventurous, here you can actually try it.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/)

Not for beginners! Despite these are in .deb format, you can encounter problems (video drivers et). Do not try it if u dont know your way in console/linux stuff.

---

### Post by handy on 2009-12-03
I run Arch, & an ATi HD2600Pro GPU.
In kernel .31 I have to turn KMS off, or I get the Linux black screen of death.

As far as the 3D support for the ATi GPUs is concerned, I think we will find that it is still a work in progress that will take at least a few more kernel & mesa versions before we have useful 3D for all of these ATi GPUs.  I hope I'm wrong of course. :)

Currently the ATi open-source drivers offer the best 2D available, they make the current catalyst 2D support look very bad in comparison.

I so look forward to being able to say the same thing about the open-source ATi drivers 3D ability.

Being able to kiss the pain in the rr's catalyst drivers goodbye is going to really be a cause for celebration.

---

### Post by pookiebear on 2009-12-03
> **handy said:**
> 

Being able to kiss the pain in the rr's catalyst drivers goodbye is going to really be a cause for celebration.

agreed

---

### Post by toupeiro on 2009-12-03
VMEM de-duplication!   hell yes!  I'm dying for this to hit Physical memory!  If you can only imagine the mileage you can get from something like that in virtualization environments...

---

### Post by phrostbyte on 2009-12-03
Feature list: 

[http://kernelnewbies.org/Linux_2_6_32](http://kernelnewbies.org/Linux_2_6_32)

---

### Post by Praxicoide on 2009-12-03
> **gradinaruvasile said:**
> For those who feel adventurous, here you can actually try it.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/)

Not for beginners! Despite these are in .deb format, you can encounter problems (video drivers et). Do not try it if u dont know your way in console/linux stuff.

That was quick!

---

### Post by u.b.u.n.t.u on 2009-12-03
> **phrostbyte said:**
> Feature list: 

[http://kernelnewbies.org/Linux_2_6_32](http://kernelnewbies.org/Linux_2_6_32)

This link was already given in the first post.

---

### Post by Malta paul on 2009-12-03
Thanks U.B.U.N.T.U. for the info. I have just install the Kernel in 9.04 on my 64 bit system, It works great (not using 9.10 yet, as my canon printer will not work due too 'I think' that the new cups version, zaps my print driver).
After installation I only had to reinstall the latest NVIDIA graphic driver using the terminal. 
Now I am happy Penguin again  ;)

---

### Post by gnomeuser on 2009-12-03
Biggest long term impact, .32 is the first kernel to ship btrfs code that is suitable for early adopters, additionally as this is the kernel that is likely going to be used in at least two major enterprise products (RHEL6 and Ubuntu Lucid) it is going to be supported for a long time and is predicted to be very solid.

This all means hopefully that fixes for btrfs will be regularly backported to this kernel as part of the enterprise cycles over the next 3-10 years (Lucid desktop is supported 3 years, server 5 years. RHEL for 7 years with exceptions made up to 10 years for certain customers). 

This is the beginning of rolling out modern storage solutions on Linux.

---

### Post by u.b.u.n.t.u on 2009-12-03
> **Malta paul said:**
> I have just install the Kernel in 9.04 on my 64 bit system, It works great (not using 9.10 yet

Good to hear! I am using 9.10 until Alpha 1 of 10.04 comes out. I look forward to using the new kernel, but I won't apply the changes myself.

---

### Post by RiceMonster on 2009-12-03
> **gnomeuser said:**
> Biggest long term impact, .32 is the first kernel to ship btrfs code that is suitable for early adopters, additionally as this is the kernel that is likely going to be used in at least two major enterprise products (RHEL6 and Ubuntu Lucid) it is going to be supported for a long time and is predicted to be very solid.

This all means hopefully that fixes for btrfs will be regularly backported to this kernel as part of the enterprise cycles over the next 3-10 years (Lucid desktop is supported 3 years, server 5 years. RHEL for 7 years with exceptions made up to 10 years for certain customers). 

This is the beginning of rolling out modern storage solutions on Linux.

Awesome stuff. I'm really excited for when btrfs goes stable.

---

### Post by u.b.u.n.t.u on 2009-12-03
> **gnomeuser said:**
> Biggest long term impact, .32 is the first kernel to ship btrfs code that is suitable for early adopters

The Btrfs file system is certainly an interesting development, especially in comparison with Ext4.

---

### Post by MaxIBoy on 2009-12-03
I've been using the release candidates of this release, and it's quite nice. I hope Con Kolivas gets a BFS patch for the final release soon. :)


> **u.b.u.n.t.u said:**
>  Devtmpfs allows for booting without Udev and lets the Linux kernel run faster."Really? I had not noticed this feature. I want to try it now. 
>  a CFQ low latency mode, tracing improvements including a "perf timechart" tool that tries to be a better bootchart,[]("http://kernelnewbies.org/Linux_2_6_32")Those two are big features for me that I am looking forward to trying out.

---

### Post by handy on 2009-12-03
Neither Catalyst 9.10 or 9.11 are compatible with kernel .32, of course.

So Arch users who are using catalyst will need to add **kernel26** into their /etc/pacman.conf *IgnorePkg =* line with the other files that keep xorg-server at version 1.6.

---

### Post by aktiwers on 2009-12-03
Im gonna compile this kernel later tonight :)

---

### Post by dragos240 on 2009-12-03
*emerges latest gentoo-sources*

---

### Post by doorknob60 on 2009-12-04
Once this hits [core] in Arch, I'll give the Open Source ATI drivers a try, currently using Catalyst and it works fine, but I'm anxious to see how the FOSS ones work now :) EDIT: Too late, already did all that :D Works well.

---

### Post by Xbehave on 2009-12-07
woot got 2.6.32 working with sound now :D, not sure which ioschedular to use though, anticipatory sounds cool but then again CFQ got some patches to make it more desktop friendly :S Anybody know much about ioschedulars?

p.s necro'd 4 toupeiro :p

---

### Post by toupeiro on 2009-12-07
> **Xbehave said:**
> woot got 2.6.32 working with sound now :D, not sure which ioschedular to use though, anticipatory sounds cool but then again CFQ got some patches to make it more desktop friendly :S Anybody know much about ioschedulars?

p.s necro'd 4 toupeiro :p

You rock, Xbehave! :)

---

### Post by BOFH+ on 2010-02-13
> **Xbehave said:**
> woot got 2.6.32 working with sound now :D, not sure which ioschedular to use though, anticipatory sounds cool but then again CFQ got some patches to make it more desktop friendly :S Anybody know much about ioschedulars?

I'd go with CFQ with the new low latency patches, or better yet you could try tweaking granularity, etc. in sched_fair.c as per [http://linux.derkeiler.com/Mailing-Lists/Kernel/2009-09/msg04417.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2009-09/msg04417.html)

At least that's what I intend to do sooner or later. ATM I'm still using the deadline scheduler because it works great with reiserfs on my root partition...

---

