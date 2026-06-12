---
title: "Why nvidia chipset is better than ATi and Intel ?"
date: 2009-06-30
forum: The Cafe
---

### Post by ubfu on 2009-06-30
I browse some post about Ati graphic card xorg problem , most of the member suggest the user to sell off thier Ati graphic card and get a new Nvidia card.
I saw there are a lot of Ati chipset problem with xorg

Why they suggested that ? Is anything link to some open source problem ?

---

### Post by Paqman on 2009-06-30
Intel is normally fine, they produce good open source drivers so Linux systems can normally run Intel graphics chipsets without any extra drivers. There's currently a problem with Intel on Jaunty, but that'll be fixed for the next release.

Nvidia also produce decent drivers, although they're not open source.

ATI/AMD have historically dragged the chain badly. Things are improving, but support for their cards is still pretty hit-and-miss.

---

### Post by 3rdalbum on 2009-06-30
> **ubfu said:**
> I browse some post about Ati graphic card xorg problem , most of the member suggest the user to sell off thier Ati graphic card and get a new Nvidia card.
I saw there are a lot of Ati chipset problem with xorg

Why they suggested that ? Is anything link to some open source problem ?

It's a proprietary software problem. ATI's drivers are poor quality, but they don't make the source code available; so we can't see where the problems are and we can't help ATI make the drivers better.

Nvidia's drivers are much better, to start off with. They're still closed-source, but they don't need anywhere near as much work as ATI's driver.

Intel graphics drivers are open-source, but the main problem with Intel graphics is that they have very low performance - the Intel graphics chipsets haven't been updated in years and were only ever intended as a basic 3D accelerator. Even an ATI graphics card, with its buggy Linux drivers, will give you better performance.

---

### Post by origin248 on 2009-06-30
Ok, so if I'm going to be buying a new graphics card/computer should be the rule of thumb be getting a nvidia card over the ATI one for Linux support?

---

### Post by gradinaruvasile on 2009-06-30
For the moment, i would say yes.

---

### Post by Miljet on 2009-06-30
There has been some suggestions that ATI is going to release their drivers as open source. But I haven't been able to find any confirmation about when, or if, that is going to happen.

Even if they released the source code for their drivers tomorrow, it would take Linux developers a little time to optimize the code.

So, for the time being, nvidia is the best bet.

---

### Post by origin248 on 2009-06-30
Would really love it if Ati does make it open source.  But somehow I'm not holding my breath.  That's too bad, I'm a fairly big fan of the value offered in the Radeon range.

---

### Post by prvteprts on 2009-06-30
> **origin248 said:**
> Would really love it if Ati does make it open source.  But somehow I'm not holding my breath.  That's too bad, I'm a fairly big fan of the value offered in the Radeon range.

Me too. There's a lot of nice things to admire about AMD/ATI especially now that they have merged. I have also read about ATI to be opening up their code for their drivers. It would benefit them too if they did that because more of the FOSS community would most likely support their products.

---

### Post by TheOrangePeanut on 2009-06-30
They won't release their proprietary driver because there is code in there that is not the intellectual property.  However, Ati has released full documentation for r500/r600 cards and will release documentation for newer generations as well.  This means that open source developers will never be locked out of developing for these cards and they don't need to be reversed engineered, either.  Also, there are a couple of developers that work for Ati that develop for the Linux stack (bridgeman from Phoronix forums and Alex... something or other as well).

Ati is poised to be the best bed for open source drivers in [I]time[I], but for now, Nvidia is top dog.

---

### Post by Arup on 2009-06-30
One word........drivers and driver development, vpdau which lets you use your GPU power to watch movies is one prime example of good work in right direciton from nvidia, neither Intel nor AMD has anything on the anvil regarding that. VDPAU enables you to watch hd movies in full screen even on older weaker PCs with slow CPU as all the work is done by the GPU. Also nvidia brings in many new stuff like open cl etc. Each and every nvidia driver brings some new stuff, some improvements and work and driver releases are more frequent than the other two.

---

### Post by 3rdalbum on 2009-06-30
Nvidia is top dog on Linux.

Intel may change the game with Larrabee (an upcoming graphics/GPGPU chipset they are working on) but I think Nvidia will still be the smart choice for performance and compatibility.

---

### Post by ssri on 2009-07-01
> **TheOrangePeanut said:**
> They won't release their proprietary driver because there is code in there that is not the intellectual property.  However, Ati has released full documentation for r500/r600 cards and will release documentation for newer generations as well.

Even though they released docs for r500 last year, there is still no GLSL, OpenGL 2.0 support.  The devs stated on phoronix that there will be no gains for either until gallium3D is stabilized, which won't happen till next year in the earliest.  One full year after ATI/AMD relegated cards that supported OpenGL 2.0 into legacy (lackof) support.  I'm sorry if I do not get misty-eyed, as you do, with ATI/AMD's crappy handling of this situation.

---

### Post by moster on 2009-07-01
I have laptop with everything AMD in it. I buy in end 2007 and it work near how I imagine only in Ubuntu 9.10 alpha. When  that ubuntu finally come, that laptop will be garbage.

In another case. I install Ubuntu on relative new nvidia chipset with integrated VGA and I feared I would have problems... But it worked perfectly. It seems that nvidia is fast in distributing chipset specifications to linux hardware experts.

I was AMD fan until I realize they are worst then others. Do not push your luck, buy nvidia/intel for now.

---

### Post by origin248 on 2009-07-02
Guess nVidia is the way to go for tme then. Thanks everyone for their replies.

---

