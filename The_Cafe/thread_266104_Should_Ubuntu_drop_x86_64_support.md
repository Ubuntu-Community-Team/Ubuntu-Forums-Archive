---
title: "Should Ubuntu drop x86_64 support ?"
date: 2006-09-26
forum: The Cafe
---

### Post by xXx 0wn3d xXx on 2006-09-26
Should the Ubuntu team stop maintaining the x86_64 version of Ubuntu ? It offers no more then the i386 version. In fact most things don't work with it. As a result they could focus more on the i386 and not have to build the desktop cds for it. Does anyone else think they should ?

---

### Post by Zweih on 2006-09-26
Personally, I think they shouldn't. When 64-bit tech is the standard (in a year or two's time), many people will be (and are) developing programs for the 64-bit architecture. Then thats when Ubuntu x86_64 will become the standard.

---

### Post by rfruth on 2006-09-26
64 bit is the wave of the future, it would be suicide not to plan 4 it :confused:

---

### Post by zachtib on 2006-09-26
no, rather, apt needs to be updated to support multiarch.  once this happens, most of the problems with 64 bit will go away

---

### Post by prizrak on 2006-09-26
Dropping 64bit support is like shooting yourself in the left nut. It hurts and criples functionality. 64 is fairly new but it is going to replace 32 pretty soon.

---

### Post by maniacmusician on 2006-09-26
kinda feel silly, i don't know much about process architecture. I know i have a 32,

but what's the difference between a 64 and a dual/quad-core

as to the OP's question, i believe it should stay. Nothing is perfect at the beginning, but supporting (or at least trying to support) new technologies is critical for an OS.

---

### Post by K.Mandla on 2006-09-26
> **prizrak said:**
> Dropping 64bit support is like shooting yourself in the left nut. It hurts and criples functionality. 
BWAHAHAHA!

---

### Post by xXx 0wn3d xXx on 2006-09-26
Whats so much better about 64 bit versus 32 bit ?

---

### Post by prizrak on 2006-09-26
> **maniacmusician said:**
> kinda feel silly, i don't know much about process architecture. I know i have a 32,

but what's the difference between a 64 and a dual/quad-core

as to the OP's question, i believe it should stay. Nothing is perfect at the beginning, but supporting (or at least trying to support) new technologies is critical for an OS.
> Whats so much better about 64 bit versus 32 bit?
To not mislead you with what I think I know here is a link to Wikipedia [http://en.wikipedia.org/wiki/64_bit](http://en.wikipedia.org/wiki/64_bit)

A dual and quad core CPU's refer to the number of CPU cores on one chip. Quad is four and dual is two. Normally multi CPU systems will have more than one physical chip, which would include the core, cache and w/e other facilities happen to reside on the chip (in AMD's case it's also a memory controller). In a multicore CPU the physical chip contains more than one core (the thing that does the actual math) but they all share the other facilities. (I do believe each core comes with own level 1 cache but don't worry about that for now)

---

### Post by maniacmusician on 2006-09-26
so right now multicore cpu's are 32-bit each? nifty. 64-bit multi-core cpu's would be nice once we get the support to be better.

---

### Post by Ziox on 2006-09-26
> **maniacmusician said:**
> so right now multicore cpu's are 32-bit each? nifty. 64-bit multi-core cpu's would be nice once we get the support to be better.

I believe that AMD has Athlon 64 X2, which is dual 64-bit processors...

64 is definately staying

---

### Post by Rhapsody on 2006-09-26
> **maniacmusician said:**
> so right now multicore cpu's are 32-bit each? nifty. 64-bit multi-core cpu's would be nice once we get the support to be better.
The Intel Core 2 Duo and AMD Athlon 64 X2 are both dual-core 64-bit CPUs. Later this year, we'll see the Core 2 Kentsfield as well, which is going to be a quad-core 64-bit CPU. That'll certainly be interesting.

Seeing as my next CPU will almost certainly be a 64-bit CPU, I voted to keep going on 64-bit development. 32-bit is a dead end now, both Intel and AMD are going to push for 64-bit to be the new standard, and we'll all benefit in the end.

---

### Post by gurgle on 2006-09-26
> **xXx 0wn3d xXx said:**
> Should the Ubuntu team stop maintaining the x86_64 version of Ubuntu ? It offers no more then the i386 version. In fact most things don't work with it. As a result they could focus more on the i386 and not have to build the desktop cds for it. Does anyone else think they should ?

FUD.

---

### Post by siimo on 2006-09-27
> **prizrak said:**
> Dropping 64bit support is like shooting yourself in the left nut. It hurts and criples functionality. 64 is fairly new but it is going to replace 32 pretty soon.

I don't think it will be replaced any time soon!

Speed increase is not noticable.

Adobe is not working on flash player for 64bit even the new FLASH 9 will be 32bit only.

Codecs are all still 32bit - not sure if Vista64 will use 32bit codecs or if new codecs will come out for quicktime/wmv/real etc after vista 64 ships.

