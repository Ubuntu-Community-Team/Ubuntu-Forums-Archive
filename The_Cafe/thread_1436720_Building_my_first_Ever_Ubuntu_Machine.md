---
title: "Building my first Ever Ubuntu Machine"
date: 2010-03-23
forum: The Cafe
---

### Post by Mike1056 on 2010-03-23
I have played with Ubuntu on my current desktop which is a 3.1 Dual Core with 4 Gigs of RAM. I decided that I liked it enough to build a dedicated 64-bit Ubuntu Machine. So, I just ordered the parts yesterday. I'm looking at a 2.4 Quad Core, 8 Gigs of RAM, 1TB HDD, and a 1 Gig Video Card. I'm looking forward to the project!! Wish me luck!

---

### Post by Sef on 2010-03-23
Moved to community cafe.

---

### Post by Psumi on 2010-03-23
Should've gotten a 3.x quad core. A lot of applications aren't built to use 3 or more cores, including 64-bit apps. This includes PCSX2, the PS2 Emulator.

---

### Post by sxmaxchine on 2010-03-23
> **Psumi said:**
> Should've gotten a 3.x quad core. A lot of applications aren't built to use 3 or more cores, including 64-bit apps. This includes PCSX2, the PS2 Emulator.

that is true but quad cores there will be much more programs will be able to use 4 0r more cores in the near future

---

### Post by Psumi on 2010-03-23
> **sxmaxchine said:**
> ...near future

Try 2+ years... and even then...

Processors are evolving too fast with logical cores (The i7 has 7/8 cores: 4 physical, 3/4 logical.)

The PS3 has 6/7 physical cores (5/6 usable, as one is used for back-up.)

With processors evolving so fast, devs are trying to get things done all at once (for most apps.)

---

### Post by Mike1056 on 2010-03-23
I can always upgrade down the road.  I already put quite a bit into it for this week, though!  The barebones kit I got from Tiger Direct cam with the 2.4 Ghz Quad Core.  I guess I didn't realize there was that much of a difference between the two.  So there are a lot of programs that just will not run on it?

---

### Post by Psumi on 2010-03-23
> **Mike1056 said:**
> So there are a lot of programs that just will not run on it?

That's not how it works. Instead of "Not running." The programs can only see 2 cores out of the 4 you have. So instead of four cores having programs distributing their processes over the four cores... they only use the first two, and max them out. if a program cannot find space enough in the first two cores, and can only see the first two cores, the expected result is that the program will be super slow, or the program will not run.

Ubuntu and the processor are NOT crystal balls, they can't tell an application to use something it thinks doesn't exist.

---

### Post by Mike1056 on 2010-03-23
So it only sees it as a 2.4 Dual Core with 8 GB RAM, then?  Either way, how slow would that really be?

---

### Post by pbpersson on 2010-03-23
The Linux kernel is undergoing constant refinements and improvements.  Would it not be the first (and most important) component in the OS to recognize the additional cores and then send applications and threads over to the additional cores?

---

### Post by Mike1056 on 2010-03-23
That's what I'm wondering.  Quad Core's aren't old, but they're also not the newest thing on the market, either.

---

### Post by Psumi on 2010-03-23
> **pbpersson said:**
> Would it not be the first (and most important) component in the OS to recognize the additional cores and then send applications and threads over to the additional cores?

Would you like it if I told you to step off a cliff because there was a bridge there that you couldn't see?

---

### Post by pbpersson on 2010-03-23
> **Psumi said:**
> Would you like it if I told you to step off a cliff because there was a bridge there that you couldn't see?

A better analogy would be landing in an unknown city, getting into a taxi, and telling the driver the address where you want to travel.  They know the city and the streets and know the fastest way there.  You don't need to know all the details, you just sit in the back seat and relax.

In much the same way, the kernel runs an application thread on a core and in a memory location.  The thread does not know where it is running nor does it care.

---

### Post by Psumi on 2010-03-23
> **pbpersson said:**
> A better analogy would be landing in an unknown city, getting into a taxi, and telling the driver the address where you want to travel.  They know the city and the streets and know the fastest way there.  You don't need to know all the details, you just sit in the back seat and relax.

In much the same way, the kernel runs an application thread on a core and in a memory location.  The thread does not know where it is running nor does it care.

Whatever makes you sleep at night.

---

### Post by Mike1056 on 2010-03-23
Well, the parts are supposed to be here today, so I'm sure I'll have it up and running before too long...I'll post how well this rig handles a 64-bit platform.

---

### Post by KegHead on 2010-03-23
Hi!

I built an atom 330 based desktop w/2gbs ram and 160 gb hd.

It's run flawlessly w/9.10, I hope to upgrade to 10.04 soon.

I expect great results.

KegHead

---

### Post by cguy on 2010-03-23
I want a dual core Atom with 4GB of ram. Is that too much to ask as a donation from my ubuntuforums colleagues? :D

---

### Post by Mike1056 on 2010-03-23
I thought this thing was supposed to be slow, but it's speed is just absolutely incredible!  It was a pain to build (never go with a Gigabyte case), and I had to swap the DVD drive out with my Windows machine, but it's all done now!

---

