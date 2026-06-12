---
title: "The end of the CPU."
date: 2010-01-25
forum: The Cafe
---

### Post by Shibblet on 2010-01-25
Does CUDA really have the ability to run all of the PC functions without the use of a CPU as Nvidia claims?

---

### Post by NoaHall on 2010-01-25
A GPU is a processor. It's just specialised.
And yes, there are a lot more cores on a GPU, and they are far more powerful in some aspects, so yes.

---

### Post by lukeiamyourfather on 2010-01-25
Short answer is no, not really. Even if all of the development was already done (which its not) the CPU would still be faster at serial tasks which is still what I would consider to be the majority of workloads. Also development at this point for GPGPU is considered to take ten times longer than equivalent development for the CPU (according to Tim Sweeney at Epic Games), which makes it not economically feasible to develop for unless the performance gains are ***huge***. Cheers!

---

### Post by audiomick on 2010-01-25
Hallo. I hadn't heard of this until I read your post.
Have you read this?
[http://en.wikipedia.org/wiki/CUDA](http://en.wikipedia.org/wiki/CUDA)

I only skimmed it, but I think claiming that this could replace a CPU is playing with words. CPU means "central processing unit". If something else takes over the processing from the CPU, doesn't it become, by definition, the CPU?

From the brief reading of the Wiki aritcle, it appears that what nVidia might be able to offer is parallel processing using the processing units from their graphics chips. Whilst this might work well, parallel processing is not a new idea.

---

### Post by Chronon on 2010-01-25
> **audiomick said:**
> 
From the brief reading of the Wiki aritcle, it appears that what nVidia might be able to offer is parallel processing using the processing units from their graphics chips. Whilst this might work well, parallel processing is not a new idea.

I agree with this assessment.

---

### Post by ubunterooster on 2010-01-25
It WILL happen; the question is WHEN.

---

### Post by Psumi on 2010-01-25
> **ubunterooster said:**
> It WILL happen; the question is WHEN.

Actually I think the OPPOSITE will happen.

Intel's Core i7 can render graphics better than a graphics card (or to equal) of the today's consumer.

---

### Post by MaxIBoy on 2010-01-25
I agree with Psumi, although I doubt the i7 can actually out-render my 4850.

On the other hand, I think tomorrow's CPUs will look very similar to today's GPUs, with tons of specialized parallel units.

---

### Post by lisati on 2010-01-25
> **ubunterooster said:**
> It WILL happen; the question is WHEN.

> **Psumi said:**
> Actually I think the OPPOSITE will happen.

Intel's Core i7 can render graphics better than a graphics card (or to equal) of the today's consumer.


Quite possibly future architectures will have elements of both central processing power and some kind of distributed and/or delegated processing, and are likely to be as different from current technology as my current laptop is from a Z80 machine I used to use. (Sadly it experienced a system failure accompanied by a puff of smelly blue smoke 17 years ago.)

---

### Post by Psumi on 2010-01-25
> **MaxIBoy said:**
> I agree with Psumi, although I doubt the i7 can actually out-render my 4850.

On the other hand, I think tomorrow's CPUs will look very similar to today's GPUs, with tons of specialized parallel units.

There's also an i9: [http://en.wikipedia.org/wiki/Gulftown_%28microprocessor%29](http://en.wikipedia.org/wiki/Gulftown_%28microprocessor%29)

6 physical cores ;)

---

### Post by Skripka on 2010-01-25
> **Psumi said:**
> There's also an i9: [http://en.wikipedia.org/wiki/Gulftown_%28microprocessor%29](http://en.wikipedia.org/wiki/Gulftown_%28microprocessor%29)

6 physical cores ;)

Meh.  AMD has had 6-core Opterons out for a bit now....as I recall, they also retail for less than the cost of my car. :)

---

