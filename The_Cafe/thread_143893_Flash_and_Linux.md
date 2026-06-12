---
title: "Flash and Linux"
date: 2006-03-13
forum: The Cafe
---

### Post by bonzodog on 2006-03-13
I know some people on here may already be aware of this, but there is an explanation here of why Linux users are being kept waiting for Flash 8:

> 
Thursday, December 22, 2005
Flash Player 8 for Linux update
Emmy Huang, Product Manager of the Flash Player, explains what the plans concerning the Linux version of Flash Player 8 are. Instead of releasing a 8.0 version we will directly move to 8.5 on Linux. This will avoid even more delay after we ship Flash Player 8.5 for Windows and Mac. That will also make sure that the new virtual machine works using gcc from start. I see that as a big benefit as gcc is a more strict and standards compliant compiler than Visual Studio or CodeWarrior.

We have a few very good engineers working on the Linux version right now in parallel to the work we do for 8.5. 64bit versions will take a little longer, there are no definite plans just yet. Just recompiling will not work unlike what you might think. The main issue here is the x86 JIT in the virtual machine and the mark&sweep garbage collection which are not 64bit aware right now, work on 32bit pointers only. Adding and testing this is not a small task as anyone who ever worked on this type of low level infrastructure might be able to attest. I can really only ask for patience here, we are aware that we need to offer a solution as soon as possible.


This also explains what the problem is with 64 bit coding, it seems that 64 bit low level code is presenting some problems for them.

---

### Post by Denta on 2006-03-13
Is there an approx release date for Flash 8.5 then?

---

