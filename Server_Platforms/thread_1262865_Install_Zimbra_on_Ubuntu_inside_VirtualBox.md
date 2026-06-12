---
title: "Install Zimbra on Ubuntu inside VirtualBox"
date: 2009-09-10
forum: Server Platforms
---

### Post by jakekatz on 2009-09-10
Just realized this deals with many topics, so, I hope it's in the correct forum...

I'm running Solaris 10 x64 x86 on AMD dual core 6GB Ram

I installed VirtualBox 3.0.6 for Solaris x86_AMD64

Inside VirtualBox I installed **Ubuntu 8.04.3 LTS x64 Server Edition**

In installed all Zimbra prerequisites, and install.sh script confirms it's all good.

Install proceeds, but the Virtual Box just up and crashes during install of 3rd package:
[B]
zimbra-core.......... .pkg[/B] 

without any error, it just dies, and Virtual box says "The virtual machine has encountered a severe error"  [No kidding] :(

Has anyone else have/had this same problem, I'm shooting in the dark, but there may be someone that's as geeky as I and have the same setup.

Tks.

(... off to post to the Zimbra forums also)

Hardware AMD 64 (dual core)
OS: Solaris 10 x86_64 [**global zone**]
Virtualize S/W: VirtualBox 3.0.6 for Solaris and OpenSolaris hosts x86/amd64
[COLOR=Blue]Guest OS: Ubuntu: 8.04.3 LTS x64 Server Edition[/COLOR]
Problem Software: Zimbra zcs-6.0.0_GA_1802.UBUNTU8_64

---

### Post by recentcoin on 2009-09-10
Have you verified that your Zimbra package is indeed good and will install on a "normal" Ubuntu server?

That's about the only suggestion I can offer.  I haven't played with VirtualBox at all.  We use VMWare ESX or Xend for that.

---

