---
title: "AMD Quad-Core vs Intel Dual-Core - Same Price?"
date: 2012-12-03
forum: The Cafe
---

### Post by dannyboy79 on 2012-12-03
I have always ran Intel CPU's. My best machine currently is 7 years old, an Intel 1.8ghz Core 2 Duo w/ 2gb of DDRII ram. I am looking to upgrade soon and am noticing a HUGE price difference between AMD and Intel CPU's.

I can get an AMD QUAD CORE combo from tigerdirect
GIGABYTE GA-78LMT-S2P AMD 760 AM3+ Motherboard and AMD FX-4100 3.60 GHz Quad Core AM3+ Unlocked Processor Bundle
for only 173.99 after rebate

and if I try to spec an intel chip for around same price this is what I get
ASUS P8H61-M LE CSM REV3 Intel 6 Series Board and Intel Core i3-2120 3.30 GHz Dual Core Processor Bundle

Why are AMD CPU's so cheap compared to intel? I do a lot of video editing with kdenlive so the 2 extra cores would be nice if I went with AMD quad-core.

Thoughts?

---

### Post by Bandit on 2012-12-03
The amount of cores does not always adequate for overall performance nor justify price.
I have been a huge AMD fan for years, but have been really sold on the Intel Ivy Bridge price/performance ratio of their new processors.  Even more so since many of them clock per clock totally dominate anything AMD has thrown at them. 

Here is benchmark link on Anandtechs site, hope it helps you make a clear judgment.
[http://www.anandtech.com/bench/CPU/2](http://www.anandtech.com/bench/CPU/2)

They only list a i3-2120 and a FX4300. They both appear to be neck and neck performance wise. I would then just assume to use what ever is cheaper. Being the AMD in this case.

Keep in mind to also use the latest motherboard chipsets. The Z77 is most current IIRC for intel, forgot the AMD chipset. But older chipsets can have less features such as USB 3.0 and PCI Express 3.0. So stick with latest chipsets as they can be just as important to performance as the CPUs themself.

---

### Post by 3Miro on 2012-12-03
The AMD FX series isn't really 4-cores, because every two cores have to share some resources. AMD's technology is better than Intel's Hyper Threading, but not quite as good as having 4 full cores.

Also, the 760 chipset is old. It comes with 4xxx series integrated video card and recently the AMD dropped their support for 4xxx series on the proprietary AMD driver.

Having said that, i3 is on the low end of Intel, so don't expect much of performance. While the Intel video drivers are good (as in not crashing), their overall performance is weak. Furthermore, i3-2120 is the older Sandy Bridge (not Ivy Bridge) and hence it comes with weaker graphics altogether.

I can't call a clear winner, in both cases I would advise you to get an additional graphics card (low end AMD or Nvidia, but modern 7xxx or 6xx).

I don't like giving advice to people on how to spend their money, but I would suggest that you consider spending a bit more money and then having a system that lasts longer, saving in the long run. AMD's new Trinity chips look promising giving both performance and graphics for a reasonable price. Also, looks at Intel's i5-3xxx Ivy Bridge processors with Intel HD 2500 or 4000 graphics.

---

### Post by Bandit on 2012-12-04
> **3Miro said:**
> The AMD FX series isn't really 4-cores, .....
Actually the AMD FX's do all have real cores. FX-4series is actually 4 cores, thus FX-6 (six), FX-8 (eight cores).. I think your getting confused with intels i7 chips. The i7-3770 in my gaming rig for example shows as 8 cores, but is actually just 4 real cores. It basicly seesaws workload back on forth on them trying to make most use of each core. Where as their i5 series only shows up as 4 cores and doesnt use the thread technology used in the i7s. Now keep in mind some laptops use a mobile version of these chips and can have less cores. My Macbook Air for example is a Core i5, but reduced to 2 cores only. 

But like I mentioned, cores dont make or break a system. Just let the benchmarks help guild you to the performance in the area you need.

---

### Post by HibyPrime on 2012-12-04
> **Bandit said:**
> Actually the AMD FX's do all have real cores....


Not true, AMD bulldozer/piledriver architectures have a weird setup.

For every "core" in these CPUs there is one ALU, and half an FPU.  So a quad core FX-4100 has 4 ALUs and 2 FPUs

Different workloads hit different parts of the CPU.  The ALU handles integer calculations, while the FPU handles calculations where the numbers have decimal points.  I honestly have no idea which part video editing will hit.

[http://www.anandtech.com/bench/Product/700?vs=677](http://www.anandtech.com/bench/Product/700?vs=677)  in these benchmarks they appear to trade blows quite a bit, making them fairly even in performance.  It's worth noting that the intel chip does it while having a 40w lower TDP though (consumes almost half the power)

---

### Post by mips on 2012-12-04
If you wanna buy AMD then I won't look at anything but Piledriver based CPUs right now. The AMD you listed earlier is pretty old.

FX-8320 vs i5 3570K
[http://www.anandtech.com/bench/Product/698?vs=701](http://www.anandtech.com/bench/Product/698?vs=701) 

Another option is the FX-8350. At the end of the day you need to do a cost vs performance comparison taking both CPU&MB prices into consideration.

---

### Post by 3Miro on 2012-12-04
> **Bandit said:**
> Actually the AMD FX's do all have real cores. FX-4series is actually 4 cores, thus FX-6 (six), FX-8 (eight cores).. I think your getting confused with intels i7 chips. The i7-3770 in my gaming rig for example shows as 8 cores, but is actually just 4 real cores. It basicly seesaws workload back on forth on them trying to make most use of each core. Where as their i5 series only shows up as 4 cores and doesnt use the thread technology used in the i7s. Now keep in mind some laptops use a mobile version of these chips and can have less cores. My Macbook Air for example is a Core i5, but reduced to 2 cores only. 

But like I mentioned, cores dont make or break a system. Just let the benchmarks help guild you to the performance in the area you need.

Intel's hyper-threading technology lets you switch between threads on a single core very efficiently. Effectively, the OS will show twice as many cores (i.e. 8 on a 4-core i7). This is better than having just 4 cores, but not nearly as good as having 8 real ones.

In the AMD case, two by two cores will share some resources. There are things that the cores can do completely independently (as if they were 4 full cores), however, there are also resources that they have to share (for example the floating point registers). While AMD's 4 technology gives you more than hyper-threading, it is still not as good having 4 full cores.

---

### Post by Bandit on 2012-12-04
> **HibyPrime said:**
> Not true, AMD bulldozer/piledriver architectures have a weird setup............

> **3Miro said:**
> Intel's hyper-threading technology ................

Hmm, (scratches head) If both of you are calling me out. Then I honestly must have mis read their datasheets.. O well it happens.. LOL.. I wouldnt purposely give out bad info and will go back and re look over the data sheets again as I must have really missed something.. 

Cheers, 
Joe :)

---

### Post by mips on 2012-12-04
> **Bandit said:**
> Hmm, (scratches head) If both of you are calling me out. Then I honestly must have mis read their datasheets.. O well it happens.. LOL.. I wouldnt purposely give out bad info and will go back and re look over the data sheets again as I must have really missed something.. 

Cheers, 
Joe :)

This could be considered a bit of a grey area due to architectual differences but in my book AMD still has 4 real cores.

---

### Post by HibyPrime on 2012-12-04
> **Bandit said:**
> Hmm, (scratches head) If both of you are calling me out. Then I honestly must have mis read their datasheets.. O well it happens.. LOL.. I wouldnt purposely give out bad info and will go back and re look over the data sheets again as I must have really missed something.. 

Cheers, 
Joe :)

