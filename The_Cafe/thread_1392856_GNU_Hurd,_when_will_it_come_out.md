---
title: "GNU Hurd, when will it come out?"
date: 2010-01-28
forum: The Cafe
---

### Post by opengl_cpp on 2010-01-28
I always wonder why gnu project uses mach microkernel as its design basis. since there was a lot of advances to microkernel design such as l3 and l4 microkernels, it may not be a good decision to insist on old mach. 

it has been proved that mach has some performance drawbacks in addition to its complex design, since l4 kernel is by far easier to understand and implement and also has performance superiority over mach.

what do you think about above words.
if you're interested in having a complete gnu os at all, like me please give your ideas?

---

### Post by FuturePilot on 2010-01-28
**Re: GNU Hurd, when will it come out?**

February 30

---

### Post by Skripka on 2010-01-28
> **FuturePilot said:**
> **Re: GNU Hurd, when will it come out?**

February 30

ArchHurd has made lots of progress, and is well on its way to having a bootable core system. :)

[http://www.archhurd.org/](http://www.archhurd.org/)

---

### Post by blur xc on 2010-01-28
Seeing hos you are more technically knowledgeable than me on this subject, I'm going to ask some rather seemingly dumb questions...

#1- What will the Hurd kernel offer than the Linux kernel lacks, besides the more fitting title "GNU Hurd" to the operating system?

#2- Driver support.  Will the Hurd kernel need completely new drivers for all the hardware that's already running well under the Linux kernel?  I understand the open source drivers could be ported across, but that's still a lot of work to do for a lot of hardware.

#3- w/ RMS being a FOSS zealot- does that mean there won't be any proprietary drivers permitted for hardware that doesn't have acceptable open source drivers?

#4- Same deal as above- but regarding Flash.  Does this mean no adobe flash?

#5- in the end- what does that gain us?

BM

---

### Post by baddog144 on 2010-01-28
It's come out April 1.

---

### Post by Skripka on 2010-01-28
> **blur xc said:**
> 

#5- in the end- what does that gain us?

BM

In the words of the Great Allan:

[Quote=]
 I could see this being an interesting waste of time! 
[/Quote]

---

### Post by szymon_g on 2010-01-28
it will never be released. Stallman is to busy fighting everything not-open-enought, that he has no time to code it (and the other developer is sick ;p)

---

### Post by opengl_cpp on 2010-01-28
it is an interesting project. i never heard about it. I wish there was an entry to this project in gnu/hurd offical website.

---

### Post by samalex on 2010-01-28
I didn't realize GNU Hurd was still being actively developed, but I know Stallman has always been abit itchy with the whole GNU/Linux thing since 'Linux' often overshadows or trumps 'GNU'.  

But with as much work that's been done in the Linux kernel over the last two decades, I don't see GNU Hurd or any other kernel becoming a viable replacement for the Linux kernel.  Only those FOSS Purists will probably run it exclusively.

Just my thoughts...

Sam

---

### Post by Simian Man on 2010-01-28
Never.  And nobody would care if it did.

---

### Post by x3roconf on 2010-01-28
I dislike Richard Stallmann so i don't like hurd at all.

---

### Post by NoaHall on 2010-01-28
Nobody except stallman would use it. GPLv3 as your core system, anyone? No? Didn't think so.

---

### Post by Xbehave on 2010-01-28
> **opengl_cpp said:**
> I always wonder why gnu project uses mach microkernel as its design basis. since there was a lot of advances to microkernel design such as l3 and l4 microkernels, it may not be a good decision to insist on old mach. 
when Hurd development started mach was new!

---

### Post by opengl_cpp on 2010-01-28
there would be a great deal of efforts to make gnu/hurd as powerful as gnu/linux. 

but there is some advantages to microkernel (hurd) over monolithic kernels (linux).
it is by far easier to maintain, debug and improve.

there are some wellknow oses that use this design among them minix is the most interesting.

i think monolithic kernels will face a lot of problems in the future. You may have heard about microsoft plans for a new operating system called Midori that is going to remove windows.

so there is a hope for gnu/hurd to be more popular in the future, because of its design.

---

### Post by Xbehave on 2010-01-28
> **NoaHall said:**
> Nobody except stallman would use it. GPLv3 as your core system, anyone? No? Didn't think so.
I agree that GPLv2 is a better license but  GPLv3 aint that bad, I would contribute to a GPLv3 projects, I just wouldn't start one as GPLv2 is I believe a license should be.

The advantage of hurd over linux is the microkernel design, meaning that bugs in modules 
1) cant crash the os
2) cant be used to exploit anything else

