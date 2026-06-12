---
title: "A few questions about Gazelle Performance laptop"
date: 2007-02-22
forum: System76 Support
---

### Post by klato on 2007-02-22
I'm thinking to get a new laptop (since my old one died), and the Gazelle Performance looks pretty attractive, but I have a few questions, so here goes!

1) I currently have a 120gb hard drive that I have already installed Ubuntu Edgy Eft on (3 partitions, /, /home, and swap).

Does the Gazelle support hard drives this large?  If so, I suppose I would have to reinstall the OS on my old hard drive in order to fully detect all the new Gazelle hardware...would I have any issues in terms of getting all of the hardware to work with a fresh install, or would I require any specific software from System76?

2) Also, I notice that it comes with a Celeron M processor and 512mb of RAM.  My old system had 512mb as well, and some old (bought in 2000) Intel processor.

Would I really notice any difference in speed if I upgraded to a Core 2 Duo processor and 1gb of RAM?  All I really use the laptop for is watching videos, doing some minimal office stuff, web browsing, chatting, and listening to music (pretty much all at the same time).

3) I'd also like to be able to run Compiz or Beryl smoothly.  I've only used an ATI card before (Radeon Mobility 7500 32mb)...but I really want to avoid ATI at this point (at least anything that uses the opensource drivers).  Is the nVidia card in the Gazelle Performance decent enough for this, or is it overkill?  Would the Intel graphics option in the Gazelle Value suffice for this? (do the opensource drivers provide full speed support for this video option?)

Thanks for any responses to any of the above...I realize it's a lot of questions!

Cheers!

---

### Post by AusIV4 on 2007-02-22
I have a gazelle value, so think I can answer your last question.

I have two laptops, each running Beryl. One has an ATI card with the Open Source drivers, my gazelle has the intel GMA card. Beryl runs better on my GMA than it does on my ATI, I assume because the driver support is better. It runs quite smoothly, the CPU getting up to about 15% during heavy animations, then quickly falls back to less than 0.1%. If all you're doing is beryl and a few videos, the nvidia card would definitely be overkill.

---

### Post by klato on 2007-02-22
Thanks for the reply.  Do you notice any slowdown or choppiness with Beryl on the Intel card?

Also, I can't remember where I read this, but I read that the lid does not fold out all the way...is that true?

One more thing, is it annoying to have the headphone jack in the front of the laptop? I'd imagine it would be...I'd be afraid of breaking off the connection!

---

### Post by AusIV4 on 2007-02-22
Beryl runs great on this graphics card. My only basis for comparison is the ATI with OS drivers I have in my other laptop, but the GMA is a significant imrpovement on the ATI, and I really can't imagine beryl running much more smoothly. You might be able to get XGL instead of AIGLX on Nvidia, which would give you some advanced special effects like water rippling, but in my experience XGL uses substantially more system resources and I'd rather drop a couple of the useless but flashy effects and use AIGLX.

My monitor rotates a little more than 180 degrees. I'd heard the same thing, but I think it must have been an older model (or perhaps the Performance is different because of the webcam, though I wouldn't think so).

As far as having the headphone jack on the front, I've only used it to make sure it works. It's positioned a little left of the middle of the laptop, about where the F and G keys on the keyboard are. I think headphones would go nicely between your hands, but if you wanted to plug in speakers it could get in the way. I'd rather have it on the side, but as I said last time, this is just my portable computer, not my primary one.

---

### Post by klato on 2007-02-22
Thanks for the replies AusIV4.

I've heard that nVidia now works with AIGLX...is that true?  If that's the case, would the nVidia route be a better option (not to mention that nVidia releases their own video drivers?)

Thanks again.

---

### Post by crichell on 2007-02-22
> 
I've heard that nVidia now works with AIGLX...is that true? If that's the case, would the nVidia route be a better option (not to mention that nVidia releases their own video drivers?)

Yes - nVidia works well with AIGLX/Beryl.  We've tested all of the machines using this How To:

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)

> would I have any issues in terms of getting all of the hardware to work with a fresh install, or would I require any specific software from System76?

You won't have any trouble with a fresh install.  Our restore process uses the standard Ubuntu disk and our system76 driver that's available for download.  Directions are located here:

[http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)

> 
Would I really notice any difference in speed if I upgraded to a Core 2 Duo processor and 1gb of RAM? All I really use the laptop for is watching videos, doing some minimal office stuff, web browsing, chatting, and listening to music (pretty much all at the same time).

I think the Celeron is a nice processor.  It's fast enough for those kind of task.  However, faster processors do make a system snappier.  I always suggest that if you're buying on a budget skimp on the memory and bump up the processor.  You can always add another stick of memory but exchanging the processor is expensive (you can't utilize the processor you purchased whereas you can utilize the first stick of memory you purchased.)

---

### Post by klato on 2007-02-23
Carl,

Thanks for the response.  What about differences in the Core 2 Duo processors?  For example, would I notice much of a difference between a 1.66 and 1.83 processor speed?

Thanks!

---

### Post by frogotronic on 2007-02-25
Hello,

I too am also think about this machine.  My main concern is this:  Does suspend (Suspend-to-RAM) and hibernate (Suspend-to-DISK) work with the appropriate nVIDIA binary drivers?  As this would be my main production machine, I would need Twinview (or alternative output support) for Impress/Powerpoint presentations, as well as OpenGL support for molecular modelling.

Thanks in advance,
 - CH

---

### Post by crichell on 2007-02-25
> What about differences in the Core 2 Duo processors? For example, would I notice much of a difference between a 1.66 and 1.83 processor speed?

Naturally 1.83 will be faster than 1.66 - Coming from an older machine either of the processors will seem like a big jump.

> Does suspend (Suspend-to-RAM) and hibernate (Suspend-to-DISK) work with the appropriate nVIDIA binary drivers?

Yes - with the nVidia drivers provided by Ubuntu's repository.  The driver is installed and configured by default as is Suspend / Hibernate support.

---

### Post by frogotronic on 2007-02-25
> **crichell said:**
> Naturally 1.83 will be faster than 1.66 - Coming from an older machine either of the processors will seem like a big jump.



Yes - with the nVidia drivers provided by Ubuntu's repository.  The driver is installed and configured by default as is Suspend / Hibernate support.

Cool.  That's a make it or break it deal for me.

- CH

:popcorn:

---

### Post by maniacmusician on 2007-02-25
Keep in mind that more critical than the clock speed could be the L2 Cache. Some models have 2MB, others have 4MB; it's a sizeable difference if you're really searching for performance.

You certainly would be satisfied with the 2MB cache, but if you really want to put down your money and juice the system for all its worth, you may also consider getting a processor with a  4MB cache.

---

