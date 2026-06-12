---
title: "Give me one reason why GNU is still developing Hurd"
date: 2012-05-01
forum: The Cafe
---

### Post by zombifier25 on 2012-05-01
...and one of the world's biggest mysteries is solved. (others include aliens, ghosts, JB fans,...)

---

### Post by szymon_g on 2012-05-01
because they have a plenty of spare time- so they can do whatever they want with it.

---

### Post by forrestcupp on 2012-05-01
> **szymon_g said:**
> because they have a plenty of spare time- so they can do whatever they want with it.

You beat me to it. :)

The same reason other people build model cars and airplanes. They like doing it.

---

### Post by Dry Lips on 2012-05-01
I didn't even know what Hurd was... I had to Google it. So, it's a replacement for Unix?

Wow! That's a really good idea... No wait, we've already got BSD and Linux, don't we?

---

### Post by HappinessNow on 2012-05-01
> **Dry Lips said:**
> I didn't even know what Hurd was... I had to Google it. So, it's a replacement for Unix?

Wow! That's a really good idea... No wait, we've already got BSD and Linux, don't we?

...and Haiku?

---

### Post by Seq on 2012-05-01
With that answered, maybe we can try and figure out why emacs is still being developed when vi is so awesome. We don't need both Chrome and Firefox, either. And why are there so many obscure window managers...

---

### Post by mips on 2012-05-01
> **Dry Lips said:**
> So, it's a replacement for Unix?


More like Linux :biggrin:

Reason I say this is there was a boat load of GNU userland stuff available but no kernel for it, Linux filled that role hence the term GNU/Linux. GNU & Linux are not the same thing, GNU was suppose to be a complete OS with it's own kernel but seeing they did not have one they adopted Linux which is not part of GNU.

