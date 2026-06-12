---
title: "Processor Speeds?"
date: 2008-07-31
forum: The Cafe
---

### Post by ghindo on 2008-07-31
I've got a gaming computer with a Pentium D processor which runs at something like 3.4 GHz.  If I got a newer processor (something like a Core 2 Duo) running at a lower frequency, will it perform better?  I've heard that processor speeds are relative, but don't know for sure.  This sorta knowledge is kinda beyond me. :p

---

### Post by Darkhack on 2008-07-31
I'm not saying Megahertz don't matter, but they are seriously overrated as a means of measuring performance.  Apple did a keynote where they had an explanation of the [Megahertz Myth]("http://www.youtube.com/watch?v=PKF9GOE2q38") where they explained why the G4, running at *half* the clock speed of a P4 was *twice* as fast.  As another example, Intel's upcoming micro-architecture, Nehalem, runs 35% faster than the Core 2 at the exact same clock speed.  The only time Mhz really matters for comparison is when you're comparing CPUs that are of the same micro-architecture.  Otherwise, it's almost a worthless means of measurement.

I'd read reviews and benchmarks online to find which processor will give you the best performance for your budget.  [Tom's Hardware]("http://tomshardware.com") is a good site and I'm sure someone can recommend a few other sources too.

---

### Post by tuxxy on 2008-07-31
AMD 2 perform much better at dualcore, althgouth slightly behind now in the quads am sure it wont be long before it overtake intel again.

---

### Post by tuxxy on 2008-07-31
please delete, re-post

---

### Post by Depressed Man on 2008-07-31
> **tuxxy said:**
> AMD 2 perform much better at dualcore, althgouth slightly behind now in the quads am sure it wont be long before it overtake intel again.

I thought the AMD2s paled in comparsion to the Intel Core 2 Duos?

---

### Post by LaRoza on 2008-07-31
Core 2's are much better than Pentium D's. Make sure your motherboard can use it however, My motherboard is the right socket, but can't use Core 2's.

---

### Post by OutOfReach on 2008-07-31
So, lets say, a Core 2 Quad at 2.5 GHz would run faster than, mm lets say, a Core 2 Duo at 3.0 GHz?

---

### Post by LaRoza on 2008-07-31
> **OutOfReach said:**
> So, lets say, a Core 2 Quad at 2.5 GHz would run faster than, mm lets say, a Core 2 Duo at 3.0 GHz?

Yes, much more so. It would also use less power and generate less heat.

---

### Post by ghindo on 2008-07-31
The answers so far have been great, thanks guys! :)  If clock speed isn't an accurate representation of how "good" a processor is, is there any single factor representative of how well a processor runs?> **OutOfReach said:**
> So, lets say, a Core 2 Quad at 2.5 GHz would run faster than, mm lets say, a Core 2 Duo at 3.0 GHz?Quad core vs. Dual core computing is a whole 'nother ballgame, if I understand correctly. I think quad core performance depends on how the program its running is designed.  

In any case, I don't think it's as simple as 4 > 2.

---

### Post by PRMan on 2008-07-31
How applications are compiled matters a little, but the reality is that on any operating system there are at least 50 things going on when you are sitting at the desktop after boot.

If you ever run 2 applications, you can definitely use 2 processors regardless of how the individual applications are written.  This is very helpful in getting around any lockup problems as hardware is accessed.

The problem with quad core is that people have a harder time doing 4 things at once.  But if you are watching a video or listening to music while copying quotes from the internet into a document, you can easily do it.  Heck, with 4 cores you could be encoding MP3s and burning CDs while you're at it.

---

### Post by Darkhack on 2008-07-31
> **ghindo said:**
> If clock speed isn't an accurate representation of how "good" a processor is, is there any single factor representative of how well a processor runs?

Not entirely.  How well a processor performs depends on the task.  Some CPUs can perform certain algorithms faster than others.  That's why you have to read benchmarks carefully, because one CPU might do well in a particular area, but be totally destroyed by the competition in others.  

There is a website created by PassMark software called [CPU Benchmarks]("http://www.cpubenchmark.net/") where they use benchmarking software to come up with an averaged number.  It can give you a rough idea of how well one CPU performs compared to another overall.

