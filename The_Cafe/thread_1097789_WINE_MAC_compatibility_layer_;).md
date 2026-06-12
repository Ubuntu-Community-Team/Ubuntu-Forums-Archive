---
title: "WINE MAC compatibility layer ;)"
date: 2009-03-16
forum: The Cafe
---

### Post by sandyd on 2009-03-16
what id like to see is something like WINE, only that the compatibility layer is Mac, not windows.

It shouldn't be that hard, b/c Mac is build on Unix (which is the same thing that Linux is built on)

It would enable linux users to run MSN messenger, office .etc.etc much more natively and stablely than if we ran it in WINE becuase of how close Mac and Linux are. 

and please, no OS bashing here

---

### Post by airtonix on 2009-03-16
> **carlee said:**
> It shouldn't be that hard, b/c Mac is build on Unix (which is the same thing that Linux is built on)

While yes macos does run on a nix variant, bsd to be exact. the core of the macoss system that provides many of the running functions of apples apps is not linux at all.

It's quartz i think, which does the job of our compiz & gnome.

Im not sure if there are other components in the MacOs structre that could be compared.

But i do know that quartz is an awesome component.

---

### Post by aaaantoine on 2009-03-16
If there is ever a market for it, I'm sure someone so technically inclined would go ahead and try to develop such at hing.

Call it "MINE". :-D

---

### Post by liamnixon on 2009-03-16
I'm not sure I'd say that Linux is built on Unix; somebody just wanted a Unix clone so he instigated development on one.

At any rate, I do think a Mac compatibility layer would be neat.  All my free time would be sucked up with Garageband, though.  :-\"

---

### Post by ssam on 2009-03-16
this question has come up before, and will come up again :-)
[http://ubuntuforums.org/showthread.php?t=475328](http://ubuntuforums.org/showthread.php?t=475328)

to recap: has not been done, not impossible, does not seem likely that it will be done in the near future (it might take 15 years to make).

---

### Post by liamnixon on 2009-03-16
Thanks for the link, ssam!

---

### Post by MikeTheC on 2009-03-16
Yeah, and while we're at it, I'd like a TARDIS, a million dollars, and world peace.

---

### Post by bsharp on 2009-03-16
> **ssam said:**
> this question has come up before, and will come up again :-)
[http://ubuntuforums.org/showthread.php?t=475328](http://ubuntuforums.org/showthread.php?t=475328)

to recap: has not been done, not impossible, does not seem likely that it will be done in the near future (it might take 15 years to make).

So did [WINE]("http://en.wikipedia.org/wiki/Wine_(software)")

---

### Post by Thelasko on 2009-03-16
The [Carbon]("http://en.wikipedia.org/wiki/Carbon_(computing)") and [Cocoa ]("http://en.wikipedia.org/wiki/Cocoa_(API)")APIs appears to be the trick.  It all seems strange to me.  If someone were to reverse engineer Carbon, and implement it on BSD/Darwin, there would essentially be an open source version of Mac OSX.

I also find it weird that the [Pidgin port to Mac]("http://en.wikipedia.org/wiki/Adium") uses Cocoa instead of GTK, like the Windows port does.

---

### Post by smartboyathome on 2009-03-16
There is a partial Cocoa API implimentation in GNUstep, just to let you know.

---

### Post by crazyfuturamanoob on 2009-03-16
I'd love to run mac apps on my Ubuntu, like iPhone SDK and Cortex Command. But Macs are PPC, not x86.

---

### Post by mrsteveman1 on 2009-03-16
> **crazyfuturamanoob said:**
> I'd love to run mac apps on my Ubuntu, like iPhone SDK and Cortex Command. But Macs are PPC, not x86.

Welcome to 3 years ago :)

