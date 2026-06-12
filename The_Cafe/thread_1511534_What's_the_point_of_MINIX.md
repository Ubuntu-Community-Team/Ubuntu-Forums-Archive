---
title: "What's the point of MINIX?"
date: 2010-06-16
forum: The Cafe
---

### Post by kaldor on 2010-06-16
I saw MINIX pop up on distrowatch today, and it made me wonder.. what's the point of MINIX now?

To my understanding it was an "education OS" to teach UNIX back in the days when there were no free UNIX-based OSes. Doesn't BSD, Linux, Solaris, etc do that?

---

### Post by KiraLexi on 2010-06-16
The point of Minix was never to teach people how to use Unix, it was to be a simple Unix-like operating system to teach OS design and development.

---

### Post by earthpigg on 2010-06-16
[http://en.wikipedia.org/wiki/MINIX](http://en.wikipedia.org/wiki/MINIX)

> Latest stable release 	3.1.7 / June 16, 2010; ***0 days ago***

maybe all the teachers told all the students to update?

---

### Post by markinf on 2010-06-16
IMHO it's not only great for teaching (since now my professor seems to use minix for operating system classes -- schedule/memory/etc) but also for embedded/real-time devices since it's microkernel design make it a system failure a lot harder since juts some very basic component can break the system. For example file servers are not part of the core kernel and can be revived on a failure.

Also it's micro in the size field, it's core part is < 4000 lines of code, which makes ideal for embedded device and real-time apps (since 4k of code can be easily inspected).

More data --> wiki

[IMG]http://upload.wikimedia.org/wikipedia/en/thumb/7/7d/The_MINIX_3_Microkernel_Architecture.png/800px-The_MINIX_3_Microkernel_Architecture.png[/IMG]

---

### Post by kaldor on 2010-06-16
yeah, but it's still in development.. does this mean it still fills a gap that no other OS can?

---

### Post by kaldor on 2010-06-16
> **markinf said:**
> IMHO it's not only great for teaching (since now my professor seems to use minix for operating system classes -- schedule/memory/etc) but also for embedded/real-time devices since it's microkernel design make it a system failure a lot harder since juts some very basic component can break the system. For example file servers are not part of the core kernel and can be revived on a failure.

Also it's micro in the size field, it's core part is < 4000 lines of code, which makes ideal for embedded device and real-time apps (since 4k of code can be easily inspected).

More data --> wiki

[IMG]http://upload.wikimedia.org/wikipedia/en/thumb/7/7d/The_MINIX_3_Microkernel_Architecture.png/800px-The_MINIX_3_Microkernel_Architecture.png[/IMG]


Ahh, this makes a lot of sense! Thanks :)

---

### Post by markinf on 2010-06-16
> **kaldor said:**
> yeah, but it's still in development.. does this mean it still fills a gap that no other OS can?

Probably on those niches that I've told you (embedded / real-time)

---

### Post by lisati on 2010-06-16
And if it wasn't for Minix we might not have Linux, and consequently Ubuntu.

---

### Post by kaldor on 2010-06-17
> **lisati said:**
> And if it wasn't for Minix we might not have Linux, and consequently Ubuntu.

Yes, but that was back when there *wasn't* an alternative ;p

I am trying out MINIX in Virtualbox.. it loads up and goes to a prompt "cd>" but that's all. What do I do from here?! :(

---

### Post by earthpigg on 2010-06-18
> **kaldor said:**
> Yes, but that was back when there *wasn't* an alternative ;p

I am trying out MINIX in Virtualbox.. it loads up and goes to a prompt "cd>" but that's all. What do I do from here?! :(

from here, you give [this]("http://wiki.minix3.org/en/UsersGuide/RunningMinixOnVirtualBox") a read :D

---

### Post by Starks on 2010-06-18
Do any distros with a viable desktop environment use the Minix kernel?

---

### Post by alexan on 2010-06-18
Minix uses the "holy grail" technology for kernels: it's called microkernel. It's the most complex technology actually know, so make a modern OS "usable" with it this technology is mostly unlikely.
Microsoft is still working on it; Apple is not know what's their point on it, Linus Trovalds is unlikely to willing "restart" ~20 years of work to "rethink" the kernel, l4linux (porting of trovald's kernel to l4 microkernel) seems inactive...

So, the only option for GNU/OpenSource community to (eventually) switch of the "holy grail" of kernels is Minix.


BTW: of course, you can find some microkernel OSses around there... but nothing able to perform the modern tasks of PC (change/configure/reinstall hardware outofbox etc)

BTW2: some say that hybrid microkernels (half way between monolithic and micro) are better than microkernel by itself (windows and osx are actually hybrid). I don't think so: hybrid microkernel is just a "quick/easy" way to access microkernel technology. The power of innovation/evolution is (IMHO) in microkernel technology.