To further my explanation about the Mhz Myth, CPU Benchmarks shows a 3.46 Ghz Celeron D as being 3x slower than a Core 2 clocked at 2.13 Ghz.  Notice that's not a Dual core, that's a plain, single core, Core 2.

> **ghindo said:**
> Quad core vs. Dual core computing is a whole 'nother ballgame, if I understand correctly. I think quad core performance depends on how the program its running is designed.  

In any case, I don't think it's as simple as 4 > 2.

You are correct.  Multiple cores are designed for parallelism (running multiple apps at once).  Some multithreaded applications can benefit from multiple cores too (such as video encoders) but it does depend on the program that's running.  If a program is doing calculations where the next calculation depends upon the result from the previous one, then you can't really do it in parallel and multiple cores won't help much.

Jeff Atwood, the author of [Coding Horror]("http://www.codinghorror.com/blog/"), had this to say on the issue...

[QUOTE=Jeff Atwood]Outside of a few niche activities, such as video encoding and professional 3D rendering, most computing tasks don't scale worth a damn beyond two cores. Yes, it's exciting to see those four graphs in Task Manager (and even I get a little giddy when I see sixty-four of 'em), but take a look at the cold, hard benchmark data and the contents of your wallet before letting that seductive 4 > 2 math hijack the rational parts of your brain.[/QUOTE]

I concur with the above statement 100%.  Although, I'm a bit disappointed in [Atwood's post]("http://www.codinghorror.com/blog/archives/001157.html"), because in the exact same blog post he said...

[QUOTE=Jeff Atwood]Despite what Intel's marketing weasels might want you to believe, **clock speed still matters very much**.[/QUOTE]

He's the one who bolded that segment, not me.  Unfortunately, Atwood failed to mention that clock speed really only matters when you're making the comparison on the **same micro-architecture**.  I know that Atwood knows this, but it was a pretty critical mistake for him to assume that his reader knows this when the Megahertz myth is still so common.

---

### Post by articpenguin on 2008-07-31
Ghz dosent mean that much anymore. That is a why a C2D can outperform a PD that is twice its Ghz. Because the C2D does more in a clock cycle than the Pentium D.

---

### Post by Atomic Dog on 2008-07-31
Been building workstations for a couple years.  We are now buying only quads and core2duo chips.  The E8400, 8500 is my personal choice right now -maybe the quads have more in the future but for now the 8500 seems snappier than a similarly priced quad.  Good balance of speed and power when mated with an appropriate motherboard.

---

### Post by tel93 on 2008-08-01
all this talk of lovely chips makes my ashamed of my 366 mhz K6-2 :(

---

### Post by ghindo on 2008-08-01
When I made this thread, I was worried if I replaced my Pentium D with a lower-clocked Core 2 Duo, I'd be throwing away money.  Now I know that it'd actually be very worthy my while :)> **Atomic Dog said:**
> Been building workstations for a couple years.  We are now buying only quads and core2duo chips.  The E8400, 8500 is my personal choice right now -maybe the quads have more in the future but for now the 8500 seems snappier than a similarly priced quad.  Good balance of speed and power when mated with an appropriate motherboard.Yeah, I was thinking about getting an E8400/E8500 - they seem to be the best buy for the money.  By the way, what do you man "an appropriate motherboard"?

---

### Post by J.T. on 2008-08-01
Another thing to look at with processors is the amount of cache. That's high speed memory that acts as a buffer for getting data to the processor. The more cache the better and the more expensive.

---

### Post by y@w on 2008-08-01
> **J.T. said:**
> Another thing to look at with processors is the amount of cache. That's high speed memory that acts as a buffer for getting data to the processor. The more cache the better and the more expensive.

Cache is probably more important than the number of cores.. In most computing environments, processing speed isn't the bottleneck anymore, it's I/O speeds. The more cache you have on your processor the less the machine has to go out to memory and the more memory the machine has, the less time it has to wait for the disk. Processors still do matter, don't get me wrong, but disk I/O and cache is probably a more important factor when looking at performance. Also, a dedicated graphics card will help as well since then the computer doesn't have to waste CPU time doing video processing.

---

