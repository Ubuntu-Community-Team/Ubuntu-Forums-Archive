---
title: "why i386 and not i686?"
date: 2009-09-09
forum: The Cafe
---

### Post by goseph on 2009-09-09
Lots of distros offer optimized 686 builds. Why doesn't Ubuntu? Would it be horrendously complicated and lots of extra work to maintain two official builds?

---

### Post by Skripka on 2009-09-09
> **goseph said:**
> Lots of distros offer optimized 686 builds. Why doesn't Ubuntu? Would it be horrendously complicated and lots of extra work to maintain two official builds?

It is something folks often wonder.  Why does Ubuntu compile for an architecture that it will NOT even RUN on.

---

### Post by Bachstelze on 2009-09-09
> **goseph said:**
> Lots of distros offer optimized 686 builds. Why doesn't Ubuntu? Would it be horrendously complicated and lots of extra work to maintain two official builds?

Mostly because those "optimized" build make no noticeable difference for most applications.

> **Skripka said:**
> It is something folks often wonder.  Why does Ubuntu compile for an architecture that it will NOT even RUN on.

I've run Ubuntu in a 486DX2 for three years without any problem.

---

### Post by Simian Man on 2009-09-09
Because that's how Debian does it.

And Debian takes years to implement any change.

---

### Post by Bachstelze on 2009-09-09
> **Simian Man said:**
> Because that's how Debian does it.

And Debian takes years to implement any change.

Also true, and given how the package building system works, it wouldn't be convenient to do an i686 version of Ubuntu alone.

---

### Post by Newuser1111 on 2009-09-09
> **goseph said:**
> Lots of distros offer optimized 686 builds. Why doesn't Ubuntu? Would it be horrendously complicated and lots of extra work to maintain two official builds?So it can run on older computers.

---

### Post by blueturtl on 2009-09-09
Why stop at i686?

Most new desktops are 64-bit anyway, so you might as well run Ubuntu AMD64 edition (also confusingly compatible with 64-bit Intel chips).

That way you get the most out of your rig.

On Debian, if something later than a P2 CPU is detected, it will automatically install the i686 kernel.

---

### Post by Skripka on 2009-09-09
> **HymnToLife said:**
> 

I've run Ubuntu in a 486DX2 for three years without any problem.

I'm talking about i386.  As per Ubuntu's own official documentation, Ubuntu will not install on an i386 processor.  Why do they compile for i386, if Ubuntu will not even install on such a rig?

And I quote:
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

At the bottom of the page...

[QUOTE=Ubuntu Documentation]
Absolute minimum requirements
Intel 486 processor 
32 MB of system memory (RAM) 
300 MB of disk space
[/QUOTE]

---

### Post by Bucky Ball on 2009-09-09
I'm running a P4 and last I heard that was i386.

---

### Post by Skripka on 2009-09-09
> **Bucky Ball said:**
> I'm running a P4 and last I heard that was i386.

Um, No.  P4s are what Intel officially called "P6" architecture... i.e. unofficially "i686"-due to courts forbidding the "_86" terminology in the early-mid 90s.

---

### Post by mcduck on 2009-09-09
> **Skripka said:**
> I'm talking about i386.  As per Ubuntu's own official documentation, Ubuntu will not install on an i386 processor.  Why do they compile for i386, if Ubuntu will not even install on such a rig?

And I quote:
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

At the bottom of the page...

because compiling for 386 works better for 586 than compiling for 686 would. And compiling for 386 works on a 686 and later better than compiling for 586 does. :)

Also note that Ubuntu's kernel still includes support for features of modern processors, so you'll have support for stuff like SSE, SSE2, SSE3, 3DNow etc, which definitely aren't 386 features.

The thing is that it really isn't as simple as "386 in package name, thus it's compiled for 386".

edit: Actually Ubuntu used to have have different kernels for 386, 686 and K7. I must say when the change to Generic kernel happened I never noticed any difference when comparing the K7 kernel with the new Generic one. So I'd say getting rid of those CPU-specific kernels was a good move.

---

### Post by Bachstelze on 2009-09-09
> **Skripka said:**
> 
At the bottom of the page...

