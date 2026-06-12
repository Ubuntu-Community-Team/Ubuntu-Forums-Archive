---
title: "SSE2 &amp; SSE3 Optimizations."
date: 2008-12-27
forum: The Cafe
---

### Post by JohnLau on 2008-12-27
Sorry for my English.
Mac OS X comes with an SSE3-optimized kernel. Wonder if ubuntu's kernel is SSE2/ SSE3 optimized or not.
My CPU (AMD Athlon 64 x2 5400+) is supposed to support SSE3, but I can't see that in /proc/cpuinfo. Any ideas why?:confused:

---

### Post by sdennie on 2008-12-27
On my machine, sse3 is actually listed as ssse3 in /proc/cpuinfo.  As for whether the kernel uses it or not, I think it's probably not a useful question.  The kernel doesn't generally do things that benefit from SSE instructions.  Where you will see SSE being useful is for things like mplayer or any application that runs in a tight loop and benefits from SIMD instructions.

---

### Post by JohnLau on 2008-12-29
Thank you for your quick response. :D
Strangely I did not see anything like 'ssse3' in /proc/cpuinfo
```
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 107
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 5400+
stepping	: 2
cpu MHz		: 2800.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips	: 5611.90
clflush size	: 64
power management: ts fid vid ttp tm stc 100mhzsteps

```
Which CPU do you have?

---

### Post by Npl on 2008-12-29
Not all Athlon64 support SSE3, new ones do, but older ones dont. [Look there]("http://en.wikipedia.org/wiki/List_of_AMD_Athlon_64_microprocessors")

---

### Post by mips on 2008-12-29
> **JohnLau said:**
> 
Strangely I did not see anything like 'ssse3' in /proc/cpuinfo

The first/older AMD64 processors did not have SSE3. This was also the case with my AMD 64.

---

### Post by mali2297 on 2008-12-29
> **JohnLau said:**
> Thank you for your quick response. :D
Strangely I did not see anything like 'ssse3' in /proc/cpuinfo


I think that it is listed as [pni](http://en.wikipedia.org/wiki/Prescott_New_Instructions).

---

### Post by Half-Left on 2008-12-29
The thing about OSX is that it's stuck to one arch so they can optimize the crap out of it for their hardware. Linux support about 20 others so the best way to optimize it is to build your own kernel, thats optimized.

Linux kernel has a generic option for optimizations which is ideal for distros wanting to support loads of hardware types.

---

### Post by sdennie on 2008-12-29
> **Half-Left said:**
> The thing about OSX is that it's stuck to one arch so they can optimize the crap out of it for their hardware. Linux support about 20 others so the best way to optimize it is to build your own kernel, thats optimized.

Linux kernel has a generic option for optimizations which is ideal for distros wanting to support loads of hardware types.

Yes, OSX does have an advantage in this case.  However, I think most users will find little (or no) difference in performance between a vendor supplied kernel and a custom built/optimized kernel.  The kernel isn't the bottleneck for most people so, making it faster usually doesn't help performance much.

---

### Post by JohnLau on 2008-12-29
> **mali2297 said:**
> I think that it is listed as [pni](http://en.wikipedia.org/wiki/Prescott_New_Instructions).

Thanks for telling me that :)
Would it be a good idea if ubuntu optimize the packages to have better performance. I suppose most of the machines running ubuntu support SSE2.

---

### Post by sdennie on 2008-12-29
> **JohnLau said:**
> Thanks for telling me that :)
Would it be a good idea if ubuntu optimize the packages to have better performance. I suppose most of the machines running ubuntu support SSE2.

Using SIMD instructions is very hit and miss.  Your application is likely to either benefit greatly or not at all.  The vast majority of applications are not likely to benefit from SSE2 instructions.  It's generally number crunching types of applications that will see a benefit from SIMD instructions because they can load a set of registers with data (even better if the instruction set supports block loading) and then issue a single instruction on the data.  Doing that over and over is where SIMD instructions shine.

---

### Post by Half-Left on 2008-12-29
> **vor said:**
> Yes, OSX does have an advantage in this case.  However, I think most users will find little (or no) difference in performance between a vendor supplied kernel and a custom built/optimized kernel.  The kernel isn't the bottleneck for most people so, making it faster usually doesn't help performance much.

Well not really, a vendor kernel is not optimized for one system, compiling your own reduces overhead and latency. You can get more responsiveness by enabling certain options, by default ubuntu kernel uses 300Hz, not highest preempt, highmem and other option that dont need to be on(including some debug)

It's all about optimizing, dont mean speed but means less overhead and more responsiveness on your desktop.

---

### Post by sdennie on 2008-12-29
> **Half-Left said:**
> Well not really, a vendor kernel is not optimized for one system, compiling your own reduces overhead and latency. You can get more responsiveness by enabling certain options, by default ubuntu kernel uses 300Hz, not highest preempt, highmem and other option that dont need to be on(including some debug)

