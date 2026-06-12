---
title: "What is the point in opensource graphic drivers ..."
date: 2009-08-02
forum: The Cafe
---

### Post by YukaToshi on 2009-08-02
... that have active proprietary driver support? Maybe I'm just being ignorant, and if so please correct me, as I currently don't see the point.

---

### Post by swoll1980 on 2009-08-02
Software Freedom. Same reason all these other programs are around.

---

### Post by gletob on 2009-08-02
Because ATI can say (and has): "Ok in our next proprietary direver we'll be dropping support for Card 1, 2, 3, and etc."

Because the community has more control over the driver, and simply the fact that most of us live in a free country and can do whatever the hell we want to do with our spare time.

---

### Post by wrtpeeps on 2009-08-02
There is none.

---

### Post by Viva on 2009-08-02
They are open source.

---

### Post by Tipped OuT on 2009-08-02
I am glad they have open source drivers. My ATI card is no longer supported, so if they didn't have open source drivers for my card, I would have to be stuck using Windows XP... forever. :(

---

### Post by Viva on 2009-08-02
> **Tipped OuT said:**
> I am glad they have open source drivers. My ATI card is no longer supported, so if they didn't have open source drivers for my card, I would have to be stuck using Windows XP... forever. :(

The card won't be supported on XP either, No?

---

### Post by spoons on 2009-08-02
> **Viva said:**
> The card won't be supported on XP either, No?

The XP drivers are much better than the Linux ones. About a million times better. So the (albiet a bit old) driver for his card on XP would do fine.

---

### Post by .Maleficus. on 2009-08-02
> **gletob said:**
> and simply the fact that most of us live in a free country and can do whatever the hell we want to do with our spare time.
Care to explain that one?  What does location/spare time have to do with open source?  I guess I could see writing a driver out of boredom in your spare time but AFAIK there are no countries that restrict driver usage.

---

### Post by Tipped OuT on 2009-08-02
> **Viva said:**
> The card won't be supported on XP either, No?

Yes, but at least I would have drivers. Understand? **_If_** Linux didn't have open source drivers for my hardware, I'd be stuck on Windows XP. Because that would be the only operating system that has drivers for my hardware.

---

### Post by benj1 on 2009-08-02
MS office has [active support for odf]("http://www.robweir.com/blog/2009/05/update-on-odf-spreadsheet.html"), does that mean we dont need open source alternatives?

also so you don't have to rely on a company for support, when it isn't really in their financial interests to provide that support.

---

### Post by gnomeuser on 2009-08-02
Ask yourself these questions:

