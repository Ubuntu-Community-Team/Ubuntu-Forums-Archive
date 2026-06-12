---
title: "General Linux Question:  Legacy Software."
date: 2010-06-14
forum: The Cafe
---

### Post by McRat on 2010-06-14
Let's say you have a Linux app that was written 15 years ago.

Would it still run today with new release of the kernel?

---

### Post by Bachstelze on 2010-06-14
Probably not. Not only because of newer kernels, but also newer libraries (especially glibc).

---

### Post by madjr on 2010-06-14
> **McRat said:**
> Let's say you have a Linux app that was written 15 years ago.

Would it still run today with new release of the kernel?

hmm you want to run 15 year old software?

---

### Post by McRat on 2010-06-14
> **madjr said:**
> hmm you want to run 15 year old software?

No, I was just curious.  I searched and could not find an answer.

The only real relevance it has to people who aren't looking towards running legacy software, would be to people who want to know what the usable lifespan of Linux software would be.

---

### Post by mickie.kext on 2010-06-14
> **McRat said:**
> Let's say you have a Linux app that was written 15 years ago.


If you have source code, it can usually be compiled without changing the source code given that dependencies are correctly listed. If you only have a binary, then no. You might want to install RHEL 3 in that case, it is still supported and drivers for new hardware are back-ported. You could probably run 10 year old binary on it ( I tried 7 year old, but not 10) but probably not 10 year. 

Linux distros have stable source-level API, but ABI is unstable by design, and for a good reason. In-kernel interfaces is also unstable with a good reason. 

If you have source code, stable source-level API is all you need.

> Would it still run today with new release of the kernel?
It does not have loot to do with kernel. It is usualy because of newer libraries. Linux kernel does not interact with user sprace apps a lot.

---

### Post by sydbat on 2010-06-14
If you have said software in your possession, why not try and run it, then let us know how it went.

However, I imagine that 15 year old software for Linux is the same as 15 year old software for any OS. It likely won't run, but if it does, what's the point.

---

### Post by koenn on 2010-06-14
> **McRat said:**
> 

The only real relevance it has to people who aren't looking towards running legacy software, would be to people who want to know what the usable lifespan of Linux software would be.

In addition to what mickie.kext said about source-level compatibility, there's also the (less important) side effect that most free software is distributed at no cost, so there is usually no reason not to upgrade, no reason to stick with old software and fall behind. 

Most "legacy support" issues evolve around proprietary software that people choose not to upgrade to avoid purchasing and licensing costs, or because the vendor EOL'd the product or simple went out of business, leaving the users without an upgrade path. Such scenarios are far less common in Free Software. 

Granted, not all software on Linux is Free Software, but that's a choice you make when you decide what software you're going to use.

---

### Post by McRat on 2010-06-14
> **sydbat said:**
> If you have said software in your possession, why not try and run it, then let us know how it went.

However, I imagine that 15 year old software for Linux is the same as 15 year old software for any OS. It likely won't run, but if it does, what's the point.

Some of the software I run is more than 20 years old.  And it still does it's job just fine. But it's DOS, and I have the source because I wrote it.  No, it won't run on Win95+ machines.  It needs full control over the CPU, no multi-tasking system will run it.  So it will always be run on a DOS/Win3.11 machine.

But I wasn't running Linux two months ago, so I was just curious about the subject.  No malice, no black helicopters, no informercial or hatemail intended.

This is hard to believe today, but a tool that does it's job well is useful indefinitely.

---

### Post by madjr on 2010-06-14
> **McRat said:**
> Some of the software I run is more than 20 years old.  And it still does it's job just fine. But it's DOS, and I have the source because I wrote it.  No, it won't run on Win95+ machines.  It needs full control over the CPU, no multi-tasking system will run it.  So it will always be run on a DOS/Win3.11 machine.

But I wasn't running Linux two months ago, so I was just curious about the subject.  No malice, no black helicopters, no informercial or hatemail intended.

This is hard to believe today, but a tool that does it's job well is useful indefinitely.

oh memories :)

would you like to port it over to new era or is it too complex and not worth the time?

---

### Post by squilookle on 2010-06-14
Another reason to run old software might be an old game, or something like that. I was playing Dizzy not so long ago, and thats just over 20 years old, but that was using an emulator. 

Speaking of which, thats one way to run old software if the OS won't run it on its own.

---

### Post by McRat on 2010-06-14
> **madjr said:**
> oh memories :)

would you like to port it over to new era or is it too complex and not worth the time?

It would be a good idea, but it's fairly far down on my ListOfThingsToDo.  

The most important program intercepts a special PRN cable signal, converts to RS-232, then turns the XYZ info into multiple CAD formats.  The actual machine control (not the DOS app), is a Z80, S100 bus, running CP/M, with 8" floppy drives.

I can't read the 8" discs, so I just tell the controller to print, and intercept the output.

---

