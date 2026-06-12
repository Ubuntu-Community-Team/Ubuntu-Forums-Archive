---
title: "Processor Technology"
date: 2009-07-03
forum: The Cafe
---

### Post by Blacklightbulb on 2009-07-03
How much did processor technology advance? 
What's the fastest processor today commercial/industrial use?
What's the future of processors?

---

### Post by Gizenshya on 2009-07-03
1.  Since when?

2.  See the following charts... (but they are just reported results.  but fair, for those that have been reported- no propaganda).

[http://www.cpubenchmark.net/high_end_cpus.html](http://www.cpubenchmark.net/high_end_cpus.html)

[http://www.cpubenchmark.net/overclocked_cpus.html](http://www.cpubenchmark.net/overclocked_cpus.html)


3.  [Quantum Computing](http://www.quantiki.org/wiki/index.php/What_is_Quantum_Computation%3F).

---

### Post by hessiess on 2009-07-03
As long as Windows is the dominent OS, and only runs on x86 hardwere nothing interesting is going to happen to CPU architectures. x86 is old and bloated.

---

### Post by Blacklightbulb on 2009-07-04
I know about quantum computing. That's what my question was really about. It's about time we begin to try to improve form these old systems. Unfortunately I will perhaps never see a quantum desktop in my life span.

---

### Post by Blacklightbulb on 2009-07-04
> **hessiess said:**
> As long as Windows is the dominent OS, and only runs on x86 hardwere nothing interesting is going to happen to CPU architectures. x86 is old and bloated.

Imagine if they somehow reached to a 20Ghz core and Linux Kernel will advance before Microsoft to be able to run onto it. On a second thought though I think Microsoft will pay the processor company to delay their release before Microsoft is ready.

---

### Post by Gizenshya on 2009-07-04
processors can't keep up with the transisters/die rate (moore's law) with current tech... but that hasn't stopped computers from becoming faster.  We just put more CPU cores per processor.  My computer is dual core @ 3.6 ghz each, thats 7.2 ghz at 100% utilization.  It is capable of over 8 ghz.  The new core i7's are quad core and each core can be faster than that, and more efficient with calculations. So it would be equiv of about a 20 Ghz processor already.  Though there can only be one processor at a time with that technology... but in the future I wouldn't doubt we see multiple multi-core processors on personal computers (servers already have that ability I think...).  And 1 ghz on a core i7 does more calculations than 1 ghz on a pentium 4.

My GPU is capable of approx the same number of calculations as my CPU.  So if I'm doing some seti@home with cuda, I'm probably pushing around the equiv of 16 ghz+  (somewhat apples and oranges, I know...)

---

### Post by hessiess on 2009-07-04
> **Gizenshya said:**
> processors can't keep up with the transisters/die rate (moore's law) with current tech... but that hasn't stopped computers from becoming faster.  We just put more CPU cores per processor.  My computer is dual core @ 3.6 ghz each, thats 7.2 ghz at 100% utilization.

This only applies with applications that are written to be multi threaded and/or multiprocess, which the vast majority are not. Eaven for applications which are multi threaded, adding more processors will not create a linear increase in application performance as the more cores there are, the more overhead there is keeping everything in sync.

---

### Post by HappyFeet on 2009-07-04
> **Gizenshya said:**
> My computer is dual core @ 3.6 ghz each, thats 7.2 ghz at 100% utilization.

That is not correct. Your computer is not running at 7.2 ghz. You do not just double your speed to get that result. You simply have 2 cpu's running at 3.6 each. But unless an app is able to take full advantage of dual core, it is not even twice as fast as a single core cpu at 3.2 ghz. All a dual core cpu is able to do is relieve some of the load a single core would experience.

---

### Post by Blacklightbulb on 2009-07-05
Well adding cores isn't really an advancement in technology. It's like in the steam era a train would have a bigger and larger engine for faster speeds. I was just asking if there is any hope that in the near future some now technology (like the promising but still far away dream of [quantum computing]("http://http://en.wikipedia.org/wiki/Quantum_computer")) will emerge.

---

### Post by MadCow108 on 2009-07-05
the memristor which has been constructed for the first time last year could bringt some performance in certain areas of computing.
[http://en.wikipedia.org/wiki/Memristor](http://en.wikipedia.org/wiki/Memristor)

---

### Post by Blacklightbulb on 2009-07-05
> **MadCow108 said:**
> the memristor which has been constructed for the first time last year could bringt some performance in certain areas of computing.
[http://en.wikipedia.org/wiki/Memristor](http://en.wikipedia.org/wiki/Memristor)
  
Thanks, wasn't aware of this yet!

---

### Post by HavocXphere on 2009-07-05
Intel has been patenting a lot of optical components lately. Used mainly for interconnects between components.

I reckon we'll be seeing some optics based PCs before quantum stuff. Sure there are devices capable of certain simplistic quantum processing. What they don't tell you is that it takes a couple of million & major lab equipment to maintain a few seconds of operation. It'll still take some time till we see that at Walmart.

---

### Post by cb951303 on 2009-07-05
ARM is the future 8) ultra low power, multi core, parallel processing beasts yeah

---

### Post by Skripka on 2009-07-05
AMD has a 6-core server processor you can pick up.

---

### Post by Skripka on 2009-07-05
> **Gizenshya said:**
> My computer is dual core @ 3.6 ghz each, thats 7.2 ghz at 100% utilization.  It is capable of over 8 ghz.  The new core i7's are quad core and each core can be faster than that, and more efficient with calculations. So it would be equiv of about a 20 Ghz processor already. 

Ummm.  No.

---

### Post by Gizenshya on 2009-07-05
> **hessiess said:**
> This only applies with applications that are written to be multi threaded and/or multiprocess, which the vast majority are not. Eaven for applications which are multi threaded, adding more processors will not create a linear increase in application performance as the more cores there are, the more overhead there is keeping everything in sync.

> **HappyFeet said:**
> That is not correct. Your computer is not running at 7.2 ghz. You do not just double your speed to get that result. You simply have 2 cpu's running at 3.6 each. But unless an app is able to take full advantage of dual core, it is not even twice as fast as a single core cpu at 3.2 ghz. All a dual core cpu is able to do is relieve some of the load a single core would experience.

> **Skripka said:**
> Ummm.  No.




Of course it only applies to multithreaded applications.  The technologies go hand-in-hand.  For instance, with Crysis, I can hit nearly 100% system-wide utilization (both cores and GPU).  In most applications, of course, I cannot.  But that isn't the point.  The point is total processor speed.  Yes applications as well, but they will follow suit with demand.

Pentium D processors were dual-core processors that came before the Core2 series.  They were not really specialized, and were essentially 2 Pentium 4 CPU's on one die.  Look at [this chart](http://www.cpubenchmark.net/common_cpus.html).  Locate the 3.2 Ghz Pentium 4, and the 3.2 Ghz Pentium D.  Same core speed... but the Pentium D performs much better, despite this "same cpu core speed."  This is because it has **two** cores.  Again,there wasn't specialization back then, and the core cache's and other issues caused overhead to be very high, but it is an undeniable and more than significant improvement (70% actual computational performance increase).  They have gotten much more efficient (overhead-wise) since that first venture into single-die multicore.  And no, it is not theoretically possible to ever reach 100%, but the faster processors get, the more specialized they become, and the lower the percentage lost to overhead will be.


Foe example, look at [this chart](http://www.cpubenchmark.net/high_end_cpus.html).  Locate the Core2 Quad Q6600 @ 2.4 ghz and the Core2 Duo P8600 @ 2.4 Ghz.  Equivalent technology, just twice the cores.  Efficiency in doubling?  This time 84.3%, a huge improvement in doubling over just one generation.  There are not equivalent single-core processors that are comparable, unfortunately.

GPU's have many, many slow processors.  They are a great example of multi-core usage, and they have been like that for many years.  Mine has well over 100, and they perform very well together.  Each one is far slower than my main CPU, but overall they have a similar calculation ability.

So you cannot treat a multi-core CPU at x Ghz as a single-core processor at the same speed.  There are real and significant improvements.

Also, for the foreseeable future, adding cores will be the main way of increasing computer performance.  They are more efficient energy-wise, cost-wise, and in other measures of practicality.  Until some revolutionary technology is ready for public consumption, that is.

And, to answer the 20 GHZ question in more detail...

Lets take a 2 GHZ pentium 4 (with a score of 260).  Now, lets take a processor like mine, overclocked to 4 ghz (2 cores), to make calculations simple.  Lets not even take overhead into consideration... lets hold it to the 8 GHZ standard and see how it performs...

so, that's 4 times the pentium 4's ghz speed.  So that would mean that, if it holds up to the efficiency of 100%, we would get a whopping 1040 score! (scores ARE linear.  200 is exactly twice as many as 100, and so on). So how did the "8" ghz dual-core stand up?

[Actual score: 3520](http://www.cpubenchmark.net/overclocked_cpus.html).  What?  but how is this possible?  adding cores, but over 3 times as efficient?  Doesn't that break every notion of logic?  No.  With each new series of processor, they calculate more efficiently.  The core i7 is even more efficient than that (by a significant margin, actually).

So... that would mean that my processor is already equivalent of a 27 Ghz processor.. even though it is only "8' Ghz.  A 338% difference (or, efficiency improvement, even after taking out the overhead-- which is done automatically, of course, because it is a real test of actual performance).  Or, if you still refuse to acknowledge the practical notion of 2 cores, it is 676% at 4 GHZ. And if you take overhead into consideration, probably somewhere in the 800% range.

My point is, a few percentage here and there given to overhead is a moot point, as Ghz are not a good measurement of processor performance, period.  Yes, increases in performance from adding core is not linear.. but neither is the scale with which we're measuring.  Advertisers and computer manufacturers would like consumer to think that... but it is not true.  So, for the dreamers in the pentium 2 ghz days of a 10 ghz computer... mine is already nearly 3 times faster (over 13.5 ghz per core), and that is just my CPU.  My GPU gets approx as many calculations as my CPU, though I acknowledge that that's a bit of "apples and oranges."  (in other words, the efficiency gained per clock has consistently been far more than the difference lost due to multi-core overhead).  So arguing that my current 7.2 ghz is not exactly that means nothing.  It is both far more than that, and not quite that at the same time, 'depending on where you measure from.'

---

### Post by moster on 2009-07-05
Let me add something. I will here post super pi results of my CPUs in this decade. It is single core program, so in some other test difference is even bigger. Here we go.

All this CPUs costed less then 100$, around 80$ in their time.

790 sec - 133 pentium 1 from 1997
XXX sec - 433 celeron from 1999
86 sec - 1,3 Ghz AMD duron from 2002
39 sec - 1,8 Ghz AMD 64 singlecore 3000+ from 2005
18 sec - 2,5 Intel dualcore E5200 from 2008
9 sec - my future core i7 now cost around 1000$ :D

I would say that we have very bright future :)

Someone should make a database from this thread below, sort it by years and we could predict future! :D
[http://ubuntuforums.org/showthread.php?t=60264]("http://ubuntuforums.org/showthread.php?t=60264")

---

### Post by Gizenshya on 2009-07-05
It is single-core, yes.. but I use that program often in testing multi-core system stability.  To do this, make a second folder of it.  Go into one folder and run it, then go into the other folder and run it, and so on, for the number of cores you have (or want to use).  Each instance runs on a separate core.

And yes... that is actually a very good idea.  If I get some free time I might actually fire up my Minitab ;)  it's windows, though :(

---

### Post by hessiess on 2009-07-05
> **cb951303 said:**
> ARM is the future 8) ultra low power, multi core, parallel processing beasts yeah

as far as the desktop is conserened, not going to happen until something shifts Windows (or MS starts supporting ARM).

> 
GPU's have many, many slow processors. They are a great example of multi-core usage, and they have been like that for many years. Mine has well over 100, and they perform very well together. Each one is far slower than my main CPU, but overall they have a similar calculation ability.


GPU's are much faster than CPU's at specific tasks, namly rendering textured polygons. Even a well written, highly optimised real time software renderer is still many times slower than a hardware accelerated one running on a low end GPU.

---

### Post by cb951303 on 2009-07-05
> **hessiess said:**
> as far as the desktop is conserened, not going to happen until something shifts Windows (or MS starts supporting ARM).

they already do: Windows CE :) (or is it called Windows Mobile now?)

EDIT: Also, it's the software companies that tries to catch up with hardware vendors not vice versa. (at least not for OS market). So if ARM does the next big CPU, Microsoft would probably support it.

---

### Post by Skripka on 2009-07-05
> **Gizenshya said:**
> 
So how did the "8" ghz dual-core stand up?


You're hopeless.  But at least you have "faith".

---

### Post by Skripka on 2009-07-05
> **hessiess said:**
> as far as the desktop is conserened, not going to happen until something shifts Windows (or MS starts supporting ARM).



GPU's are much faster than CPU's at specific tasks, namly rendering textured polygons. Even a well written, highly optimised real time software renderer is still many times slower than a hardware accelerated one running on a low end GPU.

Actually Nvidia GPUs have been EXCELLENT at cracking encryption, and are faster than current generation CPUs at said tasks by orders of magnitude.

---

### Post by Gizenshya on 2009-07-05
> **Skripka said:**
> You're hopeless.  But at least you have "faith".

cry me a river

you were wrong, get over it

---

### Post by Skripka on 2009-07-05
> **Gizenshya said:**
> cry me a river

you were wrong, get over it

No, you're not worth the effort.

---

### Post by Gizenshya on 2009-07-05
whatever makes you sleep better at night lol

keep shooting your mouth off and keep getting owned.  I enjoy the entertainment :)