And just above it:

> It is possible that you will be able to install Ubuntu on computers with lower specifications than those given below. However, installation may be extremely difficult and Ubuntu is likely to run very slowly on such a system.

... and if you know your stuff well enough, it can run acceptably well for some purposes.

---

### Post by Bachstelze on 2009-09-09
> **Bucky Ball said:**
> I'm running a P4 and last I heard that was i386.

Anything newer than a Pentium Pro is i686.

---

### Post by blueturtl on 2009-09-09
> **Skripka said:**
> I'm talking about i386.  As per Ubuntu's own official documentation, Ubuntu will not install on an i386 processor.  Why do they compile for i386, if Ubuntu will not even install on such a rig?

And I quote:
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

At the bottom of the page...

I think here the idea is that they're actually referring to the CPU architecture. The 80486 was an improved CPU over the 80386, but did not change things related to the actual workings of the CPU so much.

The 8088 was an 8-bit chip as I recall, the 80286 was 16-bit, and the 80386 was the first in the series that was 32-bit. The 80486 was/is a 32-bit CPU also. Basically 80486 is a 80386 on steroids.

So i386 refers to 32-bit CPUs between the 80386 and PentiumIII.

---

### Post by Skripka on 2009-09-09
> **HymnToLife said:**
> 
... and if you know your stuff well enough, it can run acceptably well for some purposes.

Apart from the ongoing "How old a machine can I get _____ to install on?" contest?

Why anyone would even still have a 25 year old computer artifact in their keeping is beyond me.

---

### Post by speedwell68 on 2009-09-09
> **blueturtl said:**
> I think here the idea is that they're actually referring to the CPU architecture. The 80486 was an improved CPU over the 80386, but did not change things related to the actual workings of the CPU so much.

The 8088 was an 8-bit chip as I recall, the 80286 was 16-bit, and the 80386 was the first in the series that was 32-bit. The 80486 was/is a 32-bit CPU also. Basically 80486 is a 80386 on steroids.

So i386 refers to 32-bit CPUs between the 80386 and PentiumIII.

The 8088 and 80188 were both had 8 bit external data buses.  The 8086, 80186 were 16 bit.  The 80186 was highly under utilised chip only two PCs I can think of actually used it, the RM Nimbus 186 and the RM Nimbus 186-QD.  Then of course there were the 8087 and 80187 math co-processors.  Sorry I was offering nothing further to the conversation it is just RM 80186s were the first PCs I ever used and ever worked on professionally and this conversation just sparked some dim and distant memories.:D

---

### Post by mcduck on 2009-09-09
> **Skripka said:**
> Apart from the ongoing "How old a machine can I get _____ to install on?" contest?

Why anyone would even still have a 25 year old computer artifact in their keeping is beyond me.
You are now seeing things strictly from a desktop user's point of view.

It's not rare at all to use 486 or Pentium machines on embedded systems and for automation purposes. Such computers are perfectly fine for many other purposes as well.

---

### Post by speedwell68 on 2009-09-09
> **mcduck said:**
> You are now seeing things strictly from a desktop user's point of view.

It's not rare at all to use 486 or Pentium machines on embedded systems and for automation purposes. Such computers are perfectly fine for many other purposes as well.

I concur, the 80186 chip didn't go out of production until 2006 IIRC.  Also, a lot of engineering and software history is simply being lost for all time because of the 'I'll throw it away because it is old' philosophy.

---

### Post by Bachstelze on 2009-09-09
And anyway, what's wrong with  "How old a machine can I get _____ to install on?" contests? You can learn much more about your system that way than by installing Arch on a Phenom II.

---

### Post by Skripka on 2009-09-09
> **speedwell68 said:**
> I concur, the 80186 chip didn't go out of production until 2006 IIRC.  Also, a lot of engineering and software history is simply being lost for all time because of the 'I'll throw it away because it is old' philosophy.

Intel ceased production of 80486 for embed systems 2-3 years ago.

---

### Post by Skripka on 2009-09-09
> **HymnToLife said:**
> And anyway, what's wrong with  "How old a machine can I get _____ to install on?" contests? You can learn much more about your system that way than by installing Arch on a Phenom II.