---

### Post by NoaHall on 2010-01-28
> **Xbehave said:**
> I agree that GPLv2 is a better license but  GPLv3 aint that bad, I would contribute to a GPLv3 projects, I just wouldn't start one as GPLv2 is I believe a license should be.

The advantage of hurd over linux is the microkernel design, meaning that bugs in modules 
1) cant crash the os
2) cant be used to exploit anything else

It is. You can't use anything closed source along side with GPLv3. That means no Flash, no good hardware drivers, no closed source browsers, etc.

---

### Post by lykwydchykyn on 2010-01-28
> **blur xc said:**
> Seeing hos you are more technically knowledgeable than me on this subject, I'm going to ask some rather seemingly dumb questions...

I'm not an expert, but let's have a crack at these questions:
> 
#1- What will the Hurd kernel offer than the Linux kernel lacks, besides the more fitting title "GNU Hurd" to the operating system?

It's a microkernel, and as far as I know the only major FOSS microkernel project around apart from Minix.  If that means nothing to you, I suggest googling "Microkernel vs monolithic kernel" and spend a few years reading the gigabytes of debate over which is better.

Since it's important for the next few questions, though, one of the more important differences between micro and monolithic kernels is that drivers are not part of a microkernel.  With a microkernel, drivers are run in userspace.  A monolithic kernel like Linux has drivers in the kernel.
> 
#2- Driver support.  Will the Hurd kernel need completely new drivers for all the hardware that's already running well under the Linux kernel?  I understand the open source drivers could be ported across, but that's still a lot of work to do for a lot of hardware.

Since it's a totally different kernel, and the drivers are running in userspace, yes they'd have to be rewritten.  How difficult that would be for opensource drivers I can't say, though I do know that BSD and Linux share a lot of driver code so it's not all kernel-specific.
> 
#3- w/ RMS being a FOSS zealot- does that mean there won't be any proprietary drivers permitted for hardware that doesn't have acceptable open source drivers?

Since it's a microkernel, drivers are not in the kernel but run in userspace.  So there is no licensing problem with running a proprietary driver with a microkernel as there is with Linux, where firmware and proprietary drivers have to be separately distributed.
RMS may not like it, but there would be no licensing issue IIUC.
> 
#4- Same deal as above- but regarding Flash.  Does this mean no adobe flash?

Flash has zilch to do with the kernel.  You can legally RUN any proprietary application on a GPL kernel, just as you can on Linux.  The problem comes when you distribute GPL code with proprietary in the same software (e.g., the Linux kernel with proprietary drivers embedded).
> 
#5- in the end- what does that gain us?

Another option?  Another choice?  Maybe, in 10 years when the Linux kernel has 30 years of device driver code accumulated, a possible solution to the bloat problem?

Or something to joke about on a forum, if nothing else.  Who cares, if the developers working on it feel like they're making good use of their time, I'm not bothered by it.

> **x3roconf said:**
> I dislike Richard Stallmann so i don't like hurd at all.