---

### Post by jomiolto on 2009-07-05
Outside of the mainstream processors, there is also IBM's [Power Architecture]("http://en.wikipedia.org/wiki/Power_Architecture"). The fastest POWER6 processors run at 5GHz -- they only have two cores, though. The upcoming [POWER7]("http://en.wikipedia.org/wiki/POWER7") will run at "only" 4GHz, but has 8 cores.

I have no idea on how these processors compare to desktop processors, but they must be good at something -- they are used in supercomputers, after all ;)

---

### Post by PurposeOfReason on 2009-07-05
[Gizenshya]("http://ubuntuforums.org/member.php?u=737496"), the improvements you stated were not from more cores. Of course a PD will get killed buy a C2D, it was a horrible CPU. You are overly arrogant in this market. Crysis using both cores? Crysis is not multithreaded so I want to know which one you were playing. 10:1 says it was other applications in the back and you being forgetful. I'm really not going to go into this, I have nothing to prove to anybody here, or yourself, so I will leave you as is. Just thought I should point out my first tidbit.

I have been in this market since PIII, built as low as a PI, I think I know a bit more than you and your charts.

---

### Post by cb951303 on 2009-07-05
[http://www.opensparc.net/](http://www.opensparc.net/) if only they could consume less power

---

### Post by Blacklightbulb on 2009-07-05
> **jomiolto said:**
> Outside of the mainstream processors, there is also IBM's [Power Architecture]("http://en.wikipedia.org/wiki/Power_Architecture"). The fastest POWER6 processors run at 5GHz -- they only have two cores, though. The upcoming [POWER7]("http://en.wikipedia.org/wiki/POWER7") will run at "only" 4GHz, but has 8 cores.

I have no idea on how these processors compare to desktop processors, but they must be good at something -- they are used in supercomputers, after all ;)

