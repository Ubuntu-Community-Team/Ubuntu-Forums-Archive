---
title: "Why does 64bit is always associated with AMD?"
date: 2012-05-08
forum: The Cafe
---

### Post by kenweill on 2012-05-08
I wonder why in Linux, or Ubuntu in particular, 32bit is i386 and 64bit is amd64.

Why amd64? 
And why i386?

amd64 seems like it's only for AMD and i386 is for Intel only.
Why not just 64bit and 32bit, just like MS does?

---

### Post by Bandit on 2012-05-08
AMD had the first working 64bit CPU for the masses.
Intel at the time was still working on IA64, but still couldn't get the bugs worked out enough to function for everyday users at the time.

---

### Post by kenweill on 2012-05-08
> **Bandit said:**
> AMD had the first working 64bit CPU for the masses.
Intel at the time was still working on IA64, but still couldn't get the bugs worked out enough to function for everyday users at the time.

I don't think that's still the case as of today. Or is it?

---

### Post by sammiev on 2012-05-08
> **kenweill said:**
> I wonder why in Linux, or Ubuntu in particular, 32bit is i386 and 64bit is amd64.

Why amd64? 
And why i386?

amd64 seems like it's only for AMD and i386 is for Intel only.
Why not just 64bit and 32bit, just like MS does?

Likely because AMD had troubles working with the 64bit software at first. If people do not see amd64 they will likely feel it will not work on their computers. I have no issues with the name that is given.

---

### Post by Bandit on 2012-05-08
> **kenweill said:**
> I don't think that's still the case as of today. Or is it?
Its slowly fading out, more standard now is just 64bit. But some packages still show AMD64, just because of legacy reasons. 


> **sammiev said:**
> Likely because AMD had troubles working with the 64bit software at first. If people do not see amd64 they will likely feel it will not work on their computers. I have no issues with the name that is given.
AMD? Troubles? What is this you speak of?
Intel had heck of loads of issues getting theirs worked out. I am sure AMD did to, but AMD got them fixed and released their CPU first.

---

### Post by kenweill on 2012-05-08
> **sammiev said:**
> If people do not see amd64 they will likely feel it will not work on their computers. I have no issues with the name that is given.

I have Core i5 (2nd generation) laptop and I'm always in doubt using amd64 version. It may or may not work on my machine as it's not AMD. And if it works, may end up into problems later. I'm not confident if it will be stable in my machine or not.

---

### Post by Bandit on 2012-05-08
> **kenweill said:**
> I have Core i5 (2nd generation) laptop and I'm always in doubt using amd64 version. It may or may not work on my machine as it's not AMD. And if it works, may end up into problems later. I'm not confident if it will be stable in my machine or not.

IA64/AMD64 is fully interchangeable these days. Your fine :)

By the way my wife is from Mindanao.

---

### Post by GabrielYYZ on 2012-05-08
> **Bandit said:**
> IA64/AMD64 is fully interchangeable these days. Your fine :)

By the way my wife is from Mindanao.

Intel's x86_64 name is EM64T or Intel 64. 

IA64 == itanium, it's different and incompatible with x86_64.

(just wanted to clear that up :popcorn:)

---

### Post by CharlesA on 2012-05-08
> **kenweill said:**
> I have Core i5 (2nd generation) laptop and I'm always in doubt using amd64 version. It may or may not work on my machine as it's not AMD. And if it works, may end up into problems later. I'm not confident if it will be stable in my machine or not.

It's just a name. ;) I've run the "amd64" edition of both AMD and Intel boxes with no problems.

Of course your CPU has to support 64-bit but that would be almost any of the newer CPUs.

> **GabrielYYZ said:**
> Intel's x86_64 name is EM64T or Intel 64. 

IA64 == itanium, it's different and incompatible with x86_64.

(just wanted to clear that up :popcorn:)

Yep. IA64 needed special software and hardware from what I remember. Different architecture. I guess you could say it is a bit like ARM vs x86/x64.

---

### Post by oldfred on 2012-05-08
AMD had a license for the 32bit version of Intel. Intel wanted a totally new design for 64 bit that was not compatible with the 32 bit, the IA-64. 

AMD then developed a 64 bit design that could also run the 32 bit code and it became popular and for once Intel followed someone else.

[http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

From the python page:
The binaries for AMD64 will also work on processors that implement the Intel 64 architecture (formerly EM64T), i.e. the architecture that Microsoft calls x64, and AMD called x86-64 before calling it AMD64. They will not work on Intel Itanium Processors (formerly IA-64).

---

### Post by wolfen69 on 2012-05-09
> **kenweill said:**
> I have Core i5 (2nd generation) laptop and I'm always in doubt using amd64 version. It may or may not work on my machine as it's not AMD. And if it works, may end up into problems later. I'm not confident if it will be stable in my machine or not.

Huh? <scratches head> I have the same i5 2nd gen and can assure you it is perfectly compatible. I've been running it ever since that cpu first came out.

---

### Post by Bachstelze on 2012-05-09
> **kenweill said:**
> I have Core i5 (2nd generation) laptop and I'm always in doubt using amd64 version. It may or may not work on my machine as it's not AMD. And if it works, may end up into problems later. I'm not confident if it will be stable in my machine or not.

You were told that it will work. If you're still not confident, well... it's your problem.

---

### Post by kenweill on 2012-05-09
> **wolfen69 said:**
> Huh? <scratches head> I have the same i5 2nd gen and can assure you it is perfectly compatible. I've been running it ever since that cpu first came out.

Thanks. Good to know that you didn't have problem with it.

> **Bachstelze said:**
> You were told that it will work. If you're still not confident, well... it's your problem.

I'm just confused on the naming scheme. As to why 64bit is amd64 and 32bit is i386.

Some people might think, amd64 won't work on their core i5 machine as it's not AMD processor in the first place.

Some distro uses x86_64 at the end of their ISO. I think that's more precise name for newer processors (at least dual cores).

---

### Post by craig10x on 2012-05-09
It is totally compatable on both amd and intel....i am running an intel i3 core on my laptop and running the 64 bit version and it is absolutely fine...

The only puzzle to me is why they still call it amd...i can see why people (such as yourself) would get confused into thinking that it wouldn't work for you...

---

### Post by doorknob60 on 2012-05-09
amd64 was used because at first it was only on AMD processors, and they didn't want people to confuse it with Intel's completely different IA-64. You still see amd64 floating around because some people haven't seen the need to change the name. Most of the time now though, you see it called x86_64 (or sometimes x64). Really though, all you need to know is that x86_64 and amd64 are the exact same thing, just different names.

---

