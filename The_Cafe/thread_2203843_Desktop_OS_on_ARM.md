---
title: "Desktop OS on ARM"
date: 2014-02-05
forum: The Cafe
---

### Post by alex143 on 2014-02-05
Hi thanks for reading, This is going to be a bit long, but I encourage anyone to throw in any input to better my journey. 

To start off I'm not a coder, just an enthusiast. My goal is trying to find/work/compile a full fledged desktop OS for a mobile phone (ARM based). I've been watching over the Ubuntu phone for a while now and I like where it's going however it's not actually what I'm looking for. I'm looking for a UMPC with full copy of Ubuntu on it. 

Some might ask why, I say why not? Its obviously not going to be for everyone, but the possibilities of having a desktop OS on a mobile device explain itself. We're not looking to run Half-Life  on them, but actually having the ability for total multitask is a selling point in itself. 

I know for a fact what I'm researching is very possible, And I guess what brings me here is to ask you this question: What am I missing? What is the next step? and is there any sort of project going on right now that I don't know about?


I've been on #ubuntu IRC and I did manage to get some insightful answers. Can anyone expand on this? 

 
*                > ===        IRC: freenode #ubuntu [http://www.ubuntu.com](http://www.ubuntu.com)*> 
                **medo:   Hi there, I have a few questions. Why exactly is it not possible to have Ubuntu Desktop on an ARM based phone?**
                **jinzo:**     medo, I'm no Ubuntu expert but there're several reasons probably: From that not all packages compile on ARM, that the unity probably utilizes OpenGL that is not supported by the graphic drivers in ARM SoC-es (OpenGLES is used there), and so forth
             **witheld1:**               medo, jinzo is wrong
                **ActionParsnip:**  jinzo, I wouldn’t use Unity on ARM personally
**                    jinzo:** ActionParsnip, I was listing technical reasons that came to mind
                **ActionParsnip:**  jinzo: makes sense. I'd run openbox or fluxbox to keep the desktop light
 
 
                **medo:   I guess the same question would apply to Windows RT. I understand the source code isn't available to the public, but I find it hard to believe I am the only person in the world that would love to see a fully functional UMPC; Especially with phones seemingly getting bigger. I could see a Galaxy Note utilizing that very well, and even the HTC one.**
                **witheld1:**   and you could have Ubuntu on your phone, the packages are technically there, but drivers are a problem. However, Wayland and Mir have an android driver backend so you can probably hack something up with enough time and effort, but you're definitely not going to run X on 90% of devices, the drivers just don't exist.
                **medo:**          So I'm assuming it's just due to not having the patience to compile?
                **witheld1:**    For the most part the compiling is done; Ubuntu has ARM packages for basically everything.
                **jinzo:**            There's also the problem with ASM code, and optimization, and whatnot when it comes to compiling software written with x86 in mind for ARM.
                **witheld1:**     That's less than 1% of packages, The Rasbian guys figured that out, basically everything will work if you can actually manage to get it on there.
                **jinzo:**            Yes? What do I know - there're constant breakages and problems with compiling stuff like python, Firefox, chromium when I'm trying it.
 
                **medo:   So what are the key things holding it back?**
                **witheld1:**            Other than graphics and probably kernels, you'll have to do that yourself.  Well, for one, I own a MIPS laptop, and an ARM Raspberry Pi and everything works.
                **jinzo:**     That doesn’t mean it was easy to get it working.
                **witheld1:**            but it's already working, other than kernels and graphics. Of course, those are also the hardest to get working. So good luck.
                **ActionParsnip:**  It'll get better, it’s how it goes.
                **witheld1:**            Perhaps, especially on NVidia devices now, since they're now contributing to the kernel for ARM devices.
 
                **medo:   So where would I go to support a project like this? I can't seem to find much.**
                **witheld1:**       You build it yourself, The project that is, you take your phone, you find out what needs to be done, then you do those things, there's no real interest in right now, since phones are only just getting powerful enough for that kind of thing.
                **medo:   **I understand, thank you for all who had input on my question. I appreciate it.

---

### Post by grahammechanical on 2014-02-05
I think you are missing a couple of points.

1) Ubuntu (for phones) is at version 1.0 = optimised for the phone. Work is being done to bring it up to version 1.5 = optimised for tablets. Further more, work is just starting to converge the Ubuntu phone/tablet platform with the desktop platform so that there is one code base. The aim is to complete this convergence between the release of Ubuntu 14.10 and Ubuntu 15.04.

2) Ubuntu developers have for some time been working on getting Ubuntu images for ARM CPUs.

[https://wiki.ubuntu.com/ARM](https://wiki.ubuntu.com/ARM)

Regards.

---

### Post by lykwydchykyn on 2014-02-05
Debian has had ARM ports for years; see [https://wiki.debian.org/ArmPorts](https://wiki.debian.org/ArmPorts).  I'm no expert, but my understanding about ARM is that it's a little more "wild west" than x86, and just because one thing is ARM and another thing is built for ARM doesn't mean the two will actually talk, you have to get a little more specific about chipsets, ABI versions, and so forth.

---