It's all about optimizing, dont mean speed but means less overhead and more responsiveness on your desktop.

Yes, full preemption, 1000Hz timer frequency, etc can make for a more responsive system.  But, it depends on how you use your machine.  My guess is that if you sat an average user behind a machine and let him use it with both a vendor supplied kernel and one with full preemption, 1000Hz timer frequency, RCU preemption, no debugging and correct processor family, he probably wouldn't be able to tell the difference.

Building your own kernel is fun and instructive (and sometimes even necessary) but, doing it to increase performance isn't generally a valid a reason (sometimes it is though!).  I think it's very common for a placebo effect to come into play when you try to make something fast before you've quantified slow.

---

### Post by Half-Left on 2008-12-29
> **vor said:**
> Yes, full preemption, 1000Hz timer frequency, etc can make for a more responsive system.  But, it depends on how you use your machine.  My guess is that if you sat an average user behind a machine and let him use it with both a vendor supplied kernel and one with full preemption, 1000Hz timer frequency, RCU preemption, no debugging and correct processor family, he probably wouldn't be able to tell the difference.

Building your own kernel is fun and instructive (and sometimes even necessary) but, doing it to increase performance isn't generally a valid a reason (sometimes it is though!).  I think it's very common for a placebo effect to come into play when you try to make something fast before you've quantified slow.

I think your getting ahead of yourself, I didn't say anything about slower or being faster, go look up the term "optimized" and then maybe you'll get what I mean.

It's pointless throwing in the "average user" card because it's not even about them.

---

### Post by sdennie on 2008-12-29
> **Half-Left said:**
> I think your getting ahead of yourself, I didn't say anything about slower or being faster, go look up the term "optimized" and then maybe you'll get what I mean.

It's pointless throwing in the "average user" card because it's not even about them.

I think we'll have to agree to disagree here.  That or we could agree to have a few pints at Ye Olde Trip to Jerusalem and then fight it out.  The buses in Buenos Aires are not very reliable though so, I might be late.  :)

---

### Post by klange on 2008-12-29
SSSE3 is "SSE4" (see [here](http://en.wikipedia.org/wiki/SSSE3), not really SSE4, but what came after SSE3)

Manually building a kernel is usually done *just* for the performance boost associated with optimizing for the current platform, that's why it's done - not to usually to add features.

---

### Post by sdennie on 2008-12-29
> **WindowsSucks said:**
> 
Manually building a kernel is usually done *just* for the performance boost associated with optimizing for the current platform, that's why it's done - not to usually to add features.

/sigh

Please show me the relevant benchmarks that show that compiling your own kernel increases performance in a meaningful way.  I think you may find these benchmarks hard to come by.

---

### Post by Half-Left on 2008-12-29
It's not about benchmarking, it's about having your system optimized and if it didn't make a difference then there would be no point in them extra options.

It's known fact that OS X has very low latency which is ideal for sound recording and such.

---

### Post by klange on 2008-12-29
> **Half-Left said:**
> It's not about benchmarking, it's about having your system optimized and if it didn't make a difference then there would be no point in them extra options.

It's known fact that OS X has very low latency which is ideal for sound recording and such.

One of the great things about having control over your target hardware.

You want benchmarks, I'll go get them (but not right this minute, maybe later today? Shouldn't take too long to build the kernel...). I'll custom compile 2.6.28 for my laptop and compare it to the Jaunty-distributed 2.6.28-4 that I'm currently running (just better remind me to not enable GEM when I compile my DRM modules, as that would be cheating).

The last time I personally compiled a kernel just for a feature was back when Ubuntu didn't ship with support for my ENE SD card reader...

---

### Post by sdennie on 2008-12-29
> **Half-Left said:**
> It's not about benchmarking, it's about having your system optimized and if it didn't make a difference then there would be no point in them extra options.

It's known fact that OS X has very low latency which is ideal for sound recording and such.

Like I said before, for some workloads, a custom compiled kernel will certainly be beneficial.  However, if benchmarks can't prove that a machine is operating faster for your workload then it isn't.

> **WindowsSucks said:**
> One of the great things about having control over your target hardware.

You want benchmarks, I'll go get them (but not right this minute, maybe later today? Shouldn't take too long to build the kernel...). I'll custom compile 2.6.28 for my laptop and compare it to the Jaunty-distributed 2.6.28-4 that I'm currently running (just better remind me to not enable GEM when I compile my DRM modules, as that would be cheating).

The last time I personally compiled a kernel just for a feature was back when Ubuntu didn't ship with support for my ENE SD card reader...