There's a rumor these will share the same CPU socket as the [AMD Opteron]("http://en.wikipedia.org/wiki/Opteron") (64-bit ?). That would be awesome if I could afford one and if there'll be good software available.

---

### Post by HavocXphere on 2009-07-05
> **Blacklightbulb said:**
> There's a rumor these will share the same CPU socket as the [AMD Opteron]("http://en.wikipedia.org/wiki/Opteron") (64-bit ?). That would be awesome if I could afford one and if there'll be good software available.
Just because the physical socket is the same doesn't mean it'll work. In fact I'd probably fall off my chair if that works.

> dual core @ 3.6 ghz each, thats 7.2 ghz at 100% utilization.
The ghz number refers to the frequency its clocked at. Nothing in the CPU is clocked at 7.2ghz. As for a "theoretical"/comparable ghz number, it would be lower than 7.2ghz. Doubling cores does not double performance, even if everything is neatly multithreaded and all cores are running at 100%.

Another reason to abandon the "ghz x cores" view is that it leads to widespread ridiculing.;)

---

### Post by Skripka on 2009-07-05
> **HavocXphere said:**
> Just because the physical socket is the same doesn't mean it'll work. In fact I'd probably fall off my chair if that works.


The ghz number refers to the frequency its clocked at. Nothing in the CPU is clocked at 7.2ghz. As for a "theoretical"/comparable ghz number, it would be lower than 7.2ghz. Doubling cores does not double performance, even if everything is neatly multithreaded and all cores are running at 100%.

