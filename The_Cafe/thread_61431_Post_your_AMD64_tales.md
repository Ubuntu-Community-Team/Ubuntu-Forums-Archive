---
title: "Post your AMD64 tales"
date: 2005-08-31
forum: The Cafe
---

### Post by Psycs on 2005-08-31
I'm purchasing a new Compaq Presario V2000Z notebook with a AMD Turion 64 processor and a 14" widescreen.

I'm really looking forward to installing Ubuntu Brezzy when I buy it coming November, but so far the prospect of having to deal with incipient 64 bit support on Linux has me very uneasy (that and the fact that the prospective purchase comes with an ATI 200M Xpress chipset. :-?).

Could those of you who've had similar concerns/experiences please share?

---

### Post by Ampersand on 2005-08-31
The only problems I've had with the 64bit version of ubuntu has been with Skype and flash sites.

---

### Post by Takis on 2005-08-31
My main problem was multimedia support, which is for the moment lagging behind quite badly, so I just used the i386 version instead. I can wait.

---

### Post by WildTangent on 2005-08-31
you think its bad in Ubuntu? dont try windows xp x64 edition >_<

-Wild

---

### Post by Ride Jib on 2005-08-31
[QUOTE=WildTangent]you think its bad in Ubuntu? dont try windows xp x64 edition >_<

-Wild[/QUOTE]

yeah, no kidding. I had that thing on my computer for no more than 20 minutes before I got fed up with it.

---

### Post by Psycs on 2005-08-31
[QUOTE=Ride Jib]yeah, no kidding. I had that thing on my computer for no more than 20 minutes before I got fed up with it.[/QUOTE]

Wow, I had no idea!  Is a 64 bit processor worth the trouble or should I just get a Pentium-M and forget about the whole issue?  

I'm mainly thinking of the future, though.  But still, I'm reconsidering my choice.

---

### Post by jdong on 2005-08-31
Hell,no don't go Intel on us! ;)


