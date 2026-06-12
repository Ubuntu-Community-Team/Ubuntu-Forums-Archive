---
title: "Two major gripes with s76 laptops: battery life &amp; power management"
date: 2011-03-04
forum: System76 Support
---

### Post by val67 on 2011-03-04
Hi,

I have followed this forum for a couple years now and it seems that the very short battery life and suspend & hibernate are 2 issues not completely solved by s76 (yet)

I would like to know if someone from s76 can comment on how they are planning to fix these issues because:

1. Suspend & Hibernate are advertised on their Web page

2. Short battery life are holding back many potential customers, as I have seen on the forum

Apart from this, kudos to s76 for bringing Linux experience to more and more people.

Thanks,

Val.

---

### Post by Ebonwumon on 2011-03-04
Which laptop doesn't have suspend working? I know it works flawlessly on my Lemur.

---

### Post by isantop on 2011-03-04
All of our current laptops suspend and hibernate perfectly. Desktops are different, but in general it works there too; we simply don't test it. 

We are also working on improving battery life, and I think we're hitting some good milestones. The new Serval, our high-end machine, gets about 2.5-3 hours of battery life per charge, which is a good deal longer than the SerP6, our previous model.

---

### Post by val67 on 2011-03-04
> **isantop said:**
> All of our current laptops suspend and hibernate perfectly. Desktops are different, but in general it works there too; we simply don't test it. 

Well, there have been countless threads with suspend/hibernate issues.