Another reason to abandon the "ghz x cores" view is that it leads to widespread ridiculing.;)

You're more patient than me.

---

### Post by moster on 2009-07-06
Come on guys, what is that nonsense with multicores. Only true multicore OS was BeOS and it supported 16 cores. That means every program that runs on him do not have to be specifically designed for multicores. OS alone would spread work among cores.

Windows and linux and other *nix would run much better on one 1x8 Ghz than 4x2 Ghz. Not matter if program is really written for multicore or not. They are not designed from begining for that. Programming for multicores are really pain in *** and it is harder to debug.

7zip, xvid, rar... they support multicore. Speedup is at most 80%. For example winrar have inside him benchmark. On my CPU, 1 core selected = 800kb/s speed and 2 core 1250 kb/s speed. That is only like 65% speedup. Probaby somewhere are tests for xvid and 7zip but I dubt it will be much difference. Point is, it is not DOUBLE in anything.

edit:
GNU/HURD kernel was designed for multicores from the begining. :) In few years, who know what will be from all that :)

---

### Post by Blacklightbulb on 2009-07-06
> **HavocXphere said:**
> Just because the physical socket is the same doesn't mean it'll work. In fact I'd probably fall off my chair if that works.

I seen your point. But hey who knows perhaps they'll come up with some MOBO and OS specifically for it. But than I doubt I could afford it...:(