Is there not just as much validity in trying to install SUSE 7.1 on your 17 and 3/4 bit i355 CPU toaster with 20k of memory and it's off-die numeric processor?


Sure you can, but why waste the effort on something you can barely use due to being a 1/4 century past obsolete?  I recall KiwiNZ got Ubuntu to install on some 20+ yr old hardware, and was proud of himself and wowed people here...and gave up on the endeavor a few days/weeks later-because it was obvious he couldn't really do that much with it.

---

### Post by Bachstelze on 2009-09-09
> **Skripka said:**
> 
Sure you can, but why waste the effort on something you can barely use due to being a 1/4 century past obsolete?

For that, refer to the answers above mine. Also, my 486DX2 made a perfect home router/firewall.

---

### Post by Chronon on 2009-09-09
> **mcduck said:**
> You are now seeing things strictly from a desktop user's point of view.

It's not rare at all to use 486 or Pentium machines on embedded systems and for automation purposes. Such computers are perfectly fine for many other purposes as well.

Indeed, I have to run two Win95 machines at my work.  They are each dedicated to operating a scientific instrument.  Each utilizes an ISA hardware board installed in the PC to do this.  One of them requires 16 bit application to run and will not work on a truly 32 bit system.  Win95 works because most of it is still 16 bit.  These machines will be maintained in their present configuration for the foreseeable future.  There is no advantage to upgrading the OS when the machine's sole purpose is to run a single application.

---

### Post by speedwell68 on 2009-09-09
> **HymnToLife said:**
> For that, refer to the answers above mine. Also, my 486DX2 made a perfect home router/firewall.

I used to use an old 286 as a print server.  Old technology still has a use in the real world.

---

### Post by blueturtl on 2009-09-09
> **speedwell68 said:**
> The 8088 and 80188 were both had 8 bit external data buses.  The 8086, 80186 were 16 bit.  The 80186 was highly under utilised chip only two PCs I can think of actually used it, the RM Nimbus 186 and the RM Nimbus 186-QD.  Then of course there were the 8087 and 80187 math co-processors.  Sorry I was offering nothing further to the conversation it is just RM 80186s were the first PCs I ever used and ever worked on professionally and this conversation just sparked some dim and distant memories.:D

Woah. Someone else remembers this stuff. :) I actually forgot there was a 80186 in there.

My first system was a 80386SX (and I remember this bitterly, since the SX model was kind of like a Celeron would be today: artificially crippled in performance to be sold for less money). They cut the bus width to 16-bits while internally it was still 32-bit chip, so the performance was somewhere between a 80286 and a fully blown 80386.

Ah, I remember how the Windows desktop appeared with an obvious lag. The background image filling the screen slowly from the top to bottom. You could actually see this happen. :D

---

### Post by recluce on 2009-09-09
> **Chronon said:**
> Indeed, I have to run two Win95 machines at my work.  They are each dedicated to operating a scientific instrument.  Each utilizes an ISA hardware board installed in the PC to do this.  One of them requires 16 bit application to run and will not work on a truly 32 bit system.  Win95 works because most of it is still 16 bit.  These machines will be maintained in their present configuration for the foreseeable future.  There is no advantage to upgrading the OS when the machine's sole purpose is to run a single application.

This is a **very good point**. We used to run a 386-based machine that had our PBX switchboard controller on an ISA card. That machine served only the single purpose and ran an ancient SCO Unix. The PBX finally got replaced about two years ago with an VOIP based system, after 17 years of operation.

Clients run mission-dedicated systems that are even older, especially in controlling machinery of all kinds.

