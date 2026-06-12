---
title: "other than that, ubuntu is no. 1"
date: 2006-06-18
forum: The Cafe
---

### Post by pelle.k on 2006-06-18
Hi fellas. I'm hiding from all tomates i'm going to get thrown at me :)
Ubuntu is my first choice of linux distro. If only there was a i686 optimized version.
I dont care what you say - "Prove there is a speed difference" etc etc. In my experience i686 distros IS both snappier and faster, in all aspects. It's no small diffrence "i was imagining". I have no need to prove it to anyone, nor would i have the expertise to do so. I usually run the same number of services on other distros too so everything is pretty much the same.
Before you throw the ususal replys at me i've got the i686 kernel, nvidia driver, x render extension, bla bla bla - been there, done that.
What I wish to gain from this thread is not a discussion about IF there is a performance gain from i686, because from my perspective there no doubt, but to hear from others who think like me.

Just to clarify. If you feel i'm dead wrong please start your own thread about it. How i386 is just as fast as i686, because just as YOU feel that, I want to continue living in my own little bubble were i686 in fact is faster. And discuss it :).

---

### Post by sharkboy on 2006-06-18
I don't quite see what there would be to discuss.

Just in case you didn't know about it, you can recompile (with optimizations) all your packages with apt-build.

There's also this: [http://distrowatch.com/?newsid=03378#0](http://distrowatch.com/?newsid=03378#0)

Good luck!

---

### Post by bruce89 on 2006-06-18
[QUOTE=pelle.k]Hi fellas. I'm hiding from all tomates i'm going to get thrown at me :)
Ubuntu is my first choice of linux distro. If only there was a i686 optimized version.
I dont care what you say - "Prove there is a speed difference" etc etc. In my experience i686 distros IS both snappier and faster, in all aspects. It's no small diffrence "i was imagining". I have no need to prove it to anyone, nor would i have the expertise to do so. I usually run the same number of services on other distros too so everything is pretty much the same.
Before you throw the ususal replys at me i've got the i686 kernel, nvidia driver, x render extension, bla bla bla - been there, done that.
What I wish to gain from this thread is not a discussion about IF there is a performance gain from i686, because from my perspective there no doubt, but to hear from others who think like me.

Just to clarify. If you feel i'm dead wrong please start your own thread about it. How i386 is just as fast as i686, because just as YOU feel that, I want to continue living in my own little bubble were i686 in fact is faster. And discuss it :).[/QUOTE]
Well, then I want a k8 version as that is what I use, it just isn't practical to optimise everything.  Other people would then want a i486, i586, k6, k7, xeon, semperon, k8, k8-smp, etc. optimised versions.

---

### Post by pelle.k on 2006-06-18
> Well, then I want a k8 version as that is what I use, it just isn't practical to optimise everything. Other people would then want a i486, i586, k6, k7, xeon, semperon, k8, k8-smp, etc. optimised versions.
OK, guess i deserved that...
i686 is pretty generic though. pentium 2 +.
What about Xorg + Gnome/KDE base as i686 packages, nothing else. That would be pretty cool.

---

### Post by prizrak on 2006-06-18
It would be impractical. There are the optimized kernels you can install or you can recompile your system if you want. If you make a complete 686 version you will have to make a 686-smp version and a k7 version and a k7-smp version and a k8 version and a k8-smp version. You see where I'm going don't you? This is a desktop OS that has a general 386 kernel, which will work on any x86 CPU and includes some optimized packages for different CPU's if you want. 

Just so you know Windows (main competitor) does the same exact thing it's not compiled for a specific CPU it is compiled to run on all x86 CPU's. 64 bit versions being the only exception to the rule. 

One thing that you need to be aware off is that it's not just compile time optimizations that make a system run as it does. There could be less services running, there is different set up, there is prelinking and so on and so forth.

---

