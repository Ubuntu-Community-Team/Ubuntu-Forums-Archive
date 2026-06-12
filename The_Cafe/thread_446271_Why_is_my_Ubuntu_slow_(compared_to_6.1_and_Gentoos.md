---
title: "Why is my Ubuntu slow? (compared to 6.1 and Gentoo/slax)"
date: 2007-05-16
forum: The Cafe
---

### Post by 1veedo on 2007-05-16
I don't know why but Ubuntu is really slow.  Gentoo, arch, and slax run just fine, and even older version of Ubuntu from like 5.1 through 6.1 were never like this.  Version 7.1, however, is exceptionally slow:
1) The GUI/desktop seems lagy, like highlighting text, clicking things, moving the mouse, etc.
2) 3D games are lagy as well

Like the whole computer is lagy I guess.  I brought up system monitor and ran a game while watching the monitor and absolutely nothing is over 10% CPU, and total there's only like 20% of the CPU at work.  It's like the computer is lazy or something and wont use the rest of the 80%!  I just don't understand why.  I have nvidia set up properly -- the games run to an extent, I know what it looks like when you install your video drivers wrong, but they still lag (almost to the same extent that the desktop does -- it's as if there's this hidden process that hogs CPU for a second, goes idle for 5, and hogs everything again).  It's not all that bad on the desktop but you most definitely cannot play games.

So I'm wondering, is there anything I could have done wrong?  I mean, honestly, there's no excuse for it to be running this slowly -- something has to be wrong.

Specs in case you're wondering.
AMD64 2800+ (I'm using 32bit Ubuntu though cause I'm making a liveCD with it)
nvidia 6200 w/ 256mb vram
DDR 2GB

---

### Post by Rhox on 2007-05-16
The only thing I can suggest is to try using an older kernel.
edit: like 2.6.16

---

### Post by igknighted on 2007-05-16
You probably need to use the correct nvidia driver... in feisty there are three, nvidia-glx-new, nvidia-glx and nvidia-glx-legacy.  Make sure you get the proper driver for your card (likely nvidia-glx-new).

---

### Post by WalmartSniperLX on 2007-05-16
Aren't Arch and Slax live distros? Theyre lightweight and fast. Gentoo is extremely fast because out of the box it doesn't give you much, and it compiles everything for your architecture.

---

### Post by 1veedo on 2007-05-20
The problem was the nvidia drivers.  I thought I had the new drivers installed but for some reason they weren't.  That was one of the solutions I found on these forums but I never checked cause I assumed it was installed (really, I actually remember doing this!).  Anyway everything's running smoothly now.[quote=WalmartSniperLX]Aren't Arch and Slax live distros?[/quote]I wasn't using the slax distro, I was using the slax kernel with gentoo cause I was making livecds/usbs and thought it'd be better if I used a precompiled kernel where the person who built it intended for it to boot just about anywhere (so I didn't have to worry about that detail).> Gentoo is extremely fast because out of the box it doesn't give you much, and it compiles everything for your architecture.Well maybe but ubuntu seems just as fast as gentoo now.  I was reading elsewhere that ubuntu is slower then most distros for different reasons but it doesn't seem any slower then gentoo, which is supposedly the fastest distro around.

---

### Post by Nikron on 2007-05-20
> **WalmartSniperLX said:**
> Aren't Arch and Slax live distros? Theyre lightweight and fast. Gentoo is extremely fast because out of the box it doesn't give you much, and it compiles everything for your architecture.

I know arch isn't a live distro..

---

### Post by WalmartSniperLX on 2007-05-21
Then Lightweight maybe? Ubuntu is pretty full featured. Dont know >.<

---

### Post by kingtsy on 2007-05-22
HI

My 7.04 is also slow. i like to try replace the kernel as suggested by rhox but don't know how.

Can you help me?
 also how to revert back to existing jernel?

Thanks.

---

### Post by WalmartSniperLX on 2007-05-23
> **1veedo said:**
> The problem was the nvidia drivers.  I thought I had the new drivers installed but for some reason they weren't.  That was one of the solutions I found on these forums but I never checked cause I assumed it was installed (really, I actually remember doing this!).  Anyway everything's running smoothly now.I wasn't using the slax distro, I was using the slax kernel with gentoo cause I was making livecds/usbs and thought it'd be better if I used a precompiled kernel where the person who built it intended for it to boot just about anywhere (so I didn't have to worry about that detail).Well maybe but ubuntu seems just as fast as gentoo now.  I was reading elsewhere that ubuntu is slower then most distros for different reasons but it doesn't seem any slower then gentoo, which is supposedly the fastest distro around.

Well Ubuntu is faster than Fedora Core 6 :P It's not really that slow. I don't know where all the rumors got out about it being so horribly slow (ive read a few). But I wouldn't say Ubuntu is nearly as fast a gentoo (at least from my experience with the two). However it isnt a slug :P

---

### Post by mikewhatever on 2007-05-23
7.04 is fast and responsive in my experience.

---

### Post by xyz on 2007-05-24
Ubuntu's running fine here but...ubuntuforums, however, IS slow these days!

---

