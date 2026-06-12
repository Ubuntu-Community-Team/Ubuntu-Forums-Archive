---
title: "How to disable hyperthreading?"
date: 2010-04-22
forum: System76 Support
---

### Post by jcwilk on 2010-04-22
I'm on the pengolin with an i5, the cheapest cpu. Because it doesn't have a ton of kick it really kills me when a program that can only use one thread is only allowed use of half of one of the cores, which is basically every program I use.

Correct me if I'm wrong about assuming that a program can only utilize 25% of the cpu if it's single threaded with hyperthreading on and up to 50% (a full core out of the two cores) with it disabled, but if that's the case I would absolutely love to try disabling it since watching my cpu graph generally shows it capped at 25%, which is ridiculous. I realize it's -possible- this is just a deceptive oversight of the design of the cpu graph, but probably not.

Anyone have suggestions? Is this something I have to put into the grub config or what?

(intermediate linux user)


Thanks!

---

### Post by jcwilk on 2010-04-23
Anyone? Would really love some tips or hints on how to tackle this... The bios menu is basically worthless and mentions nothing about the cpu, is there nothing operating system level that can be done?

---

### Post by msrinath80 on 2010-04-23
> **jcwilk said:**
> I'm on the pengolin with an i5, the cheapest cpu. Because it doesn't have a ton of kick it really kills me when a program that can only use one thread is only allowed use of half of one of the cores, which is basically every program I use.

Correct me if I'm wrong about assuming that a program can only utilize 25% of the cpu if it's single threaded with hyperthreading on and up to 50% (a full core out of the two cores) with it disabled, but if that's the case I would absolutely love to try disabling it since watching my cpu graph generally shows it capped at 25%, which is ridiculous. I realize it's -possible- this is just a deceptive oversight of the design of the cpu graph, but probably not.

Anyone have suggestions? Is this something I have to put into the grub config or what?

(intermediate linux user)


Thanks!

I read your post yesterday and decided not to answer as I was lazy to type everything out. Sorry. Here is my 0.02$.

For a merely dual core CPU (i.e. no hyperthreading), what you need to be looking at is the CPU usage for a particular task in say "top". If it shows 25% there with default "top" settings, then you have a problem.

For a single program/task, even with hyperthreading enabled, chances of reduced performance are negligible if not non-existent.

With hyperthreading switched on, there can be one problem though; a problem that has been in existence ever since its introduction. Put simply, lets say you have two programs running, both of which typically tend to max out the CPU usage at 100%. If all you have is a simple dual-core, then the OS spreads out each program to a CPU core thus giving each program 100% CPU to work with. Of course each of these programs is free to hop from one CPU to another (assuming no CPU affinity constraints are in place).

With hyperthreading on, there is always the possibility that both of the programs can be sent to two individual threads of the same CPU core. In this case, physically speaking, only one of the CPU cores is completely loaded even though "top" will gladly show that both programs are using 100% CPU. The result is that both programs run slowly. How slowly is another question...

I have not been following Linux kernel development for quite a few years so I don't know if the kernel is now smart enough to automatically schedule two processes on two individual cores instead of random allocation? I do however know how to force the kernel to use two individual cores for any processes that I start on my own. The "taskset" command will help force CPU affinity. To identify which processor core/thread is from the same physical CPU identify two of the four processors that cat /proc/cpuinfo spews out and check for any two processors with different physical ids.

For the most part however, I usually find that only folks very very obsessed with performance tend to worry about such things. No offence. For daily computing, it's much easier to trust the kernel devs and your distro and just move along :)

---

### Post by satsujinka on 2010-04-23
I seem to recall a thread on the Archlinux forums on this subject. If I remember correctly, it was found that the kernel preferred to use even numbered cpus (ie. whole cpus) rather than allocating work to each cpu in sequence. However, if this isn't the behavior you are seeing then it's probably because the scheduler is older and doesn't yet know about core i3/5/7 cpus. In which case you should either compile a newer kernel or try 10.04 out.

---

