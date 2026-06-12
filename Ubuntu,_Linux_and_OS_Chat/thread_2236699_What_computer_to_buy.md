---
title: "What computer to buy"
date: 2014-07-28
forum: Ubuntu, Linux and OS Chat
---

### Post by rosswmcgee on 2014-07-28
I was unable to install Ubuntu 14.04 lts on any of my older computers that are amd athlon LE-1640 with 1.8gb. I am told ubuntu  14.04lts  will not use these amd

drivers and the drivers are the problem. If I change drivers it crashes the system. So after 10 years or so of never buying a new machine and using 

linux distros I am ready to try a new machine. Question AMD vs. intel and will ubuntu work with AMD at all? I am currently running Mint qiana mate 17 on one computer

the other maya. The older maya is more stable than the qiana, but at least I could install it. Opera works perfectly in Qiana but FF and Tbird often cause

crashes. 

Example Best buy has a dell inspirion with 1tb and 4gb for 329 dollars, do I need more? I am not partial to dell but HP mostly uses AMD. Any sugesstions appreciated. Ross

---

### Post by mikewhatever on 2014-07-28
While Ubuntu 14.04 may be too much for a 10 year old PC, I am pretty sure you can use Xubuntu or Lubuntu 14.04. We might be able to help, if you tell us exactly what the problem was.
What drivers are you talking about? AMD Athlon?

Not sure about LM, if you want help with that, please ask at their dedicated forum.

---

### Post by Rob Sayer on 2014-07-31
I suspect what you found had to do with graphics, and a quick look indicated that that CPU doesn't have integrated graphics.  What I'd do is get the gma info in windows from system information and web search "ubuntu ....".  Or download xubuntu or lubuntu 14.04.1 live cd and burn it (to a usb stick if you can boot one of them) and boot.

You may need to use the nomodeset parameter when you boot.  Open the terminal and enter:

```
lshw -C video
```

which will, I find, give more complete info.

If it's an old AMD/ATI graphics adapter you'll want to stick with the open source driver.  Ditto probably with nvidia.  There are external ppa sources for drivers for old gmas but they're unsupported by ubuntu and not very reliable.

I think you should be able to get a serviceable linux box but don't expect to be able to play HD video properly.

You can't really directly compare mint v. ubuntu on different machines, though mint is actually based on ubuntu with a 6 month or so older kernel version.

One thing I will say about mint, though, which I've had installed on my netbook more than once.  Their tech support is absolutely *dreadful* compared to ubuntu's.  There's nothing wrong with mint per se as a distro for more advanced users but if you're going to need support ubuntu is the only one I'd recommend.

---

### Post by oldrocker99 on 2014-08-01
I've been using AMD CPUs as long as Ive used computers, and any GNU/Linux distribution will work on practically any AMD CPU. In fact, the 32-bit version is named after the first 32-bit processor (i386), and the 64-bit version is named after the first 64-bit processor (AMD64). 

> One thing I will say about mint, though, which I've had installed on my netbook more than once. Their tech support is absolutely dreadful compared to ubuntu's. There's nothing wrong with mint per se as a distro for more advanced users but if you're going to need support ubuntu is the only one I'd recommend.

Truer words were never spoken; I tried Debian once as was dismayed at the number of packages not present in their repositories which are in the Ubuntu repos. Yes, it's more stable than, say, Ubuntu, but I've had very, very few (if any) instability problems using any of the Ubuntu flavors. I started with Ubuntu 8.04, and have used several of the Ubuntu derivatives (Ultimate, Mint, Bodhi) and found all of them to have various annoyances that simply aren't present with Ubuntu. Besides, these forums right here are an amazingly complete set of knowledge, where nearly every poblem's solution can be found.

Kubuntu 14.04
16 GB PC1333 RAM
GeForce 650ti

---