Hey what do you say of the ps3 processor? It also supported Linux, right? Even Ubuntu!!

The Processor is a PowerPc-based 8 core?

---

### Post by HavocXphere on 2009-07-06
> **moster said:**
> BeOS and it supported 16 cores. That means every program that runs on him **do not have to be specifically designed for multicores**. OS alone would spread work among cores.
```
A=Random
B=A + Random
C=A/B
```
Code like the above is inherently not multi-core friendly since it is linear. I'd be curious how the "OS alone would spread work among cores."

If you assign each line to a core then core 2 & 4 would still have to wait for core 1, so you'd lose _all_ of the benefits of multiple cores.

The 7zip, xvid, rar you mentioned was designed for parallel processing and would be supported equally well on BeOS/Ubuntu since they both support SMP & preemptive multitasking.

> **Blacklightbulb said:**
> I seen your point. But hey who knows perhaps they'll come up with some MOBO and OS specifically for it. But than I doubt I could afford it...:(

Hey what do you say of the ps3 processor? It also supported Linux, right? Even Ubuntu!!

The Processor is a PowerPc-based 8 core?
I'm not really familiar with the ps3 gear, but I know the cell processor in it is a once-off custom design so I'd guess that the mobo is also a once-off custom design.

Would be awesome if the manufacturers found a way to standardize these things (and actually wanted to).

> **Skripka said:**
> You're more patient than me.
Maybe I was just having a better day than you.;)

---

### Post by automaton26 on 2009-07-06
With current architectures, there's little benefit in having multiple execution unless the *data* is separate too.

i.e. as soon as data needs to be shared for writing (in memory or on a storage device) then it has to be exclusively locked by a single execution unit, which loses a significant amount of the performance potential.

Isolating data into independent logical blocks, and minimizing dependencies, is the main challenge.

---

### Post by Skripka on 2009-07-06
> **moster said:**
> 
GNU/HURD kernel was designed for multicores from the begining. :) In few years, who know what will be from all that :)

In a few years, GNU/HURD will still be a few years older, and STILL comic-relief material.

---

### Post by moster on 2009-07-06
> **HavocXphere said:**
> ```
A=Random
B=A + Random
C=A/B
```
Code like the above is inherently not multi-core friendly since it is linear. I'd be curious how the "OS alone would spread work among cores."

Wow, I had no idea... You know, you should send mail to HURD kernel hackers and tell them to stop working. Just tell them what you told me, they will be amazed of your "discovery".

> **HavocXphere said:**
> 
If you assign each line to a core then core 2 & 4 would still have to wait for core 1, so you'd lose _all_ of the benefits of multiple cores.

The 7zip, xvid, rar you mentioned was designed for parallel processing and would be supported equally well on BeOS/Ubuntu since they both support SMP & preemptive multitasking.

Of course Ubuntu/Beos support preemptive multitasking and SMP, I am not talking about that. Check termin , "pervasive multithreading".

---

### Post by moster on 2009-07-06
> **Skripka said:**
> In a few years, GNU/HURD will still be a few years older, and STILL comic-relief material.

Yes.... pity. But on paper it look great. It appear it is more difficult to design and debug it hat it seems to be. I was looking some Stallman video about that. They wanted to make modern kernel, linux has its flaws because it was based on unix and unix is old as pharaonic tomb..

---