### Post by P4man on 2010-04-23
There is no need and no benefit in disabling hyperthreading (except for some very rare corner cases where you might see an tiny slowdown).

Its not using half your cpu core, its using all its resources. Hyperthreading duplicates some resources allowing 2 threads to run on one core more or less simultaneously. For some apps that provides a nice speedup. Others, it doesnt. But it doesnt hurt to have those resources and not use them.

You are just reading too much in to the 25% thing.  Think of it as 25% of theoretical maximum load running 4 threads. If you disable hyperthreading, you reduce the maximum theoretical cpu throughput by half, so you will get 50% in the performance monitor using the same load,  but it wont be any faster at all.

in short: leave it on.

---

### Post by msrinath80 on 2010-04-23
> **P4man said:**
> There is no need and no benefit in disabling hyperthreading (except for some very rare corner cases where you might see an tiny slowdown).

Its not using half your cpu core, its using all its resources. Hyperthreading duplicates some resources allowing 2 threads to run on one core more or less simultaneously. For some apps that provides a nice speedup. Others, it doesnt. But it doesnt hurt to have those resources and not use them.

You are just reading too much in to the 25% thing.  Think of it as 25% of theoretical maximum load running 4 threads. If you disable hyperthreading, you reduce the maximum theoretical cpu throughput by half, so you will get 50% in the performance monitor using the same load,  but it wont be any faster at all.

in short: leave it on.

P4man is right. Well put :)

---

### Post by tgalati4 on 2010-04-23
sudo apt-get install htop

htop

It will show all four cores.  I don't know why it's not included in the standard distro.

---

### Post by msrinath80 on 2010-04-23
> **tgalati4 said:**
> sudo apt-get install htop

htop

It will show all four cores.  I don't know why it's not included in the standard distro.

"top" can do that too. Just hit "1" after entering "top".

---

### Post by jcwilk on 2010-04-23
Thanks guys, I really appreciate your thorough responses.

Ok, so I guess I'm just being misled by top and system monitor saying it's seeing 4 cpus, am I correct in thinking that if one of these virtual cpus is getting maxed out and nothing else is using much cpu time, it will be allowed a full core despite the fact that it's 1 out of 4 virtual cpus?

If that's the case then yeah, I agree that it would be overly anal to try and disable hyperthreading. I'll try to keep an eye on top when my cpu starts getting worked and see if this is the case or not and report back if it still seems like I'm only getting half a core per single thread, but you guys are probably right, thanks again for the explanations.

UPDATE:

So I just wrote a little ruby script (vanilla ruby is pretty guaranteed to only get one kernel thread) to just do squares and squareroots back and forth of a float and these are the cpu usages top is reporting:

(without breaking it into individual virtual cpus)
Cpu(s): 26.1%us,  0.2%sy,  0.0%ni, 73.6%id,  0.0%wa,  0.1%hi,  0.0%si,  0.0%st

(with breaking it into individual cpus)
Cpu0  :  4.5%us,  0.6%sy,  0.0%ni, 94.6%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Cpu1  :  0.0%us,  0.3%sy,  0.0%ni, 99.3%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Cpu2  : 99.7%us,  0.0%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Cpu3  :  6.3%us,  0.6%sy,  0.0%ni, 92.8%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st

As you can see it's very suggestive towards only getting half a core, or 1/4 of the total chip. I realize it's possible that the virtual cpu, Cpu2 in that case, is actually being allowed all of the resources of one of the cores and not just half of it, but it's super unclear... Anyone know of a more reliable way to determine what percentage of your core or total chip capacity a process is being given?

---

### Post by jcwilk on 2010-04-23
> **P4man said:**
> There is no need and no benefit in disabling hyperthreading (except for some very rare corner cases where you might see an tiny slowdown).

Its not using half your cpu core, its using all its resources. Hyperthreading duplicates some resources allowing 2 threads to run on one core more or less simultaneously. For some apps that provides a nice speedup. Others, it doesnt. But it doesnt hurt to have those resources and not use them.

