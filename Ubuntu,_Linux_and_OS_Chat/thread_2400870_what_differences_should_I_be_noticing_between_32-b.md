---
title: "what differences should I be noticing between 32-bit and 64-bit Lubuntu?"
date: 2018-09-11
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2018-09-11
From Lubuntu 12.04 to 16.04, I've only used 32-bit on my 2008 64-bit Desktop computer, because at the time I wasn't aware that my computer was 64-bit.

Here's the specs of my desktop:
```
Processor: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
Memory: 3072MB
Machine Type: Desktop
Operating System: Ubuntu 18.04.1 LTS 64-bit
```

I've installed Lubuntu 18.04.1 LTS 64-bit on this computer and I don't noticed much difference between 32-bit and 64-bit.

---

### Post by mastablasta on 2018-09-11
you can now use 64bit programs. some (calculating) tasks are faster done in 64bit. if all you do is browse and write you won't notice the difference.

---

### Post by ardouronerous on 2018-09-12
I still don't understand though, what makes 64-bit better than 32-bit?

---

### Post by QIII on 2018-09-12
An admittedly hyperbolic comparison:  Passenger jet vs horse and buggy.

Both move people. 

The jet can move a lot more people at a time much faster than a horse and buggy.

Consider the numbers 2^64 and 2^32.   That's not just double.  

That's 18,446,744,073,709,551,616 vs 4,294,967,296.   Set aside for the moment any consideration of what those two values mean in absolute terms (that could lead to oversimplified assumptions), and think what they represent in ***scale***.  That affects not only the scale of operations that can be done, but also the amount of RAM that can be addressed.  It does not mean that a 64 bit machine is 4 billion times faster than a 32 bit machine (that's where the oversimplification might lead you).

What it means is that a 64 bit machine/OS is capable of doing more than a 32 bit machine/OS.  A lot more.  So much more that running enough apps/calculations/whatever to make a 32 bit machine choke and give up is trivial for a 64 bit computer.

If all you are interested in are things like word processing and some light web browsing, you might never notice any difference at all if you can still find 32 bit software.  But if, like me, you use your machine for running sophisticated software, large databases and multiple Virtual Machines, using a 32 bit OS would be like trying to load 300 passengers on a buggy and getting the horse to go 550 mph.  You'd crush the buggy and kill the horse.  Again with the hyperbole.

A more practical comparison would be an SUV versus a Smart -- if they were both as fuel efficient.  Both can be used to get you back and forth to the light rail station to get to work.  But if you want to load up the family with 2 weeks of supplies and pull your boat to your favorite lake, well, the SUV is the better choice.

---

