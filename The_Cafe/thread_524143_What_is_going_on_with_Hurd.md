---
title: "What is going on with Hurd"
date: 2007-08-12
forum: The Cafe
---

### Post by guguma on 2007-08-12
I have known that the actual kernel for GNU  was considered to be the Hurd, and that Linux is just a temporary replacement. 

It is weird that What we mean by Linux is actually GNU/Linux.

I am just curious about what happens with the Hurd kernel. Is it still being developed. Have it being tried. Will we ever see a GNU/Hurd release and see Richard Stallman VERY HAPPY :). 

By the way do not think that I do not like Linus Torvalds or Linux. I love them both. But I am quite excited about the open source community. And I think that Hurd is a very imporant part of it.

---

### Post by Ozor Mox on 2007-08-12
I think the motivation to develop the Hurd dropped considerably when Linux became a good usable "temporary kernel" with the GNU stuff, and I'd be surprised if it's ever released given how much is to be done on it and how quickly it's developing at the moment.

---

### Post by frup on 2007-08-12
[http://www.superunprivileged.org/](http://www.superunprivileged.org/)

Download the Live CD and try it on your computer or in vmware. It's interesting. Hopefully the GPL3 GNU GPL2 Linux Kernel problems will allow us to have another choice with the Hurd being developed faster, ofcourse it would take quite a few years before it got anywhere near as good as Linux.

---

### Post by Anthem on 2007-08-12
See, I understand that the GNU guys claim that they plugged a Linux kernel into their userspace, but historically it's always looked like the opposite:  the Linux guys took some of the GNU userspace to make their kernel work.

GNU has gotten a lot of development as a result of Linux, but none of the Linux guys have ever claimed any kind of naming rights over GNU as a result of it.

---

### Post by Ozor Mox on 2007-08-12
> **Anthem said:**
> See, I understand that the GNU guys claim that they plugged a Linux kernel into their userspace, but historically it's always looked like the opposite:  the Linux guys took some of the GNU userspace to make their kernel work.

GNU has gotten a lot of development as a result of Linux, but none of the Linux guys have ever claimed any kind of naming rights over GNU as a result of it.

I always thought that too. Stallman claims that GNU took the Linux kernel and it formed the final missing piece for the operating system, but I've read elsewhere that developers modified the GNU tools to work with the Linux kernel and created and operating system. In that case, calling it GNU/Linux or Linux/GNU are both incorrect in some way.

Still, with the whole naming thing, though I support free software and respect what Stallman/GNU/FSF have done, I think they have to accept that Linux is, plainly and simply, a much better sounding name :)

---

### Post by Iandefor on 2007-08-12
> **guguma said:**
> I have known that the actual kernel for GNU  was considered to be the Hurd, and that Linux is just a temporary replacement. 

It is weird that What we mean by Linux is actually GNU/Linux.

I am just curious about what happens with the Hurd kernel. Is it still being developed. Have it being tried. Will we ever see a GNU/Hurd release and see Richard Stallman VERY HAPPY :). 

By the way do not think that I do not like Linus Torvalds or Linux. I love them both. But I am quite excited about the open source community. And I think that Hurd is a very imporant part of it.It's still under development. Linux ate up a bunch of its mindshare, but there are still developers on it.

[Here]("http://www.gnu.org/software/hurd/") is the GNU HURD homepage.

Debian has a [GNU HURD port]("http://www.debian.org/ports/hurd/") that seems to work adequately.

---

### Post by WishingWell on 2007-08-12
There are already choices out there, Nexenta, Schillix and Belenix are using OpenSolaris kernel, Debian/BSD is using the FreeBSD kernel.

---

### Post by RAV TUX on 2007-08-12
> **Iandefor said:**
> 

Debian has a [GNU HURD port]("http://www.debian.org/ports/hurd/") that seems to work adequately.

I have actually tried the Debian/GNU Hurd....I would call it less then adequate.

---

### Post by Anthem on 2007-08-12
The GNU folks will keep working on Hurd, though, because they don't own the copyrights on Linux, and that's important to them.  They'd love to have a kernel that they owned.

---

### Post by bread eyes on 2007-08-12
They're still discussing which microkernel to use and waiting for Coyotos I guess.

---

### Post by Quillz on 2007-08-12
I don't see much point to the GNU Herd now that Linux is a very matured operating system. After all, doesn't the original Herd concept date back to the early 1980s, before Linux was even fathomed?

---

### Post by Iandefor on 2007-08-12
> **Quillz said:**
> I don't see much point to the GNU Herd now that Linux is a very matured operating system. After all, doesn't the original Herd concept date back to the early 1980s, before Linux was even fathomed?If the design is sound, it's sound. When it was dreamed up doesn't matter. We're still using the von Neumann architecture as the basis for most computers and that's from the 40's. We're still using the basic UNIX design and that's from the 70's.

HURD is also still actively developed, so once it gets a stable release, it's not like it'll be some antiquated monster from the '80's.

