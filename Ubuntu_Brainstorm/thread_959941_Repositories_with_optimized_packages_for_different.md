---
title: "Repositories with optimized packages for different architectures"
date: 2008-10-26
forum: Ubuntu Brainstorm
---

### Post by gerymate on 2008-10-26
OK, I was reading A.S.Tanenbaum's Structured Computer Organization, and he states that a Pentium runs fixed point arithmetic code compiled with optimizations for its architecture twice as fast as compiled with optimizations for i486 (2.1.5). Than came a load of questions :).

At first, what processor architecture the packages Ubuntu currently provides are optimized for? Are the packages different if I have a PIII, an AMD Athlon, or an Intel Atom? Are the electric circles that make up MMX, SSE and the like in my CPU used at all? 

At second, what differences architecture specific optimization can make up in performance? Would the GNOME desktop run, say, 20% faster when compiled for a specific processor? Would it take noticeable less time for the Gimp to run a complex filter when compiled with multimedia extensions and fixed point arithmetic optimisations turned on where available? Could Firefox do faster Javascript? How much faster?

At third, what processors Ubuntu users use most? What is the TOP10 of CPUs running Ubuntu? How can it be measured?

At fourth, would it worth to **provide repositories of optimized packages for that TOP10 CPUs**, and let APT choose between them on demand? 

Those were the questions :). 

Now for the vision.

If we can achieve, optimistically saying, an average 3% increase in performance at workstations, that would mean also 3% increase in satisfaction and (magic word) productivity of Ubuntu users - so also corporations using Ubuntu. That would certainly mean more adoption of the system, and bring in more and more users and developers. Etc. etc. I am not sure, but afraid that currently almost the whole Ubuntu community uses "it's" computer as if it were a fast i386. It would be great to unleash the technologically already available performance of our computers with our favourite operating system!

---

### Post by smartboyathome on 2008-10-26
If this were to happen, we would have many packages go without updates for a certain architecture due to them not having a maintainer with that architecture. 

Even if we did this, it would give us at least 100 kernels to keep updated (theres about 10 in there now, and multiplying that by 10 so that each one was optimized would be 100).

---

### Post by gnomeuser on 2008-10-27
okay, this comes up every.. 3 months or so, you can search the forums for the subject and find excellent debates on the subject but I will rehash for you briefly:

Yes, optimization might have an impact (measurable even) on a single static case. However doing so over a whole system nobody has yet to provide actual data to show that it has a positive impact. That is to say when you optimize generally code gets bigger which means more IO and hgher chances of expensive cache misses. 

There is some data to show that doing -Os (size optimization in gcc) will have a greater impact as you reduce binary size meaning the load time in terms of IO might be lower. IO being the big bottleneck in your machine today, not the CPU - just notice how little faster a harddrive has become compared to your ram, cpu - it's still a million times slower meaning excessive IO is a big cost, infact so much that as CPU speed grows towards infinite, IO becomes 100% of your waittime (thus indicating that should be the subject of optimization).

None of this has though been tried on the a scale as large as the entire Ubuntu/Debian repo and it's not without problems. Doing compiler optimizations of any kind is likely to uncover bugs in code or in the compiler, often hard to pindown bugs, meaning this is not a risk free enterprise either. 

We do already pick certain optimizations that work for the largest majority of machines without costing us the ability to run universally so any impact additionally optimization might have is questionable at best.

All in all, without proper data on performance benefits across a multitude of machines and regression data, not to mention a way to measure all of this in the first place in a way that makes sense to our use cases. This whole exercise spells high risk, low gain plus the chance to even make things worse for many people.

---

### Post by gerymate on 2008-11-02
Dear gnomeuser, I have to admit many things you wrote, and also that my knowledge lacks at many places, however, I think you had misunderstood me a bit.

The only optimization I suggest is making architecture specific packages, *no* -O3 nor any such evil :-). 

Only -march, or, as my low understanding suggests me, preferably -mtune, because we _don't want_ to get the whole system optimized, just stuff that needs CPU, or runs almost always. Maybe some SSE related stuff.

I see and know that I/O is the botleneck of performance. However I see many times (System Monitor is better than TV :-)) that after long periods of no CPU usage, there are long periods of 100% CPU usage. I am using the Gimp regularly, and I am waiting for the CPU to do the job. Also, it is true that even architecture specific optimization can produce larger code, but it is not a big hit on I/O, because I/O is slow on seeks, not on data flow. 

Also, this idea is mostly for cheaper and slower computers - I simply does not care for those CPUs whose speed goes to infinite. I care for those computers that are out in less prosperous countries, say, in Asia, South-America and Africa. I think that *it is not good for the Ubuntu community to follow the speed-race generated by proprietary OSs*. What is good for the Ubuntu community is being smart and being different. If a 500 Mhz Pentium III runs 20% faster on Ubuntu, than it is a big achievement in a country where most computers contain 500 Mhz Pentium IIIs. The one size fits all model is really ugly.

However, I understand that the first thing is to gather some information about the real data. There is a Ubuntu hardware database, isn't it? Where can I find information about it? Some statistics of current Ubuntu users worldwide?

I also can imagine some profiling tool for general desktop usage. What applications consume most CPU during a week, and how much is that? Are there such tools that measure things like this? Can those tools be used in a survey?

...

I also see that 100 kernels problem a bit mathematically incorrect. For example it seems easy to adapt the logic and combine the TOP10 processors with the TOP3 of kernels. It is not even necessarily a multiplication, IMHO ;-).

---