You might want to remove the following from your machine:
[http://en.wikipedia.org/wiki/List_of_GNU_software](http://en.wikipedia.org/wiki/List_of_GNU_software)

I don't like a lot of people who contribute to Linux, at least going by their blogs and public comments.  They still make some pretty great software.

---

### Post by lykwydchykyn on 2010-01-28
> **NoaHall said:**
> It is. You can't use anything closed source along side with GPLv3. That means no Flash, no good hardware drivers, no closed source browsers, etc.

citation?

---

### Post by Xbehave on 2010-01-28
> **opengl_cpp said:**
> but there is some advantages to microkernel (hurd) over monolithic kernels (linux).
it is by far easier to maintain, debug and improve.
the fact that linux/BSD/opensolaris and even windows, improved much faster than mach suggest monolithic are the ones that are easier to maintain, debug and improve. Infact generally difficulty of implementing a microkernel is one of the things that holds them back. 

Most of the microkernel design advantages are there in modular kernels anyway, it's just safety/security that modular kernels still lack.

> **NoaHall said:**
> It is. You can't use anything closed source along side with GPLv3. That means no Flash, no good hardware drivers, no closed source browsers, etc.
Either your trolling or you really need to learn read the GPL and understand what derivative work means, it's problem is the anti-tivoisation stuff, but it definitely doesn't prevent you running closed software or drivers on GPLv3 kernel.

---

### Post by falconindy on 2010-01-28
Hurd's release will coincide with the release of Duke Nukem Forever.

---

### Post by Skripka on 2010-01-28
> **falconindy said:**
> Hurd's release will coincide with the release of Duke Nukem Forever.

E18 is the official GNU DE/WM.

---

### Post by nrs on 2010-01-28
> **NoaHall said:**
> It is. You can't use anything closed source along side with GPLv3. That means no Flash, no good hardware drivers, no closed source browsers, etc.
Ugh? Where did you hear this?

---

### Post by Xbehave on 2010-01-28
> **falconindy said:**
> Hurd's release will coincide with the release of Duke Nukem Forever.
running on wine 1.0,... dammit!

---

### Post by Ric_NYC on 2010-01-28
What?

GNU Turd?

---

### Post by mickie.kext on 2010-01-28
> **NoaHall said:**
> It is. You can't use anything closed source along side with GPLv3. That means no Flash, no good hardware drivers, no closed source browsers, etc.

Wut? That's not true. With GPLv3 software you can do exactly same things like GPLv2, except that GPLv3 is compatible with Apache license v2 and AGPLv3, while GPLv2 is not. 

Other thing is tivoisation which has nothing to do with desktop systems. It means that manufacturer of appliances can not use GPL'd sofware and then b0rk device if you change software. There is also broader patent protection which is good for everybody.

---

### Post by Simian Man on 2010-01-28
> **opengl_cpp said:**
> there would be a great deal of efforts to make gnu/hurd as powerful as gnu/linux. 

but there is some advantages to microkernel (hurd) over monolithic kernels (linux).
it is by far easier to maintain, debug and improve.

That's perhaps true in theory, but isn't true in practice.  If it was then why would Hurd be such a failure when Linux is such a success?

---

### Post by mickie.kext on 2010-01-28
In practice, microkernels are harder to develop, debug and maintain. Inter process communication makes debugging a nightmare.

---

### Post by blur xc on 2010-01-28
> **lykwydchykyn said:**
> I'm not an expert, but let's have a crack at these questions:

It's a microkernel, and as far as I know the only major FOSS microkernel project around apart from Minix.  If that means nothing to you, I suggest googling "Microkernel vs monolithic kernel" and spend a few years reading the gigabytes of debate over which is better.

Since it's important for the next few questions, though, one of the more important differences between micro and monolithic kernels is that drivers are not part of a microkernel.  With a microkernel, drivers are run in userspace.  A monolithic kernel like Linux has drivers in the kernel.

Since it's a totally different kernel, and the drivers are running in userspace, yes they'd have to be rewritten.  How difficult that would be for opensource drivers I can't say, though I do know that BSD and Linux share a lot of driver code so it's not all kernel-specific.

Since it's a microkernel, drivers are not in the kernel but run in userspace.  So there is no licensing problem with running a proprietary driver with a microkernel as there is with Linux, where firmware and proprietary drivers have to be separately distributed.
RMS may not like it, but there would be no licensing issue IIUC.

Flash has zilch to do with the kernel.  You can legally RUN any proprietary application on a GPL kernel, just as you can on Linux.  The problem comes when you distribute GPL code with proprietary in the same software (e.g., the Linux kernel with proprietary drivers embedded).

Another option?  Another choice?  Maybe, in 10 years when the Linux kernel has 30 years of device driver code accumulated, a possible solution to the bloat problem?

Or something to joke about on a forum, if nothing else.  Who cares, if the developers working on it feel like they're making good use of their time, I'm not bothered by it.



You might want to remove the following from your machine:
[http://en.wikipedia.org/wiki/List_of_GNU_software](http://en.wikipedia.org/wiki/List_of_GNU_software)

I don't like a lot of people who contribute to Linux, at least going by their blogs and public comments.  They still make some pretty great software.

thanks for the thought out answer- and the driver deal makes a lot of sense to me.  W/ the microkernel, that I assume only drivers specific to your hardware get installed vs. the Linux kernel being bogged down w/ drivers for all kinds off software, w/ no way to remove them w/o hacking the source code?

What kind of kernel does DOS/Windows have?  From what I understand, the was DOS handles drivers is what makes is BSOD when there's a bug in the driver (like my dell docking station, that fails to undock, and BSOD's my computer- first BSOD I've experienced in years, not counting when I had a virus).

I thought the Linux kernel was immune to BSOD type failures because of the way it handled drivers?

When I have a bit of free time, I'll do a microkernel vs. monolithic kernel search.

Thanks again,
BM

---

### Post by opengl_cpp on 2010-01-28
at the time gnu uses mach microkernel, that is a nasty version of microkernel. in regard to this design, i agree that it is harder to debug and maintain than linux kernel.

but there have been many improvement and research jobs around this field, and now you can see some simpler interfaces to microkernels and even smaller kernel that is simpler than monolithic.

things are going to change, although gnu/hurd may never achieve its goals, i am sure the linux design will change as its kernel gets larger and larger everyday.

---

### Post by szymon_g on 2010-01-28
> **blur xc said:**
> thanks for the thought out answer- and the driver deal makes a lot of sense to me.  W/ the microkernel, that I assume only drivers specific to your hardware get installed vs. the Linux kernel being bogged down w/ drivers for all kinds off software, w/ no way to remove them w/o hacking the source code?

What kind of kernel does DOS/Windows have?  From what I understand, the was DOS handles drivers is what makes is BSOD when there's a bug in the driver (like my dell docking station, that fails to undock, and BSOD's my computer- first BSOD I've experienced in years, not counting when I had a virus).

I thought the Linux kernel was immune to BSOD type failures because of the way it handled drivers?

When I have a bit of free time, I'll do a microkernel vs. monolithic kernel search.

Thanks again,
BM

I'm not sure about DOS, but NT's kernel is a hybrid kernel [http://en.wikipedia.org/wiki/Hybrid_kernel](http://en.wikipedia.org/wiki/Hybrid_kernel)

and no- Linux kernel isn't immune to 'bsods' (or, rather, kernel panics). even not-fully working usb-stick can crash it :)

And, when you run linux, you do not run unnecessery drivers; it loads only these needed on your system. Default kernels in most distributions have a lot of drivers enabled (either compiled-in or as modules)- because they can be needed by someone (it have to be universal). You can disable them during kernel compilation.

---

### Post by dragos240 on 2010-01-28
There is debian hurd also.

---

### Post by k64 on 2010-01-28
GNU Hurd is even older than Linux, for one. Two, it already came out - in the 1980's! Three, it does not have good hardware support - at all!

GNU Hurd != new kernel. GNU Hurd == OLDER than Linux.

---

### Post by handy on 2010-01-28
I remember when Barrucadu started the Hurd thread over at the Arch forums, & Allan, said that he had fiddled about with a cross compiler in the past, & then off they went... :)

Due to seeing this thread in the UF I just went & read through the Arch Hurd thread.  It's great, they are really close to having an installable system that will use pacman.

When it gets to that point I'll start playing with it too, just for fun. :)

Who knows, the gathering Arch Hurd team may make some important breakthroughs, like getting X to work on Hurd, which would certainly be an important milestone.

They have already solved some of the bugs.

---

### Post by Eclipse. on 2010-01-28
Mabey never.

---

### Post by madhi19 on 2010-01-28
The same week that Duke Nuken Forever come out! Don't lose hope after all Axl did release Chinese Democracy so everything possible!

---

### Post by handy on 2010-01-28
It is interesting to see that there seems to be primarily two contrasting types of people:

1. Those that take a negative approach & knock whatever, whenever the opportunity arises.

2. Those that take a positive approach & appreciate the positive potential whenever the opportunity arises.

There is of course some overlap between these two fundamental attitudes, though people tend to fit into one or the other primary group.

You get out what you put in, I say.

---

### Post by BuffaloX on 2010-01-28
I would love to see Hurd succeed.
Especially if it makes it a little easier to make/distribute drivers.

We have a very nice kernel as it is, but nothing lasts forever.

---

### Post by handy on 2010-01-28
> **BuffaloX said:**
> I would love to see Hurd succeed.
Especially if it makes it a little easier to make/distribute drivers.

We have a very nice kernel as it is, but nothing lasts forever.

I wonder if the Linux kernel will end up being hybridised mono/micro to take care of the ever growing driver problem?

---

### Post by DeadSuperHero on 2010-01-28
Part of me dearly would love to see the HURD succeed, at least in some small way. Mach really is a crapfest though. I haven't checked in on Viengoos in a while though, so you never know...

---

### Post by LightB on 2010-01-29
I just hope it can run Duke Nukem Forever.

---

### Post by Barrucadu on 2010-01-29
> **Skripka said:**
> ArchHurd has made lots of progress, and is well on its way to having a bootable core system. :)

[http://www.archhurd.org/](http://www.archhurd.org/)

> **handy said:**
> I remember when Barrucadu started the Hurd thread over at the Arch forums, & Allan, said that he had fiddled about with a cross compiler in the past, & then off they went... :)

*feels loved*

I wouldn't say we've made *lots* of progress; we have something which can boot, yes, but can't run GCC or pacman on it yet&#8230;

> **blur xc said:**
> #1- What will the Hurd kernel offer than the Linux kernel lacks, besides the more fitting title "GNU Hurd" to the operating system?

A different way of doing things. Do you *need* more of a reason to play around with an OS? :P

> **blur xc said:**
> #2- Driver support.  Will the Hurd kernel need completely new drivers for all the hardware that's already running well under the Linux kernel?  I understand the open source drivers could be ported across, but that's still a lot of work to do for a lot of hardware.

Currently there seems to be a lot of work in porting the L4 ddelinux26 to Mach. This would allow you to run Linux 2.6.29 drivers with Mach natively, with no rewriting or patching (theoretically).

> **blur xc said:**
> #3- w/ RMS being a FOSS zealot- does that mean there won't be any proprietary drivers permitted for hardware that doesn't have acceptable open source drivers?

I'm sure he won't be able to stop 3rd party developers writing drivers, even if he *can* successfully influence them away from the official distribution.

> **blur xc said:**
> #4- Same deal as above- but regarding Flash.  Does this mean no adobe flash?

It's a kernel used only by (currently) people who want to make life difficult for themselves, and HURD developers. It's unstable, has awful hardware support, and seemingly spontaneously develops problems. I didn't really consider Flash being ported an event likely to occur in the near future&#8230;

> **blur xc said:**
> #5- in the end- what does that gain us?
A new OS to play with :popcorn:

---

### Post by Xbehave on 2010-01-29
> **handy said:**
> I wonder if the Linux kernel will end up being hybridised mono/micro to take care of the ever growing driver problem?
The only problems (**I** see) w.r.t 3rd party drivers linux has are:
1) ditros like arch :P and ubuntu :(, don't stick to stable releases (largely because users don't want to) so it's hard to target a binary that will support "linux" (nvidia manage it by maintaining a shim of GPLd code). 
2) Lack of interest in producing 3rd party drivers due to low market share (Hurd will have this worse!)

