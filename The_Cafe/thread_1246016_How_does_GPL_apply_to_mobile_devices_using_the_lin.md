---
title: "How does GPL apply to mobile devices using the linux kernel?"
date: 2009-08-21
forum: The Cafe
---

### Post by Glenn Jones on 2009-08-21
Hi Guys,

The recent GPL, BSD license thread got me thinking about mobile phones which use linux kernel as their base (e.g. Google's Android platform)  and how GPL applies in such cases if it applies at all!!!!

I have a HTC Hero phone (which is awesome might I add) and that has it's own UI called the Sense UI. I am not sure if Sense is open source or not. 
Seeing that the UI is built on top of the kernel does this mean that it too must be licensed under GPL? or can it be licences with something else? If you can license it with something else surely there is nothing stopping me using the linux kernel and building a propriety UI on top to sell to the masses (e.g. similarly to what Apple did with Darwin BSD).

Also how does GPL apply to the Android application store for example. Does the code have to be released under GPL? if so there is nothing stopping me getting the code, compiling the app on my phone, doing all of this for free.

Thanks

---

### Post by Bachstelze on 2009-08-21
> **Glenn Jones said:**
> 
Seeing that the UI is built on top of the kernel does this mean that it too must be licensed under GPL?

No. The UI and the kernel are two independent parts, so the UI is not affected by the virality of the kernel's GPL. The X server, which you use everyday on your Linux desktop, is not GPL either. All this applies to other applications as well.

---

### Post by Glenn Jones on 2009-08-21
I see thanks. I always thought that so long as part of the sofware was licensed under GPL they whole thing was GPL. 

So in theory Apple could have used the linux kernel for OSX, but if they made any changes to the kernel they would have to release it.

In a way GPL is a reactive solution to a moral problem.

---

### Post by Bachstelze on 2009-08-21
> **Glenn Jones said:**
> I see thanks. I always thought that so long as part of the sofware was licensed under GPL they whole thing was GPL.

That's true, but the kernel and the UI are not the same software.

> So in theory Apple could have used the linux kernel for OSX, but if they made any changes to the kernel they would have to release it.

Correct.

---

### Post by ssam on 2009-08-21
if you modify the linux kernel (and distribute the modified version), then you have to allow people the same rights they had to the original kernel, eg to see and be able to modify the code.

if you run a program on top of a kernel they are considered separate by the GPL.

it is slightly more complex with libraries. if you use a library then you are including those functions/classes into your application. so your application is considered a modified version of the library code. so only an GPL program can use a GPL library. the LGPL allows non-GPL code to link to a GPL library.

---

### Post by 3rdalbum on 2009-08-21
> **Glenn Jones said:**
> I see thanks. I always thought that so long as part of the sofware was licensed under GPL they whole thing was GPL. 

So in theory Apple could have used the linux kernel for OSX, but if they made any changes to the kernel they would have to release it.

Not only that, but you cannot distribute a Linux kernel with pre-inserted proprietary drivers.

---

### Post by Glenn Jones on 2009-08-21
Thank you guys.

That has cleared a lot of things up.

---

### Post by perce on 2009-08-21
> **ssam said:**
>  the LGPL allows non-GPL code to link to a GPL library.

You mean to a LGPL library I guess

---