### Post by yaknowwat on 2008-11-02
Ubuntu should switch to either i586 or i686 minimum  with optimization's to a Pentium 4 or higher.

---

### Post by gnomeuser on 2008-11-03
> **yaknowwat said:**
> Ubuntu should switch to either i586 or i686 minimum  with optimization's to a Pentium 4 or higher.

Kindly prove:

A) That there are worthwhile benefits from this.
B) That there are no regressions.
C) That there are no adverse performance profiles on machines not fitting the exact target.

This thread suffers from a complete lack of data. We have this debate every 3 months or so, please go back and search why we don't do this.

---

### Post by yaknowwat on 2008-11-03
> **gnomeuser said:**
> Kindly prove:

A) That there are worthwhile benefits from this.
B) That there are no regressions.
C) That there are no adverse performance profiles on machines not fitting the exact target.

This thread suffers from a complete lack of data. We have this debate every 3 months or so, please go back and search why we don't do this.

I'll be honest and say its not truely the kernel than needs these optimizations but the applications do.

The lowest specs someone will be running ubuntu on is a Pentium II with say openbox.  Which is i586  Optimizing for a Pentium 4 or higher would be a good choice because just about everyone using ubuntu has a processor that is capable of the extensions a P4 has.

---

### Post by Npl on 2008-11-03
> **yaknowwat said:**
> I'll be honest and say its not truely the kernel than needs these optimizations but the applications do.

The lowest specs someone will be running ubuntu on is a Pentium II with say openbox.  Which is i586  Optimizing for a Pentium 4 or higher would be a good choice because just about everyone using ubuntu has a processor that is capable of the extensions a P4 has.That would rule out all Athlon K7 (no SSE), AthlonXP (no SSE2) and previous Pentium CPUS.
On the other hand if you have a processor with SSE2 Extension, then its either a Pentium4 or a 64-bit capable one. So either go run 64-bit Linux which has those Extensions as default, or dont assume that its worth breaking compatibility with alot of processors just because of the P4.

---

### Post by gnomeuser on 2008-11-04
> **yaknowwat said:**
> I'll be honest and say its not truely the kernel than needs these optimizations but the applications do.

The lowest specs someone will be running ubuntu on is a Pentium II with say openbox.  Which is i586  Optimizing for a Pentium 4 or higher would be a good choice because just about everyone using ubuntu has a processor that is capable of the extensions a P4 has.

Since you do not appear to have understood the first time I told you.

You still have thus far failed to provide any shred of actual proof that your idea even has merit. It's very simple, recompile an entire Ubuntu with i586 or i686 optimizations enabled. Then show that it is measurably faster on a number of different machines (be sure to test multiple chips from multiple cpu vendors to get good test coverage), that it does not introduce regressions and that it does not adversely affect performance on any platform. A graph showing this with an accompanying few pages of analysis would be far sufficient initial investigation into your idea.

The burden of proof in on you, not me.

---

### Post by yaknowwat on 2008-11-04
> **Npl said:**
> That would rule out all Athlon K7 (no SSE), AthlonXP (no SSE2) and previous Pentium CPUS.
On the other hand if you have a processor with SSE2 Extension, then its either a Pentium4 or a 64-bit capable one. So either go run 64-bit Linux which has those Extensions as default, or dont assume that its worth breaking compatibility with alot of processors just because of the P4.

I never said break compatibly.  I was just saying bring it up to i586 (which is Pentium II ) then optimize for say pentium4.

The minimal base of ubuntu uses about 30 MiB of RAM  which is too much for say a pre-Pentium II processor.


As for benifits I'm not talking about just the kernel I'm talking about libraries and so on, and yes this does help those extensions were made to be used bring major improvements in some cases I've heard things like xvid encoding can be done 3-4 times faster with SSE and its successors. Something of which ubuntu tends to be falling in actually (Not talking small drops either.).

Something like ArchLinux doesn't get its snappiness from just an i686 kernel, but because everthing in it is designed around that. Along with i'll admit having only what is necessary does help some, but most of that stuff is suppose to wait to be called upon and shouldn't interrupt typical performance unless you run low on RAM.

To normal users they don't know all the optimizations brought to the 64bit version and figure its the same as the 32 bit version just with more memory support and less troubles.

---

### Post by jacksaff on 2008-11-07
The original poster would probably be interested in gentoo where everything is compiled on your own machine and you have full control over the optimizations.

You can get a fair amount of this on debian (ubuntu) systems using apt-build which takes a lot of the hassle out of it and allows you to download, compile and install an app with one command as well as allowiing global upgrades.

Compiling your own kernel used to make a fair bit of difference when I ran linux 5 years ago on 8 year old hardware. Compiling other apps generally made little to no noticable difference. On modern gear it isn't worth the hassle unless you have a real pressing need for speed (or you're a ricer, but then you already use gentoo...)

---

### Post by gerymate on 2008-11-11
Thank you, jacksaff, I will check out apt-build. In fact, I *was* using Gentoo for a while; however, now I am not talking about my own interest, but the - had to admit, imagined - interest of people technically or monetarily less potent than me.

However, I also have to admit that I lack knowledge of the ways GCC works. For example, I don't see why should the whole operating system, every package of it be optimized for the same processor. Is this really necessary? 

I think that the less frequently used or not CPU intensive applications are just fine in their current, perfectly compatible form. However, I think that for frequently used and CPU intensive applications it would be great to have CPU-specific optimized packages. This idea seems reasonable to me, but probably I have to learn more about optimizations, and than I probably will see a sharper picture.

Having such packages "for the masses" could be something Ubuntu can excel with.

---