You are just reading too much in to the 25% thing.  Think of it as 25% of theoretical maximum load running 4 threads. If you disable hyperthreading, you reduce the maximum theoretical cpu throughput by half, so you will get 50% in the performance monitor using the same load,  but it wont be any faster at all.

in short: leave it on.

From what you're saying it sounds like turning hyperthreading on actually doubles the potential throughput of the cpu, which no offense, sounds a little too good to be true. Are there actually double the physical components in the core i5 as compared to a comparable non-hyperthreading core duo?

I was under the impression that hyperthreading just improved general responsiveness since it makes it easier to break up the cores into smaller virtual parts which can be more readily shared between processes on the low level hardware layer... Which wouldn't provide any benefit to total cpu capacity. Am I incorrect in this thinking?

---

### Post by P4man on 2010-04-23
> **jcwilk said:**
> From what you're saying it sounds like turning hyperthreading on actually doubles the potential throughput of the cpu, which no offense, sounds a little too good to be true. Are there actually double the physical components in the core i5 as compared to a comparable non-hyperthreading core duo?

Yes there are physical resources (registers are duplucated, I think even trace caches and some other parts). No IRL you will allmost never see a twofold performance increase, but you can get fairly close on some code. 70% is not unheard off on branchy (and not very optimised) code and it should possible to write code that does pretty much double its performance with HT, although that would be really poorly optimized code.