### Post by Atomic Dog on 2008-08-02
> **ghindo said:**
> When I made this thread, I was worried if I replaced my Pentium D with a lower-clocked Core 2 Duo, I'd be throwing away money.  Now I know that it'd actually be very worthy my while :)Yeah, I was thinking about getting an E8400/E8500 - they seem to be the best buy for the money.  By the way, what do you man "an appropriate motherboard"?

Something that obviously supports dual channel memory, 1066/1333 Mhz bus, maybe some overclocking capability.  The real cheapie boards (like the cheap ECS boards) can lack some features you will probably want.  For a company workstation that will only run Word, and excel, ECS works fine, for my home system...Asus CK5C [http://usa.asus.com/products.aspx?l1=3&l2=11&l3=534&l4=0&model=1694&modelmenu=1](http://usa.asus.com/products.aspx?l1=3&l2=11&l3=534&l4=0&model=1694&modelmenu=1)
I have also setup the new 45nm chips with this gigabyte board: [http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2778&ProductName=GA-EP35-DS3L](http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2778&ProductName=GA-EP35-DS3L)
and it worked great also.

So when I say appropriate, I really mean something of good quality and performance.

---

### Post by daverich on 2008-08-02
and yet no matter how many cores you have, insert a cd into your drive for burning and it'll hold up everything....

I wish someone would fix that.

Kind regards

Dave Rich

---

### Post by Zero Prime on 2008-08-02
Also remember that your chipset plays a big factor as well.  Example.  I have an AMD 4600+ dual core and my motherboard uses the AMD 780G chipset and 2 gigs of ram in dual channel mode.  You would think a dual core 5000+ AMD proc should out perform it, yet in benchmarks where the 5000+ had the same amount of RAM, but using an Nvidia chipset, my system actually out performes the 5000+ system.

---

### Post by mips on 2008-08-02
> **OutOfReach said:**
> So, lets say, a Core 2 Quad at 2.5 GHz would run faster than, mm lets say, a Core 2 Duo at 3.0 GHz?

Hmm, that depends. If all four cores are used by an application then it will be faster. If the application however is not optimised for multiple cores and only uses one core it will run faster on the 3.0GHz Core 2 Duo.

It's not always a clear cut thing if you get what I mean.

---

### Post by mips on 2008-08-02
> **ghindo said:**
>  By the way, what do you man "an appropriate motherboard"?

You have to make VERY sure that the motherboard will support the CPU you are buying. There are cases where motherboards will support one version of a Q6600 but not the other version of the Q6600.

Best bet is to check on your motherboard manufacturers website where that specific model of CPU will work on your motherboard. Socket type is no onger a gaurantee as to whetehr it will work or no.

---

### Post by Delever on 2008-08-02
I find two cores to be perfect for me.

Cases:

1. CPU intensive application, like virtual machine, uses only one core, but takes all of it's power. I can **always** use other apps at the same time because one core remains free (no slow down).
2. Working with huge images in GIMP, applying filters. Many filters only use one core, which with Quad CPU would mean using only 1/4 of power.
3. It's better to buy processor for existing applications, not for "would be" applications. Some say hundreds of cores are the future, but right now it does not mean nothing more than 1/100 of power in most cases.

And yes, I know what threads are.

---

### Post by OutOfReach on 2008-08-02
> **mips said:**
> Hmm, that depends. If all four cores are used by an application then it will be faster. If the application however is not optimised for multiple cores and only uses one core it will run faster on the 3.0GHz Core 2 Duo.

It's not always a clear cut thing if you get what I mean.

Yes I get what you're saying if the program is multithreaded (correct term?) then it will run faster on more than one core, right?
Well I guess it can't hurt to have a Quad core.

---

### Post by Delever on 2008-08-02
> **OutOfReach said:**
> Yes I get what you're saying if the program is multithreaded (correct term?) then it will run faster on more than one core, right?
Well I guess it can't hurt to have a Quad core.

If program is multithreaded, it can run on both.
If program is single threaded, it can only take advantage of one core.

Coding multithreaded applications is harder than single-threaded ones. Just imagine code executed not from start-to-finish, but all-over-the-place. Yeah. Little bit more planning required ;)

---

### Post by mips on 2008-08-03
> **OutOfReach said:**
> 
Well I guess it can't hurt to have a Quad core.

That was my thoughs as well when I got a Q6600.

---