AMD64 Linux largely varies in experience depending on vendor support level. With Ubuntu, you're virtually forced into a pure64 system. This is mainly because dpkg doesn't yet support resolving dependencies across multiple architectures on one install (i.e. if I pull in gnome 64-bit, I need gtk 64-bit, but I currently have glib 32-bit, which can't support gtk 64-bit, and so on).

As a result, you lose the ability to run most 32-bit programs under Ubuntu, since not that many 32-bit compat libs were built. In addition, you can't choose exactly which 32-bit or 64-bit programs you want -- that's predetermined by the package maintainer... As a result, 32-bit only plugins won't work on 64-bit system, mostly a concern with Flash.



However, on the other side of the spectrum is SuSE. RPM is capable of resolving dependencies across archs, and SuSE's YAST takes full advantage of that. Right now, I'm running SuSE 64-bit, with 32-bit firefox and a few other 32-bit emulated programs, like VMWare, mplayer, and win32codecs. I've tested even swapping out KDE with 32-bit, and YaST fully supports that. It provides you with the option to choose 32-bit vs 64-bit at a package-by-package level.


-------------

With that said, it becomes obvious that at the desktop level AMD64 Ubuntu won't be that attractive to the multimedia fanatic. I'd recommend for you to go 32-bit if you want to run Ubuntu.

As far as performance difference between 32 and 64 bit, I've yet to see much difference in my setup. I mainly installed 64-bit SuSE to evaluate the system's performance and because a friend told me about YaST's hybrid support. Since everything "worked", I decided not to switch back for convenience sake. I can't say that at the desktop level, I've ever felt a speed improvement. Looking at benchmarks, 64-bit has a *slight* advantage during CPU-intensive calculations, like compiling or number-crunching. In addition, large file support is much improved for servers and such.

So, basically, on a laptop, you don't get much more out of 64-bit mode. This isn't to say that you've "wasted" an AMD64 -- these chips were designed to be great 32-bit chips AND 64-bit chips! In the end, you'll still get better performance out of it than with a Pentium M.

---

### Post by WildTangent on 2005-08-31
ya, im going to agree with jdong here, the Turion outperforms the pentium, and it still works great with 32 bit, and youll be prepared for when 64 bit becomes more mature in the coming years (or possibly months)

-Wild

---

### Post by poofyhairguy on 2005-08-31
[QUOTE=Psycs]I'm purchasing a new Compaq Presario V2000Z notebook with a AMD Turion 64 processor and a 14" widescreen.

I'm really looking forward to installing Ubuntu Brezzy when I buy it coming November, but so far the prospect of having to deal with incipient 64 bit support on Linux has me very uneasy (that and the fact that the prospective purchase comes with an ATI 200M Xpress chipset. :-?).[/QUOTE]

Don't be scared. The 32bit version will still fly on there. Why rush a relationship that is not ready?

---

### Post by Psycs on 2005-08-31
poofyhairguy, jdong and Tangent, I thank you all immensely.  I think I'll give it a try, although I still feel I should be crossing my fingers.   

For the non-technical user, like me, these issues are very tough to understand and thus it can be difficult to form a solid opinion for yourself.  Which is not a good thing when you are planning what for you is an important investment.

---

### Post by Psycs on 2005-08-31
Incidentally, I just found a great article comparing the Pentium M and Turion processors.  Highly recommended read @ [Laptop Logic.](http://www.laptoplogic.com/resources/articles/42/5/1/)

> A main reason many people consider purchasing a Turion-based laptop is for x86-64 support. With the release of the 64 bit-capable Windows XP X64 and with Windows Vista coming in 2006, a performance increase by merely updating the OS seems tempting to many. However, one must realize that the shift from 32-bit to 64-bit will take a much longer time than one would expect. Unless you are keeping the laptop for more than a couple years, converting to a 64-bit OS like Vista as soon as it's released is just asking for trouble, due to the countless bugs and lack of softwar e/driver support that are bound to follow. Of course, if you love tinkering with new technology, then x86-64 support is a good reason to choose Turion over Dothan.

---

### Post by jdong on 2005-08-31
First of all, by Pentium M, I hope you mean P4-based Centrinos... If you're comparing a Turion to a standard Pentium M, then Turion dominates PERIOD, no arguments.

Turion has amazing power management, and my experience with AMD64-based PowerNow has been that it's flawlessly fluid at dynamic frequency shifts. With Intel's non-Centrino frequency control, I've seen wacky time warps, 3D applications going into hyperspeed (VERY annoying when using Blender, an entirely OpenGL app), and sometimes even failed Backports compiles.

A Turion is certainly worth your investment, whether or not you use a 64-bit OS. I've used my Athlon64 in 32-bit for all but the recent month of its three years of service, and do not feel I've "wasted" my money in any way. The chip will be very thermally stable, which is **extremely** important in laptops! Go for it!

-----------

**NOTE**: I've never been in contact with a Turion except for minor tests at the computer store, where they have a single turion laptop. If it comes with a built-in wireless card, I highly recommend for you to scope out its compatibility with Linux.

---

### Post by WildTangent on 2005-08-31
[QUOTE=jdong]First of all, by Pentium M, I hope you mean P4-based Centrinos... If you're comparing a Turion to a standard Pentium M, then Turion dominates PERIOD, no arguments.[/QUOTE]
actually, the Pentium M is an amazingly powerful CPU, much more so than mobile P4s, and even full-fledged P4s

[http://www.tomshardware.com/cpu/20050525/index.html](http://www.tomshardware.com/cpu/20050525/index.html)

and the benchmark page:
[http://www.tomshardware.com/cpu/20050525/pentium4-10.html](http://www.tomshardware.com/cpu/20050525/pentium4-10.html)
yes, it beat even the mighty Athlon FX-55, and the P4EE. granted, this was done with an overclocked CPU, but the top model still holds its own quite well.

the Turion is still awesome though :) much cheaper too

-Wild

---

### Post by jdong on 2005-08-31
I wasn't talking about sheer power, more about mobility, both temperature tolerance, heat generation, and power management support.

---

### Post by WildTangent on 2005-08-31
[QUOTE=jdong]I wasn't talking about sheer power, more about mobility, both temperature tolerance, heat generation, and power management support.[/QUOTE]
well, there, the turion does have a slight advantage, with a thermal output of 25 watts IIRC. the Pentium M is 37, which is still quite low. The P4 threatens to render you sterile if you use it on your lap for too long :P as for power management, i cant comment for the pentium, because i dont know how well it works. if the turion is anything like my athlon 3000, then you will always have power right when you need it ;)

-Wild

---

### Post by Psycs on 2005-09-01
The battery tests in the comparison article I linked to are particularly interesting.  The Pentium M (Dothan), performs better under constant load than a Turion ML-37 (by the way. a Turion MT uses 30% less power than the ML), which is nothing to be surprised about.

However, > "with a 10.5% lead in the life test, the Turion CPU and AMD&#8217;s PowerNow! Technology provide a more efficient platform when you consider real world usage... the tests (in the article) clearly show the Pentium M providing better high-load power consumption and Turion offering longer battery life during more realistic non-intensive usage."

That is regardless of performance, in which the AMD has an advantage (AND provides 64 bit processing.)

[http://www.laptoplogic.com/resources/articles/42/13/1/](http://www.laptoplogic.com/resources/articles/42/13/1/)

EDIT:  Also, the article cleared the confusing, in my mind at least, about the Centrino.  Its not a processor per se, rather the the marketing name under which the Pentium M, the Intel Wireless Card and chipset are sold.

---