The most ancient system I personally see in operation (not at a client) is a 286-based automotive diagnostic box (huge orange thing with an IBM AT look-alike computer sort of "tacked in". Useless for modern cars, but the best diagnostic system for cars from the 70s and 80s. The system runs DOS and has a green Hercules screen...

---

### Post by YeOK on 2009-09-09
> **recluce said:**
> This is a **very good point**. We used to run a 386-based machine that had our PBX switchboard controller on an ISA card. That machine served only the single purpose and ran an ancient SCO Unix. The PBX finally got replaced about two years ago with an VOIP based system, after 17 years of operation.

Clients run mission-dedicated systems that are even older, especially in controlling machinery of all kinds.

The most ancient system I personally see in operation (not at a client) is a 286-based automotive diagnostic box (huge orange thing with an IBM AT look-alike computer sort of "tacked in". Useless for modern cars, but the best diagnostic system for cars from the 70s and 80s. The system runs DOS and has a green Hercules screen...

You wouldn't upgrade the OS of a mission critical machine, if its working, you leave it be. If it needs an upgrade, you may as well change the hardware while your at it. That's why Enterprise distro's stick to one generation of Kernel and import patches that are required.

Fedora 11 dropped i386 for i586 and plan to drop i586 for i686 in Fedora 12. I'm sure if the Fedora project decided its worth doing, Ubuntu / Debian will be thinking about it too.

---

### Post by Bucky Ball on 2009-09-10
> **Skripka said:**
> Um, No.  P4s are what Intel officially called "P6" architecture... i.e. unofficially "i686"-due to courts forbidding the "_86" terminology in the early-mid 90s.

I sit very comfortably with a glass of my favourite corrected. I love this community!

---

### Post by SunnyRabbiera on 2009-09-10
I thought the x86 was kinda catchall anyway, as the kernel is 32bit anyway.

---

### Post by doorknob60 on 2009-09-11
> **Skripka said:**
> I'm talking about i386.  As per Ubuntu's own official documentation, Ubuntu will not install on an i386 processor.  Why do they compile for i386, if Ubuntu will not even install on such a rig?

And I quote:
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

At the bottom of the page...

Because I've run it (well, not with Gnome, but Ubuntu variants) on an i586 CPU before, and if it was compiled for i686 it wouldn't have worked. If it wasn't for that I'd have Arch on there :(

---

### Post by jrusso2 on 2009-09-11
> **Bucky Ball said:**
> I'm running a P4 and last I heard that was i386.

i386 is 386 processor. i486 is 486 processor.  586 is Pentium, I, II, and III I believe.  i686 starts with Pentium 4 to present 32 bit.

Either that or 686 starts with Pentium II I am foggy on that.

---

### Post by Skripka on 2009-09-11
> **jrusso2 said:**
> i386 is 386 processor. i486 is 486 processor.  586 is Pentium, I, II, and III I believe.  i686 starts with Pentium 4 to present 32 bit.

Either that or 686 starts with Pentium II I am foggy on that.

i686 started with Pentium II family CPUs (as well as "Pentium Pro")

---

### Post by sertse on 2009-09-11
> **YeOK said:**
>  Ubuntu / Debian will be thinking about it too.

A minor point, but Ubuntu and Debian's goals are different. Debian aims to be an universal OS that is able to run on anything. Ubuntu emphasises on end user desktops etc.

That might be another factor. Ubuntu would have to do it alone.

---

### Post by Exodist on 2009-09-11
> **goseph said:**
> Lots of distros offer optimized 686 builds. Why doesn't Ubuntu? Would it be horrendously complicated and lots of extra work to maintain two official builds?

Only diference in a i386 build and a i686 build is sometimes in multimedia where MMX and SSE extensions are turned on during the configure process prior to building the package.

Thus there is no difference what so ever in 95% of the packages.
The bottom like is all i386 and i686 packages are all 32bit.

Another main reason for stating i386 was to id the package as 32 -vs- older 286 machines that where mostly 16bit systems.

So for all practicality i386 and i686 are the same, so dont bash your head in on a naming theme.

-Exo

---

### Post by lisati on 2009-09-11
> **Skripka said:**
> Apart from the ongoing "How old a machine can I get _____ to install on?" contest?

Why anyone would even still have a 25 year old computer artifact in their keeping is beyond me.
I might blow the dust off the two Commodore 128s in my spare room one day, possibly even start them in CP/M mode, just to keep Mrs Lisati from giving them away or tossing them out.

> **SunnyRabbiera said:**
> I thought the x86 was kinda catchall anyway, as the kernel is 32bit anyway.

Kind of.... but Linux got under way on '386-based systems.

---

