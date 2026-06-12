---
title: "MAC OSX and GPL"
date: 2007-07-07
forum: The Cafe
---

### Post by Warpnow on 2007-07-07
Okay..seen alot of posts now about how MAC OSX is basically just Ubuntu version 8 (or maybe 6, I think they stepped back). They're based off Linux now...they use workspaces...it even looks alot like Ubuntu...

Isn't linux distributed under the GPL? How do they use it for their OS and not release the source code?

Also...I've heard of a lot of legal battles where things are considered "derivative works" even if there is no code sharing if they deem that one project drew heavy influence from another...wouldn't Mac OSX be able to be considered a linux derivative and subject to the GPL anyway?

---

### Post by needtolookatascreenshot on 2007-07-07
[http://ubuntuforums.org/showthread.php?t=519877](http://ubuntuforums.org/showthread.php?t=519877)

---

### Post by PhatStreet on 2007-07-07
> **needtolookatascreenshot said:**
> It's not based on Linux, but on BSD.

IIRC, the userland is based on FreeBSD and they use a Mach kernel.
Yep, and let's not forget that the BSD license is a lot less restrictive.

---

### Post by OrbJinzo on 2007-07-07
Mac OSX is a hybrid of the NeXTStep kernel and the orignal BSD kernels.

---

### Post by stmiller on 2007-07-07
Like others said OS X is not under the GPL license, but the source is available:

[http://www.opensource.apple.com/darwinsource/](http://www.opensource.apple.com/darwinsource/)

OS X is under this license, I think: [http://www.opensource.apple.com/apsl/](http://www.opensource.apple.com/apsl/)

There was even a recent project that built an OS based on theses sources. It was pretty much a *BSD:

[http://en.wikipedia.org/wiki/OpenDarwin](http://en.wikipedia.org/wiki/OpenDarwin)

---

### Post by Syke on 2007-07-07
> Like others said OS X is not under the GPL license, but the source is available:
Mac OS X is most certainly not available in source code. Only Darwin is, which is a very small subset of OS X. Don't for a second mistake OS X as open source.

---

### Post by darkog on 2007-07-07
> **Warpnow said:**
> ...it even looks alot like Ubuntu...

Do you mean it looks like Gnome? You know you can change that way Ubuntu looks. From the [standard WM's]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Other_Desktop_Environments") to some [very new ones]("http://shaneosullivan.wordpress.com/2007/02/16/ubuntu-on-thinkpad-x41-installing-the-beryl-window-manager/").

---

### Post by Adamant1988 on 2007-07-08
> **Warpnow said:**
> Okay..seen alot of posts now about how MAC OSX is basically just Ubuntu version 8 (or maybe 6, I think they stepped back). They're based off Linux now...they use workspaces...it even looks alot like Ubuntu...

Isn't linux distributed under the GPL? How do they use it for their OS and not release the source code?

Also...I've heard of a lot of legal battles where things are considered "derivative works" even if there is no code sharing if they deem that one project drew heavy influence from another...wouldn't Mac OSX be able to be considered a linux derivative and subject to the GPL anyway?

This message brought to you, in part, by misinformation.  For all your ignorant forum posting needs, get misinformation. 

Seriously though, OS X is BSD based.

---

### Post by Polygon on 2007-07-08
> **Syke said:**
> Mac OS X is most certainly not available in source code. Only Darwin is, which is a very small subset of OS X. Don't for a second mistake OS X as open source.

it still is more friendly towards open source then windows (as in darwin is open source)

---

### Post by Dr. C on 2007-07-08
> **Polygon said:**
> it still is more friendly towards open source then windows (as in darwin is open source)

But don't the recent versions require a TPM (Trusted or Treacherous Platform Module) to boot?

---

### Post by Adamant1988 on 2007-07-08
> **FineE said:**
> But don't the recent versions require a TPM (Trusted or Treacherous Platform Module) to boot?

What does it matter if Macs require that?  They're designed for one OS anyway.

---

### Post by DJ_Max on 2007-07-10
OS X requires TPM, Darwin doesn't.

---

### Post by qpieus on 2007-07-10
> **PhatStreet said:**
> Yep, and let's not forget that the BSD license is a lot less restrictive.

That's right. My understanding is that basically someone can use the licensed code in free OR proprietary software and not have to provide the source code back to the community. That's why Apple can use the BSD userland stuff in OSX and not have give back the source code.

---

### Post by Hex_Mandos on 2007-07-10
OSX is far more restrictive than Windows, let alone Ubuntu or any other Distro. At least with Windows I can install the OS in any computer that's powerful enough. Darwin code is worthless to me (and the world at large, basically nobody uses Darwin and the license is GPL-incompatible, so Linux, and the BSDs can't use it).

---

### Post by macogw on 2007-07-10
> **FineE said:**
> But don't the recent versions require a TPM (Trusted or Treacherous Platform Module) to boot?

Their motherboards have a TC chip, but you can load OSX on a non-Apple computer (a few friends have done it) and you can load non-OSX on Apple computers.  The chip is currently inactive.

---

### Post by phrostbyte on 2007-07-10
OS X built with a lot of open source software, even GPL and LGPL software. The entire WebKit HTML engine is LGPL (based from KHTML, KDE's HTML engine). An HTML engine is A LOT of source code. It also includes Emacs and Vim which are GPL.

---

### Post by DJ_Max on 2007-07-10
> **qpieus said:**
> That's right. My understanding is that basically someone can use the licensed code in free OR proprietary software and not have to provide the source code back to the community. That's why Apple can use the BSD userland stuff in OSX and not have give back the source code.
Yep, BSD license allows you to take base FreeBSD and its source, modify it and sell the result. It does not require you ship sources with your product.

---

### Post by Hex_Mandos on 2007-07-10
> **macogw said:**
> Their motherboards have a TC chip, but you can load OSX on a non-Apple computer (a few friends have done it) and you can load non-OSX on Apple computers.  The chip is currently inactive.

Wrong. What you can install is actually OSx86, an OSX image cracked to eliminate the need for the TPM. A store bought copy of OSX can't be installed on any random computer.

Of course, as OSX isn't designed with hardware compatibility in mind, getting it to work on random hardware is a lottery. It's the logical thing to do, though. I might try installing it someday soon, since my new laptop is a lot like a MacBook internally.

---

### Post by Atomic Dog on 2007-07-11
> **Hex_Mandos said:**
> OSX is far more restrictive than Windows, let alone Ubuntu or any other Distro. At least with Windows I can install the OS in any computer that's powerful enough. Darwin code is worthless to me (and the world at large, basically nobody uses Darwin and the license is GPL-incompatible, so Linux, and the BSDs can't use it).

I don't get the rump swabbery over Apple and their BSD variant OS.  The company claims to be so user friendly and yet treats their customer like open mouthed breathers.  What have they given back?  How much $$$ have they made?

---