It's possible it will be a poorly-designed monstrosity. Poor design also transcends mere temporal differences.

Of course, HURD is mostly irrelevant to anybody but FSF, who would prefer to retain full copyrights on all parts of their GNU operating system.

---

### Post by bread eyes on 2007-08-12
> **Quillz said:**
> I don't see much point to the GNU Herd now that Linux is a very matured operating system.

Microkernel have some advantages but ya, it's pretty pointless.

---

### Post by Darkhack on 2007-08-12
> **guguma said:**
> But I am quite excited about the open source community. And I think that Hurd is a very imporant part of it.

By very important you mean not important at all.... right?

---

### Post by jrusso2 on 2007-08-13
Obviously the FSF doesn't have the talent to make Hurd work I mean come on it does not take twenty years to build a kernel.

Even RMS does not use GNU/HURD

---

### Post by DeadSuperHero on 2007-08-13
> **jrusso2 said:**
> Obviously the FSF doesn't have the talent to make Hurd work I mean come on it does not take twenty years to build a kernel.

Even RMS does not use GNU/HURD
Well, YOU build a kernel that works with 100% of Open Source software perfectly (or near-perfectly), with nice fast loading.
Just saying, don't criticize unless you can do better.

---

### Post by DoctorMO on 2007-08-13
To be honest it's not fair to call the operating system gnu or linux, since it requires far more than just linux or the gnu toolsets to form a complete operating system for the modern desktop. Linux is now just an idea, a collection or technological platform, and yet that only fits a little since Gnu is a real platform even without linux. So...

Linux -> Kernel and hardware integration platform
Gnu -> Simple Operating System and software platform
Ubuntu -> Full operating system, polished and focused on a market.

---

### Post by izanbardprince on 2007-08-13
The HURD is still symbolically "in-development", look at the changelog for this year though and laugh....hard.

Even the FSF considers the HURD low priority, GNASH has higher priority to them.

---

### Post by jrusso2 on 2007-08-13
> **Mr. Psychopath said:**
> Well, YOU build a kernel that works with 100% of Open Source software perfectly (or near-perfectly), with nice fast loading.
Just saying, don't criticize unless you can do better.

I don't have to Linus and the Kernel Development Group has already done that, so has FreeBSD, and they did it years ago.

---

### Post by Anthem on 2007-08-13
> **Iandefor said:**
> Of course, HURD is mostly irrelevant to anybody but FSF, who would prefer to retain full copyrights on all parts of their GNU operating system.
Exactly.  That's why the FSF won't really endorse Linux, even though it's under the GPL.  They want to own the copyrights.

---

### Post by AlbinoButt on 2007-08-15
[Hurd 1.0 was released June 1, 2006]("http://humorix.org/articles/2006/06/hurd/") (not)

---

### Post by ry4n on 2007-08-18
> **AlbinoButt said:**
> [Hurd 1.0 was released June 1, 2006]("http://humorix.org/articles/2006/06/hurd/") (not)

June 6th, 2006 

This article actually pretty funny. 

I do hope that some day there really will be a bunch of distros based off the HURD...but I'm a dreamer

---

### Post by Dr. C on 2007-08-18
I do not see the HURD as a priority for the FSF because there are already many Free (as in speech) Kernels:  Linux, Solaris, BSD ...
On the other hand there are areas such as  Gnash, 3D drivers, Free Bios etc., where there are no real Free alternatives. These are among  the real priorities for the FSF. 
So it only makes sense that the HURD be on the back burner.

---

### Post by tehkain on 2007-08-19
I have no idea what is going on with HURD but I hope we have another kernel soon.

I love the linux kernel but having another open kernel with a different structure that is still compatible will be great for the free software operating system community. In my mind it will end in an amazing desktop world. The Micro kernel design might allow for the mixing of licenses. Microkernels use servers for most of the current work done by the kernel(other then the actual computation). So you could have a driver servers based on code in linux. Depending upon licenses that is. Like a bsd style license communication layer could be used too.

Also I like the technical advantages of a microkernel and its servers is appealing.

---

### Post by guguma on 2007-08-19
Yes. A microkernel is (in my opinion) better tnan a monolithic kernel. I cannot understand why so many people are against it. I did not start this argument to become a duel between linux and hurd. We all like the Linux kernel, but it is good to have another one to like.

It is important that hurd is a mircokernel, open source community is a very dynamic one and a microkernel could cope very well with dynamic changes.

---

### Post by Ultra Magnus on 2007-08-19
> **guguma said:**
> It is weird that What we mean by Linux is actually GNU/Linux.

This kind of annoys me, the kernal is technically the 'operating system' so what we mean by Linux is Linux. - RMS uses the 80s marketing term of operating system - ie kernal plus tools and text editors etc - so a basic distrobution could be described as a GNU/Linux distrobution (or more accurately Linux/GNU), but with more sophisticaed distros like Ubuntu there is a whole lot of other stuff like Xfree86 etc which also contribute a lot of code to the 'OS' - So it makes no sense to called it GNU/Linux

---