It's a pretty easy mistake to make, AMD describes 2 Module (4ALU and 2FPU) as quad-core pretty much everywhere.  It's an open question as to whether they're justified in doing that.

Anandtech has a pretty in-depth write up in their original bulldozer review that describes it all: [http://www.anandtech.com/show/4955/the-bulldozer-review-amd-fx8150-tested/2](http://www.anandtech.com/show/4955/the-bulldozer-review-amd-fx8150-tested/2)

---

### Post by leclerc65 on 2012-12-04
End of life, AMD dumps these quite cheap

[http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=1724262](http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=1724262)

---

### Post by Bandit on 2012-12-04
> **leclerc65 said:**
> End of life, AMD dumps these quite cheap

[http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=1724262](http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=1724262)

Gonna miss those. They were quite good and they out performed the FX-8series hands down..

---

### Post by dannyboy79 on 2012-12-05
> **Bandit said:**
> Gonna miss those. They were quite good and they out performed the FX-8series hands down..so would that be a good purchase for me? Money is tight, seems like a great CPU. Even has onboard video to my understanding?

---

### Post by HibyPrime on 2012-12-05
> **dannyboy79 said:**
> so would that be a good purchase for me? Money is tight, seems like a great CPU. Even has onboard video to my understanding?

6-core phenom II?  $100?  YES!

It doesn't have on-chip video, but it wouldn't be hard to find a motherboard with integrated video.  Here's an example: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813138345](http://www.newegg.com/Product/Product.aspx?Item=N82E16813138345)

If your video editing software is hardware (GPU) accelerated you might want to think about getting a cheap discrete GPU though.

---

