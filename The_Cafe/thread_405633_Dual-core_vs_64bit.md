---
title: "Dual-core vs 64bit"
date: 2007-04-10
forum: The Cafe
---

### Post by yano on 2007-04-10
What I have found ironic about the processor race between Intel and AMD is that they have been pushing for the Dual-core and now even Quad-core for Intel.

Why has the focus shifted more towards the dual-cores (which I think still run 32bit) and less focus on a single core 64 bit.) Wouldn't a dual-core of a 32 bit be equvilant to a single 64 bit?

What do you guys think?

---

### Post by SunnyRabbiera on 2007-04-10
Intel's dual core run's circles around AMD right now I am afraid, I have seen it for myself.
I am not sure how intel's new dual cores work but in terms of sheer speed intel is waaay ahead.

---

### Post by hardyn on 2007-04-10
the core2duos are dual core 32/64bit.
most of the amd offerings are the same, dual core 32/64bit

but intel has come up with a really efficent design, and even better manufacturing process... they have a better design, and are able to make them cheaper than AMD... and if that wasn't enough, the new 45nanometer process allows them to change the chemestry of the transistors to make them more efficent and faster... so a faster cooler processor that uses less current.

AMD is going to have to figure something out, they are going to behind the ball for the next few years.  although that is with conventional processor design... this merger with ATI has them looking in different ways of designing processors, making them more like GPUs with have better Floating speeds that most x86 derived processors right now.  they have also been looking at manuf. physics co-processors that are all the buzz in the game world right now.

---

### Post by siimo on 2007-04-10
No.

Dual Core 32bit means theres 2 CPUs  capable of addressing 32bit long addresses.  So if you run multiple things together you have 2 CPUs to share the load.

A 64bit single core CPU can address more memory 64bit long.  But it is just a single CPU.   A dual core would be a lot faster than a single core regardless of its bit size.

But this is all besides the point.  As currently **ALL** new AMD and Intel CPUs are 64bit.  Both single and dual core ones, cheap and expensive ones.   Yes the Centrino and Core Duo (original not Core2 Duo) were 32bit.  

But now Core 2 Duo desktop and mobile, Pentium D, Celeron D, AMD Athlon, Turion, Sempron desktop and mobile are ALL 64bit.

---

### Post by Spr0k3t on 2007-04-10
> **yano said:**
> Wouldn't a dual-core of a 32 bit be equvilant to a single 64 bit?

Oh my, you should learn a bit more about the differences of 32bit cisc and 64bit cisc.  Two processors running the same speed and cache settings will be about the same speed regardless of the bit structure unless the application used to test the processor is optimized for 64bit.  Depending on how the endian bit is set in the machine language is how the memory is controlled at the processor level.  A well developed test application designed for 64bit will run faster than the 32bit optimized version of the same application, but not by leaps and bounds to say the equivalency of two separate processors.  Essentially, 32bit + 32bit = 32bit times 2.  Unless the test application is able to handle asynchronous parallel processing, it will still only utilize the single core of the two core processor.  Please keep in mind, I'm no expert on the subject either and will more than likely be corrected for some of my statements.

Personally 64bit is the way to go imho, but if you can't afford a two core 64bit processor, save up a bit more and then shop around.  You will be happier with a two core 64bit... at this time it's the closest thing you can get to a future proof processor.

(am I the only one who hates the name "core2duo"?)

---

### Post by beefcurry on 2007-04-10
Sorry, for me its always been Intel for the win.

I do loads of things and dual core/HT technology is just better for that, just cause one program eats 100% of one core dosnt mean the other core will fill up too. 64bit by theory is faster then 32bit for processing large amounts of data (such as database etc) but 2 x 32 runs as many cycles as 64bit. anyway this is My Opinion only. It could be disputed depending on which chip vs which chip.

---

### Post by %hMa@?b&lt;C on 2007-04-10
> **beefcurry said:**
> Sorry, for me its always been Intel for the win.

I do loads of things and dual core/HT technology is just better for that, just cause one program eats 100% of one core dosnt mean the other core will fill up too. 64bit by theory is faster then 32bit for processing large amounts of data (such as database etc) but 2 x 32 runs as many cycles as 64bit. anyway this is My Opinion only. It could be disputed depending on which chip vs which chip.

you are correct about the 2x32 > 64, but almost every single dual core out is a 64 bit.  For example the C2Ds are EM64T (64 bit) the whole Hammer (opteron) series is 64 bit.  All the Athlons that are Dual core are 64 bit.

---

### Post by Compucore on 2007-04-10
At any rate your running more processes when your running with a dual core or quad core processors. If you have software besides the operating system like Ubuntu, or Windows 2000, XP pro or Vista that will take advantage of a dual core, quad or two or more single core processors. You'll never really see the difference of what is happening with the exception of being faster access to the software. When it gets assigned to a processor or one of the two cores if your running a dual core machine. I can understand using a dual processor or a dual core single processor if you need the sheer power of calculations or your processing large amounts of raw data that needs to be processed like in a dataware in Oracle. Or your into something like High performance computation. So far software wise that will take advantage of this are these. Operating systems, CGI animation for making films, Oracle 10G.

The light version of Oracle like the 10G express will only use a single processor, 1 gig of ram, and about 4.3 gigs for the data. And doesn't use a second processor at all.

Compucore

---

