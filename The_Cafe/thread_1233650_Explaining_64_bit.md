---
title: "Explaining 64 bit"
date: 2009-08-06
forum: The Cafe
---

### Post by billdotson on 2009-08-06
So, 64 bit allows for double something with processors and it allows a lot more RAM to be used.

I read that XP and Vista 64 bit can't run 16 bit programs, is that a choice or is there some weird incompatibility between 64 bit and 16 bit at the hardware level?

I have a 64 bit processor and I know some driver support is still sketchy (and there aren't many 64 bit apps) but would it be worth having at least one 64 bit OS installed on my computer? (thinking of trying Ubuntu 9.04 64 bit and comparing the Windows 7 32 release candidate and the 64 bit one).

So, other than driver support and the fact that there aren't many 32 bit applications out are there any other cons to 64 bit? 

Please excuse me, until today I thought that you could only run 64 bit apps on a 64 bit OS... (I have no clue why I was so ignorant).

---

### Post by Kingsley on 2009-08-06
This thread should help you answer most of your questions:
[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

---

### Post by gletob on 2009-08-07
I'm running 64 bit on my computer right now.  There are tons of apps that work on 32 and 64 bit platforms.  As far as I know neither 64 bit or 32 bit XP and Vista can run 16 bit apps.  The only program that I have ever had a problem with was Bitpim, it's in the repos and works on my machine but I want the newest Bitpim for better support of my phone.  Other than that it's all smooth sailing.

---

### Post by BoyOfDestiny on 2009-08-07
The main difference is 64-bit is twice as large as 32-bit (duh, I know.) You can usually get speed gains by using more memory (a trade off). Sorry if this is gross over simplification. 

As of lack of 64-bit apps? That's not the case with the majority of Free and Open Source software. What doesn't have a 64-bit port...?

As for 16-bit, if you want 16-bit windows apps to run, use wine. Works just fine.

---

### Post by matthew.ball on 2009-08-07
Because it's base-2, wouldn't 33-bit be double...

2^32 = 4294967296 (~4 gbs)
2^33 = 8589934592 (~8 gbs)
...
2^64 = ~ 1.844674407e19 (~16 million tbs)

But, I am totally lost at this point (no wonder I only got a pass for comp systems....)

---

### Post by SunnyRabbiera on 2009-08-07
Well one can run a 32bit system on a 64bit compatible processor and it can work just as well.
In truth right now you can use either or.

---

### Post by Tipped OuT on 2009-08-07
Either way, 64 bit is the future, and we should all start to adapt to it, so the transition of no more 32 bit will be easier for us.

---

### Post by SunnyRabbiera on 2009-08-07
> **Tipped OuT said:**
> Either way, 64 bit is the future, and we should all start to adapt to it, so the transition of no more 32 bit will be easier for us.

Yes but there are still many PCs that can only use a 32bit kernel, older PC's that still need that kind of kernel.
Pushing 32bit out of the way will not be as easy as pushing 16bit away.

---

### Post by armandh on 2009-08-07
first explaining it [for the non tech]
dear OP
I assume you have noticed that top processor speeds have not jumped up recently? there are a few engineering roadblocks.
besides thermal there is the quaint resistance inversion at 1/4 wave lengths.[open connections appear shorted and shorted appear open] etc.

so if one needs to get more traffic down the highway and the bends in the road prevent higher speed then more lanes are the alt. but moving to 64 lanes [bit] requires re instructing the users [recompiling the OS and programs] of the 32 lanes to use 64. such a change was last experienced when 286 16 bit PC processors gave way to the 386 32 bit processors.

enter the dual mode processors. my sons AMD powered box will process both 64 and 32 bit instruction. since it was 50% faster than his previous box, he has opted for 32 bit until the OS and games catch up.

then he can double boot a 64 bit OS and get double the performance.

another method is the second processor 

deviding the traffic over two highways requires instructions to the alt, but dual processor OS and programs have been arround since before XP. this [and 32/64 processors] is also slowing the 64 bit adoption.

another area of improvement is to off load simple conversion tasks to the output hardware. such video and audio cards doing the codec work keeps the main highways free of such traffic. not to mention on die math [and now phisics] processing.

---

### Post by Tipped OuT on 2009-08-07
> **SunnyRabbiera said:**
> Yes but there are still many PCs that can only use a 32bit kernel, older PC's that still need that kind of kernel.
Pushing 32bit out of the way will not be as easy as pushing 16bit away.

Yes, such as my laptop, but at one point, we all go to move forward. You know what I mean?

---

### Post by ukripper on 2009-08-07
I am running 64bit GNU/LINUX since 2006 and yet to find any big issue with the setup.

---

### Post by 3rdalbum on 2009-08-07
64-bit software and drivers might be hard to find on Windows, but they are not a problem on Linux because everything can be compiled for 64-bit. I mean, Linux software can be compiled for 20 completely different CPU architectures; a simple change of bit width is not an obstacle.

64-bit does not mean "double the performance of 32-bit", nor does it mean "can process two things at a time". 64-bit means that a processor can work with "longer" numbers - bigger, smaller, or to more decimal places. Some mathematical operations take two passes to perform on a 32-bit processor, and one pass on a 64-bit processor.

64-bit processors can work internally with bigger numbers, including bigger memory addresses.

---

### Post by billdotson on 2009-08-08
So if I get the 64 bit version of Jaunty my computer will run faster, or only if I have more than 3GB of RAM (the working RAM limit in 32 bit OSes)?

If all you have to do is recompile for 64 bit architecture why is there a problem even in Windows? Couldn't Crytek just recompile Crysis for 64 bit so it would run faster?

---

### Post by Hallvor on 2009-08-08
Read this: 64 bit will give your computer a performance boost - especially on very CPU intensive tasks, like encoding.

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

---

### Post by 3rdalbum on 2009-08-08
> **billdotson said:**
> So if I get the 64 bit version of Jaunty my computer will run faster, or only if I have more than 3GB of RAM (the working RAM limit in 32 bit OSes)?

If all you have to do is recompile for 64 bit architecture why is there a problem even in Windows? Couldn't Crytek just recompile Crysis for 64 bit so it would run faster?

1. You only see a speed improvement if you have programs that do intense number-crunching; that's where the "long numbers" performance comes into play.

2. Crytek did compile a 64-bit version of Crysis, or so I heard.

The issue with Windows is that program developers only ever targeted 32-bit x86 architecture, whereas FLOSS developers knew that their code would be compiled and run on 20 different CPU architectures. Windows-based developers often wrote convenient (at the time) assumptions into their programs; assumptions that numbers were only 32-bits long, and assumptions that they would only be working in 2 gigabytes of memory. Remember the Millennium Bug? That was a case of programs being written with the assumption that the year was <2000. So it can happen easily enough.

Windows programs, if written correctly, can be recompiled for 64-bit. But all are not written correctly.

Linux programs are almost always written to be fully portable between CPU architectures, so a simple change in bit width doesn't cause any problems. A notable exception is Flash Player, which is tremendously ironic seeing as it's probably the most ported proprietary software ever!

---

### Post by hobo14 on 2009-08-08
> **matthew.ball said:**
> Because it's base-2, wouldn't 33-bit be double...

2^32 = 4294967296 (~4 gbs)
2^33 = 8589934592 (~8 gbs)
...
2^64 = ~ 1.844674407e19 (~16 million tbs)

But, I am totally lost at this point (no wonder I only got a pass for comp systems....)


No....
64 bits is just that; 64 bits, not a kilobyte, or gigabytes or terabytes!

2^64 is the number of possible combinations (numbers representable) of 64 bits.  This can, for example allow addressing of 16 million TB (assuming your numbers above are correct, I didn't check) of RAM.

Buses will go from 32 bits wide to 64 bits wide, doubling their "capacity". Sort of like doubling the number of lanes on a road, or the cross sectional area of a pipe.

These are the two main benefits of 64 bit architecture (very simply).

---

### Post by .Maleficus. on 2009-08-08
> **billdotson said:**
> So if I get the 64 bit version of Jaunty my computer will run faster, or only if I have more than 3GB of RAM (the working RAM limit in 32 bit OSes)?

If all you have to do is recompile for 64 bit architecture why is there a problem even in Windows? Couldn't Crytek just recompile Crysis for 64 bit so it would run faster?
It will run "faster", but whether or not you can tell is for you to decide.

As for the problem with Windows, I'm not familiar with the one your talking about.  There isn't one.  Since the release of Vista, most of the computers we sell at work have had 64-bit.  ALL computers with 4GB+ of RAM will have it, and some with 3GB have to too, just to make it upgradeable.  I've been running 64-bit Windows since Vista and the only program I've ever had a problem with was the TI Connect software.  I've also never had a customer come back to the store after buying a computer because a certain program wouldn't work.

And Crysis is already 64-bit.  It was optimized for mutli-core CPUs out-of-the-box.

---

### Post by BigSilly on 2009-08-08
I decided to move to 64 bit with Jaunty. Bit daunted, as I'd heard there were less apps, problems with Flash, that it was only worth it if you have more than 3Gb RAM (I have 3Gb), and some of my favourite emulators don't have 64 bit versions either. In reality, it's been an absolute breeze and it really is much faster. I actually managed to find 64 bit versions of my fave emus just fine, and even found a script to create them myself. For me there has been only benefits from moving over, and I would recommend it to anyone.

---

### Post by 3rdalbum on 2009-08-08
I've just found my first problem with 64-bit (kinda): I can't seem to get Jaunty 64-bit to work as the guest OS, with 64-bit Jaunty as the host, in Virtualbox.

Admittedly that's probably a problem with Virtualbox's 64-bit-on-64-bit support or its hardware virtualisation support, but it's kinda annoying. 32-bit-on-64-bit works fine.

---

