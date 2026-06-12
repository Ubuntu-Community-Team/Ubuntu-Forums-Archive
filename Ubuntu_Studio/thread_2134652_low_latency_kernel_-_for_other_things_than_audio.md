---
title: "low latency kernel - for other things than audio"
date: 2013-04-11
forum: Ubuntu Studio
---

### Post by kanaida on 2013-04-11
Hey guys, I've been running ubuntu 12.10/04 on my desktop for a while now but decided to give ubuntu studio a go.

What I can tell you is that it's infinitely faster. From POST to desktop is like under 5-10 seconds. Instant.
checking and installing updates is ridiculously faster too.
Ubuntu Desktop was nowhere near this fast on the same hardware.

I have a samsung 840 SSD + Corei7  + Nvidia card + 10Gb ram in there by the way.

My question is, what parts of the lowlatency kernel are actually lower latency tuned? processor queues? other stuff?
What technical differences are there?

I'm trying this kernel out on my workstation at work right now to experiment running virtualbox on it to see if it's more responsive as well.
So far it's pretty snappy, but hard to tell.

I'm not sure if it's the kernel or xfce. At work i'm using Mint so it's cinnamon.

---

### Post by zequence on 2013-04-11
linux-lowlatency is actually slower than linux-generic. This is because it takes greater care in making sure scheduled events happen on time. This actually makes some things slower, and therefore, linux-lowlatency would be bad for servers. 

Low latency is really only important if you want a process to deliver on time, such as live audio processing, where for instance you are hitting a key on the keyboard, and want to hear the sound instantly, and not half a second later. 

What you are describing has more to do with what applications you use, and what processes start during boot time. So, yes, more about XFCE, but also about the configuration of the system, mostly derived from Xubuntu.

---

### Post by wkulecz on 2013-04-15
Unless you were also using XFCE on your desktop you are looking at the overhead of a "heavyweight" desktop system like Unity, Gnome or KDE.

If you want really fast try Lubuntu (LxDE), but I find it a bit lame for any system much stronger than a Pandaboard.

The low latency kernel generally reduces server thruput with the benefit of giving higher priority processes faster and more reliable scheduling for smoother audio -- the obvious benefit here, but data acquisition systems and heavily threaded applications on multi-core CPU also benefit.

---