There are millions of 32bit computers in the world still very capable! 

there is TONS of 32bit software out there.


My guess is that 32bit will remain mainstream for atleast 5 years.. even then it wont be "replaced", though might become less popular than 64bit but thats a long long way off.



to original poster: i think it shouldn't be dropped! even if it does get dropped theres tons of enthusiasts with 64bit machines and will want to build a 64bit version themselves - Kind of like  slamd64 for slackware etc.

---

### Post by angkor on 2006-09-27
> **xXx 0wn3d xXx said:**
> In fact most things don't work with it.

Of course it should stay, I'm using it atm. ;) Can you explain what exactly doesn't work?

---

### Post by Krakatos on 2006-09-27
Drop it? Any why? It is unquestionable that 64bit is the way to the future. Most likely somewhere during 2007, all the cpus on the market (except leftovers) will be 64bit. What would be the point of doing something suicidal?

Apart from the fact that I use it, and it works. The only things that do not work are:
- flash (but you CAN install it if you want to mess a bit)
- wmv9 videos (but, same as above)
- ok, the repositories sometimes contains packages a little older

That's it. I personally don't see any other difference..... What other things you think do not work?

---

### Post by JsPr on 2006-09-27
Drop 64-bit??? OK, and cars didn't replace horses either. :-)

---

### Post by mips on 2006-09-27
The problem is this, Debian has no real multi-arch support. Ubuntu is based on Debian so the problem is the same.

If you want to use 64bit then I suggest you use a Distro that is multi-arch and not based on debian. Your experiences would be better.

---

### Post by prizrak on 2006-09-27
> **siimo said:**
> I don't think it will be replaced any time soon!

Speed increase is not noticable.

Adobe is not working on flash player for 64bit even the new FLASH 9 will be 32bit only.

Codecs are all still 32bit - not sure if Vista64 will use 32bit codecs or if new codecs will come out for quicktime/wmv/real etc after vista 64 ships.

There are millions of 32bit computers in the world still very capable! 

there is TONS of 32bit software out there.


My guess is that 32bit will remain mainstream for atleast 5 years.. even then it wont be "replaced", though might become less popular than 64bit but thats a long long way off.



to original poster: i think it shouldn't be dropped! even if it does get dropped theres tons of enthusiasts with 64bit machines and will want to build a 64bit version themselves - Kind of like  slamd64 for slackware etc.

Practical reasons may not dictate the death of 32bit but marketing does. All new "regular" (by that I mean not Sempron or Celeron and even then I  think those are switched over) CPU's are 64bit. Vista will come with native 64bit support and I'm sure will still be bundled woth new machines. While I agree that in a practical sense 32bit is more than fine for any kind of desktop/laptop use the chipmakers will kill 32bit off as quickly as possible. 

> The problem is this, Debian has no real multi-arch support. Ubuntu is based on Debian so the problem is the same.

If you want to use 64bit then I suggest you use a Distro that is multi-arch and not based on debian. Your experiences would be better.
From what I know Gentoo is the best as far as 64bit support goes.

---

### Post by Krakatos on 2006-09-27
> **mips said:**
> The problem is this, Debian has no real multi-arch support. Ubuntu is based on Debian so the problem is the same.

If you want to use 64bit then I suggest you use a Distro that is multi-arch and not based on debian. Your experiences would be better.


Well, that may be true, but it doesn't mean it should be this way. As many have posted, 64 bit processors are the future. ok, it's not unavoidable to buy a 64bit processor right now, but it will be soon. 
With all due respect to debian (cause it was debian that made Ubuntu possible, and it still is  avery important support for it), their way is NOT the way to spread linux to the world. Ubuntu in fact is doing a lot better...

What I mean, 64 bit support will be as critical to GNU/linux success (or lack of thereof) as the graphics and eyecandy (how many millions people like windows cause of graphics? how many download illegaly programs to add skins?) and simplicity and functionality.

If open source software is to spread, a certain degree of adaptation to the masses' tastes is unavoidable. No use in saying: but I can do everything with shell. Most users will never use a shell, no matter what .. Just an example of course...

---

### Post by mips on 2006-09-27
> **prizrak said:**
> 
From what I know Gentoo is the best as far as 64bit support goes.

That's what I've heard as well. Have a look at 64bit Sabayon Linux based on Gentoo, very nice.

---

### Post by mips on 2006-09-27
> **Krakatos said:**
> Well, that may be true, but it doesn't mean it should be this way. 

Yes, but unfortunately it is for now. What we want and what we get are two different things. It would be nice if debian gave us multi-arch.

Being pratical I would say try another distro.

---

### Post by henriquemaia on 2006-09-27
Hey??? What?? I'm writing this post on my Dapper 64bit where there's very little I can complain about it, and you ask if Ubuntu should kill it?

No way!

:D

---

