---
title: "Compile Kernel?"
date: 2007-03-17
forum: The Cafe
---

### Post by penguinchrissy on 2007-03-17
Is it worth it to compile a kernel? Does it make things quicker or run smoother also can I update easily. I've been running ubuntu for six months and have become fairly confident with it.

---

### Post by Crashmaxx on 2007-03-17
There is no reason to bother unless you want to do it as a learning experience.

If you use Dapper then there are already precompiled kernels optimized for different chipsets that are in the repositories. In Edgy the "Generic" kernel is suppose to be optimized well for most architectures.

If you needed a specific driver or piece to be built into the kernel, then most, if not all, are now available as a LKM. Which stands for Linux Kernel module. They run at the kernel level, but are not  compiled into the kernel so they are much easier to manage.

So, unless you want to do it for fun, or have very specific needs, it is no longer necessary to compile your own kernel. I'm not against it, but its no longer the defacto standard that it used to be. At least for Debian based systems, other distros still use a very different approach.

---

### Post by Tomosaur on 2007-03-17
If you're getting poor performance from your current kernel, then recompilling it to specifically suit you could well give you a performance increase, yes. Ubuntu's kernel has a lot of stuff compiled into it, because Ubuntu aims to work as well as possible for everyone who uses it. For that reason, it's very likely that there's stuff in your kernel that you simply don't need. There are probably also daemons running which you don't need. So yes, compiling your own kernel could give a performance increase.

However - "rolling your own" is not a light task. You will need to know what your machine needs to run, what your hardware needs, etc etc. Perhaps the biggest mistake is to compile everything as a module. This helps improve performance because you can disable and enable modules as you see fit. However, there are things which YOUR machine will need to be compiled directly into the kernel. A common example is this:

While configuring your kernel before compiling, you notice that it is possible to configure filesystem support as modules. You set them all as modular, and then compile your kernel. Reboot, and blammo, kernel panic. You need to compile support for YOUR filesystem directly into the kernel, because modules are not loaded immediately. If the kernel doesn't know how to use your filesystem, then it will suffer a panic, and you won't be able to boot. The situation is true for other things, so you really need to know what you're doing before trying it.

However - if you want to do it, go ahead. The only damage you'll do is being unable to boot. All you need to do then is just select the previous kernel from the boot menu, and try compiling your own kernel again. It's not going to break your machine, or delete any files, or anything like that. Just make sure you don't delete your old kernel before making sure the new one works. Also check that your bootloader is set up properly to show more than one kernel version, not just the latest. This is not absolutely necessary since you can make grub find and boot an older kernel version from Grub's command line, but it does save time.

However, if you've no immediate reason to do so, then there's no real point. If you're not noticing any problems with your current kernel, then you may aswell just save yourself the time and do something more constructive (compilation can take quite a while, depending on your configuration and hardware). It CAN teach you a lot though, particularly if you use a graphical configurator (kconfig, for example), which will give you a nice explanation of each bit of the kernel to make it easier to decide what you want.

---

### Post by BuffaloX on 2007-03-17
It would be extremely cool, if I could recompile the default Ubuntu kernel, but with some changes.
Like changing timer for real time performance from 256 to 4096 ticks per second.
But it seems to be a bit more of a job than I first thought...

Anyways Ubuntu rules. :)

---

### Post by raffytaffy on 2007-03-17
for my laptop ; yes its tottaly worth it ; big speed increase and other things

---

### Post by gholen on 2007-03-17
Yes, it's woth it. In these "Generic" kernels, it's a lot of stuff you dont need, the stuff that you need are a bit of 25% of whats in the Generic stuff, the first thing that hits my new systems is a selfcompield kernel. the bloated stuff is gone, mu speed is up, and the system is more stable.

---

### Post by siimo on 2007-03-17
Yes I like to configure my system right down to its core.. =)

---

### Post by penguinchrissy on 2007-03-21
Even though the poll says no I think in going to try and do it as in expernce. I hope to get back with how it went some time soon.

---

### Post by digitzero on 2007-03-21
Definitely worth it for learning and for performance.

Before I started tinkering with my kernel, I made sure /boot/grub/menu.lst did not have a hidden 
menu,

ex:
# hiddenmenu (note how it's commented out)


This is so when you screw something up on your new kernel, you can just as easily boot into your old/working kernel.

---

### Post by stmiller on 2007-03-30
You have to recompile your kernel if you do major audio work. To enable a realtime kernel, that is low-latency, with a higher resolution timing. The newer post 2.6.18 kernels have excellent realtime features. But these features are not enabled in the official ubuntu releases...

*******
EDIT: In the current Feisty repos there are i386 low-latency kernels, with a higher resolution timing also. No need to recompile a kernel for me now! Woo-hoo!

---

### Post by migla on 2007-03-30
There's this creative commons licensed O'reilly-book by kernel-person Greg Kroah-Hartman out there. It's about compiling the kernel, called [Linux Kernel in a Nutshell]("http://www.kroah.com/lkn/"). Check it out.

---

### Post by karellen on 2007-03-31
I've never felt the need to compile a kernel. the standard one works pretty well with my pc (as it has an old configuration)

---