[http://en.wikipedia.org/wiki/Apple_Intel_transition]("http://en.wikipedia.org/wiki/Apple_Intel_transition")

---

### Post by mrsteveman1 on 2009-03-16
As far as i know the Linux kernel doesn't support the Mach-o binary format (we use ELF), but i don't think that's a huge problem, the kernel doesn't support PE either but Wine handles it just fine.

Biggest problem is going to be supporting the development frameworks, and there are a lot of them. Part of Apples push for their platform is to make development easy, which means you can write applications and reuse existing code or use their libraries. They are apparently cleaner than Win32 (which is trash), but they are huge, complex and Apple is unlikely to sit back and let their applications work elsewhere easily.  What do you think would happen if it were possible to easily run iLife on another OS? Apple would go crazy.

For anyone who cares, OS X is not just BSD. There is some BSD code in the kernel (not the majority of it, not even close), and the userland components for the commandline come from FreeBSD, i believe the C library is descended from the original BSD code (which is older than FreeBSD) but thats about it. It is UNIX 03 compliant, but the OS is more complex than that (so is Linux for that matter).

Most of the system is either developed by Apple in-house like some of the newer systems, launchd for instance, or came from NeXT like the library frameworks (which predate FreeBSD, Linux, Gnome, KDE etc, entirely), or came from some open source projects. They use some LGPL libraries, some GPL components, they BOUGHT the CUPS printing system. As a whole, the OS is very much Apples own baby right now, rather than the common line that gets tossed around, that it is just FreeBSD with some pretty GUIs.

---

### Post by dragos240 on 2009-03-16
Also i have a question:
Does mac use X for their GUI?

---

### Post by mrsteveman1 on 2009-03-16
> **Thelasko said:**
> I also find it weird that the [Pidgin port to Mac]("http://en.wikipedia.org/wiki/Adium") uses Cocoa instead of GTK, like the Windows port does.

Adium isn't a port of Pidgin, the only thing they have in common is that they use the same library for communication, libpurple.

---

### Post by mrsteveman1 on 2009-03-16
> **dragos240 said:**
> Also i have a question:
Does mac use X for their GUI?

The display system on OS X is called Quartz, but there is an X11 subsystem that can run on top of it. Many applications built to use X11 can run on OS X, like Wireshark.

---

### Post by Thelasko on 2009-03-16
> **mrsteveman1 said:**
> Adium isn't a port of Pidgin, the only thing they have in common is that they use the same library for communication, libpurple.

Please explain the difference.

---

### Post by mrsteveman1 on 2009-03-16
> **Thelasko said:**
> Please explain the difference.

The majority of the code has nothing to do with Pidgin, it is a different program just like Safari and Konqueror are completely different programs even though both use a rendering engine rooted in khtml. 

The program itself, the interface, the logic that controls how the program functions, is not a port of the Pidgin code. 

The part they do share is libpurple, which is an implementation of various communication protocols and chat systems. It makes it easier to implement a program that can communicate with AIM, or MSN, or the Google Talk.

---

### Post by billgoldberg on 2009-03-16
> **carlee said:**
> 

It shouldn't be that hard, b/c Mac is build on Unix (which is the same thing that Linux is built on)



If only that was true, which it isn't, at all.

---

### Post by billgoldberg on 2009-03-16
> **crazyfuturamanoob said:**
>  But Macs are PPC, not x86.

Without pointing out your errors, Ubuntu does have a PPC port.

---

### Post by dragos240 on 2009-03-16
thank you steve

---

### Post by MikeTheC on 2009-03-16
> **crazyfuturamanoob said:**
> But Macs are PPC, not x86.

Dude, seriously... What the --- ?

---

### Post by Skripka on 2009-03-16
> **carlee said:**
> what id like to see is something like WINE, only that the compatibility layer is Mac, not windows.

It shouldn't be that hard, b/c Mac is build on Unix (which is the same thing that Linux is built on)

It would enable linux users to run MSN messenger, office .etc.etc much more natively and stablely than if we ran it in WINE becuase of how close Mac and Linux are. 

and please, no OS bashing here

It will never happen.


My understanding is that Apple's OSX API is proprietary, patented, and copywritten- and they have enough lawyers to lock anyone up in jail for trying....or sue them for the collected income of all the programmer's future families.

---

### Post by MikeTheC on 2009-03-16
> **Skripka said:**
> It will never happen. <snip>

Yep, pretty much. Besides, if you consider how long it's taken the Wine community -- to say nothing of what has had to take place in that community (i.e.: formation of CodeWeavers, etc.) -- it is a fairly safe bet you'll never see the effort replicated for Mac OS X. Besides, take a look at just about any non-Mac message board out there (even ones which have nothing to do with OSs) and it's not like there's some "community of users" who are champing at the bit for Darwin/Carbon/Cocoa/Aqua environment support.

Just look at UbuntuForums by themselves. One of the fastest ways to get people around here to be derogatory is to simply *mention* Apple or a Mac or Mac OS X. Why would a community which ostensibly "hates" Mac OS X want to build a bridge to supporting it in Linux?

Then take a look at Apple, and let's compare them with Microsoft. Neither wants their OS to be stolen or ripped off or to have their sales "diluted", but there's a fundamental difference between the companies. Microsoft would rather people emulate the Win32 environment because that just helps strengthen their platform's ubiquity, and reinforces the notion that Windows *is* the de facto standard.

Apple, on the other hand, is not interested in world domination. They're only interested in you running Mac OS X on their terms. Those terms, in essence, are: 1. Original copy from Apple; 2. On Apple-distributed hardware. If you want to use Mac OS X in any fashion *other* than ***both*** those terms, then they really couldn't care less that you're not contributing to their platform's ubiquity, that you're not spending money with them otherwise (for, say, iWork or iLife, or on an iPod, iPhone, etc.)

Now, you can argue whether that's "good" or "bad" on Apple's part, but *that* doesn't really matter. Those are Apple's terms, and it represents a totally different world-view than Microsoft's. Ergo, a snowball has a better chance in Hell than, for reasons explored here and in prior posts, there being a "Wine" for Mac OS X.

---

### Post by mrsteveman1 on 2009-03-17
There is a significant part of some of the APIs implemented in GNUStep, but so far as i know they are aiming for source compatibility and not binary compatibility.

---

### Post by Thelasko on 2009-03-17
> **Skripka said:**
> It will never happen.


My understanding is that Apple's OSX API is proprietary, patented, and copywritten- and they have enough lawyers to lock anyone up in jail for trying....or sue them for the collected income of all the programmer's future families.

You reminded me that because OSX is so similar to BSD, creating such program wouldn't really be a compatibility layer like Wine.  It would be more of a clone.

---

### Post by mrsteveman1 on 2009-03-17
> **Thelasko said:**
> You reminded me that because OSX is so similar to BSD, creating such program wouldn't really be a compatibility layer like Wine.  It would be more of a clone.

You'd still need a binary layer of some kind to read mach-o binaries unless the kernel can do it some day. And you'd need to VERY closely match the binary interface of Apples frameworks just like WINE follows Win32.

---

