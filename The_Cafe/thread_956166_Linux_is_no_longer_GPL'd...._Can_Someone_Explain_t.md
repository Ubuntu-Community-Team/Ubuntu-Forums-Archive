---
title: "Linux is no longer GPL'd.... Can Someone Explain the Android OS 'Free' License to me?"
date: 2008-10-22
forum: The Cafe
---

### Post by earthpigg on 2008-10-22
I haven't found any threads on this, but read the [_wikipedia article_]("http://en.wikipedia.org/wiki/Android_(mobile_device_platform)").... which tells me just enough to be confused about what i **thought** i understood about FOSS and GPL software.

How is Android using the Linux kernel but **not** using the GPL? Why can google randomly choose some other FOSS license? Can i go ahead and unilaterally declare some random license a 'free software license' and distribute Linux using that?

How is this operating system 
> It has also come to light that some functionality will be reserved for approved applications making it impossible for 3rd parties to develop some types of application to compete with pre-install applications such as Marketplace.
free software...?

Wasn't GPL 2 re-written to GPL 3 **specifically** to combat [_Tivoization_]("http://en.wikipedia.org/wiki/Tivoization")?

is that why Google is somehow trying (succeeding) in using a different software license (Apache)?


these questions are not sarcastic, i am genuinely puzzled.

---

### Post by zachtib on 2008-10-22
the kernel is still gplv2, not gplv3

linus has made it very clear he does not live gplv3

---

### Post by earthpigg on 2008-10-22
.... are they using the last Linux kernel that was released under GPL 2 and getting away with it because of that somehow?

---

### Post by cardinals_fan on 2008-10-22
> **earthpigg said:**
> .... are they using the last Linux kernel that was released under GPL 2 and getting away with it because of that somehow?
What do you mean by "the last"?  Linus Torvalds isn't using GPL v3.

---

### Post by LaRoza on 2008-10-22
> However, Google has since announced that all parts of the OS will be released under the Apache License where applicable and under the GPL elsewhere. 

From the wikipedia page.

---

### Post by TBOL3 on 2008-10-22
Yup.  That's pretty much it.  The linux kernel is still under the GPL, but the new stuff is under a different license.

Another example of this type of thing is ubuntu and firefox.  Linux is under the GPL, and Firefox is under Mozilla's license.  But they can be packaged together.

---

### Post by dhughes on 2008-10-23
It's like OS X which is BSD based (not sure if it's freeBSD or not), the kernel 'Darwin' is Open Source but all the added stuff; everything else other than the kernel is not. It's like Linux which is the kernel and GNU which is everything else you see.

---

### Post by MaxIBoy on 2008-10-23
Not really, the BSD licenses allow companies to rip off code and put it in closed-source stuff (that's how Microsoft got Internet support into their products.) Apple *could*'ve kept Darwin closed-source, but they were hoping to profit from community code contributions for free (which didn't work out, but still.)

Darwin is based on NEXTstep, with bits and pieces taken from various other BSDs. (Although all current BSDs forked from FreeBSD at one point or another.)

---

### Post by earthpigg on 2008-10-23
well then. it looks like linus is indeed set on sticking with gpl 2. see [this link]("http://lkml.org/lkml/2006/1/27/339") for details....

---

### Post by nvteighen on 2008-10-23
Wait a minute. Are you sure they're trying to re-license the kernel? Or have they just created non-GPL stuff around the GPL Linux kernel?

If it's the second, it's absolutely legal, as it is considered usage of the kernel, not a derivative work.

---

### Post by Mr. Picklesworth on 2008-10-23
Simple answer:
*Android* has nothing to do with the kernel. It just runs on it.

---

### Post by bruce89 on 2008-10-23
> **TBOL3 said:**
> Another example of this type of thing is ubuntu and firefox.  Linux is under the GPL, and Firefox is under Mozilla's license.  But they can be packaged together.

That's not the case for a couple of reasons:

Firefox is not a derivative of the kernel.
Mozilla products are tri-licensed under the GPL, the LGPL and the MPL.

---

### Post by forrestcupp on 2008-10-23
> **bruce89 said:**
> That's not the case for a couple of reasons:

Firefox is not a derivative of the kernel.
Mozilla products are tri-licensed under the GPL, the LGPL and the MPL.

I think he was trying to show an example of why it's ok to have non-GPL stuff together with the GPL'ed kernel.  If you're not satisfied with that example, there are others.  Like the fact that people legally use Opera or proprietary video drivers with Linux.

It's ok to *use* software with different licenses together.  You just can't modify the code and release it under a different license.

---