If you want to know more about hyperthreading, I suggest reading this:
[http://arstechnica.com/hardware/reviews/2008/11/nehalem-launch-review.ars/13](http://arstechnica.com/hardware/reviews/2008/11/nehalem-launch-review.ars/13)

> I was under the impression that hyperthreading just improved general responsiveness since it makes it easier to break up the cores into smaller virtual parts which can be more readily shared between processes on the low level hardware layer... Which wouldn't provide any benefit to total cpu capacity. Am I incorrect in this thinking?

Yes  you are incorrect. You are thinking of the pentium 4 days, where we had single cores and HT's biggest asset was "better responsivness", just like expensive dual cpu machines back then; but having 2 or  more cores nowadays gives you the same anyway. 

The pentium 4 implementation was also not so great, often resulting in performance loss due to cache trashing (each virtual core shares the cache memory). In new i5 and i7s a performance drop is extremely rare, and the typical gain on threaded code considerable.

---

### Post by jcwilk on 2010-04-23
> **P4man said:**
> Yes there are physical resources (registers are duplucated, I think even trace caches and some other parts). No IRL you will allmost never see a twofold performance increase, but you can get fairly close on some code. 70% is not unheard off on branchy (and not very optimised) code and it should possible to write code that does pretty much double its performance with HT, although that would be really poorly optimized code.

If you want to know more about hyperthreading, I suggest reading this:
[http://arstechnica.com/hardware/reviews/2008/11/nehalem-launch-review.ars/13](http://arstechnica.com/hardware/reviews/2008/11/nehalem-launch-review.ars/13)



Yes  you are incorrect. You are thinking of the pentium 4 days, where we had single cores and HT's biggest asset was "better responsivness", just like expensive dual cpu machines back then; but having 2 or  more cores nowadays gives you the same anyway. 

The pentium 4 implementation was also not so great, often resulting in performance loss due to cache trashing (each virtual core shares the cache memory). In new i5 and i7s a performance drop is extremely rare, and the typical gain on threaded code considerable.

Cool, thanks very much for the info p4man, I'll look into that link when I'm not at work, sounds like I've much to learn about modern hyperthreading. And yes, I was indeed thinking of hyperthreaded p4's.

---

### Post by P4man on 2010-04-23
> **jcwilk said:**
> Cool, thanks very much for the info p4man, I'll look into that link when I'm not at work, sounds like I've much to learn about modern hyperthreading. And yes, I was indeed thinking of hyperthreaded p4's.

P4 hyperthreading got a bit of an bad reputation because of windows moronic thread scheduling and because the implementation wasnt stellar. But the concept is really clever, and the flaws have been worked out (even in windows). There is basically no reason to disable it, unless you are only running one specific workload where you know HT does not help and/or you know for sure you will never need more threads than you have cores. Some server workloads come to mind. For desktop, leave it on, especially if you "only" have 2 physical cores (and you run a cleverer OS than XP).

---

### Post by happypup on 2010-05-22
Well I decided to look into hyper-threading when after disabling it in my BIOS for kicks my computer seamed to boot faster "alot faster".

Found this article: [http://www.taranfx.com/hyper-threading-cpu](http://www.taranfx.com/hyper-threading-cpu)

I'm still undecided for now on weather to have hyper threading on or off.

So far I'm going to leave it off for a while.

I'm running the i7 920

Thanks for the interesting read. :biggrin:

---

### Post by jcwilk on 2010-05-22
> **happypup said:**
> Well I decided to look into hyper-threading when after disabling it in my BIOS for kicks my computer seamed to boot faster "alot faster".

Found this article: [http://www.taranfx.com/hyper-threading-cpu](http://www.taranfx.com/hyper-threading-cpu)

I'm still undecided for now on weather to have hyper threading on or off.

So far I'm going to leave it off for a while.

I'm running the i7 920

Thanks for the interesting read. :biggrin:

Well, that article was focused almost exclusively on servers and server software which have -way- different needs than desktops and desktop software. It touched on desktops but was extremely vague.

Also, if the only benchmark you're relying on is boot speed I highly suggest you look at other ones. Boot speed is the rice rocket spoiler and carbon fiber hood of benchmarks. You only do it at most once every time you use a computer and it likely won't change by more than 10 seconds.

Lastly, these i7's and i5's, as this thread illustrates, are a special kind of hyperthreading where most or all of the registers are duplicated. If you turn off hyperthreading then a good chunk of your physical processor is sitting idle, unused. It's almost like turning off some of your cores.

---

### Post by P4man on 2010-05-22
> **happypup said:**
> Well I decided to look into hyper-threading when after disabling it in my BIOS for kicks my computer seamed to boot faster "alot faster".

Measure it. Install bootchart and post the result. Id be very interested in seeing if and possibly why it boots slower, but I strongly suspect you're mistaken. Make sure to boot either setting at least twice so its not ureadahead kicking in and slowing your boot.

> 
Found this article: [http://www.taranfx.com/hyper-threading-cpu](http://www.taranfx.com/hyper-threading-cpu)

Its rubbish. Honestly. It throws all misconceptions untruths and semi truths on a big pile. Just to clarify one thing, why does MS recommend you disable HT for SQL server? Because its one of those highly optimized (server) apps that doesnt benefit and it increases power consumption a tiny bit. The other articles linked there are half a decade old and refer to pentium4 hyperthreading. Thats intellectually dishonest.

For most things, the difference with HTT on or off isnt big, but you are much more likely to see an improvement than a deterioration on threaded code.

---

### Post by -humanaut- on 2010-05-22
I just buy AMD Chips :) HTT Is good.

---

### Post by dewdrop_world on 2010-12-26
Sorry to revive an old thread, but I have it from a good source that hyperthreading can harm performance for applications where minimum latency is more important than maximum throughput, e.g. real-time audio.

[http://comments.gmane.org/gmane.comp.audio.supercollider.devel/31165](http://comments.gmane.org/gmane.comp.audio.supercollider.devel/31165)

> for low-latency applications, i strongly suggest to disable hyperthreading: it
may increase throughput, but at the cost of latency. some time ago, i have done
some benchmarks on the effects of hyperthreading on the scheduling latency of
the os. it was raising the worst-case latency by about 250 microseconds. (for a
block-size of 64 samples at 44100hz, it would reduce the performance in the
worst case by about 20%).

btw, i doubt that hyperthreading will speed up any number-crunching application.
from my understanding, it is better suited for server/database workloads.Since real-time audio is what I do, I would actually like an answer to the OP's question. P4man's recommendation to use hyperthreading is available makes sense for typical consumer-grade applications. If it makes real-time audio threads lose steam in a live performance situation, though, then I don't want it.

I looked in the bios on my machine, no option that looks like SMT or hyperthreading. Can this be configured in the GRUB boot items? How?

Ubuntu 10.04, Core i3-350M. (I know this is a System 76 forum and I'm using different HW, but it's the only thread I find where there's any serious discussion of switching off HT.)

Thanks,
James

---

### Post by isantop on 2010-12-27
It would depend on your computer's manufacturer. In our systems, we put an option in the BIOS under the Advanced tab. It's labeled as hyperthreading. I think the best option would be to contact your hardware vendor.

---

### Post by dewdrop_world on 2010-12-27
> **isantop said:**
> It would depend on your computer's manufacturer. In our systems, we put an option in the BIOS under the Advanced tab. It's labeled as hyperthreading. I think the best option would be to contact your hardware vendor.

Understood. I just posted on the manufacturer's forum. Thanks!
James

---

### Post by areeda on 2011-01-16
Did you every get an answer to how to disable hyperthreading?  I'm running some very cpu intensive tasks (Einstein@Home) and would like to compare throughput with and without hyper threading.  That system is dual Xeon running 10.04.

Joe

---

### Post by isantop on 2011-01-17
What type of computer do you have? It will vary depending on your System76 Model Number.

---

### Post by areeda on 2011-01-17
> **isantop said:**
> What type of computer do you have? It will vary depending on your System76 Model Number.
I'm not sure what a System76 Model Number is, would you define it and tell me how to find it? 

I am of course looking for a temporary disable command to allow benchmarking with and without HT.

The 2 that I'm interested in are a Dell Precision workstation about 5 years old that reports 4 processors that look like:

```
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 2
model name    : Intel(R) Xeon(TM) CPU 2.40GHz
stepping    : 7
cpu MHz        : 2392.485
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid
bogomips    : 4784.97
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 32 bits virtual
power management:

```
It's running Ubuntu 10.04 (Linux angela2 2.6.32-27-generic #49-Ubuntu SMP Wed Dec 1 23:52:12 UTC 2010 i686 GNU/Linux).

The other is a thinkPad T510 also running 10.04 (Linux jsa 2.6.32-27-generic #49-Ubuntu SMP Thu Dec 2 00:51:09 UTC 2010 x86_64 GNU/Linux) and reports 4 processors all like:

```
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 37
model name    : Intel(R) Core(TM) i5 CPU       M 540  @ 2.53GHz
stepping    : 5
cpu MHz        : 2534.000
cache size    : 3072 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt aes lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid
bogomips    : 5053.33
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

```

---

### Post by areeda on 2011-01-17
> **areeda said:**
> I'm not sure what a System76 Model Number is, would you define it and tell me how to find it? 
I apologize.

A little time with Google plus looking at what forum I posted in makes it more clear what System76 is.

I got to this thread by searching not browsing forums.

Is there a Ubuntu wide solution?

Joe

---

### Post by isantop on 2011-01-18
Not at the Software Level. You'll have to go to your Hardware vendor to know for sure what the process is. Typically, it's a setting in the Bios.

---

### Post by areeda on 2011-01-18
> **isantop said:**
> Not at the Software Level. You'll have to go to your Hardware vendor to know for sure what the process is. Typically, it's a setting in the Bios.
Thank you!

---

### Post by Elim-Garak on 2011-03-10
I just want to add a simple comment on hyperthreading. Lately, I had a discussion with a friend about this issue and a proposed a simple yet conclusive test on how to find out if a single program, command, etc. uses one core or just one of the virtual threads. 

Here is what I did:

I ran 1,2,4 instances of

```
dd if=/dev/zero of=/dev/null
```

in different terminal and compared the number of GB/s "dumped".

This is what I found:

1x 1.6GB/s
2x 1.5GB/s
4x 750MB/s

For me this clearly shows, that the whole core is used for a program and not only a single thread.

---

