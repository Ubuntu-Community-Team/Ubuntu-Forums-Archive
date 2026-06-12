---
title: "FreeBSD"
date: 2010-07-24
forum: The Cafe
---

### Post by MattBD on 2010-07-24
Today I saw that FreeBSD 8.1 has been released, so I'm downloading a copy and for the first time ever, I plan to try installing it on physical hardware (I have an older machine that's currently running Slackware 13, and even if I stick with Slackware I'd want to upgrade to 13.1 so it an ideal opportunity to try FreeBSD for a bit). I've tried it in Virtualbox before but it tends to be rather dodgy in that.

Anyone else tried it? What do you think of it?

---

### Post by Shining Arcanine on 2010-07-24
FreeBSD has a commandline installer. That is not "do it yourself" so much as it is "we do not make decisions for you". Linux From Scratch is more representative of the "do it yourself" experience:

[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

Anyway, FreeBSD is capable of running software designed for UNIX. Software that takes advantage of Linux specific features (e.g. SystemD) will not run on it. PC-BSD is an option for people that want a graphical installer:

[http://www.pcbsd.org/](http://www.pcbsd.org/)

---

### Post by MattBD on 2010-07-24
> **Shining Arcanine said:**
> FreeBSD has a commandline installer. That is not "do it yourself" so much as it is "we do not make decisions for you". Linux From Scratch is more representative of the "do it yourself" experience
Linux from Scratch is awesome - I tried it earlier this year and managed to get through it, although I managed to screw up the Grub install somehow and couldn't get it right. But I should never, ever have tried it on a laptop that needed to connect to the Internet via wifi. I'll wait till I can buy an old machine someone's throwing out or selling on cheap before I try it again.

---

### Post by Sporkman on 2010-07-24
> **MattBD said:**
> Linux from Scratch is awesome - I tried it earlier this year and managed to get through it

Nice - good job! I've looked through the manual, it's pretty long and involved...

BTW freebsd 8.0 32bit (at least just the base cli system) works in VirtualBox - the 64bit version seems to crap out though...

---

### Post by mickie.kext on 2010-07-24
I guess I'll try PC-BSD again. Hope they fixed the locking and freezing issues.

PS: I just now saw that is in fact FreeBSD thread. FreeBSD doesn't have that issue. BTW, PC-BSD 8.1 is also out.

---

### Post by MattBD on 2010-07-24
> **Sporkman said:**
> Nice - good job! I've looked through the manual, it's pretty long and involved...

Nah, it's not too bad. I used the live CD, and for the most part I was just copying and pasting commands. But when I had to go back to it after running out of time the previous day, it was a bit of a pain to restart it. Would have been better if I could have used a desktop and left one of the longer things to compile overnight.

---

### Post by Shining Arcanine on 2010-07-24
> **mickie.kext said:**
> I guess I'll try PC-BSD again. Hope they fixed the locking and freezing issues.

PS: I just now saw that is in fact FreeBSD thread. FreeBSD doesn't have that issue. BTW, PC-BSD 8.1 is also out.

Locking and freezing issues could indicate hardware problems. Are you sure that your hardware is sound?

---

### Post by mickie.kext on 2010-07-24
> **Shining Arcanine said:**
> Locking and freezing issues could indicate hardware problems. Are you sure that your hardware is sound?

No problems with Linux. No problems with FreeBSD. Only PC-BSD. It maybe has to do with the way how PC-BSD is configured. With FreeBSD, I do it myself. PC-BSD has some KDE integration hacks and PBI is crap. Also, kernel is probably compiled with different flags. I didn't bothered to go into detail, but I think it is one of those three that makes problem. If I poked PC-BSD around to see what is the problem, I would end up having FreeBSD :lolflag:

So I just installed FreeBSD.

---

### Post by nerdopolis on 2010-07-28
You made me curious: Whats wrong with PBI's? Do they not work or something?

(I wanted to try them out, but could not get PC-BSD installed from my half defective CD drive...)

---

### Post by RiceMonster on 2010-07-28
I didn't even notice. I may try it out. FreeBSD is fun to mess around with, but I prefer Linux overall, especially on the desktop. It's mainly because I don't like ports and pkg_add. I find it a little tedious. It is a good, and very reliable server OS though.

---

### Post by mickie.kext on 2010-07-28
> **nerdopolis said:**
> You made me curious: Whats wrong with PBI's? Do they not work or something?

(I wanted to try them out, but could not get PC-BSD installed from my half defective CD drive...)

PBIs put all libraries along with program, so there are no shared libraries. If for example 10 programs use same library and all 10 are installed by PBI, then you will have 10 duplicate libraries installed, consuming space and maybe creating runtime conflicts when you start those programs at once. That might explain frezing and locking up that I had problems with. PBI is brain dead design. 

For example, Firefox PBI is 70 megs, that's just crazy.

---

### Post by RiceMonster on 2010-07-28
> **mickie.kext said:**
> PBIs put all libraries along with program, so there are no shared libraries. If for example 10 programs use same library and all 10 are installed by PBI, then you will have 10 duplicate libraries installed, consuming space and maybe creating runtime conflicts when you start those programs at once. That might explain frezing and locking up that I had problems with. PBI is brain dead design. 

Just wondering because I have never used PC-BSD, would it not simply overwrite the other library if they are using the same one?

For example, if the package was going to install libstuff at /usr/local/lib/libstuff.so and another PBI had already installed it there, would it make a separated copy, or would it just overwrite that file with the same contents?

---

### Post by handy on 2010-07-28
I used PC-BSD for a few months maybe as long ago as a couple of years ago. It was the nicest KDE desktop I have ever used. (& I don't really like KDE) It was also perfectly reliable.

I also used FreeNAS, the FreeBSD based NAS system for well over a year with NEVER even a hint of a hiccup.

I think that FreeBSD is a superb option for anyone that is not caught by any of the software limitations of the system.

---

### Post by mickie.kext on 2010-07-28
> **RiceMonster said:**
> Just wondering because I have never used PC-BSD, would it not simply overwrite the other library if they are using the same one?

For example, if the package was going to install libstuff at /usr/local/lib/libstuff.so and another PBI had already installed it there, would it make a separated copy, or would it just overwrite that file with the same contents?

If I remember corectly, it doesn't install in /usr. It installs in /Programs/NameOfTheProgram and since every program has its directory, then libstuff.so goes with every program in its directory. So, a separate copy of library, in different directories.

---

### Post by RiceMonster on 2010-07-28
> **mickie.kext said:**
> If I remember corectly, it doesn't install in /usr. It installs in /Programs/NameOfTheProgram and since every program has its directory, then libstuff.so goes with every program in its directory. So, a separate copy of library, in different directories.

If that's the case, that is indeed brain dead design.

---

### Post by nerdopolis on 2010-07-28
Oh... The idea of PBI's are cool though.

If you ask me the lack  of an easy universal installer (for both the packager and the user) is a  pretty top reason on whats keeping the Linux desktop usage share  down... or at least I think so anyway...

---

### Post by phrostbyte on 2010-07-28
You are very lucky if you are able to get a *BSD to work right on physical hardware. Unfortunately, the *BSDs are way behind Linux in terms of hardware drivers.

---

### Post by mips on 2010-07-29
> **phrostbyte said:**
> You are very lucky if you are able to get a *BSD to work right on physical hardware. Unfortunately, the *BSDs are way behind Linux in terms of hardware drivers.

That's a load of nonsense. I have never had issued with *BSDs working on my desktops or laptops.

---

### Post by Bachstelze on 2010-07-29
> **mips said:**
> That's a load of nonsense. I have never had issued with *BSDs working on my desktops or laptops.

Ditto.

---

### Post by szymon_g on 2010-07-29
> **mips said:**
> That's a load of nonsense. I have never had issued with *BSDs working on my desktops or laptops.

yeah. we all know that fbsd supports as many hardware as linux 

;)

but seriously- FreeBSD is really nice system, in some ways superior to Linux (well... apart from drivers)- but, unfortunatly, its package manegment sucks (both: ports and binary packages)- each of them could be much better :|

---

### Post by Bachstelze on 2010-07-29
> **szymon_g said:**
> but, unfortunatly, its package manegment sucks

A FreeBSD user would tell you Apt sucks.  I've had a lot more problems with Apt than with FBSD's ports, they are more KISS-compliant.

---

### Post by phrostbyte on 2010-07-29
> **mips said:**
> That's a load of nonsense. I have never had issued with *BSDs working on my desktops or laptops.

You != everyone.

---

### Post by Legendary_Bibo on 2010-07-29
> **Bachstelze said:**
> A FreeBSD user would tell you Apt sucks.  I've had a lot more problems with Apt than with FBSD's ports, they are more KISS-compliant.

such as?

---

### Post by DeadSuperHero on 2010-07-29
> **Legendary_Bibo said:**
> such as?

Mwah. ;)

If only someone would make a solid GUI frontend that worked like Synaptic, but for Ports...

---

### Post by jerenept on 2010-07-29
Sulphur

or sulfur, for you all.

that is the frontend on sabayon, which uses ports.

---

### Post by Dustin2128 on 2010-07-29
> **phrostbyte said:**
> You are very lucky if you are able to get a *BSD to work right on physical hardware. Unfortunately, the *BSDs are way behind Linux in terms of hardware drivers.

Oh come on, does linux run on a toaster? [NetBSD does]("http://www.embeddedarm.com/software/arm-netbsd-toaster.php").

---

### Post by jerenept on 2010-07-29
i think so.... not sure [DuckDuckGo-Linux toaster]("http://www.duckduckgo.com/?q=linux%20toaster")

BTW... FreeBSD is NOT linux. I know.

---

### Post by themarker0 on 2010-07-29
Oh my dad helped me with that! My first taste of BSD. Its great. PC-BSD itself is not the greatest yet... I've had my issues. Though really, you cannot go wrong with FreeBSD as a server. I can't say an OS that stacks up to a BSD based server.

---

### Post by phrostbyte on 2010-07-29
> **Dustin2128 said:**
> Oh come on, does linux run on a toaster? [NetBSD does]("http://www.embeddedarm.com/software/arm-netbsd-toaster.php").

The manufacturer of the computer running on that toaster, seems to think so. In fact, they [recommend using Linux]("http://www.embeddedarm.com/products/board-detail.php?product=TS-7200#").

I wouldn't underestimate Linux in this matter. I wouldn't be surprised if it supports more hardware architectures then NetBSD. :D

Don't get me wrong, *BSD is cute and all. It's just way behind Linux on so many levels, IMO of course. Linux development is sponsored heavily by commercial entities, it's just more actively developed.

---

### Post by DeadSuperHero on 2010-07-29
> **phrostbyte said:**
> 
Linux development is sponsored heavily by commercial entities, it's just more actively developed.

And fragmented.

---

### Post by phrostbyte on 2010-07-30
> **DeadSuperHero said:**
> And fragmented.

You want to talk about fragmentation? There is something like four different independently developed *BSD kernels. :p

On top of this, the BSD license ensures and encourages forks even in directions the Linux kernel can never go (closed source).

---

### Post by Bachstelze on 2010-07-30
> **phrostbyte said:**
> You want to talk about fragmentation? There is something like four different independently developed *BSD kernels. :p

s/kernels/OSes/

You're comparing apples and oranges.  How many OSes that use the Linux kernel?

> **phrostbyte said:**
> 
On top of this, the BSD license ensures and encourages forks even in directions the Linux kernel can never go (**anything and everything besides GPL**).

Fixed that for you.  Typical GPL zaelot hypocrisy: they're always ranting about how the BSD license allow use of code in closed source projects, but they never mention that it also allows use of code in other open source projects, and that they're always the first to take advantage of it and use BSD code.

---

### Post by DeadSuperHero on 2010-07-30
> **phrostbyte said:**
> You want to talk about fragmentation? There is something like four different independently developed *BSD kernels. :p

On top of this, the BSD license ensures and encourages forks even in directions the Linux kernel can never go (closed source).

36 FreeBSD-based distributions that are all binary compatibile with one another.

Thousands of Linux distributions that are a packaging nightmare.

Why? Because BSD is more than a kernel, and actually has specific standards to it. (Not to mention, if you look at how insanely active their development community and Ports maintainers are, you can really get a feel of FOSS working as an entity)

---

### Post by phrostbyte on 2010-07-30
> **Bachstelze said:**
> 
Fixed that for you.  Typical GPL zaelot hypocrisy: they're always ranting about how the BSD license allow use of code in closed source projects, but they never mention that it also allows use of code in other open source projects, and that they're always the first to take advantage of it and use BSD code.

That's exactly why the BSD license is so terrible - ANYONE can use BSD code and contribute nothing back.

---

### Post by phrostbyte on 2010-07-30
> **DeadSuperHero said:**
> 36 FreeBSD-based distributions that are all binary compatibile with one another.

Thousands of Linux distributions that are a packaging nightmare.

Why? Because BSD is more than a kernel, and actually has specific standards to it. (Not to mention, if you look at how insanely active their development community and Ports maintainers are, you can really get a feel of FOSS working as an entity)

Are you talking about POSIX? I don't know of any *BSD specific standards.

---

### Post by DeadSuperHero on 2010-07-30
> **phrostbyte said:**
> Are you talking about POSIX? I don't know of any *BSD specific standards.

Standard library versions, standard binary compatibility in applications. It's designed as a complete system, with goals of upwards of 5 years backwards compatibility per each stable release. 

What you also overlook is the phenomenon in which companies actually contribute back to the FreeBSD project for the sake of practicality. It's hard to keep a proprietary product when upstream makes huge sweeping changes. Just look at Juniper Labs.

---

### Post by Bachstelze on 2010-07-31
> **phrostbyte said:**
> That's exactly why the BSD license is so terrible - ANYONE can use BSD code and contribute nothing back.

Anyone *can*, but the vast majority of people who *do* are GPL projects developers.  Apple and other companies do contribute back, GPL projects like the Linux kernel just wrap the GPL around the code and do not contribute back.

The BSD license is like UNIX: it doesn't keep you from doing bad things, because that would also keep you from doing good things.  It just takes a lot of maturity and good will, when given a powerful tool, to use it for good and not for evil.  Apparently some GPL people are lacking a lot in that regard.

---

