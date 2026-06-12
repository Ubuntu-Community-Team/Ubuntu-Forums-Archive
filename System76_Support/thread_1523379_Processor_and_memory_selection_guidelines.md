---
title: "Processor and memory selection guidelines"
date: 2010-07-03
forum: System76 Support
---

### Post by Morgan le Fay on 2010-07-03
Hi! I'm considering buying a system76 laptop, and I'm a bit lost among the processor and memory options. I have three specific questions, although unsolicited advice would also be appreciated. ;)

[LIST=1]
[*]Memory options are described like this:
> 4 GB – DDR3 1066 MHz 2 DIMMsIs "1066 MHz" the front side bus speed?
[*]Are there bottleneck effects that make certain processor/memory combinations less cost-effective, or can I choose processor and memory pretty much independently of each other?
[*]I've heard that a quad-core processor can slow down applications that aren't designed to take advantage of it, because the cores of a quad-core processor tend to be substantially slower than the cores of a dual-core processor (as is the case with system76's processor options). Am I right to be afraid that my shiny quad-core processor will be worse than useless unless I custom-build my favorite performance-hungry applications at 3:00 AM using obscure, unreliable compiler flags?
[/LIST]
Thanks for your help! :)

---

### Post by PabloH on 2010-07-03
> **Morgan le Fay said:**
> Hi! I'm considering buying a system76 laptop, and I'm a bit lost among the processor and memory options. I have three specific questions, although unsolicited advice would also be appreciated. ;)

[LIST=1]
[*]Memory options are described like this:
Is "1066 MHz" the front side bus speed?
[*]Are there bottleneck effects that make certain processor/memory combinations less cost-effective, or can I choose processor and memory pretty much independently of each other?
[*]I've heard that a quad-core processor can slow down applications that aren't designed to take advantage of it, because the cores of a quad-core processor tend to be substantially slower than the cores of a dual-core processor (as is the case with system76's processor options). Am I right to be afraid that my shiny quad-core processor will be worse than useless unless I custom-build my favorite performance-hungry applications at 3:00 AM using obscure, unreliable compiler flags?
[/LIST]
Thanks for your help! :)

The speed next to the ram is the speed at which the ram operates, not the FSB.

For a look at how much faster ram helps:

[http://techreport.com/articles.x/15967](http://techreport.com/articles.x/15967)


Older quad cores did not have turbo boost and they were indeed slower at single threaded tasks that dual cores with higher clock rates. 

You need a quad core that supports turbo boost. i7 supports it.  Figure out the maximum amount that the turbo will take the processor core's to-- and use that number to compare it with a  dual core's. If the turbo value goes up to 3.2 Ghz, for example-- then your machine will be as fast as the equivalent dual core (with the same cores) at 3.2 Ghz when running only one thread. 

This gives you the best of both worlds. 

As for getting the best performance out of multiple cores with a program, that is a complicated subject. Suffice it to say that recompiling is often (not always) a waste of time. The program must be structured and programmed to take advantage of the multiple cores. If it is not, it will won't matter much how many flags you use when you compile it.

---

