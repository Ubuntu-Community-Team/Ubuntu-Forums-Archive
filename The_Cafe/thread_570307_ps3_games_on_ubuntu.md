---
title: "ps3 games on ubuntu?"
date: 2007-10-08
forum: The Cafe
---

### Post by bone2006 on 2007-10-08
I was reading how ps3 was going to use linux, but scrapped it the last minute.  The one thing I just don't understand and maybe somebody can help me out here, is if you can install ubuntu on the ps3, why can't you play ps3 games on a regular ubuntu machine? Is it because of the CPU?  No emulator either?

---

### Post by Leeghoofd on 2007-10-08
> **bone2006 said:**
> I was reading how ps3 was going to use linux, but scrapped it the last minute.  The one thing I just don't understand and maybe somebody can help me out here, is if you can install ubuntu on the ps3, why can't you play ps3 games on a regular ubuntu machine? Is it because of the CPU?  No emulator either?

As far as I'm aware the ps3 user IBM processors with a large number of cores. The architecture is completly different from Intel based machines and you wont be able to get a simular pc configuration. So yes, processors would be one of the reasons you will not be seeying any ps3 games on your average pc system. Another reason is that programmers have a unique code for the ps3 that adress hardware in a specific way, so getting it to work on other systems would be next to impossible.

---

### Post by andy gee on 2007-10-08
> The one thing I just don't understand and maybe somebody can help me out here, is if you can install ubuntu on the ps3, why can't you play ps3 games on a regular ubuntu machine? Is it because of the CPU? No emulator either?

Maybe these examples will help: 

[LIST]
[*]you can install Linux on a Windows PC but you can't play Windows games on Linux (without WINE, and even then it's not certain).
[*]you can install Linux on a Mac, but you can't play Mac games on a regular PC with a Linux-based OS.
[/LIST]

I think you have to have the same system OS to run the same games. There are also system architecture issues (eg 32 vs 64 bit), which might make running something like WINE problematic. Hope this helps.

---

### Post by Lord Illidan on 2007-10-08
Yes, I read somewhere that the game OS is not Linux..Although you can install Linux on it, it doesn't follow that you can install the games on Linux.

---

### Post by incidence on 2007-10-08
And I bet that the games are compiled and optimized only for the Cell architecture.

---

### Post by peterbrewer on 2007-10-08
A large amount of the problem is that the PS3 isn't using a standard processor, its using something specific to it made by ibm.  Therefore an emulator would require a pc at least 10x more powerful than the ps3 or a ps3 in which case you play the games on that.

---

### Post by incidence on 2007-10-08
> **peterbrewer said:**
> A large amount of the problem is that the PS3 isn't using a standard processor, its using something specific to it made by ibm.  Therefore an emulator would require a pc at least 10x more powerful than the ps3 

You can get over 10x more powerful pc than ps3 is, with a couple PCI card's [URL="http://www.clearspeed.com/products/cs_advance/"]
http://www.clearspeed.com/products/cs_advance/
[/URL] :)

> 
a 3.2 GHz Cell with 8 SPEs delivering a performance equal to 100 GFLOPS on an average double precision Linpack 4096x4096 matrix.

Took that from [http://en.wikipedia.org/wiki/Cell_microprocessor]("http://en.wikipedia.org/wiki/Cell_microprocessor")

---

### Post by bone2006 on 2007-10-08
Lord Illidan answered what I was really looking for.  The OS isn't linux based and even though you can install Linux on the OS it's not going to play the games.

thanks

---

### Post by lagana37 on 2010-02-18
Hey all, I recently got a ps3 for the netflix/blu Ray capabilities. But I was thinking it'd be fun to get a couple games to pass some time. I'm going to grab gta4 this afternoon but wanted to also get something I could play when friends are over. Any recommendations? I like most genres, just looking for a well designed game that won't get stale quickly for me and my buddies. Or, you know, any good game recommendations at all would be awesome... Thank you!

---

### Post by Icehuck on 2010-02-18
No, you won't be able to play PS3 games on Ubuntu. 


Side note - The PS3 is almost the perfect example of physical access /= root access.

---

### Post by swoll1980 on 2010-02-19
> **bone2006 said:**
> I was reading how ps3 was going to use linux, but scrapped it the last minute.  The one thing I just don't understand and maybe somebody can help me out here, is if you can install ubuntu on the ps3, why can't you play ps3 games on a regular ubuntu machine? Is it because of the CPU?  No emulator either?

It's all about how the software (the game) interacts with the hardware (the console). On your computer you do this through the OS. The OS acts as a middle man between the application software, and the hardware. This allows an application to run on more than one set of hardware. The PS3 either has it's own OS, or the games communicate directly with the hardware, I'm not sure in that case. If you can write a program that can translate the instructions from the game into a language your OS can understand then you can play the game on your computer. This type of program is called an emulator.

---

