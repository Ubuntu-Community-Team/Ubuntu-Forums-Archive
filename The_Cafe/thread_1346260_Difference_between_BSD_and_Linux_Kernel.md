---
title: "Difference between BSD and Linux Kernel?"
date: 2009-12-04
forum: The Cafe
---

### Post by Kdar on 2009-12-04
What is major differences between those two sets of OS?
I always was wondering what was advantage of one or another.

Somewhere I was reading that the BSD kernel was build is better than Linux, but I don't if it had much truth to it.

What is your opinion about those two? What do you think is better (or have potential to be better)?

---

### Post by earthpigg on 2009-12-04
apples and oranges.

Linux is developed as a kernel.

*BSD is developed as an entire operating system.

both the *BSD kernel and Linux kernel are useless alone.

The difference comes when you add in the other stuff.... 

the *BSD stuff is developed by the same guys putting the kernel together.

the Linux stuff is developed by anyone that feels like it, and individual distributions mix-and-match [kernel+other stuff] as they see fit. an example is [upstart]("http://en.wikipedia.org/wiki/Upstart") v [traditional runlevels]("http://en.wikipedia.org/wiki/Runlevel").

in *BSD, the entire project is generally committed to a single thing providing that functionality at once... whereas Linux distributions [have a choice]("http://en.wikipedia.org/wiki/Upstart#Adoption"):

> Upstart has replaced sysvinit in Fedora 9. It currently functions in the same manner as it did in Ubuntu, i.e. it replaces sysvinit, while retaining the existing scripts. Debian[4] is considering a switch for the Squeeze release.

Upstart replaces the sysvinit in the Maemo 5 operating system for Nokia Internet tablets.[5]

Upstart is used in Palm's webOS for the Palm Pre smart phone. [6]


the difference between the two isn't as much legal as it is ***cultural***. this is also why the BSD License and GPL are so different: BSD values developer freedom above all else, GPL values end-user freedom above all else. 

a Free Software lover is likely to regard Apple's proprietary OS X using stuff that was formerly Free Software as a tragedy, whereas an Open Source lover is likely to regard the same as a great success.

"better"? remains to be seen.

competition is healthy, and benefits all involved parties.

its Intelligent Design and Order (BSD) versus Natural Selection and Chaos (GNU/Linux).

---

### Post by BuffaloX on 2009-12-04
BSD is a true UNIX version, Linux is not.
BSD license is compatible with GNU.
GNU license is NOT compatible with BSD.
Linux supports more hardware.

Some claim BSD is more secure than Linux, and has better stability.
but I don't know if this is actually true.

If you want best security and stability, you might want to consider BSD.
If you want compatibility and flexibility, you should probably choose GNU/Linux.
If you want insecurity and inflexibility I guess you could choose this other OS which name escapes me ATM.

---

### Post by Sporkman on 2009-12-04
BSD is managed by a cult, whereas Linux is managed by a loose association of hippies and commies.

---

### Post by lykwydchykyn on 2009-12-04
> **BuffaloX said:**
> BSD is a true UNIX version, Linux is not.

People say this, but I don't know what exactly it means.  Neither BSD nor Linux is officially certified as Unix, though both aim for POSIX and SUS compliance.

Can you elaborate, because I'm curious.

---

### Post by blueshiftoverwatch on 2009-12-04
> **earthpigg said:**
> both the *BSD kernel and Linux kernel are useless alone.
Don't some devices only use the Linux kernel, like cellphones or Tivo players?

---

### Post by chris200x9 on 2009-12-04
> **lykwydchykyn said:**
> People say this, but I don't know what exactly it means.  Neither BSD nor Linux is officially certified as Unix, though both aim for POSIX and SUS compliance.

Can you elaborate, because I'm curious.

I think people say this because BSD was built as an extension to unix where as linux was indipendantly developed as a clone. The point is moot though since as you say neither are certified, and BSD on legal troubles was forced to rewrite the "UNIX" parts. So in reality neither is "more" UNIX than the other. IMO

---

### Post by phrostbyte on 2009-12-04
There is no UNIX code in BSD or Linux. They are both "Unix-like" or mostly POSIX compliant OSes, but neither is derived from AT&T's operating system.