### Post by Greenwidth on 2010-01-25
13 GPU's - 12 TFlops - 6000 euros:
[http://fastra2.ua.ac.be/](http://fastra2.ua.ac.be/)

"Almost meets the minimum requirements for Crysis2"

'the early 70's called, they want their knitwear back..'

---

### Post by MaxIBoy on 2010-01-25
> **Psumi said:**
> There's also an i9: [http://en.wikipedia.org/wiki/Gulftown_%28microprocessor%29](http://en.wikipedia.org/wiki/Gulftown_%28microprocessor%29)

6 physical cores ;)That's nice, my 4850 has 800 physical cores.

---

### Post by Simian Man on 2010-01-25
Since Moore's Law hasn't slowed down yet, but we don't need really larger caches or many more traditional CPUs any more, we're going to have more heterogeneity in a single chip.

Some of the cores will be fast, general-purpose units like todays CPUs.  Some of them will be slower, highly parallelized cores geared towards 3D transformations like todays GPUs.  Some of them will ASICs that only implement specific functionality that is found to be useful.  Some of them will be other things entirely.

---

### Post by Frak on 2010-01-25
I think the opposite will happen. We'll probably see graphics hardware turn into specialty peripherals before Nvidia overtakes Intel. Current processors are moving dangerously close to the graphics-on-the-processor with good performance.

---