What's microkernel in short: it act like human nervous system (actual monolithic of linux is like you need to put "little brain" in every muscle)

---

### Post by samalex on 2010-06-18
For the casual user you're right, I don't think MINIX has much to offer, but as everyone else pointed out from an educational standpoint MINIX is still pretty great to work with.

Personally I've wanted to check-out MINIX because it apparently still has decently modern ports (last 5 years or so) that work on pre-80486 systems.  I'd love to find, all be it more for fun, some use for an old 8088 Tandy laptop I have layout around, and even if I could boot it into Minix and have a basic Shell and network support it'd be a fun project.

Also from a nostalgic point of view, it's neat to play with MINIX since in the early days of Linux both Torvalds and Tanenbaum had some debates on the merits of each OS.  For anyone interested in the history of Linux read through Usenet archives and you'll see some heated debates between the two.  Some fun stuff to read now'days.

Sam

---

### Post by RiceMonster on 2010-06-18
> **alexan said:**
> Linus Trovalds is unlikely to willing "restart" ~20 years of work to "rethink" the kernel, l4linux (porting of trovald's kernel to l4 microkernel) seems inactive...

I think it's more than unlikely, because Linus has said before that he thinks micro kernels are a waste of time.

---

### Post by iponeverything on 2010-06-18
If I am not mistaken it was Linus's impatience in waiting for  prentice hall to mail him the minix disks for his i386 that prompted him start working on building his kernel. 

So, I can at least thank prentice hall and minix for getting the bee in Torvalds bonnet.

---

### Post by samalex on 2010-06-18
> **iponeverything said:**
> If I am not mistaken it was Linus's impatience in waiting for  prentice hall to mail him the minix disks for his i386 that prompted him start working on building his kernel. 

So, I can at least thank prentice hall and minix for getting the bee in Torvalds bonnet.

It's been a few years since I read ["Just For Fun"]("http://www.thinkgeek.com/books/nonfiction/38b2/") but I think you're right.  Lots of variables that led up to this wonder OS :)

But then again isn't everything just by chance?  What if Kildall hadn't been flying that fateful day IBM came knocking in 1980.

Sam

---

### Post by chessnerd on 2010-06-18
> **iponeverything said:**
> If I am not mistaken it was Linus's impatience in waiting for  prentice hall to mail him the minix disks for his i386 that prompted him start working on building his kernel. 

So, I can at least thank prentice hall and minix for getting the bee in Torvalds bonnet.
I recently read "Just for Fun." I thought it was really good. A great read if you are a nerd who likes reading the biographies of nerds. If you are a person like this, you might also check out "The Know It All" by A.J. Jacobs.

Anyway, back to topic...

Linus spent a lot of time waiting for the Minix disks, this is true, but he didn't start work on the base of Linux until later.

You see, Linus was at the University of Helsinki and they were using Unix systems. He wanted to be able to use a terminal emulator to sign into the university system, but Minix had almost no support for such things.

This from Wikipedia's article "History of Linux":

*It (Linux) was initially a terminal emulator, which Torvalds used to access the large UNIX servers of the university. He wrote the program specifically for the hardware he was using and independent of an operating system because he wanted to use the functions of his new PC with an 80386 processor.*

It was the limitations of Minix that prompted Linus to start work on Linux, not slow shipping to the fjords of Finland. However, this doesn't mean that Minix wasn't important in the creation of Linux. In fact, the early builds of Linux were compiled using Minix (with the GNU C compiler), Linus Torvalds ported the Minix builds of programs to Linux, and it was Andrew Tanenbaum's book that Linus used to learn about operating system design. Minix is an important part of Linux's history. And just because Minix was once buggy and incomplete, that doesn't mean that it is a bad OS today.

What is the point today? 

Well, what is the point of continuing to work on GNU Hurd when we have the Linux kernel? Because some people think that Linux isn't the be-all end-all of kernels. The micro-kernel is still strongly advocated by some people, so development on Hurd and Minix will continue.

---

### Post by iponeverything on 2010-06-19
> **chessnerd said:**
> I recently read "Just for Fun." I thought it was really good. A great read if you are a nerd who likes reading the biographies of nerds. If you are a person like this, you might also check out "The Know It All" by A.J. Jacobs.

Anyway, back to topic...

Linus spent a lot of time waiting for the Minix disks, this is true, but he didn't start work on the base of Linux until later.

You see, Linus was at the University of Helsinki and they were using Unix systems. He wanted to be able to use a terminal emulator to sign into the university system, but Minix had almost no support for such things.

This from Wikipedia's article "History of Linux":