p.s I think linux is too modular to be a microkernel image the IPC needed to get sound working 
```
snd_hda_codec_realtek   276291  1
snd_hda_intel          26255  2
snd_hda_codec          82553  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6654  1 snd_hda_codec
snd_mixer_oss          17157  1 snd_pcm_oss
snd_pcm                87261  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_rawmidi            22244  1 snd_seq_midi
snd_seq_midi_event      6867  2 snd_seq_oss,snd_seq_midi
snd_seq                54665  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23408  2 snd_pcm,snd_seq
snd_seq_device          6488  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    68622  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7810  1 snd
snd_page_alloc          8412  2 snd_hda_intel,snd_pcm

```
but hey hurd driver-modules could be modular (so all of the above runs in a single process, while you can still load what linux calls modules in/out of it). mmm, modular modules, recursive recursion FTW!

> Currently there seems to be a lot of work in porting the L4 ddelinux26 to Mach. This would allow you to run Linux 2.6.29 drivers with Mach natively, with no rewriting or patching (theoretically).
On the one hand that would be awesome as it would get Hurd a lot of driver support and if hurd takes off sharing driver code between linux & hurd would mean better drivers for everybody (granted hurd will eventually hurdify the code, but if the cooperation is there i'm sure both kernels can help each other), on the other hand [SIZE="4"]dey tuk r drivers![/SIZE]

> It's a kernel used only by (currently) people who want to make life difficult for themselves
Or as i like to call them Arch users :P

IIRC hurd also has a cool security design (more than unix, less than SElinux (but easier to use than gauging your eyes out with a blunt spoon)), so it probably appeals to old skool unix types or might result in somebody porting the system to linux.

> A new OS to play with
Wile I wish Hurd the best of luck i don't think it will ever truely compete with linux for most uses, but just like BSD & openSolaris, it will be another OS to play with and will probably have a niche too.

---

### Post by handy on 2010-01-29
The driver problem I was very loosely referring to is the incredible & ever increasing bloat that they are responsible for in the Linux monolith.

---

### Post by Xbehave on 2010-01-29
> **handy said:**
> The driver problem I was very loosely referring to is the incredible & ever increasing bloat that they are responsible for in the Linux monolith.
But they arn't bloat if they are never loaded! a modular kernel and a microkernel behave pretty much the same wrt to bloatiness and size, it's only security and stability (due to memory protection) that a micokernel has over a modular kernel. If anything microkernel will be **more** bloated because of IPC code and slow because of IPC latency.

---

### Post by MisfitI38 on 2010-01-29
> **Xbehave said:**
> But they arn't bloat if they are never loaded! a modular kernel and a microkernel behave pretty much the same wrt to bloatiness and size, it's only security and stability (due to memory protection) that a micokernel has over a modular kernel. 
I agree. Further, Linux kernel drops support for hardware slowly as it evolves.
> 
If anything microkernel will be **more** bloated because of IPC code and slow because of IPC latency.
I disagree..unless you were running it on a Pentium II or older. ;)

---

### Post by Xbehave on 2010-01-29
> **MisfitI38 said:**
> I disagree..unless you were running it on a Pentium II or older. ;)
Oh the performance hit doesn't matter on modern computers, but if either one is going to be called 'bloated', surely it's the one with it. Unless your saying process switching and IPC is free?

---

### Post by handy on 2010-01-29
I was talking off the top of my head, being inspired from whatever I read once that stated the micro kernel handled drivers in a superior way to that of the the monolithic kernel, & that it would be vastly superior to the kernel bloat that Linux has.

I may be remembering incorrectly &/or what I read may have been incorrect.  Either way, I'm learning more in this thread, so my understanding is growing & changing.

(I can't post a link as it was way too long ago, I have no idea where I read it.)

---

