---
title: "flash x64, gnash, or swfdec?"
date: 2009-10-16
forum: The Cafe
---

### Post by sandyd on 2009-10-16
Ive been having a whole lot of problems with the x64 beta flash. It sometimes allows me to click on something in the flash animation, then after a while, the flash applet completely becomes unclickable. (i can click all i want on the button, but nothing happens)

is gnash or swfdec better?

---

### Post by NoaHall on 2009-10-16
It's a alpha.

And no, gnash and swfdec on 64 bit are just horrible, and they'll give you install problems with proper flash.

What browser are you using?
Are you 100% sure it's the 64 bit version, not the 32 bit version from the repos?

---

### Post by dragos240 on 2009-10-16
Well. I've tried gnash, it's pretty alpha, has quite a few bugs, and can't play anything past version 5.

---

### Post by FuturePilot on 2009-10-16
Make sure you don't have the 32bit plugin + nspluginwrapper installed. 64bit Flash plugin has always worked great for me.

---

### Post by Pogeymanz on 2009-10-16
Unfortunately gnash and swfdec are probably not going to be any better. Out of the two, swfdec works better for me.

---

### Post by hoppipolla on 2009-10-16
Can you not use official flash at all on 64 bit? I have had a pretty bad time with the unofficial ones but then I don't think I've tried many...

---

### Post by dragos240 on 2009-10-16
Well. Adobe has not released the source to the official flash player, and it is not under a free software lisence. So some people here may not like the idea of a closed source player. I don't really mind. But I would prefer an open source player.

---

### Post by sandyd on 2009-10-16
> **FuturePilot said:**
> Make sure you don't have the 32bit plugin + nspluginwrapper installed. 64bit Flash plugin has always worked great for me.
im verry sure i got the 64 bit plugin installed.
remember downloading it manually from the adobe site.

---

### Post by dragos240 on 2009-10-16
I recommend getting the 32 bit version. It works much better.

---

### Post by jonian_g on 2009-10-16
What browser do you use?

With firefox, flash x64 works great for me. Never had a single problem.
With opera, it seems that it likes flash to be in /usr/lib/opera/plugins.

---

### Post by NoaHall on 2009-10-16
> **dragos240 said:**
> I recommend getting the 32 bit version. It works much better.

That's not true. It's been proven.

---

### Post by sandyd on 2009-10-16
> **dragos240 said:**
> I recommend getting the 32 bit version. It works much better.
heres where im clueless.
how do i do that?
i tried simply using flashplugin-nonfree before i installed the x64 bit flash, but youtube videos just showed up as a black square,

---

### Post by NoaHall on 2009-10-16
It's in the repos, as stated in my first post.

---

### Post by falconindy on 2009-10-16
just install the package 'flashplugin-installer' if you really want the 32 bit. I assure you, as have others, that the 64-bit alpha works a LOT better.

---

### Post by FuturePilot on 2009-10-16
> **carlee said:**
> im verry sure i got the 64 bit plugin installed.
remember downloading it manually from the adobe site.

Sorry I should have clarified this better. What I meant was make sure you don't have the 32bit one **and** the 64bit one installed at the same time.

---

### Post by sandyd on 2009-10-16
> **FuturePilot said:**
> Sorry I should have clarified this better. What I meant was make sure you don't have the 32bit one **and** the 64bit one installed at the same time.
i **had** 32 bit flash installed, but i overwrote the 32 bit file with the new x64 plugin 
( i can't remove it either konqueror will non-stop bug me to install it )

---

### Post by wmcbrine on 2009-10-16
> **falconindy said:**
> I assure you, as have others, that the 64-bit alpha works a LOT better.I assure you it doesn't, on my system. I gave up on all three of these, and went back to the 32-bit w/ the wrapper. It used to crash on me after a while (leaving the browser running), but it doesn't seem to have that problem anymore.

I'm wondering if the 64-bit version is compiled with some instructions that weren't available on the oldest AMD64 processors, or somesuch. That could explain why it crashes on my system, but reportedly works well for others.

---

### Post by dragos240 on 2009-10-16
> **NoaHall said:**
> That's not true. It's been proven.

Works better for me! I can't view some things with the 64 bit version. But the 32 bit version works like a charm.

---

### Post by FuturePilot on 2009-10-16
> **wmcbrine said:**
> I assure you it doesn't, on my system. I gave up on all three of these, and went back to the 32-bit w/ the wrapper. It used to crash on me after a while (leaving the browser running), but it doesn't seem to have that problem anymore.

I'm wondering if the 64-bit version is compiled with some instructions that weren't available on the oldest AMD64 processors, or somesuch. That could explain why it crashes on my system, but reportedly works well for others.

There is a problem with the 64bit plugin and processors that don't have the "lahf_lm" flag. Does your processor have that flag?

---

### Post by wmcbrine on 2009-10-16
> **FuturePilot said:**
> There is a problem with the 64bit plugin and processors that don't have the "lahf_lm" flag. Does your processor have that flag?Nope. I guess that's it, then. Thanks. It's annoying... the only other problem I have with this vintage CPU is that it won't run 64-bit guests, or OS/2, in VirtualBox.

---

### Post by FuturePilot on 2009-10-16
> **wmcbrine said:**
> Nope. I guess that's it, then. Thanks. It's annoying... the only other problem I have with this vintage CPU is that it won't run 64-bit guests, or OS/2, in VirtualBox.

See this thread. [http://ubuntuforums.org/showthread.php?t=1263905]("http://ubuntuforums.org/showthread.php?t=1263905") It should solve your problem.

---

### Post by HappyFeet on 2009-10-16
> **FuturePilot said:**
> 64bit Flash plugin has always worked great for me.

Same here. 64 bit flash works a treat. As good as 32bit did when I used to use 32bit ubuntu.

---

### Post by HappyFeet on 2009-10-16
> **wmcbrine said:**
> Nope. I guess that's it, then. Thanks. It's annoying... the only other problem I have with this vintage CPU is that it won't run 64-bit guests, or OS/2, in VirtualBox.

Yeah, my Phenom quad core is nice. ;) Everything works beautifully.

---

### Post by wmcbrine on 2009-10-17
> **FuturePilot said:**
> See this thread. [http://ubuntuforums.org/showthread.php?t=1263905]("http://ubuntuforums.org/showthread.php?t=1263905") It should solve your problem.Works. :)

---