I'm running 2.6.28 with a .config that I've been lugging around for years.  The problem with benchmarking for kernel optimizations is that you are probably going to end up benchmarking a synthetic load.  If you are able to benchmark a real load then, yes, you now have a measurement and can actually apply changes to the kernel config that may benefit your day to day usage of the machine.  Outside of that ability, all performance enhancements to the kernel are anecdotal and probably a placebo.

---

### Post by klange on 2008-12-29
> **vor said:**
> ... Outside of that ability, all performance enhancements to the kernel are anecdotal and **probably a placebo**.

I'm not sure I get this "placebo effect" you're talking about: Are you saying that I'm going to will my laptop into taking less time to do thousands of ssl signs and pi calculations because I *think* it's on a faster kernel?

---

### Post by Half-Left on 2008-12-29
Yes, just go tell the kernel devs that their work for performance is placebo, you just flushed their work down the toilet without providing any evidence yourself to the contrary.

---

### Post by sdennie on 2008-12-29
> **WindowsSucks said:**
> I'm not sure I get this "placebo effect" you're talking about: Are you saying that I'm going to will my laptop into taking less time to do thousands of ssl signs and pi calculations because I *think* it's on a faster kernel?

No, I'm saying that if your workload lends itself to a certain kernel configuration then using that kernel configuration will help you.  If you blindly change your kernel configuration so that it seems like it's going to be fast, regardless of whether or not it is faster, you are likely to think it is.

> **Half-Left said:**
> Yes, just go tell the kernel devs that their work for performance is placebo, you just flushed their work down the toilet without providing any evidence yourself to the contrary.

As I've already said a few times, for some workloads a different kernel configuration can make a night and day difference in performance.  However, as my signature states, you need to understand "slow" before you can make something "fast".  Pushing all the "Go Fast" buttons in "make menuconfig" doesn't mean that your machine will run faster for your particular usage.

---

### Post by Half-Left on 2008-12-29
> **vor said:**
> No, I'm saying that if your workload lends itself to a certain kernel configuration then using that kernel configuration will help you.  If you blindly change your kernel configuration so that it seems like it's going to be fast, regardless of whether or not it is faster, you are likely to think it is.



As I've already said a few times, for some workloads a different kernel configuration can make a night and day difference in performance.  However, as my signature states, you need to understand "slow" before you can make something "fast".  Pushing all the "Go Fast" buttons in "make menuconfig" doesn't mean that your machine will run faster for your particular usage.

And as I said, it helps to reduce latency and overhead, I didn't say it would make your system magically run at warp speed.

---

### Post by sdennie on 2008-12-29
> **Half-Left said:**
> And as I said, it helps to reduce latency and overhead, I didn't say it would make your system magically run at warp speed.

Ok.  Then show me your benchmarks that show that latency and overhead is noticeable and usefully decreased with your custom kernel.  I have done performance optimization for many years and have learned that benchmarking of the way you actually use your machine is the only way to understand "fast", "slow" or "optimized".  Unless you have those benchmarks, any and all optimization is, once again, probably a placebo.

---

### Post by Half-Left on 2008-12-29
Your the one thats making the accusations, go mail the kernel devs. I've said already one of the reasons why OS X is so good for music is because it has very low latency.

I suggest you mail Linus and tell him to yank out all the optimization and customization because it's only placebo.

> **Optimize**

Modify to achieve maximum efficiency in storage capacity or time or cost; "optimize a computer program"
Make optimal; get the most out of; use best; "optimize your resources

---

### Post by sdennie on 2008-12-29
> **Half-Left said:**
> Your the one thats making the accusations, go mail the kernel devs. I've said already one of the reasons why OS X is so good for music is because it has very low latency.

I suggest you mail Linus and tell him to yank out all the optimization and customization because it's only placebo.

I'm really not looking for an argument here.  Yes, for some workloads, a custom kernel will be beneficial.  And, I'm thankful to the kernel devs that they have had the foresight to predict those workloads and include the relevant options.  That doesn't mean that compiling your kernel with "--OMG-FAST" will make any noticeable difference in how your machine behaves.

---

### Post by InspiredIndividual on 2009-01-17
This discussion has certainly moved away from the original question:
> **JohnLau said:**
> My CPU (AMD Athlon 64 x2 5400+) is supposed to support SSE3, but I can't see that in /proc/cpuinfo. Any ideas why?:confused:

I had a similar question and I might have found the answer in another thread ([http://ubuntuforums.org/showthread.php?t=576963](http://ubuntuforums.org/showthread.php?t=576963).).
> **psychicist said:**
> (...) do have SSE3 support but it's not called that way. You should look for "pni", which stands for Prescott New Instructions, when typing "cat /proc/cpuinfo".

One of the flags in /proc/cpuinfo of both the original poster and myself is 'pni' indeed, so I hope this answers the original question.

---

