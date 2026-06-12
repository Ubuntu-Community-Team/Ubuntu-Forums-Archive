---
title: "Is the GNU HURD alive?"
date: 2009-07-27
forum: The Cafe
---

### Post by praveesh on 2009-07-27
Is the GNU HURD ALIVE? Do the GNU project has any plan to release hurd? Is there exists any project to develop hurd , now? DO ANY ONE KNOW ?

---

### Post by Skripka on 2009-07-27
It has been in "development" for 25 years now...and STILL no sign of even an Alpha level testing release.  Worse, the tech world moves on in 6 months cycles, and HURD is decades behind.

---

### Post by raronson on 2009-07-27
Apparently, it's still in work with current updates (but that's been the case for the last 10+ years).

[http://www.gnu.org/software/hurd/index.html](http://www.gnu.org/software/hurd/index.html)

---

### Post by Simian Man on 2009-07-27
Hurd is an epic failure.  If the GNU people weren't so darn stubborn, it would have been abandoned decades ago like it should have been.

---

### Post by raronson on 2009-07-27
It's just a speculation, but I suspect that on some level they'd like a divorce from Linux.  It makes sense, given their position on not being beholden to anyone.  I'm not sure of the point anymore though.  I mean if they're using the Mach Kernel as a base, it's not exactly a "from scratch" replacement for that last elusive UNIX component.  Although there are some pretty slick ideas in HURD that deal with distributed computing (last I recall reading).  Then again, NASA's Beowulf already exists.

---

### Post by koenn on 2009-07-27
> **Skripka said:**
> It has been in "development" for 25 years now...and STILL no sign of even an Alpha level testing release.
This call foçr testing sems to contradict that
[http://www.debian.org/ports/hurd/](http://www.debian.org/ports/hurd/)


> **Skripka said:**
> , the tech world moves on in 6 months cycles, and HURD is decades behind.
hm, what 6 month cycle are you referring to ?

---

### Post by Skripka on 2009-07-27
> **koenn said:**
> This call foçr testing sems to contradict that
[http://www.debian.org/ports/hurd/](http://www.debian.org/ports/hurd/)



hm, what 6 month cycle are you referring to ?
I still don't see the announcement of a Hurd Alpha anywhere.

Every 6-8 or 10 months we get new CPUs and GPUs etc from manufacturers, this spring it was 45nm Nehalem CPUs from Intel and LGA1366...this fall it will be 35nm CPUs, this winter USB3 comes out and so on.  FOSS can't even keep up with the pace of new drivers and support for GPU cards, last I knew radeonhd etc barely had support 3d for obsolete ATi cards.

---

### Post by MikeTheC on 2009-07-27
The last I heard from Richard Stallman himself, he wasn't sure if it was ever going to go anywhere, either.

My guess is that once the Real-Time Kernel project gets finished and starts being distributed, that will be the final nail in HURD's coffin.

And, frankly, not a decade too late, if you ask me.

---

### Post by raronson on 2009-07-27
From [http://www.gnu.org/software/hurd/hurd/status.html](http://www.gnu.org/software/hurd/hurd/status.html) 

> 
The Hurd, together with the GNU Mach microkernel, the GNU C Library and the other GNU and non-GNU programs in the GNU system, provide a rather complete and usable operating system today.  It may not be ready for production use, as there are still many bugs and missing features. However, it should be a good base for further development and non-critical application usage.


And...

Debian's GNU/Hurd distribution is a fork from GNU/Hurd, and not necessarily associated with the main project, but they do live CD's and whatnot:

> 
The Debian GNU/Hurd [distribution]("http://www.gnu.org/software/hurd/hurd/running/debian.html") offers *LiveCDs and QEMU images* to test-drive the Hurd in a real life system...


It's been years since I've had a look at their docs.

---

### Post by RiceMonster on 2009-07-27
> **MikeTheC said:**
> The last I heard from Richard Stallman himself, he wasn't sure if it was ever going to go anywhere, either.

My guess is that once the Real-Time Kernel project gets finished and starts being distributed, that will be the final nail in HURD's coffin.

And, frankly, not a decade too late, if you ask me.

What is the Real-Time Kernel project?

---

### Post by MikeTheC on 2009-07-27
> **RiceMonster said:**
> What is the Real-Time Kernel project?

[Take a look here.](http://rt.wiki.kernel.org/index.php/Frequently_Asked_Questions)

The purpose of RT is to guarantee predictable availability of resources to a given process. There are already plenty of real-time OSs out there, it's just that they're all vertical-market appliance OSs for things such as medical monitoring devices, etc.

Now, just imagine if you will, let's suppose we get the RTK up and running and totally solid in Linux. One of the biggest and highest-profile uses of that would be potentially by, for instance, NASA, on board spacecraft (both manned and unmanned). They could now safely use Linux because there would be QoS guarantees for processes to have access to external resources, such as navigation, propulsion, environmental control, and on and on. If that happened, I think the argument over which OS is technologically "best" would be over. Who wouldn't want (apart from tinkerers, no offense) a human-rated and mission critical-rated OS as *their* computer's OS? I sure would, I can tell you that.

Imagine having an OS that's got all the other things you'd expect out of a modern OS -- secure, multi-user, multi-threaded, etc. -- and more responsive and efficient and considered dependable enough to bet human life on. If such an OS was F/OSS and also "free as in beer" then you'd have tons of people lined up to get it. And, you'd have tons of businesses, too. Which kind of brings us back to the point of this thread, which is that despite whatever technical advantages HURD may have, its "perpetual development" would have turned into a millstone around its neck.

(As a separate note, can you imagine how badly Microsoft would be s****ing themselves trying to compete? How would they argue that? "Our non-human-rated OS is better than your human-rated OS is" ? Now *that* would be a funny commercial to behold, don't you think?)

---

### Post by DeadSuperHero on 2009-07-27
As far as I can tell, HURD is still well into production. There's been some experimental forks over the years, (my current favorite is Neal Walfield's Viengoos microkernel)

I hope to some day see it completed, even if I'm an old man by the time the kernel gets finished.

---

### Post by Skripka on 2009-07-27
> **Mr. Psychopath said:**
> As far as I can tell, HURD is still well into production. There's been some experimental forks over the years, (my current favorite is Neal Walfield's Viengoos microkernel)

I hope to some day see it completed, even if I'm an old man by the time the kernel gets finished.

Then you could run LongHorn in a VM inside an E17 Stable/Hurd environment! :)

---

### Post by DeadSuperHero on 2009-07-27
> **Skripka said:**
> Then you could run LongHorn in a VM inside an E17 Stable/Hurd environment! :)

Although you may laugh, I believe that the design of Viengoos (on paper, at least) is a far superior design to the average monolithic Linux kernel. 

Just like at what AmigaOS was. A microkernel-based operating system, the only reason they failed was because Commadore was stupid about marketing it. AmigaOS was fast, beautiful, and capable of running extremely efficiently on even the smallest amounts of memory. (One such example: the average Amiga processor is about 750 Mhz or so, and in many cases I've seen it outperform both Mac OS and Linux on "Superior" hardware.)

Even if it may not be "the future of all technology", it would be nice to have a complete system based upon the principles of good microkernel design, especially in the FOSS world. The closest we've come is Viengoos (still early in progress), AROS (limited driver support), and six or seven "research" kernels that never go anywhere. (L4, Coyotos,)

Then, there's Mach, which most people will say is a flawed implementation...why it got included into Darwin under XNU, I'll never understand. The way Apple implemented it has something to do with only focusing on userspace, instead of the full features of microkernel design.

---

### Post by koenn on 2009-07-27
> **Skripka said:**
> 
Every 6-8 or 10 months we get new CPUs and GPUs etc from manufacturers, this spring it was 45nm Nehalem CPUs from Intel and LGA1366...this fall it will be 35nm CPUs, this winter USB3 comes out and so on.  FOSS can't even keep up with the pace of new drivers and support for GPU cards, last I knew radeonhd etc barely had support 3d for obsolete ATi cards.
Sounds pretty irrelevant to me, I don't see *any* os  (other than maybe linux) releasing new kernels every 6 months. It's still the same CPU architectures, with occasional new extensions, and backward compatibility down to the 1990s. 
As lagging behind in support for GPU cards and other driver issues, that's a matter of access to specs or the time it takes for reverse engineering - it's not about not being able to write that software.

---

### Post by doas777 on 2009-07-27
the project doomed itself to failure, as soon as they named it.

---

### Post by jomiolto on 2009-07-27
> **Mr. Psychopath said:**
> Just like at what AmigaOS was. A microkernel-based operating system, the only reason they failed was because Commadore was stupid about marketing it. AmigaOS was fast, beautiful, and capable of running extremely efficiently on even the smallest amounts of memory. (One such example: the average Amiga processor is about 750 Mhz or so, and in many cases I've seen it outperform both Mac OS and Linux on "Superior" hardware.)

The Amiga I had as a kid had a 7MHz processor and, as far as I know, the fastest Amigas had a 75MHz processor. Makes it even more amazing :)

(Unless you were talking about AmigaOS 4, which I've never seen in action.)

> **Mr. Psychopath said:**
> Even if it may not be "the future of all technology", it would be nice to have a complete system based upon the principles of good microkernel design, especially in the FOSS world. The closest we've come is Viengoos (still early in progress), AROS (limited driver support), and six or seven "research" kernels that never go anywhere. (L4, Coyotos,)

It's nice to see that there's someone who agrees with me on this :)

Most people (outside of Andrew Tannenbaum :p) seem to think that microkernels are a waste of time, but I've always wanted to see a modern implementation of the idea. It worked very well for AmigaOS and I don't see why it wouldn't work for more modern hardware.

I've always thought that there is certain elegance in the microkernel design (drivers *should* be separate from each other), but I've got no idea how much more difficult it is to implement when compared to monolithic design. If I got caught in a time warp and had a few extra years of free time, perhaps I'd try implementing a microkernel myself... :D

---

### Post by DeadSuperHero on 2009-07-27
> **jomiolto said:**
> . If I got caught in a time warp and had a few extra years of free time, perhaps I'd try implementing a microkernel myself... :D

Half of the time, my life FEELS like a time warp. So you never know...

---

### Post by Sporkman on 2009-07-27
> **praveesh said:**
> Is the GNU HURD ALIVE? Do the GNU project has any plan to release hurd? Is there exists any project to develop hurd , now? DO ANY ONE KNOW ?

I HURD it's alive...

---

### Post by Skripka on 2009-07-27
> **Sporkman said:**
> I HURD it's alive...

And THAT was when I SHOT HIM, Your Honor.

---

### Post by Sporkman on 2009-07-27
BTW, real men don't needs OSs - real men program for *bare metal*... :guitar:

---

### Post by MikeTheC on 2009-07-27
> **Skripka said:**
> And THAT was when I SHOT HIM, Your Honor.

roflmao!!!!!!!

---

### Post by Slug71 on 2009-07-27
Pieces of HURD will be in Ubuntu Karmic 9.10 ;-)

[http://www.techradar.com/news/software/operating-systems/koala-will-be-a-definitive-shift-for-ubuntu-linux-613835](http://www.techradar.com/news/software/operating-systems/koala-will-be-a-definitive-shift-for-ubuntu-linux-613835)

---

### Post by Chilli Bob on 2009-07-28
Only a few months ago there was an article on Slashdot or somewhere about the latest Hurd live CD being released.  I downloaded it and could boot to the command line, but apart from running emacs, I couldn't find a use for it.  So, in theory it is still alive, but I think it's gasping for breath.

---

### Post by lykwydchykyn on 2009-07-28
> **Chilli Bob said:**
>  I downloaded it and could boot to the command line, but apart from running emacs, I couldn't find a use for it.

And what are these other uses for an OS that you seem to be implying the existence of?  Saint Ignucious would like to know...

---

### Post by Grant A. on 2009-07-28
> **Mr. Psychopath said:**
> Although you may laugh, I believe that the design of Viengoos (on paper, at least) is a far superior design to the average monolithic Linux kernel.


I'm not quite sure about Viengoos, however, I do too think that the monolithic Linux kernel is outdated. Linux is a dinosaur in its design, due to the fact that it is a clone of UNIX. Although, Linux is my first pick for an operating system. Perhaps the Real-Time Kernel will make Linux less of a dinosaur?

> 
Even if it may not be "the future of all technology", it would be nice to have a complete system based upon the principles of good microkernel design, especially in the FOSS world.

Sorry if this isn't what you're looking for, but MINIX is a UNIX-like microkernel operating system. It's also, as of MINIX 3, under the GNU GPL. It's really primarily used for research, but I've heard of some people installing KDE and such on it. It's actually what Linus himself used when he just started on the Linux kernel.

---

### Post by ssam on 2009-07-28
why rush?

---

### Post by 3rdalbum on 2009-07-28
Good things come to those who wait.

---

### Post by Sporkman on 2009-07-28
> **ssam said:**
> why rush?

Well, for one thing I can remember writing programs back in the 80's while listening to Rush. Genesis, too.

---

### Post by howlingmadhowie on 2009-07-28
the way i see it, after linux 1.0 was launched there was no need to continue developing GNU/Hurd, so very little work has been done on it. I imagine most of the Hurd programmers just started doing other things. Some of them doubtless contribute to the linux kernel.

---

### Post by raronson on 2009-07-29
> **MikeTheC said:**
> Now *that* would be a funny commercial to behold, don't you think?)

I smell a future rendition of a "Get the Facts!" campaign.

---

### Post by cronopios on 2009-09-01
> **Grant A. said:**
> Sorry if this isn't what you're looking for, but MINIX is a UNIX-like microkernel operating system. It's also, as of MINIX 3, under the GNU GPL.
BSD, actually

> **Grant A. said:**
> It's really primarily used for research, but I've heard of some people installing KDE and such on it.
Where did you hear about KDE on Minix? Please provide some URL, I'd like to take a look.

> **Grant A. said:**
> It's actually what Linus himself used when he just started on the Linux kernel.
Not really. Linus used MINIX 1, and according to Tanenbaum, MINIX 1 and MINIX 3 are related in the same way as Windows 3.1 and Windows XP are: same first name.

---

### Post by matthew.ball on 2009-09-01
Heh, on the topic... Let me just drool over this book:

[http://www.amazon.com/Operating-Systems-Design-Implementation-3rd/dp/0131429388/ref=dp_ob_title_bk/189-0643032-7353607](http://www.amazon.com/Operating-Systems-Design-Implementation-3rd/dp/0131429388/ref=dp_ob_title_bk/189-0643032-7353607)

Would love a copy! Oh well :(

---

