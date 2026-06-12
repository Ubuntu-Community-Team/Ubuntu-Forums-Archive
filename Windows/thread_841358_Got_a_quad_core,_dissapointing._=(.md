---
title: "Got a quad core, dissapointing. =("
date: 2008-06-26
forum: Windows
---

### Post by skymera on 2008-06-26
Hey.

Last week i bought a new processor, i was chuffed. =D

I had a Core 2 Duo E6300 @ 1.86GHz 2MB L2 for 18months, i needed more oomph for games and compiling kernels.

So looking around i settled for a Q6600 2.40GHz 8MB L2.
I was expecting a lot more speed in loading times and games.

Well i've had it a week and if anything, i had a performance DECREASE.
Seriously, feels like I've blown £130.

Compiling kernels has been quicker but that's about it.

Windows XP i use for gaming.
In Assassins creed I've had a performance decrease, if i go to "Assassinate" someone, my PC freezes for a bout a second then it finally does it. That NEVER happened with my E6300..

Garrys Mod based on Half Life 2 i get sharp FPS decrease when spawning LESS things than my E6300. If i stack 40 things i go from 160FPS to 1FPS! My E6300 would usually go down to 30-40FPS. It's a joke! >_<

Also if i have all 4 cores at 30% load my PC is so sluggish the mouse cursor wont even move!!

Something has to be wrong, does XP need to be tweaked for it to enable quad cores and use them effectively?

Can someone shed some light on this? It's so frustrating.:mad:

---

### Post by eragon100 on 2008-06-26
Thanx, I also have an e6300 @ 1.86 GHz and I *was* considering to buy a new one, now I won't! :)

---

### Post by Trail on 2008-06-26
Well, compiling stuff is certainly very much dependant on the number of cores you have; you should see great improvement there.

Concerning most other things, they are rarely coded to take full advantage of multiple cores, so unless you put your system under a LOT of load... well...

---

### Post by Moustacha on 2008-06-26
There might be drivers for XP to properly balance the load or timing, like the AMD dual-core optimiser

---

### Post by dominiquec on 2008-06-26
I believe XP only supports up to two processors.

---

### Post by Moustacha on 2008-06-26
two physical sockets for Pro, 1 physical for home, as many cores as you can fit on there (atm)

---

### Post by msrinath80 on 2008-06-26
For modern games, it is the GPU and the total memory bandwidth in the GPU that matters most. Not the CPU. You could use a machine with even 32 CPU cores and would not see any improvement. Of course, you could see some minor improvement if the game in question is multithreaded or specifically coded to take advantage of multiple cores. But this is pretty rare to my knowledge.

As for faster game loading times, the peripheral of interest is the hard drive. Try to make sure it has enough onboard cache and the highest possible RPM. Also, a fast memory chip can boost the data transfer rates, especially in Intel-based computers which still use the FSB to communicate data from main memory (RAM) to the CPU. Of course a higher FSB clock speed will also help.

---

### Post by skymera on 2008-06-26
I have a feeling it's XP.

In Ubuntu i can run several things with ease.

---

### Post by gn2 on 2008-06-26
Have you checked on the motherboard support page to see if there is a BIOS upgrade for the Q6600 ?

---

### Post by Black Mage on 2008-06-26
Ok, for your problem, first thing you should do is learn about the operating system. It expliciting says in EULAs of XP that it will only use 2 cores. Same for certain versions of Vista.

And then even if the operating system is able to use all 4 cores, the applications have to be able to use 4 cores also.

Now I have the same CPU that you have and it works great. What I do is I run XP using VMare running on top of Linux, and give two processors to the emulator. The result is XP works perfectly fine, and this is while virtualizing two sessions of XP and having my Linux side stream video.

---

### Post by skymera on 2008-06-26
Even if the applications use 1 core, then why are they performing worst on 2.4GHz than 1.86?

---

### Post by toupeiro on 2008-06-26
I've actually been in some, and done some talks relating to multi-core hardware and multi-threaded software.  There is most definitely a point of diminishing return with multi-core chips with todays systems that consist of primarily single-threaded with some multi-threaded applications.  Even some multi-threaded apps are not designed to leverage multi-core to the fullest.

Most people outside of work I know spent money on a quad core chip just to say they have it, not because they did any research on whether or not it would actually benefit them.  Cache is a big thing.  You have to be careful with a quad core chip and shared cache because its very easy for a heavy single-threaded application to get greedy and suck up the resources from your other multi-threaded apps, resulting in a net loss of performance.

AMD's current Quad Core Opteron got this right.  What you have effectively is 4 dedicated L1/L2 chahes for each core with a third shared L3 cache.  With the Intel quads available now, what you essentially have is 2 dual cores in their I/O design with an integrated memory controller that shares all the layers of cache.  While this will make your single threaded apps rock the casbah, while they are rocking, they are hurting your multi-threaded apps.  Intel's next gen Quad core will implement a very similar, almost exact design of the opteron quad, of course taking the necessary measures like increasing the amount of L3 cache, but they are leaving the l2 cache at 256 while the current day Opteron gives you 512.  L2 is significantly faster cache so it will be interesting to see where the next-gen intel benchmarks on true multi-threading.


Another misconception is that all multi-threading is the same.  It isn't!  There are apps designed for core major multi-threading, and apps written for socket-major multithreading, and boards that support the same respectively.  If your apps are written for socket-major multithreading, and you have 4 cores on one chip, you are not going to properly utilize your quad-core processor.

I'll briefly try to explain with a cat /proc/cpuinfo of one of my Sun x4600's at work.  Its not using the quad core chips, but it doea have 4 dual core chips in it. :> 

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 65model name      : Dual-Core AMD Opteron(tm) Processor 8220
stepping        : 3
cpu MHz         : 2792.920
cache size      : 1024 KB
**physical id     : 0**
siblings        : 2
**core id         : 0**
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes


processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 65
model name      : Dual-Core AMD Opteron(tm) Processor 8220
stepping        : 3
cpu MHz         : 2792.920
cache size      : 1024 KB
**physical id     : 0**
siblings        : 2
**core id         : 1**
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1

processor       : 2
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 65
model name      : Dual-Core AMD Opteron(tm) Processor 8220
stepping        : 3
cpu MHz         : 2792.920
cache size      : 1024 KB
**physical id     : 1**
siblings        : 2
**core id         : 0**
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1

processor       : 3
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 65
model name      : Dual-Core AMD Opteron(tm) Processor 8220
stepping        : 3
cpu MHz         : 2792.920
cache size      : 1024 KB
physical id     : 1
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1

processor       : 4
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 65
model name      : Dual-Core AMD Opteron(tm) Processor 8220
stepping        : 3
cpu MHz         : 2792.920
cache size      : 1024 KB
physical id     : 2
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1

processor       : 5
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 65
model name      : Dual-Core AMD Opteron(tm) Processor 8220
stepping        : 3
cpu MHz         : 2792.920
cache size      : 1024 KB
physical id     : 2
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1

processor       : 6
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 65
model name      : Dual-Core AMD Opteron(tm) Processor 8220
stepping        : 3
cpu MHz         : 2792.920
cache size      : 1024 KB
physical id     : 3
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1

processor       : 7
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 65
model name      : Dual-Core AMD Opteron(tm) Processor 8220
stepping        : 3
cpu MHz         : 2792.920
cache size      : 1024 KB
physical id     : 3
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1

The things I've bolded indicate this motherboard is configured to support core-major.    As you can see, physical CPU ID 0 is associated with Core-ID 0 and 1.

If this were a socket-major configuration, what you might see here is Physical ID 0 is associated with Core ID 0 and Physical ID 1 or 2 is associated with Core-ID 1 depending on the configuration.  This is done to multi-thread between sockets, and was the absolute standard of multi-threading before multi-core chips became commonplace.  There are still benefits to socket-major multi-threading if your computing is memory intensive, but if your computing is CPU intensive then core major is a better choice for you because you can eliminate a potential bottleneck in your hypertransport.  Socket major multi-threading with quad cores means you are not even close to fully utilizing your cores before you start leveraging the other socket, and you put more CPU I/O across the hypertransport.  Because multi-socket systems have dedicated DDR# RAM, this can be a good thing for you, or a wasteful thing.

I hope I've done a half way decent job at explaining this.  Its an interesting subject for me.  In my personal opinion, the sweetspot is still a really good dual-core processor unless you really need CPU intensive resources.  Remember that some commercial software licenses by core and not socket. :)

Cheers!

---

### Post by FuturePilot on 2008-06-26
> **skymera said:**
> Even if the applications use 1 core, then why are they performing worst on 2.4GHz than 1.86?

I've heard this before, that sometimes running games on a multi-core CPU that were not designed to take advantage of a multi-core CPU can actually decrease performance. Try specifically telling an application to use only one core. You can do this through Task Manager by changing the Affinity value, but I've never fooled around with that so I don't know exactly how to do it.

---

### Post by ezphilosophy on 2008-06-26
> **gn2 said:**
> Have you checked on the motherboard support page to see if there is a BIOS upgrade for the Q6600 ?

+1

I bought an e8400 and had to flash my bios.

---

### Post by timzak on 2008-06-26
Did you verify in XP that all 4 cores are running (via Task Manager->Performance tab)?  Did you just plug the cpu in, or did you reinstall XP?  When I upgraded from single core to dual core on Windows 2000, I needed to reinstall the OS for it to recognize both cores.  Might be worth looking into.

---

### Post by skymera on 2008-06-26
@toupeiro - very helpful and very detailed thanks!

@timzak - Yes all 4 cores show with some activiy usally 6% on each etc.

@ezphilosophy - my BIOS is latest and supports the Q6600 fully.

---

### Post by timzak on 2008-06-26
Since you only seem to be having a problem in XP, it might be worth your while to do a clean install anyhow to see if it clears it up.

> **skymera said:**
> @toupeiro - very helpful and very detailed thanks!

@timzak - Yes all 4 cores show with some activiy usally 6% on each etc.

@ezphilosophy - my BIOS is latest and supports the Q6600 fully.

---

### Post by skymera on 2008-06-27
> **timzak said:**
> Since you only seem to be having a problem in XP, it might be worth your while to do a clean install anyhow to see if it clears it up.

Would be a bit tricky, i have XP installed on 2 seperate hard drives.:(

---

### Post by hessiess on 2008-06-27
personaly i like my Q6600, it decreses rendering times ALOT. I dont polay games(waste of time) so that dosent matter. quad cores will only help with multithreded apps, or running a large number of single thredded apps.

---

### Post by toupeiro on 2008-06-27
Couple of things to verify:  

Are you running XP Pro or Home?  XP Home will only support 2 processors while Pro will support 4 with a little help.  I truly recommend you read this thread on [notebookreview.com]("http://forum.notebookreview.com/showthread.php?t=60416") and verify the steps against your XP Pro installation.  In your case, you would not perform the AMD specific steps, and keep in mind that if this is a desktop, make the PerfEnablePackageIdle reghack a 0 instead of a 1 as you're not really worried about battery life.

Another caution for you is the boot.ini settings on this page.  It sounds like you have multiple instances of windows XP installed on multiple drives, so make sure you BACK UP your current boot.ini as this boot.ini indicated that the first drive on your primary disk controller will be the first bootable drive.

Also keep in mind that even with these hacks, It doesn't change the fact that XP Pro itself it not truly multithreaded, it sets affinity for its processes across your cores, but it does not factor in load balancing.  What it can do with these tweaks is much more efficiently load balance multi-threaded applications you run on XP.

---

### Post by skymera on 2008-06-28
Thanks, im using XP Media Center Edition which is Pro so that's good.

Just reading your link now..

---

### Post by Canis familiaris on 2008-06-28
I am sure Linux would be performing better in your Quad Core. Though programs are not exclusively coded to utilize the quad cores but Linux does well in balancing tasks on multiple cores. It does well on my dual core at least.
Do not think you wasted your money on Q6600. It is one hell of an overclocker.

ALSO perhaps XP SP3 will help.

---

### Post by Erunno on 2008-06-28
> **skymera said:**
> 
I was expecting a lot more speed in loading times and games.


Loading times are mostly dependent on I/O throughput and latency and not raw number crunching power of a CPU. Most operating systems try improve loading times by prefetching data from the hard disks or keep it cached in memory if it has been read already but if you happen to hit cold caches then your CPU will have to wait until the data is read from the relatively slow harddisk while twirling its thumbs.

> 
Well i've had it a week and if anything, i had a performance DECREASE.
Seriously, feels like I've blown £130.

As others have already written most current applications are not optimized for heavy parallel computing so they'll do most of their computation in one thread. 2 cores have been a nice improvement over the single core architectures even with single-threaded applications as the OS can do all of its maintenance stuff on one core while applications run on the other. With more cores the gains are much more dubious although I'd expect from a scheduler that it distribute applications on different cores.

> 
Compiling kernels has been quicker but that's about it.

GCC has been heavily optimized for parallel computing so it's one of the applications which will scale nicely with an increasing number of CPUs / CPU cores.

---

### Post by mips on 2008-06-28
skymera,

Check that your cpu freq scaling is properly setup. Post the output of cpufreq-info here. You need **cpufreutils** installed though.

You will probably find that your cpu is being clocked at 1.6GHz and not at 2.4GHz

Next see these two threads:
[http://ubuntuforums.org/showthread.php?t=749947](http://ubuntuforums.org/showthread.php?t=749947)
[http://ubuntuforums.org/showthread.php?t=652312](http://ubuntuforums.org/showthread.php?t=652312)

EDIT: Oops, I see the problem is windows specific. Others might still find the info usefull though.

---

### Post by MaxIBoy on 2008-06-28
> **dominiquec said:**
> I believe XP only supports up to two processors.

[img]http://img179.imageshack.us/img179/391/quadcoresnx3.png[/img]
So there.

---

### Post by MellonCollie on 2008-06-30
> **MaxIBoy said:**
> [img]http://img179.imageshack.us/img179/391/quadcoresnx3.png[/img]
So there.



As Moustacha said...

> **Moustacha said:**
> two physical sockets for Pro, 1 physical for home, as many cores as you can fit on there (atm)

---

### Post by jnw222 on 2008-07-03
the only thing that is multi-threaded is Flight Simulator X (sp1 or 2)

---