Sometimes people say BSD is more Unix-like because Linux likes to diverge in a lot of places. For instance Linux uses it own sound architecture ALSA, while OSS is considered more "Unix-like" because of it's /dev/dsp interface. Linux also has the /proc directory, which is a feature from Plan 9. It takes ideas from any OS if it's a good idea. Basically Linux is trying to make a kernel which is mostly POSIX compliant, but not necessarily a clone of Unix.

---

### Post by earthpigg on 2009-12-04
> **blueshiftoverwatch said:**
> Don't some devices only use the Linux kernel, like cellphones or Tivo players?

if they ***only*** use the linux kernel, you dont even get the [GNU Core Utilities]("http://en.wikipedia.org/wiki/GNU_Core_Utilities") *ls* or *uname* or *uptime*, much less any form of graphical user interface.

you would turn on your TiVo and see... i dont even think you would get a bash screen.

if they use the kernel, and then add their own GUI and other stuff? well, they aren't ***only*** using the linux kernel, are they? :D


with BSD, however, you ***do*** get all that (a fully functional command line system with package management and whatnot, but still without any GUI) even if ***all you use*** is BSD stuff.

GNU/Linux distributions are different pieces from different places with different designers all thrown together. including stuff from *BSD, such as [OpenSSH]("http://en.wikipedia.org/wiki/Openssh"), and stuff maintained by Apple, such as [CUPS]("http://en.wikipedia.org/wiki/CUPS"). adherence to the [Unix Philosophy]("http://en.wikipedia.org/wiki/UNIX_philosophy#McIlroy:_A_Quarter_Century_of_Unix") means they ***should*** still work well together, and they usually do.

---

### Post by SunnyRabbiera on 2009-12-05
> **BuffaloX said:**
> BSD is a true UNIX version, Linux is not.
Not necessarily true, even though though BSD has a more direct bloodline to the original UNIX I think by now BSD is a much different beast then UNIX

> BSD license is compatible with GNU.
GNU license is NOT compatible with BSD.
Err no its compatible with the GPL actually, the old BSD license wasnt but the newer one is as the old one had the UC Berkeley advertising clause.

> Linux supports more hardware.
yes it does

> Some claim BSD is more secure than Linux, and has better stability.
but I don't know if this is actually true.
Actually I can confirm this one, BSD is very solid and secure.
However there are a few things linux does better, like hardware detection.

---

### Post by dmn_clown on 2009-12-05
> **SunnyRabbiera said:**
> Not necessarily true, even though though BSD has a more direct bloodline to the original UNIX I think by now BSD is a much different beast then UNIX

BSD is Unix it is just not UNIX as none of the organizations putting together a BSD distribution have paid for that distinction.  Linux is a copy and has ultimately forgotten the Unix adage of do only one thing and do it well.


> Err no its compatible with the GPL actually, the old BSD license wasnt but the newer one is as the old one had the UC Berkeley advertising clause.

The GPL is the default license for GNU, there was no reason to split hairs.


> yes it does

Depends on your hardware.  It's difficult to claim a wireless driver as being supported when it drops connections at whim.  Oddly enough for all of the hooplah about Linux hardware support, early RaLink wireless cards are better supported in FreeBSD 7.x than the Linux kernel as connections aren't dropped with no notice.

> 
However there are a few things linux does better, like hardware detection.

This is a subjective argument that I disagree with.  The only thing that I've found Linux Distributions do better than BSD is the time saving, pre-packaged default configurations.

---

### Post by BuffaloX on 2009-12-05
> **lykwydchykyn said:**
> People say this, but I don't know what exactly it means.  Neither BSD nor Linux is officially certified as Unix, though both aim for POSIX and SUS compliance.

Can you elaborate, because I'm curious.

> **SunnyRabbiera said:**
> Not necessarily true, even though though BSD has a more direct bloodline to the original UNIX I think by now BSD is a much different beast then UNIX


Err no its compatible with the GPL actually, the old BSD license wasnt but the newer one is as the old one had the UC Berkeley advertising clause.