How do you vet a driver for correctness when you have no source code? (you don't, and since no programmer is perfect the code will have bugs, these cause software to crash - e.g. the nvidia module has a history of abusing the stack causing applications to crash randomly).

How do you vet a driver for security for which you have no source code? 

You don't, and drivers like the nvidia module load megs of code directly into your kernel at high privilage levels, code you have no direct way of ensuring what does - security issues can and have happened with that very module and you are at the mercy of the vendor to fix them.. feel safe?

How do you support platforms the vendor has no interest in such as the PS3 under Linux when you have no source? 

Again, you don't, meaning a number of users are out in the cold and entry to the market for players who aren't supported platforms is harder - point in case currently ARM, Linux on the PS3 and the Loongson MIPS based platform which is becoming popular in China.

How do you support outdated hardware which the vendor has obsoleted in their driver and actively removed both support and the code for when you have no source? 

You don't, that hardware is effectively turned into a crippled version of it's former glory for no reason - costing you money and costing the environment for the quick replacements this tactic is designed to further.

How do you ensure timely updates to the driver when the underlying system requires changes but you have no source?

Again a situation where you are in trouble, as a distribution you are now either forced to hold back improvements to your stack for one or two drivers or ship without support. Either way  you are at the mercy of the vendor to update and your business as well as your users suffer.

No.. open source doesn't matter one bit, unless of course one cares about security, stability, platform and use case innovation, control over the platform you (the distribution) ship or enabling users keep perfectly good hardware even if it is no longer profitable for the vendor to support it regardless of it's continued usefulness.

---

### Post by YukaToshi on 2009-08-02
> **gnomeuser said:**
> Ask yourself these questions:

How do you vet a driver for correctness when you have no source code? (you don't, and since no programmer is perfect the code will have bugs, these cause software to crash - e.g. the nvidia module has a history of abusing the stack causing applications to crash randomly).

How do you vet a driver for security for which you have no source code? 

You don't, and drivers like the nvidia module load megs of code directly into your kernel at high privilage levels, code you have no direct way of ensuring what does - security issues can and have happened with that very module and you are at the mercy of the vendor to fix them.. feel safe?

How do you support platforms the vendor has no interest in such as the PS3 under Linux when you have no source? 

Again, you don't, meaning a number of users are out in the cold and entry to the market for players who aren't supported platforms is harder - point in case currently ARM, Linux on the PS3 and the Loongson MIPS based platform which is becoming popular in China.

How do you support outdated hardware which the vendor has obsoleted in their driver and actively removed both support and the code for when you have no source? 

You don't, that hardware is effectively turned into a crippled version of it's former glory for no reason - costing you money and costing the environment for the quick replacements this tactic is designed to further.

How do you ensure timely updates to the driver when the underlying system requires changes but you have no source?

Again a situation where you are in trouble, as a distribution you are now either forced to hold back improvements to your stack for one or two drivers or ship without support. Either way  you are at the mercy of the vendor to update and your business as well as your users suffer.

No.. open source doesn't matter one bit, unless of course one cares about security, stability, platform and use case innovation, control over the platform you (the distribution) ship or enabling users keep perfectly good hardware even if it is no longer profitable for the vendor to support it regardless of it's continued usefulness.


To answer your questions;

1:Vet a driver for correctness? The opensource drivers are far more buggy than the proprietary ones for the same hardware. Even the totally opensource Intel drivers are lacking. No OpenGL 2.0 support?

2:Ok I didn't know it ran so much at root so no argument there.

3: The PS3 is a game console and not a PC so I don't think that is a valid point. As for outdated hardware my original post did state **active proprietary driver support**.

---

### Post by benj1 on 2009-08-02
> 1:Vet a driver for correctness? The opensource drivers are far more buggy than the proprietary ones for the same hardware. Even the totally opensource Intel drivers are lacking. No OpenGL 2.0 support?
i suspect the open source drivers have had to be reverse engineered because they havent been given info on the chips etc, and anyway it is possible for open drivers to be better than their closed counter parts, the opensource linux driver for my mobile broadband dongle is far better than the closed windows driver, second at least there is the chance of improvement, if a company brought out a rubbish closed driver, we would be stuck with it.

> 2:Ok I didn't know it ran so much at root so no argument there.
dont know the details but yes the nvida driver does run as root 

> 3: The PS3 is a game console and not a PC so I don't think that is a valid point. As for outdated hardware my original post did state **active proprietary driver support**.
so are we to wait until a driver stops being supported until we develop an alternative ?
atleast this way, at the very least we have a replacement for when active support stops.

---

### Post by YukaToshi on 2009-08-02
> **benj1 said:**
> i suspect the open source drivers have had to be reverse engineered because they havent been given info on the chips etc, and anyway it is possible for open drivers to be better than their closed counter parts, the opensource linux driver for my mobile broadband dongle is far better than the closed windows driver, second at least there is the chance of improvement, if a company brought out a rubbish closed driver, we would be stuck with it.

They have to be reverse engineered or they have to wait for vendors to release source ala ATi. As for your mobile (3G?) dongle that has nothing to do with this thread, I never questioned opensource wireless drivers, if your wireless driver is even opensource of course.

> dont know the details but yes the nvida driver does run as rootAgain ok, I didn't know that so no argument.


> so are we to wait until a driver stops being supported until we develop an alternative ?
atleast this way, at the very least we have a replacement for when active support stops.Good point especially if you own ATi pre-HD2000.

---

### Post by frrobert on 2009-08-02
> **YukaToshi said:**
> ... that have active proprietary driver support? Maybe I'm just being ignorant, and if so please correct me, as I currently don't see the point.

To answer your question with a question.

What is the point in using an opensource operating system on a computer ...
... that has active support for proprietary operating system 

I am not trying to be a smart aleck but the same freedom you find in using ubuntu is the same freedom you will find in an opensource driver.

---

### Post by Tipped OuT on 2009-08-02
> **frrobert said:**
> To answer your question with a question.

What is the point in using an opensource operating system on a computer ...
... that has active support for proprietary operating system 

I am not trying to be a smart aleck but the same freedom you find in using ubuntu is the same freedom you will find in an opensource driver.

Agreed. :)

---

### Post by Keyper7 on 2009-08-02
> **YukaToshi said:**
> 1:Vet a driver for correctness? The opensource drivers are far more buggy than the proprietary ones for the same hardware. Even the totally opensource Intel drivers are lacking. No OpenGL 2.0 support?

He didn't say "open source drivers are more correct". He said "you are able to see for yourself if open source drivers are correct".

This statement has nothing to do with which driver is currently better.

> **YukaToshi said:**
> 3: The PS3 is a game console and not a PC so I don't think that is a valid point.

Why? It's a computer with an nVidia graphics card and you can install Linux in it.

---

### Post by gnomeuser on 2009-08-03
> **Keyper7 said:**
> He didn't say "open source drivers are more correct". He said "you are able to see for yourself if open source drivers are correct".

This statement has nothing to do with which driver is currently better.


Actually, I said that with Open Source, I can fix the driver with a proprietary driver I am up a certain creek if the vendor finds the issue unimportant. I've done QA for Linux for years and this is a real problem.

> 
Why? It's a computer with an nVidia graphics card and you can install Linux in it.

It's also supported by Sony as running Linux, you can go and buy a Linux kit. Linux was the first platform to run on the Cell chip and is still providing highly efficient computing on such devices - everything in the PS3 runs beautifully on Linux except the video card since nvidia considers it an unimportant target.

He also convienently ignored the ARM and MIPS cases of just the few examples I gave. Nvidia themselves e.g. have recently launched a whole portable platform called Tegra which is basically an ARM CPU with an nvidia card. From a technical stance this is a great platform, e.g. you can compute for 24 hours or watch multiple high definition videos on one full charge. Nvidia themselves are very excited about this platform and rightfully so, it is certain that we will see them bet heavily on it's success. However Nvidia are openly hostile to Linux as a platform on Tegra and refuse to support it so far, meaning Linux users and what devices might be built with it are at a disadvantage it terms of hardware support. Without an open driver any innovation beyond nvidias limited imagination is doomed.

---

### Post by xir_ on 2009-08-04
> **gnomeuser said:**
> 
He also convienently ignored the ARM and MIPS cases of just the few examples I gave. Nvidia themselves e.g. have recently launched a whole portable platform called Tegra which is basically an ARM CPU with an nvidia card. From a technical stance this is a great platform, e.g. you can compute for 24 hours or watch multiple high definition videos on one full charge. Nvidia themselves are very excited about this platform and rightfully so, it is certain that we will see them bet heavily on it's success. However Nvidia are openly hostile to Linux as a platform on Tegra and refuse to support it so far, meaning Linux users and what devices might be built with it are at a disadvantage it terms of hardware support. Without an open driver any innovation beyond nvidias limited imagination is doomed.

What operating system do they want to run on arm other than something linux based? :confused:

Windows CE is hardly going to be a good subsitute. And using something custom would be reinventing the wheel.

---

