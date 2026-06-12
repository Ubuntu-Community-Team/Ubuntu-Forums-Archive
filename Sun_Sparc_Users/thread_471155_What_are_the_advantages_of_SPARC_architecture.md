---
title: "What are the advantages of SPARC architecture?"
date: 2007-06-11
forum: Sun Sparc Users
---

### Post by Tommerz on 2007-06-11
what are the advantages of SPARC architecture, and why do people use them?

I've read a little on wikipedia, but still find myself mystified. :o

Is there anywhere to buy a SPARC pc, and can you use them as home computers, or is it more of a server product? Is it a bit like Powerpc in that you can get a pegasus style board and just add generic pc components and build a sparc machine?

---

### Post by halfconscious on 2007-06-11
My understanding is that for pure power sparcs fell off the curve a few years back.
Sun have given up that race and moved to intel architecture for their own server and 
workstation products. 
Sparcs are still worth considering if you're making your own system (on chip or FPGA) as
they have an open architecture - last I heard you could get a license for $99 from Sparc
Intl, but hopefully they've stopped even that tax. There are free implementations if you
don't fancy making your own ( LEON ) . 
A typical feature of Sparc architecture is the large number of registers - grouped into 
overlapping sets indexed by CWP (current window pointer). CWP is decremented as a function
is entered  - the output registers of the calling code become the input registers for current
function. It's quite a neat way to pass up to 8 32bit function arguments ( for Sparc8 32bit)
in a single cycle. In lightweight systems this feature can to some extent mitigate the absence
of a data cache for carefully crafted code.

---

### Post by jpdrawneek on 2007-06-11
> **halfconscious said:**
> My understanding is that for pure power sparcs fell off the curve a few years back.
Sun have given up that race and moved to intel architecture for their own server and 
workstation products. 


Not quite, theres only one intel box so far.  Theres also a load of AMD boxes, its a case of thats what people are buying so lets sell them too.

Sparc T1 are quite cool, i do really nice things with them in web and multimedia streaming.

Theres also Rock on the horizon so sparc is not quite dead in suns eyes.

---

### Post by reidms on 2007-06-11
Sparc boxes have way less downtime than Intel/AMD.  i.e. on Sparc machines, you can access the BIOS with the machine still running(no reboot, etc)

The cheapest place to buy Sparc machines: eBay, unless you are willing to pay a minimum of about 3000USD for a new one.

You can use them as home computers- I just ordered another for a home computer

You can buy parts outta best buy, etc for a Sparc-

Sparc machines are rock solid- If you are interested- you could buy a older system to try out, like an Ultra 5 or Ultra 10 and see if you like it-

Though Sparcs are limited to which operating systems they can run(main supported Linux distros: Debian, Ubuntu, Gentoo;;FreeBSD;;Or Suns own Solaris operating system)

Just make sure it comes with a keyboard, and you have an adaptor for your monitor(The Ultra 5s and 10s have a normal 15pin type connector- but most Sun machines have a 13w3 connector)


> Sun have given up that race and moved to intel architecture for their own server and
workstation products. 

Half of their current workstations are Sparc..... and I believe there are more Sparc servers than intel/AMD

---

### Post by tgalati4 on 2007-06-12
My meager understanding is that SPARC and PPC are RISC architectures--reduced instruction set.  There are perhaps ~50 opcodes used to program the assembly language for these processors.  The Intel family is a CISC or complex instruction set with perhaps ~100 instructions.

This was important when instruction cache was small so that a RISC machine could run more efficiently with a smaller cache and optimize more easily because there are less op codes to handle.

Now, CPU's have large instruction and data caches available.  Combined with higher bus speeds and cranked up CPU clocks, I'm not sure if there really is a performance edge between CISC and RISC.

Perhaps someone out there has run recent benchmarks to see the performance difference.

Because of the increased, original cost, perhaps the build-quality of SPARC and PPC machines is better than new, low-end Intel machines.  So for server use or dedicated workstation use (i.e. not multimedia, but number-crunching/scientific analysis) then RISC machines may have an advantage.

I like the old Silicon Graphics Octane machines with the 64-bit IRIX OS.  It's double precision was 128-bits (called quad precision or 4x32-bit) and it allowed you to solve some interesting problems on an astronomic scale.

---

### Post by deserthowler on 2007-06-12
When it comes to price, I buy scrap working Sparcs for about $5.  :D  I found some free on free-cycle.  I have 3 Tatung COMP station 10s, one U30, one U60, one U10 and one SS20 and a used 3-13 monitor for less than $50.  They seem to just sit there and crank away forever. 

Graphics aren't great.  Program availability is limited.  I work in LaTeX, Emacs, Bash and Xterm mostly and they are great.  Iceweasel runs fine but refreshes a little slow and many plugins are lacking.  I use FVWM as a window manager and AMSN for chatting.  I use the Gimp once in a while and they all work just fine.

They just feel like they are designed by engineers and not accountants.

Not everyone has one and they do present challenges sometimes.

Earl

---

### Post by max_lan on 2007-06-25
The SPARC and Sun computers are great for multi-user environments. We had 30 developers working happily on a server with 4*270Mhz CPUs, 2G RAM and an FC-AL disk array. They were developing a graphical memory hungry program.
They actually had more CPU/RAM on their own desktops but it just wasn't efficient to use it. Even compiling on the server versus a more apparently powerful Linux desktop box, the Sun was quicker.
Simple answer :
one user : PC
10 users : Sun/HP/other 'real' unix box (not linux on a single CPU with IDE disk)

---

### Post by ykanello on 2007-07-06
I will speak for modern processors for new systems.
Sun seems to be focusing on sparc-T processors. 
I had few tests machines (t2000) and i played enough with them.
The T2000 has 8 cores but with one ALU for all cores.
According to spec web performace it is outstanding. The problems arise though when the cpu needs to do some computing.
Just as an apache/php server it run faster than most of the systems we had.
Running sql on it as well was killing the machine. 
On the other hand a dual dual opteron (2 cpu's 2 cores) was actually running heavy applications much faster. 
Personally I would be careful in what cpu I use for what application. 
As for the older sparc machines, they might rock solid, but a 200% execution time of the same php command (0.45sec on intel p4, 1.2sec on sparc niagara)  is really making the system obsolete :(
I am in the process to replace all sparc based cpu systems with opteron ones. still prefer sun hardware, but not RISC anymore :(

---

