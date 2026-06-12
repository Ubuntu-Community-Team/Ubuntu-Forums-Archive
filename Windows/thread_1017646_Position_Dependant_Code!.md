---
title: "Position Dependant Code!"
date: 2008-12-21
forum: Windows
---

### Post by night_fox on 2008-12-21
Each and every .exe file, .dll file, etc. in windows comes with a specific memory address that it has to be loaded at! If windows cannot load it at that address, it has to load the executable at the wrong address, and then go through the entire program looking for addresses that need to be changed! A hideous bodge! How could this fundamental sloppiness and inefficiency find its way into 90% of all computers?

Does this surprise you?

---

### Post by Battie on 2008-12-22
> **night_fox said:**
> Each and every .exe file, .dll file, etc. in windows comes with a specific memory address that it has to be loaded at! If windows cannot load it at that address, it has to load the executable at the wrong address, and then go through the entire program looking for addresses that need to be changed! A hideous bodge! How could this fundamental sloppiness and inefficiency find its way into 90% of all computers?

Does this surprise you?

I haven't heard of that.  What is the source (I'm really just curious)?

Actually, I thought since Vista Windows loads stuff into memory unpredictably to try to thwart buffer overflow attacks.

Edit: Yes.  It's called [ASLR]("http://blogs.msdn.com/michael_howard/archive/2006/05/26/address-space-layout-randomization-in-windows-vista.aspx").

---

### Post by Battie on 2008-12-22
I'm still thinking about this because I'm curious and don't fully remember what I've read about Windows internals.

Doesn't Windows reserve a lower portion of system memory that's more or less guaranteed to be there for itself, and then applications run in a higher address space?  I can only think that this is bad because of the buffer overflow problem, but ASLR attempts to address this.  Why else would it be a problem?

How does Linux load its system files into memory?

---

### Post by JohnFH on 2008-12-22
> **night_fox said:**
> Each and every .exe file, .dll file, etc. in windows comes with a specific memory address that it has to be loaded at! If windows cannot load it at that address, it has to load the executable at the wrong address, and then go through the entire program looking for addresses that need to be changed! A hideous bodge! How could this fundamental sloppiness and inefficiency find its way into 90% of all computers?

Does this surprise you?

It does surprise me, yes.  Why?  Because it's complete nonsense.  What is your source or how do you arrive at such conclusions?

---

### Post by night_fox on 2008-12-24
Yes, sorry I just posted something really stupid. Pretty much all code is position dependant but it gets loaded at any address and the MMU fakes it's position. I don't properly understand the rest and I don't really know what I'm talking about. I thought my source was wikipedia.

---

### Post by cammin on 2008-12-25
[http://en.wikipedia.org/wiki/Conventional_memory](http://en.wikipedia.org/wiki/Conventional_memory)

---