### Post by Gallahhad on 2010-01-26
Just give me this [http://en.wikipedia.org/wiki/Quantum_computer](http://en.wikipedia.org/wiki/Quantum_computer)

---

### Post by lostinxlation on 2010-01-26
ATI having been acquired by AMD, Intel will really come aggressive on graphics market.
As Intel comes into graphics market, Nvidia has no choice other than trying to getting into CPU territory.  This is just one of the necessary steps that Nvidia has to take to fight back.

---

### Post by 3rdalbum on 2010-01-26
The GPU cannot replace the CPU without completely replacing current PC architecture; because the GPU can only execute code if there is a driver for it.

---

### Post by Warpnow on 2010-01-26
Bigger, more expensive, and more power hungry hardware...yaaaayyy!

*waits patiently for the Cortex A9, all alone in his line...*

---

### Post by Skripka on 2010-01-26
> **Gallahhad said:**
> Just give me this [http://en.wikipedia.org/wiki/Quantum_computer](http://en.wikipedia.org/wiki/Quantum_computer)

Are you sure?

---

### Post by Zoot7 on 2010-01-26
I remember reading an analogy somewhere to the effect that the GPU is sort of similiar to a group of a few hundred school children performing simple numeric caculations simultaneously, whereas the full blown CPU is like 2/3/4 Mathematics Professors performing much more calculated calculations simultaneously.

And it's actually not a bad one. A GPU despite being a full blown Microprocessor, is largely an ASIC. Whilst you can code stuff for it, it's designed for graphics and thus will perform much more efficiently with graphics.

Anyway, the CPU is going nowhere. What's more likely to happen is that the GPU will be integrated on-die with the CPU in the future, and thus the "discrete" GPU is more likely to be phased out.
It makes a huge amount of sense because you can cut out the bottleneck incurred by having a physical connection between individual parts on a motherboard. Power consumption, however becomes a far bigger problem, thus they can really only hope for really capable combinations of the two at much lower technologies than now (45/55/40/32nm), and then huge fabrications challenges that will be presented. 
In short, CPU/GPU platforms are likely to take off big time, but a true powerhouse is a long long way away indeed.

---

### Post by Psumi on 2010-01-26
> **Zoot7 said:**
> Anyway, the CPU is going nowhere. What's more likely to happen is that the GPU will be integrated on-die with the CPU in the future, and thus the "discrete" GPU is more likely to be phased out.
It makes a huge amount of sense because you can cut out the bottleneck incurred by having a physical connection between individual parts on a motherboard. Power consumption, however becomes a far bigger problem, thus they can really only hope for really capable combinations of the two at much lower technologies than now (45/55/40/32nm), and then huge fabrications challenges that will be presented. 
In short, CPU/GPU platforms are likely to take off big time, but a true powerhouse is a long long way away indeed.

You people do realize that the PS2 slim has this, right? A GPU/CPU combo chip?

---

### Post by Zoot7 on 2010-01-26
> **Psumi said:**
> You people do realize that the PS2 slim has this, right? A GPU/CPU combo chip?
Does it? I honestly don't know, it's a loooooong time since I opened up my PS2 to solder a Modchip to the motherboard, and I'm too lazy to google it now. :p

Anyway, that was why I said a *Really Capable Combination*. ;)
I was referring to a typical gaming PC, for instance there's no way any IC Fabricator could put something like an i7/i5/Phenom II on the same die as one of the ATi Evergreen GPUs.
AFAIK both AMD and Intel have such a chip in works but you can be the GPU is going to be rather limited.

---

### Post by Radicc on 2010-01-26
> **Warpnow said:**
> 
*waits patiently for the Cortex A9, all alone in his line...*

You are not alone.  I'm still waiting for more ARM based solutions.

---

### Post by tom66 on 2010-01-26
A GPU is no good as a CPU.

Why? No conditional jumps, no external interface (e.g. you can't access the disk drive, USB, CD or the northbridge), only fast with vector operations (where a CPU can do both scalar and vector operations fast.)

---

### Post by aaaantoine on 2010-01-26
Not only do I think the opposite is true (that a dedicated GPU will move into niche territory moreso than it already is), but Intel [already](http://en.wikipedia.org/wiki/Clarkdale_(microprocessor)) [has](http://en.wikipedia.org/wiki/Arrandale_%28microprocessor%29) CPUs with GPUs built-in to the die (or circuit board; however is the right way to say it, I'm trying to say it's [not the same chip](http://images.hardware.info/news/clarkdale_01.jpg) as the CPU).

CPUs aren't going anywhere.  Even if the GPU becomes the standard processor, it'll just be called a CPU anyway regardless of its architecture.

---

### Post by Chronon on 2010-01-26
> **Gallahhad said:**
> Just give me this [http://en.wikipedia.org/wiki/Quantum_computer](http://en.wikipedia.org/wiki/Quantum_computer)

Why the heck would you want that?  You can't run any traditional programs on it.  It isn't a deterministic state machine.  It's good as a search engine or for cracking public-key encryption and probably certain other tasks that rely on ultra-parallel computation.  A quantum computer will behave more like a specialized computation engine and will probably never run traditional software that is expected to take specific inputs and produce predictable outputs.  I can see a quantum processing unit being integrated into a classical computer, but not taking its place.

---

### Post by juancarlospaco on 2010-01-26
_CPU and GPU get fusioned... ?_

GPU with x86 CPU instructions?, or  CPU with speciallyzed GPU capability?

---

### Post by Shibblet on 2010-01-26
Take a look at the current Nvidia processors.  Up to 260 cores.  Handles the physics processing on the chip.  All graphics calculations are done on the processor now.

This is why when you play a game on a Celeron it runs the same as if you played it on a Core 2 Duo.  Assuming you have the same video card.  Games are becoming less and less dependent on the CPU, and more on the GPU.

Of course this is just games.  However, every thing we look at is graphics anymore.  If you work in a desktop environment, very few things need to be dependent on a CPU.  They are dependent, but it doesn't seem like they need to be.  

Take Nvidia's ION for Netbooks.  It's set up to be a co-processor, and allows for a pretty high-end gaming machine, with an Intel Atom running the system.

It seems to me we're only a few steps away from a single processor that handles CPU and GPU functions.

---

### Post by mmix on 2010-01-26
[http://en.wikipedia.org/wiki/D-Wave_Systems](http://en.wikipedia.org/wiki/D-Wave_Systems)

Although, looks like fake at all, i love to see multiple tries sort of like this.

---

### Post by phrostbyte on 2010-01-26
No. GPUs can't easily do simple things like conditional branching. They are very specialized in doing parallel, mathematical computations that contain no unpredictable branching.

---