Most recent one is [http://ubuntuforums.org/showthread.php?t=1695023]("http://ubuntuforums.org/showthread.php?t=1695023")


We are also working on improving battery life, and I think we're hitting some good milestones. The new Serval, our high-end machine, gets about 2.5-3 hours of battery life per charge, which is a good deal longer than the SerP6, our previous model.

---

### Post by Slave2Metal on 2011-03-04
I would think the s76 with nvidia optimus cards would be a huge power hog.  How is optimus implemented on these?  Are they able to shut down the nvidia gpu?  

> **isantop said:**
> All of our current laptops suspend and hibernate perfectly. Desktops are different, but in general it works there too; we simply don't test it. 

We are also working on improving battery life, and I think we're hitting some good milestones. The new Serval, our high-end machine, gets about 2.5-3 hours of battery life per charge, which is a good deal longer than the SerP6, our previous model.

---

### Post by isantop on 2011-03-07
Most of the hibernate issues on this board are issues caused by software problems, and don't represent our systems as a whole. My PanP7 hibernates and suspends very well, both in Maverick and Natty. If a particular system dosen't suspend and resume out of the box in Ubuntu, we issue a fix in the System76 Driver. A good example of this are the Laptop systems with USB3. While the USB itself works great, the module required to make it work cause suspend to hang, so we fix this problem in the driver.

As for optimus, we don't currently have an implementation. Those are systems running full-time on the discreet graphics cards. I'd expect huge battery performance increases when we get integrated Sandy Bridge systems.

---

### Post by bill516 on 2011-03-08
Hibernate/suspend has worked perfectly well for me on this PanP4 over the last several Ubuntu iterations.  I have stayed with 10.4 and there are no problems.  Debian Squeeze also has no problems.  aptosid and Mepis both will suspend but I have not been able to make hibernate work with those systems.  Ubuntu/Debian are both Gnome environments, aptosid and Mepis are both KDE.  Might that have something to do with it?  I suspect so.

Battery life is the Achilles heel of these laptops, it would seem.  Two to three hours just is not going to get it done for people who must spend substantial lengths  time away from external power sources. It really is too bad that some greater improvement cannot be made.  At the very least hinge designs ought to allow substitution of a 9 cell battery for a 6 cell unit.  The greater battery bulk is a bit awkward but many people might appreciate it.

That said System 76 is the best vendor I have used in years - period.  So I'll live with the battery life.

---

### Post by isantop on 2011-03-08
Keep in mind that the 2-3 hour times are now from our professional line, which historically has had the worst battery life. I'd expect huge leaps when Sandy Bridge becomes available across the line.

---

### Post by bill516 on 2011-03-08
Great!  In my experience better battery life is going to make these machines very attractive indeed.  My PanP4 obviously has a few miles on it, but people who try it are impressed.  The only two negatives I have heard are the battery life and the miserable sound quality.  My point about the latter is that it is a laptop after all!

---

### Post by pafufta503 on 2011-03-08
> **bill516 said:**
> Great!  In my experience better battery life is going to make these machines very attractive indeed.  My PanP4 obviously has a few miles on it, but people who try it are impressed.  The only two negatives I have heard are the battery life and the miserable sound quality.  My point about the latter is that it is a laptop after all!haha.  earbud headphones and laptop speakers are essentially killing the quality of music.  odd to think that cassette tapes have better sound quality than many modern computers sound outputs.

battery life... well for 2.66ghz and 4g ram i don't expect much battery life out of my panp7.  if you want battery life then generally you will need a slower computer.  can anyone point to some links from dell or other mainstream manufacturers that surpasses sys76 laptops battery life with the same specs?

---

### Post by val67 on 2011-03-08
> **pafufta503 said:**
> haha.  earbud headphones and laptop speakers are essentially killing the quality of music.  odd to think that cassette tapes have better sound quality than many modern computers sound outputs.

battery life... well for 2.66ghz and 4g ram i don't expect much battery life out of my panp7.  if you want battery life then generally you will need a slower computer.  can anyone point to some links from dell or other mainstream manufacturers that surpasses sys76 laptops battery life with the same specs?

Well, check this for instance:

the XPS 15 from Dell with 

	Processor:
Intel® Core™ i3-380M (2.53GHz, 4 threads, 3M cache)

	Memory:
4GB Shared Dual Channel DDR3 Memory

	Hard Drive:
500GB 7200 RPM SATA Hard Drive

	Video Card:
NVIDIA® GeForce® GT 420M 1GB graphics with Optimus

	Battery:
56 WHr 6-cell Lithium Ion Primary Battery

is advertised at 5+ hours.

What would be the s76 equivalent?

Val.

---

### Post by Flyers2391 on 2011-03-09
> **val67 said:**
> Well, check this for instance:

the XPS 15 from Dell with 

	Processor:
Intel® Core™ i3-380M (2.53GHz, 4 threads, 3M cache)

	Memory:
4GB Shared Dual Channel DDR3 Memory

	Hard Drive:
500GB 7200 RPM SATA Hard Drive

	Video Card:
NVIDIA® GeForce® GT 420M 1GB graphics with Optimus

	Battery:
56 WHr 6-cell Lithium Ion Primary Battery

is advertised at 5+ hours.

What would be the s76 equivalent?

Val.

In defense of system 76, they advertise ACTUAL battery life when most manufacturers advertise potential ... when wifi is off, screen is all but off, etc

Also, there is nothing offered that compares to that system so it's not worth it.  The question is does Dell or others offer a top speed processor with battery life that exceeds others?  I'm not sure after you factor out W7 driver optimizations.  Though, I would like to see the lemur with 6+ hours

---

### Post by isantop on 2011-03-09
That has similar specs to a Lemur, but with a Pangolin screen size. 

The Lemur gets up to around four with the extended battery, and that's an actual use in Ubuntu. Dell quotes times in Windows, which will be longer, and as stated above, it's potential, not average.

If you threw in the Pangolin's big screen, then it may suck the battery down faster. So the Dell might get slightly longer, but it certainly not huge.

---

### Post by satsujinka on 2011-03-10
As an aside on battery life, you can generally gain about a half hour of battery life (on a 9 cell if I remember correctly) by choosing your programs carefully.
In the past I've found xfce and openbox to be much nicer to the battery than gnome or kde. Theoretically, I would guess that I'm saving more battery life currently since I'm using dwm, but the advantage is pretty small compared to openbox.

---

### Post by pafufta503 on 2011-03-10
i'm considering gentoo or freeBSD, i just need to confirm the sys76 drivers will work.  i'd like to see if a more minimalist OS configuration will gain battery life.  bear in mind that ubuntu is sort of bloated for the CPU.

i honestly doubt the Dell laptop equivalent would get double the battery life.  that would be a rating for the lowest screen brightness, wifi off, the HD isn't writing data, the CPU usage is idle with only OS running.  if you start browsing the internet, and have 3-4 programs open, you would see a large decrease in battery life.

---

### Post by satsujinka on 2011-03-11
> **pafufta503 said:**
> i'm considering gentoo or freeBSD, i just need to confirm the sys76 drivers will work.  i'd like to see if a more minimalist OS configuration will gain battery life.  bear in mind that ubuntu is sort of bloated for the CPU.

sys76 driver certainly won't work on freeBSD :tongue:
Generally speaking if you don't use your hardware it can't use energy, so anything that allows you to have a lighter cpu load and to have less hd i/o will save you energy.
Gentoo probably won't give you much of an energy advantage over a minimalistic ubuntu set up. This of course depends on how much the software you use benefits by being more optimized for your system.
FreeBSD also won't save you much in battery life. Even if their execution of power saving was better, since all *BSDs tend to have more correct code in them they tend to be a little more cpu intensive (since they don't accept hacks.)

---