Unix or !Unix:
BSD is a true Unix, it is derived directly from AT&T Unix codebase.
BSD was later rewritten because AT&T sued BSD, this however did not satisfy AT&T, because BSD was still doing the exact same as UNIX, only now with their own codebase.
When Novell bought the rights to Unix, they stopped the case against BSD, and allowed BSD to continue.
Linux and GNU tools are build to be mostly Posix compatible. But the designs to achieve compliance are original. Posix is not Unix, but a standard for how the kernel and userland interact.
Posix is what made GNU/Linux possible, all the GNU tools was Posix compatible, so Linux was build to be Posix compatible too, and thus we have a complete OS GNU/Linux.
Posix is just a thin layer of standards, which was originally made for Unix, but being Posix compatible doesnt make it Unix, just Unix friendly.

BSD / GPL license:
Just to be clear.
You can include BSD licensed code in GPL licensed projects.
You cannot include GPL licensed code in BSD licensed projects.

---

### Post by Kdar on 2009-12-05
> **BuffaloX said:**
> Some claim BSD is more secure than Linux, and has better stability.
but I don't know if this is actually true.

Anyone know why they claim BSD is more secure? This is just curious to me.. I am using Linux now, happy with it, and will continue to do so, but this argument is kind of interesting to me.

Somewhere (in article or some video, most likely biased) it was telling how the separation of components/system-parts in Linux (kernel independent from everything else.. etc) give bigger security gap/hole. And then it continued to tell how BSD is more secure because of the way it is build.

That article or video was also telling how BSD can use both Linux and BSD apps and used it as their strong argument, however this not really give any incentive for me to use BSD instead, I don't even know any BSD apps.

PS. I think it was about PC-BSD or something like that (by them or someone else)

---

### Post by Sporkman on 2009-12-05
> **Kdar said:**
> Anyone know why they claim BSD is more secure? This is just curious to me..

Because it's more obscure.

---

### Post by phrostbyte on 2009-12-05
> **Kdar said:**
> Anyone know why they claim BSD is more secure? This is just curious to me.. I am using Linux now, happy with it, and will continue to do so, but this argument is kind of interesting to me.

BSD has nothing really technologically wise that makes it more secure then Linux. OpenBSD developers however, make security a priority, so it's thought that the code they write is less likely to contain holes. Linus opinion on the matter is security people are a nuisance and make things more complicated for minor benefit.

---

### Post by kk0sse54 on 2009-12-05
BSD *is* a certified Unix Operating System and was directly based off AT&T Unix, however by the time of the BSDi vs. USL lawsuit the majority had been rewritten already. Nevertheless BSD is dead and has been for a while.

> There is no UNIX code in BSD

So yes there is Unix code in  the BSD variants but I'd imagine that most of it must have been rewritten by now.

As for the original question you can't really compare the *BSD kernels to the linux kernel. The *BSDs aren't distributions and unlike linux, they have completely different and incompatible kernels. The only thing they have in common in this regard is their development model which is highly centralized and focused on developing a clear and distinct base system *seperate* from the system's package manager or other add-on software.

> **phrostbyte said:**
> BSD has nothing really technologically wise that makes it more secure then Linux. OpenBSD developers however, make security a priority, so it's thought that the code they write is less likely to contain holes. Linus opinion on the matter is security people are a nuisance and make things more complicated for minor benefit.

Security isn't exactly my thing and perhaps someone else can respond in a more well thought out manner but besides the obvious focus on security by such projects like OpenBSD here's just a few BSD technologies from the plethora that are available  ;)

Jails, ProPolice SSP, portaudit, various projects from TrustedBSD i.e. openBSM, pf, and all the software available ffrom OpenBSD i.e. OpenSSH that most people take advantage of

---

### Post by Chame_Wizard on 2009-12-05
> **BuffaloX said:**
> BSD is a true UNIX version, Linux is not.
BSD license is compatible with GNU.
GNU license is NOT compatible with BSD.
Linux supports more hardware.

Some claim BSD is more secure than Linux, and has better stability.
but I don't know if this is actually true.

If you want best security and stability, you might want to consider BSD.
If you want compatibility and flexibility, you should probably choose GNU/Linux.
If you want insecurity and inflexibility I guess you could choose this other OS which name escapes me ATM.
 
I love them both,especially since Debian is using a BSD kernel.:lolflag:

---