*It (Linux) was initially a terminal emulator, which Torvalds used to access the large UNIX servers of the university. He wrote the program specifically for the hardware he was using and independent of an operating system because he wanted to use the functions of his new PC with an 80386 processor.*

It was the limitations of Minix that prompted Linus to start work on Linux, not slow shipping to the fjords of Finland. However, this doesn't mean that Minix wasn't important in the creation of Linux. In fact, the early builds of Linux were compiled using Minix (with the GNU C compiler), Linus Torvalds ported the Minix builds of programs to Linux, and it was Andrew Tanenbaum's book that Linus used to learn about operating system design. Minix is an important part of Linux's history. And just because Minix was once buggy and incomplete, that doesn't mean that it is a bad OS today.

What is the point today? 

Well, what is the point of continuing to work on GNU Hurd when we have the Linux kernel? Because some people think that Linux isn't the be-all end-all of kernels. The micro-kernel is still strongly advocated by some people, so development on Hurd and Minix will continue.

agreed, as well it should. I used Tanenbaum's book in my OS design class as well. It is very resource and I kept it around for quite few years until I got tired of lugging it around. Some kid in Kyrgyzstan has it now as well as my K&R book..

---

### Post by cb951303 on 2010-06-19
From minix website:
> 
MINIX 3 is a new open-source operating system designed to be highly reliable, flexible, and secure. It is loosely based somewhat on previous versions of MINIX, but is fundamentally different in many key ways. **MINIX 1 and 2 were intended as teaching tools; MINIX 3 adds the new goal of being usable as a serious system on resource-limited and embedded computers and for applications requiring high reliability**

Also there are no other microkernel based OS around so *there is* a point whether it's popular or not.

---

### Post by DeadSuperHero on 2010-06-19
I'm holding out to see when they'll support an actual desktop environment. I imagine either KDE or E17 would fly on that thing one day. (Not to mention, a lot of people's brains would just explode.)

---

### Post by formaldehyde_spoon on 2010-06-19
> **alexan said:**
> Minix uses the &quot;holy grail&quot; technology for kernels: it's called microkernel. It's the most complex technology actually know, so make a modern OS &quot;usable&quot; with it this technology is mostly unlikely.
Microsoft is still working on it; Apple is not know what's their point on it, Linus Trovalds is unlikely to willing &quot;restart&quot; ~20 years of work to &quot;rethink&quot; the kernel, l4linux (porting of trovald's kernel to l4 microkernel) seems inactive...

So, the only option for GNU/OpenSource community to (eventually) switch of the &quot;holy grail&quot; of kernels is Minix.


BTW: of course, you can find some microkernel OSses around there... but nothing able to perform the modern tasks of PC (change/configure/reinstall hardware outofbox etc)

BTW2: some say that hybrid microkernels (half way between monolithic and micro) are better than microkernel by itself (windows and osx are actually hybrid). I don't think so: hybrid microkernel is just a &quot;quick/easy&quot; way to access microkernel technology. The power of innovation/evolution is (IMHO) in microkernel technology.



What's microkernel in short: it act like human nervous system (actual monolithic of linux is like you need to put &quot;little brain&quot; in every muscle)  That's one viewpoint, and a hotly debated one.

---

### Post by alexan on 2010-06-19
> **cb951303 said:**
> From minix website:


Also there are no other microkernel based OS around so *there is* a point whether it's popular or not.

Symbian was, and it wide more diffused than you can immagine. It got about 50% global market share among cellphone. It was _strongly_ limited to some hardware and application sandboxed: but still almost all cellphone companies did get that this was HUGEly preferable to anything microsoft (windows ce/mobile&co) made
When I heard that Nokia buy it's right to bring it opensource with linux I thought something like "Oh my, these are going to beat the M$ asses"
Sadly it took some time, but nokia did realize that was more stuff than they can chew. Microkernel technology is too much complex to apply the common rules of a modern PC (upgrades, different hardware etc). Even Microsoft it's actually stained behind it.

> **formaldehyde_spoon said:**
> That's one viewpoint, and a hotly debated one.
That's because everyone had his/her own "hero"
There's no exist the "defenitive" OS (it's like "the definitive shovel" or "the ultimate screwdriver").
Microkernel had some vantages.. but when you make the step from monolithic you lost many thing.
The power of the Monolithic kernel is that "it's easy" to understand as whole. Everyone with the right skill can provide piece of it's own knowledge to improve the whole "system".
Example: make compiz on a microkernel would require more research, "mind power", time than it needed to be made for linux (monolithic).
Tanenbaum would tell you "it's even more easy make it on Minix".. <--- the problem is this: you need the Tanenbaum mind and knowledge (developer of Minix) to actually know do it.

---