### Post by bluenova on 2006-09-27
> **Krakatos said:**
> Drop it? Any why? It is unquestionable that 64bit is the way to the future. Most likely somewhere during 2007, all the cpus on the market (except leftovers) will be 64bit. What would be the point of doing something suicidal?

Apart from the fact that I use it, and it works. The only things that do not work are:
- flash (but you CAN install it if you want to mess a bit)
- wmv9 videos (but, same as above)
- ok, the repositories sometimes contains packages a little older

That's it. I personally don't see any other difference..... What other things you think do not work?
I'm looking to build a new system at the moment, and my parts retailer doesn't have any AMD 32 bit chips available only AMD 64.

---

### Post by mips on 2006-09-27
> **bluenova said:**
> I'm looking to build a new system at the moment, and my parts retailer doesn't have any AMD 32 bit chips available only AMD 64.

Thats not a problem You can still use a 32bit OS or one of many 64bit OSs.

---

### Post by kripkenstein on 2006-09-27
> **xXx 0wn3d xXx said:**
> Should the Ubuntu team stop maintaining the x86_64 version of Ubuntu ? It offers no more then the i386 version. In fact most things don't work with it. **As a result they could focus more on the i386** and not have to build the desktop cds for it. Does anyone else think they should ? [emphasis mine]

Actually having a 64-bit version benefits the 32-bit. It seems counterintuitive, at first, but it isn't: testing on more than one platform is a good way to get rid of certain very subtle bugs. Sometimes code 'works', but it doesn't work because of the coder's intent - it works because of a coincidence in how things are compiled and executed. Developing for many architectures is the best way to detect such bugs.

---

### Post by Virak on 2006-09-27
I am currently using an x86-64 Ubuntu install, so no. If Ubuntu drops x86-64 support, then I and likely many others using it will switch to another distro.

---

### Post by bonzodog on 2006-09-27
No, definitly not. Most new hardware is 64 bit now, and 64 bit development is coming along at a fair pace. Nearly every major distro has HAD to develop a 64 bit port, as it has become a nessecity. I am just waiting for the initial port of Zenwalk to x86-64.

---

### Post by bruce89 on 2006-09-27
> **bluenova said:**
> I'm looking to build a new system at the moment, and my parts retailer doesn't have any AMD 32 bit chips available only AMD 64.

AMD only makes 64 bit chips now AFAIK.

Here is a line explaining why AMD64 support shouldn't be dropped - > Linux Scooby-Doo 2.6.17-9-generic #2 SMP Thu Sep 21 22:33:03 UTC 2006 x86_64 GNU/Linux

What reason would there be to drop AMD64?  PowerPC could be dropped in a few years time probably.

> **Krakatos said:**
> - ok, the repositories sometimes contains packages a little older

How?

> **siimo said:**
> there is TONS of 32bit software out there.

Any software which provides the source code can be compiled on AMD64 usually.

> **xXx 0wn3d xXx said:**
> Whats so much better about 64 bit versus 32 bit ?

Essentially, 64 bit allows more than 4GiB of memory to be installed.

---

### Post by mips on 2006-09-27
> **bruce89 said:**
> 
Essentially, 64 bit allows more than 4GiB of memory to be installed.

It's not only that. Data can also be move around faster seing you have a 64bit bus/instruction set.

---

### Post by .t. on 2006-09-27
And don't forget more registers!

---

### Post by siimo on 2006-09-28
> **mips said:**
> It's not only that. Data can also be move around faster seing you have a 64bit bus/instruction set.

I dont think thats correct. 

but you can have larger data as you are able to address more memory.

---

### Post by gnomeuser on 2006-09-28
Offers nothing more???? Excuse me did your mother drop you as a child or something becuase that's so wrong it's not even right. :confused:  :confused: 

64 bit bares with it significant performance increases, take a simple string operation with 64 bit optimization that goes at least twice as fast on the same CPU. 

But sure if you want to take the future of desktop computing and throw it out the window for no reason what so ever.. why? And don't say proprietary software, we have no control over that to fix it for 64 Bit.. complain to the relevant software vendors to get it fixed.

---

### Post by Kindred on 2006-09-28
Nah... get rid of 32 bit support if anything, this is 2006. ;) :mrgreen:

---

### Post by gnomeuser on 2006-09-28
> **Kindred said:**
> Nah... get rid of 32 bit support if anything, this is 2006. ;) :mrgreen:

Don't be so hasty to dismiss that notion, there has been serious talk of moving i386 to be a subarch of x86_64 in the next few years in the kernel. This would mean we are moving to defaulting to 64bit, we are already seeing a big marketshare of 64bit capable cpus today nearly every new computer sold has 64bit technology, it wouldn't be unthinkable that we would see 64bit be the assumption rather than the exception within say 2-3 years after which it would make sense to default to make Ubuntu x86_64 only and then handle i386 as a subarch.

So this is very likely to happen although it will take a bit to get there.

---

### Post by BWF89 on 2006-09-28
64bit is the future of computers. Mabye it's not very popular now but in a couple of years it will be.

---