### Post by bruce89 on 2006-06-18
[QUOTE=pelle.k]OK, guess i deserved that...
i686 is pretty generic though. pentium 2 +.
What about Xorg + Gnome/KDE base as i686 packages, nothing else. That would be pretty cool.[/QUOTE]
Yes, that would work, but also k7, k8, xeon and so on versions too.  I think multiarch may bring this kind of thing, I read it on Debian Weekly News - [http://www.debian.org/News/weekly/2006/20/](http://www.debian.org/News/weekly/2006/20/)

---

### Post by fuscia on 2006-06-18
[QUOTE=tetsagui]We need people to join our forum, weve already got 63 members but would like to have more. Our forum relates to everything game related. Classic, action, First Person Shooter, etc. individual system help (incase you have a problem and dont want to pay money to have it fixed, you can state the problem under the topic called Courtesy Desk), and just plain System talk, as well as topic that are just for fun (ie: music, arts&literature, Lounge(spam topic), and much more). So feel free to stop by at [http://gametalk.invisionzone.com](http://gametalk.invisionzone.com)[/QUOTE]

i'm sorry, but i'm not much of a gamer. i do appreciate you coming by, though.

---

### Post by Lord Illidan on 2006-06-18
[quote=fuscia]i'm sorry, but i'm not much of a gamer. i do appreciate you coming by, though.[/quote]

He's probably a spammer, fuscia..

About this 686 thing, could it be that these 686 distros are lighter than Ubuntu? However, it would be interesting if you could apt-build and optimise your Ubuntu, and then comment on the speed increases, perhaps then work might begin on another version of Ubuntu, 686 alongside with 386.

---

### Post by fuscia on 2006-06-18
[QUOTE=Lord Illidan]He's probably a spammer, fuscia..[/QUOTE]

really? damn! that's what i get for being neighborly.

---

### Post by bruce89 on 2006-06-18
I wasn't saying that optimisation would be impractical, i'm just pointing out that there is more than one subarchitecture available, and the one that you personally use isn't the only one.  It seems as if lots of people here use i686, but then I use k8.

---

### Post by pelle.k on 2006-06-18
> Yes, that would work, but also k7, k8, xeon and so on versions too. I think multiarch may bring this kind of thing, I read it on Debian Weekly News - [http://www.debian.org/News/weekly/2006/20/](http://www.debian.org/News/weekly/2006/20/)

***Multiarch Status Update.** Matt Taggart pointed out a report by Canonical Ltd. and HP which investigates potential implementation strategies of multiarch in Debian. Scott James Remnant prepared a specification for the changes needed in dpkg. Multiarch will allow Debian many improvements like a better support for systems that can run multiple binary targets, like i386 on amd64, or i386 on ia64.*

This isn't really the same thing, right?

Seriously, i know the effort needed to support multiple architectures, but you would get a big performance gain if you would only do that for core packages like xorg and base gnome/kde. Thats the packages which are in use 24/7 on a desktop computer. I too can see that doing this for all packages in the ubuntu repositories would be, well, time consuming.

---

### Post by bruce89 on 2006-06-18
[QUOTE=pelle.k]... report by Canonical Ltd. and HP which investigates ...[/QUOTE]
I wonder what HP has to do with it?
Choice bits from the report:
[QUOTE=Report]A proposal is to extend this to include additional system features, for example
processor &#64258;ags such as sse and other later instruction sets, our example home
desktop might actually provide &#8220;i386 i486 i586 i686 sse&#8221;. Packages that
would bene&#64257;t from can then be compiled and depend on these features, and
located in a small architecture with only a tiny handful of other packages. One
might then install mplayer 1.0-1 i686+sse.deb onto their system, in e&#64256;ect,
every system becomes a Multi-Arch one.
...
Our recommendation therefore is to place Multi-Arch support directly into the
package manager, either by modi&#64257;cation of the existing dpkg 1.13 code or by
developing dpkg 2. While in the short term developing and testing dpkg 2
may seem more expensive and thus not the best option, we believe that in the
long term it will ultimately prove a better course than retro-&#64257;tting support into
dpkg 1.13 as all of the problems can be met head-on.[/QUOTE]

---

### Post by Lord Illidan on 2006-06-18
[quote=bruce89]I wonder what HP has to do with it?[/quote]

Perhaps they are helping Canonical. Good to know that we have support from the heavy hitters in the IT industry.

---

### Post by prizrak on 2006-06-18
[QUOTE=pelle.k]***Multiarch Status Update.** Matt Taggart pointed out a report by Canonical Ltd. and HP which investigates potential implementation strategies of multiarch in Debian. Scott James Remnant prepared a specification for the changes needed in dpkg. Multiarch will allow Debian many improvements like a better support for systems that can run multiple binary targets, like i386 on amd64, or i386 on ia64.*

This isn't really the same thing, right?

Seriously, i know the effort needed to support multiple architectures, but you would get a big performance gain if you would only do that for core packages like xorg and base gnome/kde. Thats the packages which are in use 24/7 on a desktop computer. I too can see that doing this for all packages in the ubuntu repositories would be, well, time consuming.[/QUOTE]
Not much of a point, compile time optimization is fairly meaningless. There exists runtime optimization, which is nothing more than a program with such a feature detects the CPU that is being used and what features it supports and will use them. Also you must realize that compile time optimization while POTENTIALLY beneficial for performance could be degrading to stability. As I said earlier optimizing the code is hardly the only or even the most important step in overall system performance. In the same way that XFCE is faster than Gnome regardless of what hardware is being used or what optimizations are applied.

---

### Post by pelle.k on 2006-06-18
Why i chose to start a new thread on this topic is because i have arch installed on the same machine i''m using now, and the sad part is, even if kubuntu/ubuntu is amongst the snappier distros i've tried out, everything pales in comparison to a arch kde/gnome desktop. I can't belive arch KDE is as snappy as xubuntu, but it is.
I'm not going to whine about it. I choose (K,X)ubuntu as my primary distro, because it really is well polished, but...
All i'm saying is, it would be nice if ubuntu was as snappy. Like the missing piece of a flawless puzzle.

---

### Post by DR_K13 on 2006-06-18
you need a haircut

---

### Post by pelle.k on 2006-06-18
Yeah, LOL. I probably do. It's even longer by now. :D 
I have it like that - like the stoner in "grandmas boy". Looks totally ridicolous.

---

### Post by prizrak on 2006-06-19
I also hear good things about Arch's speed. However I do believe it was said it was less stable than Ubuntu. My test machine is an AXP so I can't run a 686 distro on it. On the other hand there are other fast distros out there, there are also slower distros. 

I think Ubuntu is as fast as it was possible to make it within the contstraints that had to be met for it as an OS.

---

### Post by woedend on 2006-06-19
ubuntu's slowness is not because it's 386(486) optimized.
I do like arch though, its very fast and clean.

---

### Post by 23meg on 2006-06-19
Given the presence of fully available source code, tools such as apt-build, fast computers, clustering tools, lots of free time and energy (perhaps, since those who bring up the subject beat it to death every time), I'm surprised to still not have heard of an independent, unofficial project that aims to compile all packages with "optimizations".

In the open source world there's usually little excuse not to at least have a go at implementing something if it comes close to making the slightest bit of sense, and there's enough interest. With everything including the know-how required available in the open, and people with similar interests all around, I guess time wasted on "it would be cool" threads in forums *which will change absolutely nothing* would be better spent learning to use apt-build, doing research on compile-time optimizations and getting to know GCC.

Why not act up instead of whine and beg? You have everything you need.

---

### Post by tseliot on 2006-06-19
[QUOTE=pelle.k]Why i chose to start a new thread on this topic is because i have arch installed on the same machine i''m using now, and the sad part is, even if kubuntu/ubuntu is amongst the snappier distros i've tried out, everything pales in comparison to a arch kde/gnome desktop. I can't belive arch KDE is as snappy as xubuntu, but it is.
I'm not going to whine about it. I choose (K,X)ubuntu as my primary distro, because it really is well polished, but...
All i'm saying is, it would be nice if ubuntu was as snappy. Like the missing piece of a flawless puzzle.[/QUOTE]
You're absolutely right about Arch speed (it has made a miracle on my laptop which had never been fast with Windows, Xubuntu or Vector Linux).

And BTW Arch runs fine on my AMD 64.

---

### Post by Castar on 2006-06-19
I am now running a k7-smp kernel that I have found on the repositories!

Just try to install linux-k7. It should be in the restricted repositories. No k8 images though... I can give you my sources.list if you want.

---

### Post by pelle.k on 2006-06-19
> Why not act up instead of whine and beg? You have everything you need.
I'm not going to whine any more. I consider this thread taken as far as possible (that was my intent).

I read this review of kubuntu dapper 64bit yesterday, and the guy claimed it was fast as lightning, and that got me thinking - dapper 64 bit is really optimized for a NEW architecture. That must be it. Accordign to him, things just popped up before you were expecting them too. It was FAST.
Yeah i know what you are gonna say, - "buy a freakin 64bit CPU then...", and maybe i will (again, action instead of whining)

I might even do a compile of xorg to i686.

---

### Post by Sushi on 2006-06-19
[QUOTE=prizrak]It would be impractical. There are the optimized kernels you can install or you can recompile your system if you want. If you make a complete 686 version you will have to make a 686-smp version and a k7 version and a k7-smp version and a k8 version and a k8-smp version. You see where I'm going don't you?[/quote]

But does it need to be like that? i386 is the absolute lowest common nominator in x86-world. And i386 is OLD. i686 would be better, and it would still be very, very compatible.

---

### Post by Sushi on 2006-06-19
[QUOTE=bruce89]I wasn't saying that optimisation would be impractical, i'm just pointing out that there is more than one subarchitecture available, and the one that you personally use isn't the only one.  It seems as if lots of people here use i686, but then I use k8.[/QUOTE]

But isn't K8 a subset of i686? I fail to see this argument that offering a more optimized version of the distro (say, i686) means that there should be zillion optimized versions available.

Using i686 might break some Via-CPU's (which are only aboit 98% compatible with i686), but rest would be OK (and faster).

EDIT: OK, maybe K8 is not a subset of i686, but K7 is. K8 is alredy served by the x86-64 version of Ubuntu.

---

### Post by maagimies on 2006-06-19
I don't think it's the processor optimizations which makes some distros snappier then others. Well, I would *maybe* compile xorg for my AthlonXP, but basically nothing else.

No, what I think matters more is:

1. The way system is built. Many snappy distros (Gentoo, Arch, Puppy linux) are almost all build from ground up. When you install you get the most basic packages only, and you add only what you want.
The downside to this is that you may not know what you want, and you can possibly break something.

Ubuntu installs tons of stuff to initscripts I surely don't need. So after installing, I usually have to spend some time disabling services I surely won't need, and if I need them, I can just enable them. The good thing about this that there's less change that I'll be unable to boot.

2. Packaging, and the distro devs patching the software to "their liking"
I've literally screamed at Debian and Ubuntu many times, when they have built some packages totally different way that I would have liked them.
And I don't like distribution devs patching the packages, I want the stuff fresh from their own developers, without any patches between.
I can say that my KDE runs better and more stable then the packaged one in Kubuntu Dapper. Kubuntu's KDE was always jerky no matter what I did, so I compiled my own.

---