[http://en.wikipedia.org/wiki/GNU/Linux_naming_controversy](http://en.wikipedia.org/wiki/GNU/Linux_naming_controversy)

---

### Post by Dry Lips on 2012-05-01
Is Hurd so mature that it is possible to use it as a more or less functional system?

---

### Post by Paqman on 2012-05-01
Sheer bloody-minded refusal to face reality?

---

### Post by dpny on 2012-05-01
> **paqman said:**
> sheer bloody-minded refusal to face reality?

+5

---

### Post by donkyhotay on 2012-05-01
> **szymon_g said:**
> because they have a plenty of spare time- so they can do whatever they want with it.

+1

---

### Post by KiwiNZ on 2012-05-01
> **Paqman said:**
> Sheer bloody-minded refusal to face reality?

Hmmmm, I was under the impression the OSS/GNU movement was about freedom

---

### Post by Dry Lips on 2012-05-01
Have anyone here actually tried Hurd?

---

### Post by Paqman on 2012-05-01
> **KiwiNZ said:**
> Hmmmm, I was under the impression the OSS/GNU movement was about freedom

The freedom to choose doesn't imply that all choices are equally valid. The GNU system already has an excellent, mature, widely supported kernel. Wasting developer time on building another might be a fun technical exercise, but it's not going to achieve anything useful.

We're all free to punch ourselves in the face any time we like. Doesn't mean anyone will applaud you for doing so.

---

### Post by KiwiNZ on 2012-05-01
> **Paqman said:**
> The freedom to choose doesn't imply that all choices are equally valid. The GNU system already has an excellent, mature, widely supported kernel. Wasting developer time on building another might be a fun technical exercise, but it's not going to achieve anything useful.

We're all free to punch ourselves in the face any time we like. Doesn't mean anyone will applaud you for doing so.

Freedom is allowing those developers to select what project they work on.

Your logic could easily be applied to Linux desktop, after all it has only achieved +/- 1% and could be deemed as achieving nothing useful.

---

### Post by lykwydchykyn on 2012-05-01
Is there currently a FOSS kernel out there with a microkernel design?  HURD is a microkernel, with a unique design.  It's possible that someday the monolithic kernel approach will fail to scale (or at least be inappropriate for a given application), and won't it be nice to have a readily available microkernel to drop in and go?

BTW, last time I heard, Debian Wheezy is supposed to have a HURD flavor by the time it's released.

---

### Post by BeRoot ReBoot on 2012-05-01
Because why not? I'm still hoping to one day be able to use a fully GNU-based OS, preferably with the HURD kernel and Emacs as the userland.

---

### Post by forrestcupp on 2012-05-01
> **lykwydchykyn said:**
> Is there currently a FOSS kernel out there with a microkernel design?  HURD is a microkernel, with a unique design.  It's possible that someday the monolithic kernel approach will fail to scale (or at least be inappropriate for a given application), and won't it be nice to have a readily available microkernel to drop in and go?If there were a viable one, you would probably know about it.

> **lykwydchykyn said:**
> BTW, last time I heard, Debian Wheezy is supposed to have a HURD flavor by the time it's released.
Just because Debian is going to have a HURD version doesn't mean HURD is going to be any less crappy than it always has been. ;)

It's got a long way to go before it supports enough hardware to be viable.

---

### Post by Copper Bezel on 2012-05-01
Honestly, I'm surprised that there *isn't* *more* support for it, for the reason lykwydchykyn raised. Yes, kernels are hard, and it's more straightforwardly applicable to real life to do work on the Linux kernel than to work with another esoteric alternative. Yes, the hardware support is a very serious issue, because that's most of what a kernel does and most of the limitations that even GNU / Linux faces. But it's rather broadly accepted that the microkernel model is just *better* than the monolithic kernel strategy. To me, Haiku or *BSD offers less distinction from Linux than does Hurd, yet people do develop them. If each project were really seriously considering what the practical outcomes of its enterprise really might be, as the question assumes, then I'd think that people interested in providing another option that isn't Linux would *flock* to Hurd.

---

### Post by szymon_g on 2012-05-01
> **Dry Lips said:**
> I didn't even know what Hurd was... I had to Google it. So, it's a replacement for Unix?

no. Plan 9 was a replacement for Unix.

---

### Post by dpny on 2012-05-01
> **Copper Bezel said:**
> But it's rather broadly accepted that the microkernel model is just *better* than the monolithic kernel strategy.

Not unless they've solved the messaging latency inherent in microkernels.

---

### Post by BrokenKingpin on 2012-05-01
> **lykwydchykyn said:**
> Is there currently a FOSS kernel out there with a microkernel design?  HURD is a microkernel, with a unique design.  It's possible that someday the monolithic kernel approach will fail to scale (or at least be inappropriate for a given application), and won't it be nice to have a readily available microkernel to drop in and go?
This. They feel it is a better design than the current kernels... simple as that.

That being said I think Linux is doing a damn fine job and Hurd is a long way out from being usable on the desktop IMO.

---

### Post by Bandit on 2012-05-01
> **zombifier25 said:**
> ...and one of the world's biggest mysteries is solved. (others include aliens, ghosts, JB fans,...)

Becuase its hurd to build :D

---

### Post by wolfen69 on 2012-05-01
> **Dry Lips said:**
> Is Hurd so mature that it is possible to use it as a more or less functional system?

As far as I know, you would have to have a pretty generic type setup for it to be compatible. No thanks, it's too plain to have any practical use for me.

---

### Post by lykwydchykyn on 2012-05-02
I don't see anywhere -- even on the HURD project site -- that it's suggested that HURD is faster, more stable, or provides a better user experience than Linux or BSD.  It's just a different design for a kernel, one that some developers find interesting and want to hack on.  One that may one day prove to be more applicable to some technology stack than Linux.  Or may not.

Who knows where technology is heading?  5 years ago most of you would have wondered why anyone bothered to keep up an ARM port of Linux, since x86 was so obviously the only platform that mattered.  Now ARM is the next big thing, and other OS vendors are scrambling to support it.  Linux is already there. Not because someone had a crystal ball and knew that ARM would be the next big platform, but because some people (for whatever reasons) were "wasting their time" maintaining a port to some obscure platform.

Be happy that people are hacking on HURD, or plan 9, or AROS, haiku, Syllable, etc.  They aren't competing with Linux, they're enriching FOSS.

---

### Post by mbarland on 2012-05-02
> **lykwydchykyn said:**
> Is there currently a FOSS kernel out there with a microkernel design

Minix is about as close as I can see. Version 3 isn't really feature complete for desktop use, but it does present a useable desktop OS.

---

### Post by zombifier25 on 2012-05-02
> **Seq said:**
> With that answered, maybe we can try and figure out why emacs is still being developed when vi is so awesome. We don't need both Chrome and Firefox, either. And why are there so many obscure window managers...
Because emacs and vi are not the same. Chrome and Firefox are not the same. But Hurd wants to do what Linux has already done 10 years ago: A kernel for the GNU project, a free/libre operating system.

I support competition, but with GNU already adopting Linux AND still working on Hurd (for 20 freakin' years), it's the same as using cars and still working on horse chariots.
> **szymon_g said:**
> because they have a plenty of spare time- so they can do whatever they want with it.
Convinced:lolflag:

---

