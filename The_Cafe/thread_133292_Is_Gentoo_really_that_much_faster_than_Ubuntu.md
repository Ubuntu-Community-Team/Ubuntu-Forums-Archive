---
title: "Is Gentoo really that much faster than Ubuntu?"
date: 2006-02-19
forum: The Cafe
---

### Post by Protex on 2006-02-19
Hey there,

I've been contemplating making the change to Gentoo Linux, mainly because I heard about it's speed.

Can anyone confirm that it is faster than Ubuntu?

---

### Post by Jedeye on 2006-02-19
speed can greatly depend on the window manager that you use with each distro as far as specifics I have no idea

---

### Post by briancurtin on 2006-02-19
theres been a thread about this

i use Arch right now, and its definitely faster. ive never actually used gentoo, but Arch is supposed to be similar in speed for several reasons.

---

### Post by LordHunter317 on 2006-02-19
No, it isn't.  It's placebo effect.  Anyone who tells you otherwise understands nothing about compilers, save for a few small, corner cases.  And Ubuntu ships optimized packages for nearly all of those cases, as well.

---

### Post by midwinter on 2006-02-19
Sure, I use Arch myself and it's a good deal faster.  Gentoo is similarly fast (but I prefer Arch).

I believe this is due to all the excess services and patched packages that Ubuntu provides by default.. as opposed to any real difference in compiling though.

---

### Post by Stormy Eyes on 2006-02-19
[QUOTE=Protex]I've been contemplating making the change to Gentoo Linux, mainly because I heard about it's speed.[/QUOTE]

What you gain from Gentoo isn't speed, but tighter control over your system than is provided by Ubuntu and other distros. With Gentoo, *you* determine the configuration of your system. The only daemons running are those you install yourself.

---

### Post by CaptainTux on 2006-02-19
[QUOTE=Stormy Eyes]What you gain from Gentoo isn't speed, but tighter control over your system than is provided by Ubuntu and other distros. With Gentoo, *you* determine the configuration of your system. The only daemons running are those you install yourself.[/QUOTE]
Hence why a gentoo linux system is usually faster than most other distros.  

Look, at the end of the day, gentoo is whatever you want it to be.  It can be as fast, bloated, stable, or bleeding edge as you want more-so than any other distro.  It is also not for the feint of heart to install and configure, but once you get there, emerge is simple amazing.

It is a control freaks dream distro...pretty much one step shy of rolling your own distro.

---

### Post by Arc Owner on 2006-02-19
I'm actually in the process of installing gentoo right now, mostly for the learning experience. 

Gentoo's speed increase is generally too small to be noticed, and what speed increase there is, is taken away by the LONG compile times. At the end of the day, the great thing about gentoo isn't that it might give you a slight increase of speed by configuring it for your system, but the fact that there are so many options with it and that it is extremely customizable. If customization is not what you want, and you don't have any need or want to learn more about linux, then gentoo is definitely not for you.

---

### Post by LordHunter317 on 2006-02-19
> **midwinter]Sure, I use Arch myself and it's a good deal faster.  Gentoo is similarly fast (but I prefer Arch).[/quote]No, it isn't.  Provide benchmarks.  You'll be shocked.

> I believe this is due to all the excess servicesUbuntu doesn't provide any excessive services OOB.

 > and patched packages that Ubuntu provides by default..Patches don't negatively effect performance, *per se*.  They can in fact, improve it.

[quote=Stormy Eyes]What you gain from Gentoo isn't speed, but tighter control over your system than is provided by Ubuntu and other distros. [/quote]No, you actually have less.  Portage has infinitely less control than any binary package system said:**
> I'm actually in the process of installing gentoo right now, mostly for the learning experience. All you'll learn is compiling is a pain.

---

### Post by midwinter on 2006-02-20
[QUOTE=LordHunter317]No, it isn't.  Provide benchmarks.  You'll be shocked.

Ubuntu doesn't provide any excessive services OOB.

 Patches don't negatively effect performance, *per se*.  They can in fact, improve it.

No, you actually have less.  Portage has infinitely less control than any binary package system; it cannot do things they can, nor does it do all the things it ought to.  It's dependency checking is inadequate (-D should be default), it doesn't enforce dependences on erasure, it has to ignore USE flags on binary packages.

All you'll learn is compiling is a pain.[/QUOTE]

In my experience Gentoo/Arch are much faster than Ubuntu.   However, I say this as someone who has used the default Ubuntu install vs the default install of Arch and Gentoo (ie. practically nothing) built up to approx the same point (Gnome etc).  I'm not going to get analytical with this because I really don't care all that much. 

I'd love to build up a Ubuntu desktop from a server install and judge for myself, as I think this would be the fairest way, but (and this brings me to the 'tighter control' point), try doing a server install of Ubuntu, installing a few things and then upgrading to the next version cleanly... not gonna happen. Because you don't have a *-package.  Not much room for 'control' there.  Stuck with the packages you're given. 

And yeah, patched packages don't necessarily slow down or break things but that default firefox in 5.10 is pretty borked so I don't have much faith in these things. 

I agree though, compiling can be a pain.  Arch is the way to go imo.

---

### Post by LordHunter317 on 2006-02-20
[QUOTE=midwinter]In my experience Gentoo/Arch are much faster than Ubuntu.[/quote]**And that's not proof.**  Benchmarks are proof.  I shouldn't have to repeat that.

> I'd love to build up a Ubuntu desktop from a server install and judge for myself, as I think this would be the fairest way, but (and this brings me to the 'tighter control' point), try doing a server install of Ubuntu, installing a few things and then upgrading to the next version cleanly... not gonna happen. Yes, it happens all the time.  I've had the same servers running Debian sid for *years*.  From early woody all the way to today.  And I haven't to reinstall or ever run into a program that prevented me from upgrading more than temporarily.

[edit]I completely messed that sentence up. My apologies.

> Because you don't have a *-package.You don't need one.  That's what apt-get upgrade and apt-get dist-upgrade are for.  You don't need one anywhere.  I can't even fathom what would make you believe you do, or that you cannot install software at an arbitrary point, or upgrade your installed software at an arbitrary point.

>  Not much room for 'control' there.  Stuck with the packages you're given.No, you're not.  You don't even understand how to use APT or what it can do, and you expect use to believe you?  Go read some first.  Then come back.  Your ignorance here is overwhelming.

> And yeah, patched packages don't necessarily slow down or break things but that default firefox in 5.10 is pretty borked so I don't have much faith in these things. Most packages by most distributors of anything significant are heavily, heavily patched.  Ubuntu is hardly unique in that regard.  Even Gentoo does it.

---

### Post by Arc Owner on 2006-02-20
[QUOTE=LordHunter317]No, it isn't.  Provide benchmarks.  You'll be shocked.

Ubuntu doesn't provide any excessive services OOB.

 Patches don't negatively effect performance, *per se*.  They can in fact, improve it.

No, you actually have less.  Portage has infinitely less control than any binary package system; it cannot do things they can, nor does it do all the things it ought to.  It's dependency checking is inadequate (-D should be default), it doesn't enforce dependences on erasure, it has to ignore USE flags on binary packages.

All you'll learn is compiling is a pain.[/QUOTE]

Gentoo is actually one of the harder distro's to install, and requires a lot of dedication and patience for the install. I really have learned a lot, more than any other distro, from the install.

---

### Post by LordHunter317 on 2006-02-20
What, specifically then, have you learned?

---

### Post by briancurtin on 2006-02-20
of course this isnt "proof" but just another user testimonial: arch is faster than ubuntu. theres no "placebo effect" here, shit just loads much, much faster and things are much more responsive. that is just one of the many advantages to a system like arch, but there are many others.

ubuntu is great for some, good for others. just face it, people have different results on different machines. im running a P4-HT 3.2 with a gig of memory, and it flys on Arch. on ubuntu with the i686 kernel it was alright, but was lacking to me. its noticeable, but is by no means a benchmark, but its not like what i am saying is complete garbage that has no value or something.

---

### Post by LordHunter317 on 2006-02-20
[QUOTE=briancurtin]of course this isnt "proof" but just another user testimonial: arch is faster than ubuntu. theres no "placebo effect" here, shit just loads much, much faster and things are much more responsive. that is just one of the many advantages to a system like arch, but there are many others.[/quote]**As I've said, benchmark it.**  I'm sure you'll be suprised.

---

### Post by nemik on 2006-02-20
i certainly learned a lot from my attempt at a gentoo install a LONG time ago. but it taught me more about myself than about linux which is, IMO, a much more important lesson.

i learned that whatever speed there was to gain from such an install/config would be nothing compared to the stress on my health and frustration incurred by me at having oh so many things go wrong with the install.
i also learned that while i love linux, i do not care so much how it works at its roots. i have other interests that i want to start on as soon as possible without so much work in other things. ubuntu does this very well. it lets me concentrate on the things i want to do and not waste a lot of time getting there.

nuts to gentoo i say. then again, there are some people who like getting raped while installing a distro.

---

### Post by briancurtin on 2006-02-20
[QUOTE=LordHunter317]**As I've said, benchmark it.**  I'm sure you'll be suprised.[/QUOTE]
i wont be surprised at all, i know how my system runs, and i can count. cut it with this benchmark stuff too, you can just say you are a ubuntu fanboy and we would be alright with it. ubuntu is a good distribution, dont get me wrong, but its not competing with some of the others.

---

### Post by briancurtin on 2006-02-20
also, while i realize the absolute importance of benchmarks in a debate on an internet forum, just step back and look at the fact that Arch, one of the given examples, is an i686 optimized distro. when running an i686 machine, it may occur to you that an i686 optimized distribution is more than likely faster than a non-optimized one. of course that isnt a benchmark, but just take that, and then what users are saying is their experience, and give it some sort of value.

---

### Post by LordHunter317 on 2006-02-20
[QUOTE=briancurtin]i wont be surprised at all, i know how my system runs, and i can count. cut it with this benchmark stuff too, you can just say you are a ubuntu fanboy and we would be alright with it.[/quote]Seeing as I don't have Ubuntu running anywhere except one virtual machine (with it's disks removed for space, hah) I think you have no clue what you're talking about.

My basis for the consideration is that most of what you're seeing is logically explainable (e.g., starting less services at bootup) or is clearly placebo effect.

>  ubuntu is a good distribution, dont get me wrong, but its not competing with some of the others.**You have no proof of that, until you provide benchmarks.**

---

### Post by briancurtin on 2006-02-20
what the **** do i look like here, a god damned research lab? ill provide you benchmarks with a ******* stopwatch...but what does that prove? nothing. thats nothing, at all.

---

### Post by briancurtin on 2006-02-20
also, id like to mention this much: LordHunter317 - you have no proof that Arch is not faster, until you provide benchmarks.

---

### Post by LordHunter317 on 2006-02-20
It proves plently.  Proper testing proves that *suprise* the same code running on the same system produces statistically identical results.

And, that any differences can be deterministically accounted for.

---

### Post by briancurtin on 2006-02-20
wheres the benchmark for that?

---

### Post by LordHunter317 on 2006-02-20
[QUOTE=briancurtin]also, id like to mention this much: LordHunter317 - you have no proof that Arch is not faster, until you provide benchmarks.[/QUOTE]The onus is not on me to provide it.  I never made any claims about it's speed, just that you cannot say it's faster until you provide benchmarks.

---

### Post by briancurtin on 2006-02-20
...but if you are going to say i cant prove it, i could just as well say that you cant prove it otherwise. by saying that Arch is not faster, you in turn believe that ubuntu is either equal or that it is faster, not picking one of those but it is one of them by deduction. prove it.

---

### Post by LordHunter317 on 2006-02-20
[QUOTE=briancurtin]...but if you are going to say i cant prove it, i could just as well say that you cant prove it otherwise.[/quote]Right, but that doesn't matter.  I'm not saying it faster, I'm not saying it's not.  What I am saying is that anything short of a benchmark **says nothing about it's speed.**


> by saying that Arch is not faster, you in turn believe that it is either equal or that it is faster,No, that's contradictory.  If it isn't faster, it can be at most equal, or slower.  a !> b <=> a <= b.  Not a >= b, which is what you stated.

>  not picking one of those but it is one of them by deduction. prove it.There's no onus on me to prove anything.  I couldn't care one way or the less.  What I care about is people spouting crap about, "Distro a is faster than distro b" without any support for it.

---

### Post by briancurtin on 2006-02-20
the second point that you covered was edited while you were posting, my apology on not stating that "it" was really supposed to be "ubuntu"

---

### Post by LordHunter317 on 2006-02-20
Very well then.  My correction is meaningless.

---

### Post by prattrs on 2006-02-20
LordHunter:

I wanted to try and speak to some of your questions, even though I'm not the OP.  As a bit of background, I've run Gentoo and Ubuntu both for a bit, but I'm running Gentoo right now.

What you learn with Gentoo: 

You get a basic sense of how a linux system is laid out, what fstab is, how grub.conf (menu.lst in debian/Ubuntu IIRC) works, how to use fdisk, how to compile your kernel, configure X, add users, where your system logs are, what a cron daemon is...  you know, all those things we take for granted after a while?  I think the only way to dismiss the value of learning these things is to not realize what a mystery they are to a linux newbie.

Why people like it:

-The init system: It's nice to be able to say /etc/init.d/service_name restart.  I'm led to believe that this scheme is uncommon in linux, but it's very convenient.

-The ease with which you can re-compile your kernel: While I was using Ubuntu, I was frustrated when I wanted to re-compile my kernel with PREEMPT and a few other options in it.  Yes, I RTFM'd on the wiki, but from 10,000 ft the directions look like a PITA compared to Gentoo - I think mostly because the sources aren't there by default, and the directions I read seemed to imply that making a deb package out of your new kernel was the way to go, which seemed annoying to me at the time.  YMMV.

-Gentoo has niceties, to include:
  gentoo-syntax for editors (for config files and such)
  a nice console environment with FB and so forth, very easily
  emul-linux-x86-java for things like open-office
  java-config (I like it better than alternatives-config, YMMV)
  it will update cedega for me

I'm sure there are other things, and to each their own, but I wanted to put in a response to defend my beloved distro :)

BTW, I don't think anyone in the Gentoo community cares to much about what instructions the compiler emits, or is deluded into thinking it makes much of a difference.  For the most part, we like the control, the convenience and the niceities.  And the community. YMMV :)

Sandy

---

### Post by LordHunter317 on 2006-02-20
[QUOTE=prattrs]You get a basic sense of how a linux system is laid out, what fstab is, how grub.conf (menu.lst in debian/Ubuntu IIRC) works, how to use fdisk, how to compile your kernel, configure X, add users, where your system logs are, what a cron daemon is...  you know, all those things we take for granted after a while? I think the only way to dismiss the value of learning these things is to not realize what a mystery they are to a linux newbie.[/quote]Frankly, coming from the era where knowing all that was required, I simply don't need to know it on a desktop, that often.

And on a server?  Well, I expect people to know it, and most of that stuff is documented.  I'm not convinced Gentoo is the best way to learn such things, but it is a way.

> -The init system: It's nice to be able to say /etc/init.d/service_name restart.  I'm led to believe that this scheme is uncommon in linux, but it's very convenient.It's not only common, it's standard according to LSB.

> -The ease with which you can re-compile your kernel: While I was using Ubuntu, I was frustrated when I wanted to re-compile my kernel with PREEMPT and a few other options in it.It's no more difficult than any other OS, unless you want a package.  And even then, make-kpkg isn't impossible, after you use it once.

I'm pretty anti-kernel recompiling anyway, because it's generally not needed.

>   emul-linux-x86-java for things like open-officeFor AMD64?  Ubuntu has that.

> BTW, I don't think anyone in the Gentoo community cares to much about what instructions the compiler emits, or is deluded into thinking it makes much of a difference.Ha.  Plently of people are.  Maybe not a majority, but a large minority, no doubt.

---

### Post by prattrs on 2006-02-20
> Frankly, coming from the era where knowing all that was required, I simply don't need to know it on a desktop, that often.

And on a server? Well, I expect people to know it, and most of that stuff is documented. I'm not convinced Gentoo is the best way to learn such things, but it is a way.


Well, I don't think good ole days are in the past, sadly =/

I'm simply asserting that lots of peole have credited Gentoo with teaching them alot about linux, myself included.  In that regard, I will certainly say that there's no particular reason to think that Debian is any better to learn on.  BSD or Solaris, maybe...

Re: init system
> It's not only common, it's standard according to LSB.

You're probably correct, which shows how little I do that sort of thing on Ubuntu, which reinforces the above point about learning.

Re: x86 emulation for AMD64
> For AMD64? Ubuntu has that.

This was not my experience with Ubuntu.  Please cite.

As far as the kernel goes, I'll take your word for it.

---

### Post by LordHunter317 on 2006-02-20
If you're reffering specifically to java, then no such beast exists.  You need to install a 32-bit JRE manually.  However, most AMD64 libs are packaged.

---

### Post by Bandit on 2006-02-20
Many of my friends from the SuSE forums run Gentoo also. Many of the actually prefere portage. Not really sure how much time they have spent using Ubuntu recently to make a accurate statement on which can be faster.
Personelly I like Ubuntu and Kubuntu both because they don't install as much garbage as other distros.
I don't bother with Gentoo because why the hell should I spend a week compiling Gnome when the Ubuntu team do a damn great job of it.
As far as speed goes, most (90%) of the apts would get compiled by the Ubuntu team exactly the way I would compile them at home. Now the only real speed increase over all with the system would have to do with the Kernel settings. I say just build your own kernel like I have, compile your own multimedia apts and manually choose the system services you want running then you should have a fully optimized system without the hours of staring at the CLI waiting for Gentoo to come to life.
IMHO,
Joey

---

### Post by bjweeks on 2006-02-20
Lordhunter I normally agree with you but emerge is more powerful apt-get. USE flags are the best thing about gentoo no binary distro can offer what USE flags can. About -D many users don't use or recommend  it. Gentoo has less shit installed no cups, no hp printer service, etc. Can I see a speen differince in gnome, no.

---

### Post by egodust on 2006-02-20
Gentoo is faster default install, thats because gentoo has been developed to be fastest, here is a bunch of stuff it does and most of it isn't special to Gentoo:

1. default kernel compiles with the CK patchset, which improves system responsiveness even under heavy load

2. during installation you are encouraged to setup hdparm settings properly, not only including DMA but IO and such

3. hardware detection is non existant, you are encouraged to compile the kernel and remove all the things you don't need and then auto load all the modules your hardware needs yourself.

4. during installation you are encouraged to explore different partitions and settings, e.g. ext3 with dir_index, full logging and removing root partition reservations, etc..

5. packages are compiled for target CPU, this only really has a impact on glibc, X, kernel, gnome, etc..

6. prelink, all your binaries are prelinked to load faster: i.e. system relocation is done once and then it's trivial to load a binary without fixing up all the relative addresses 

Here is what I do when I install Ubuntu:

1. Remove a crapload of packages I'll never use, including python packages, bluetooth, laptop stuff, and so on (debfoster is your friend)

2. setup hdparm for my disks, change any ext3 settings if required (using jfs atm)

3. recompile the kernel with CK patchset and remove all the boot services I don't need, including hotplug and then load all the modules for my hardware

4. install prelink :)

Ubuntu's packages are optimised enough with -O settings that -march and -mcpu won't have that much difference, the only place where it'll help is with faster mem copy routines using CPU instructions that are faster, but thats the price you pay.

Gentoo's flaws are to do with compiling everything, yes there are -bin options but then you are better off with another distro all together, here are some really BAD points about Gentoo:

1. emerge --sync is unsafe! portage sync has mirrors but no signatures, MD5SUMs are useless without signatures!

2. portage is only JUST NOW getting _it_ with GPG signatures on everything, this is yet to be rolled out, even after all this time.. MD5SUMS just provide a way of detecting changes, but they can be overrwritten with a bad mirror, you can't trust the mirror to provide you with untamped ebuilds + MD5SUMS..

In the end Ubuntu wins because you get a nice desktop system with all the power of a normal Linux distro with binary package system of APT and you can apply most of Gentoo's techniques yourself.

You'll have to compile the kernel, Mplayer and so on for Ubuntu anyway, but least you don't _have_ to.

As for Arch Linux, I don't think there are any signature checks on the packages, not that I saw anyway..

---

### Post by SuperDiscoMachine V.5.7-3 on 2006-02-20
[QUOTE=egodust]Gentoo is faster default install, thats because gentoo has been developed to be fastest, 
[/QUOTE]
No, it hasn't. But if I'm wrong, maybe you could provide a document where drobins states that this was the primary purpose of gentoo.

[QUOTE=egodust]
here is a bunch of stuff it does and most of it isn't special to Gentoo:

1. default kernel compiles with the CK patchset, which improves system responsiveness even under heavy load
[/QUOTE]
There's a default kernel now in gentoo? I highly doubt this.

[QUOTE=egodust]
2. during installation you are encouraged to setup hdparm settings properly, not only including DMA but IO and such
[/QUOTE]
Are you? By whom?
I never was encouraged to do anything when installing gentoo. And how is tweaking hdparm on gentoo different from tweaking it on ubuntu?

[QUOTE=egodust]
3. hardware detection is non existant, you are encouraged to compile the kernel and remove all the things you don't need and then auto load all the modules your hardware needs yourself.
[/QUOTE]
Not true, at least if genkernel is still around. And what about the new gentoo installer?

[QUOTE=egodust]
4. during installation you are encouraged to explore different partitions and settings, e.g. ext3 with dir_index, full logging and removing root partition reservations, etc..
[/QUOTE]
Again, who on earth encourages you to do so and how is this different from doing the same thing on ubuntu?

[QUOTE=egodust]
5. packages are compiled for target CPU, this only really has a impact on glibc, X, kernel, gnome, etc..
[/QUOTE]
The impact is minimal at best and looking at all the broken CFLAGS of many gentoo ricers, binaries may well be slower even though people tweaked their compile settings.

[QUOTE=egodust]
6. prelink, all your binaries are prelinked to load faster: i.e. system relocation is done once and then it's trivial to load a binary without fixing up all the relative addresses 
[/QUOTE]
Again, I highly doubt that gentoo now defaults to prelink. If it doesn't, what's the difference between installin and using prelink on gentoo and doing the same on ubuntu?

[QUOTE=egodust]
Here is what I do when I install Ubuntu:

1. Remove a crapload of packages I'll never use, including python packages, bluetooth, laptop stuff, and so on (debfoster is your friend)
[/quote]
Wouldn't it be saner to simply not install them in the first place?


[QUOTE=egodust]
You'll have to compile the kernel, Mplayer and so on for Ubuntu anyway, but least you don't _have_ to.[/QUOTE]
Huh? You have to but you don't have to?
Aha?
And why on earth should I recompile mplayer or my kernel?

---

### Post by bjweeks on 2006-02-20
[QUOTE=egodust]Gentoo is faster default install, thats because gentoo has been developed to be fastest, here is a bunch of stuff it does and most of it isn't special to Gentoo:

1. default kernel compiles with the CK patchset, which improves system responsiveness even under heavy load

2. during installation you are encouraged to setup hdparm settings properly, not only including DMA but IO and such

3. hardware detection is non existant, you are encouraged to compile the kernel and remove all the things you don't need and then auto load all the modules your hardware needs yourself.

4. during installation you are encouraged to explore different partitions and settings, e.g. ext3 with dir_index, full logging and removing root partition reservations, etc..

5. packages are compiled for target CPU, this only really has a impact on glibc, X, kernel, gnome, etc..

6. prelink, all your binaries are prelinked to load faster: i.e. system relocation is done once and then it's trivial to load a binary without fixing up all the relative addresses 

Here is what I do when I install Ubuntu:

1. Remove a crapload of packages I'll never use, including python packages, bluetooth, laptop stuff, and so on (debfoster is your friend)

2. setup hdparm for my disks, change any ext3 settings if required (using jfs atm)

3. recompile the kernel with CK patchset and remove all the boot services I don't need, including hotplug and then load all the modules for my hardware

4. install prelink :)

Ubuntu's packages are optimised enough with -O settings that -march and -mcpu won't have that much difference, the only place where it'll help is with faster mem copy routines using CPU instructions that are faster, but thats the price you pay.

Gentoo's flaws are to do with compiling everything, yes there are -bin options but then you are better off with another distro all together, here are some really BAD points about Gentoo:

1. emerge --sync is unsafe! portage sync has mirrors but no signatures, MD5SUMs are useless without signatures!

2. portage is only JUST NOW getting _it_ with GPG signatures on everything, this is yet to be rolled out, even after all this time.. MD5SUMS just provide a way of detecting changes, but they can be overrwritten with a bad mirror, you can't trust the mirror to provide you with untamped ebuilds + MD5SUMS..

In the end Ubuntu wins because you get a nice desktop system with all the power of a normal Linux distro with binary package system of APT and you can apply most of Gentoo's techniques yourself.

You'll have to compile the kernel, Mplayer and so on for Ubuntu anyway, but least you don't _have_ to.

As for Arch Linux, I don't think there are any signature checks on the packages, not that I saw anyway..[/QUOTE]

1. No, gentoo-sources is the recommended kernel.

2. No, your not.

3. You can use gen-kernel

4. Again not in the handbook

5. Yep

6. No, prelink is not default

How it compileing a flaw thats the whole point!!! emerge sync is not unsafe and if you pick an official mirror you won't have any issues.

---

### Post by bjweeks on 2006-02-20
SuperDiscoMachine damn you! lol

---

### Post by SuperDiscoMachine V.5.7-3 on 2006-02-20
[QUOTE=bjweeks]SuperDiscoMachine damn you! lol[/QUOTE]
:twisted: 
Cue joke about how I was answering faster because I was using gentoo... ;)

---

### Post by bjweeks on 2006-02-20
[QUOTE=SuperDiscoMachine V.5.7-3]:twisted: 
Cue joke about how I was answering faster because I was using gentoo... ;)[/QUOTE]

I blame windows!!!!!!!!!(gentoo is on the box next to me and ubuntu on mu laptop)

---

### Post by midwinter on 2006-02-20
[QUOTE=LordHunter317]**And that's not proof.**  Benchmarks are proof.  I shouldn't have to repeat that.

Yes, it happens all the time.  I've had the same servers running Debian sid for *years*.  From early woody all the way to today.  And I haven't to reinstall or ever run into a program that prevented me from upgrading more than temporarily.

[edit]I completely messed that sentence up. My apologies.

You don't need one.  That's what apt-get upgrade and apt-get dist-upgrade are for.  You don't need one anywhere.  I can't even fathom what would make you believe you do, or that you cannot install software at an arbitrary point, or upgrade your installed software at an arbitrary point.

No, you're not.  You don't even understand how to use APT or what it can do, and you expect use to believe you?  Go read some first.  Then come back.  Your ignorance here is overwhelming.
[/QUOTE]

Okay, this is interesting to me because i've heard and read several things that contradict with this.  I'd be happy if you are right though, so enlighten me further.  I am at least certain I read that upgrading without a *-desktop package is not officially suported.
 
If I do a minimal server install, install X, and a few other things (maybe a base gnome package.. if ubuntu has one of these..), you mean if I do a dist-ugpgrade after this, I will just have updated packages of what I currently have installed? I wont have to deal with a whole ubuntu-desktop or whatever?   And it wont break?  This is certainly good news if true.

As to the benchmark thing, well i'm not trying to provide proof.  All I can suggest (and i'm sure no one would disagree) is that the original poster try out some other distros and see for him/herself. :)

---

### Post by bjweeks on 2006-02-20
[QUOTE=midwinter]
If I do a minimal server install, install X, and a few other things (maybe a base gnome package.. if ubuntu has one of these..), you mean if I do a dist-ugpgrade after this, I will just have updated packages of what I currently have installed? I wont have to deal with a whole ubuntu-desktop or whatever?   And it wont break?  This is certainly good news if true.
[/QUOTE]


Yep that works fine, ubuntu-desktop is just a meta package.

---

### Post by egodust on 2006-02-20
[QUOTE=SuperDiscoMachine V.5.7-3]No, it hasn't. But if I'm wrong, maybe you could provide a document where drobins states that this was the primary purpose of gentoo.
[/QUOTE]

[http://www.gentoo.org/main/en/about.xml](http://www.gentoo.org/main/en/about.xml)
> 
Thus, Enoch was born. Daniel wanted Enoch to be a blazingly fast distro with capabilities to completely automate the package creation and upgrading process. Soon there was a #enoch on irc.freenode.net and 10 developers helping with the distro. Over a period of time, as Enoch started improving, they felt that it needed a new name. They called it Gentoo Linux


I thought that was obvious, otherwise what's the point of make.conf? and reading info gcc?

[QUOTE=SuperDiscoMachine V.5.7-3]
There's a default kernel now in gentoo? I highly doubt this.
[/QUOTE]

[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=7#doc_chap2](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=7#doc_chap2)

> 
For x86-based systems we have, amongst other kernels, vanilla-sources (the default kernel source as developed by the linux-kernel developers), gentoo-sources (kernel source patched with performance-enhancing features), ...


[QUOTE=SuperDiscoMachine V.5.7-3]
Are you? By whom?
I never was encouraged to do anything when installing gentoo. And how is tweaking hdparm on gentoo different from tweaking it on ubuntu?
[/QUOTE]

It is different, Ubuntu doesn't mention it at all -- if you know about it then you would set it up yourself, if you don't then you might not and suffer slower video or whatever.

[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=2](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=2)
> 
Optional: Tweaking Hard Disk Performance

If you are an advanced user, you might want to tweak the IDE hard disk performance using hdparm. With the -tT options you can test the performance of your disk (execute it several times to get a more precise impression):

Code Listing 7: Testing disk performance

# hdparm -tT /dev/hda

To tweak, you can use any of the following examples (or experiment yourself) which use /dev/hda as disk (substitute with your disk): 


[QUOTE=SuperDiscoMachine V.5.7-3]
Not true, at least if genkernel is still around. And what about the new gentoo installer?
[/QUOTE]

I can't really comment on things that are around the corner regarding things, I can only talk about what is the state of play at the moment.

[QUOTE=SuperDiscoMachine V.5.7-3]
Again, who on earth encourages you to do so and how is this different from doing the same thing on ubuntu?
[/QUOTE]

Same as above. Gentoo handbook

[QUOTE=SuperDiscoMachine V.5.7-3]The impact is minimal at best and looking at all the broken CFLAGS of many gentoo ricers, binaries may well be slower even though people tweaked their compile settings.
[/QUOTE]

[QUOTE=SuperDiscoMachine V.5.7-3]Again, I highly doubt that gentoo now defaults to prelink. If it doesn't, what's the difference between installin and using prelink on gentoo and doing the same on ubuntu?
[/QUOTE]

However the user finds out about it, the difference between Ubuntu and Gentoo regarding prelink is pretty much USE flag "pic"

[QUOTE=SuperDiscoMachine V.5.7-3]
Wouldn't it be saner to simply not install them in the first place?
[/QUOTE]

I didn't install them, Ubuntu did. 

[QUOTE=SuperDiscoMachine V.5.7-3]
Huh? You have to but you don't have to? Aha? And why on earth should I recompile mplayer or my kernel?[/QUOTE]

The kernel is different from say MPlayer, the default Ubuntu kernel will compile alot of built ins and modules plus restricted modules that the user won't need, if they don't know they don't need it, they won't remove it, this is the same as a Windows user not turning off system services etc..

For me, the default Breezy kernel doesn't support my TV card where as the latest kernel does and so I could either wait for Dapper or recompile it. If you do recompile then you can remove alot of stuff that you won't need and so on. MPlayer default packages on Ubuntu are fine but CVS uses GTK2 as well as better CPU optimisations

---

### Post by bjweeks on 2006-02-20
gentoo-sources is NOT ck-sources.

> 4. during installation you are encouraged to explore different partitions and settings, e.g. ext3 with dir_index, full logging and removing root partition reservations, etc..


Link?

---

### Post by bjweeks on 2006-02-20
[http://www.gentoo.org/doc/en/gentoo-kernel.xml](http://www.gentoo.org/doc/en/gentoo-kernel.xml)

> ck-sources is Con Kolivas's kernel patch set. This patchset is primarily designed to improve system responsiveness and interactivity and is configurable for varying workloads (from servers to desktops). The patchset is also quite mature and has been put through numerous iterations of development and tuning. The emphasis of each release is on stability and security. Support and information is available at [http://kernel.kolivas.org](http://kernel.kolivas.org) and in #ck on irc.oftc.net.

> gentoo-sources is a kernel based on Linux 2.6, with various kernel patches included to fix security problems, kernel bugs, and to increase compatibility with the more uncommon system architectures. Linux 2.6 is the current official stable kernel tree, and development is progressing rapidly. For highest performance, best hardware support, and its large new feature set, we recommend 2.6 over its older 2.4 counterpart.

---

### Post by SuperDiscoMachine V.5.7-3 on 2006-02-20
[QUOTE=egodust][http://www.gentoo.org/main/en/about.xml](http://www.gentoo.org/main/en/about.xml)
I thought that was obvious, otherwise what's the point of make.conf? and reading info gcc?
[/quote]
No, it's not obvious at all. And even the little marketing site you linked to doesn't claim performance to be gentoo's primary purpose.
P.S.:
Ask ciaranm, he'll tell you what the point of make.conf is and I'm sure he'll also will find nice words about the misconceptions that the main purpose of gentoo is performance.


[QUOTE=egodust]
[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=7#doc_chap2](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=7#doc_chap2)
[/quote]
As I said, no default kernel. And please tell me you don't believe that the ubuntu kernels aren't also havily patched.

[QUOTE=egodust]
It is different, Ubuntu doesn't mention it at all -- if you know about it then you would set it up yourself, if you don't then you might not and suffer slower video or whatever.
[/quote]
Ehm, then you didn't look at the ubuntu documentation.

[QUOTE=egodust]
I can't really comment on things that are around the corner regarding things, I can only talk about what is the state of play at the moment.[/quote]
Genkernel has been around for several years now...

[QUOTE=egodust]
Same as above. Gentoo handbook
[/quote]
Same as above. Ubuntu documentation.

[QUOTE=egodust]
However the user finds out about it, the difference between Ubuntu and Gentoo regarding prelink is pretty much USE flag "pic" [/quote]
Then you don't know how to probably use prelink with ubuntu. You can automate it too, you know.
Again, take a look at the available documentation.


[QUOTE=egodust]
I didn't install them, Ubuntu did. 
[/quote]
Nope, you did by choosing the default install.

[QUOTE=egodust]
The kernel is different from say MPlayer, the default Ubuntu kernel will compile alot of built ins and modules plus restricted modules that the user won't need, if they don't know they don't need it, they won't remove it, this is the same as a Windows user not turning off system services etc..
[/quote]
Huh? And this very same user who isn't able to remove what he doesn't need should rebuild his kernel?

---

### Post by egodust on 2006-02-20
[QUOTE=bjweeks]
1. No, gentoo-sources is the recommended kernel.
[/QUOTE]

I'm pretty sure that includes the CK patchset, but it's been a while so don't hold me to it.

[QUOTE=bjweeks]
2. No, your not.
[/QUOTE]

Yes you are, hdparm is mentioned in the handbook

[QUOTE=bjweeks]
3. You can use gen-kernel
[/QUOTE]

Sure, but the handbook states '7.c. Default: Manual Configuration' - if genkernel is so great, why isn't it the default?

[QUOTE=bjweeks]
4. Again not in the handbook
[/QUOTE]

Sure it is: [http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=4](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=4)
> 
ext3 is the journaled version of the ext2 filesystem, providing metadata journaling for fast recovery in addition to other enhanced journaling modes like full data and ordered data journaling. ext3 is a very good and reliable filesystem. It has an additional hashed b-tree indexing option that enables high performance in almost all situations. You can enable this indexing by adding -O dir_index to the mke2fs command. In short, ext3 is an excellent filesystem.


It has a breakdown of the most common filesystems too.

5. Yep

[QUOTE=bjweeks]
6. No, prelink is not default
[/QUOTE]

Yes sure, but you have to conceed that the handbook links to the documentation which links to prelink, Ubuntu hasn't got that at all.. 

[QUOTE=bjweeks]
How it compileing a flaw thats the whole point!!! emerge sync is not unsafe and if you pick an official mirror you won't have any issues.[/QUOTE]
[/QUOTE]

Because it doesn't have that much impact compared relatively to other gcc flags in real world use.

As for securtiy, here is another breakdown:

A1. handbook doesn't verify sources, you are encouraged to use a mirror to pull the stage* files as well as portage, there are MD5SUMs checks but these are useless -- what if the mirror is hacked?  No GPG verification

A2. emerge sync uses rsync and even if it's an official mirror it might get hacked and you have no way of preventing this, no GPG verification or stopping man in the middle attack

A3. Handbook tells you to select a mirror nearer to you, and this doesn't mention anything about security.

A4. Even if you pull an MD5SUMS file from gentoo itself, if gentoo is hacked you won't have a leg to stand on, and the handbook doesn't mention this at all.

Every other major distro has some form of verification, but portage+gpg is still in testing? gentoo forums mention the problems way back til 2002/2003!

Til portage FEATURES 'gpg' verification as well as all the gentoo mirrors SIGN THEIR DAMN MD5SUMS! gentoo is a joke for package security. This paranoia is relative to other distros.

---

### Post by egodust on 2006-02-20
[QUOTE=SuperDiscoMachine V.5.7-3]No, it's not obvious at all. And even the little marketing site you linked to doesn't claim performance to be gentoo's primary purpose.
P.S.:
Ask ciaranm, he'll tell you what the point of make.conf is and I'm sure he'll also will find nice words about the misconceptions that the main purpose of gentoo is performance.
[/QUOTE]

I don't need to - you got what you asked for -- gentoo's goals have most likely evolved since the project has evolved from a one man show, etc.

[QUOTE=SuperDiscoMachine V.5.7-3]
As I said, no default kernel. And please tell me you don't believe that the ubuntu kernels aren't also havily patched.
[/QUOTE]

Never said that.

[QUOTE=SuperDiscoMachine V.5.7-3]
Genkernel has been around for several years now...
[/QUOTE]
Still not mentioned first.

[QUOTE=SuperDiscoMachine V.5.7-3]
Then you don't know how to probably use prelink with ubuntu. You can automate it too, you know.
Again, take a look at the available documentation.
[/QUOTE]

I know?

[QUOTE=SuperDiscoMachine V.5.7-3]
Huh? And this very same user who isn't able to remove what he doesn't need should rebuild his kernel?[/QUOTE]

No - Ubuntu Breezy's kernel was fine, except a newer kernel was able to support some hardware that Breezy wasn't, so options included waiting or getting the latest and making it work.  Could of just waited.

---

### Post by SuperDiscoMachine V.5.7-3 on 2006-02-20
[QUOTE=egodust]I don't need to - you got what you asked for -- gentoo's goals have most likely evolved since the project has evolved from a one man show, etc.
[/quote]
No, I didn't. And you should really ask if you think make.conf only makes sense when it comes to performance.

[QUOTE=egodust]
Never said that.
[/quote]
But you implied it. Otherwise all you wrote about the kernel didn't make any sense.

[QUOTE=egodust]
Still not mentioned first.
[/quote]
So?

[QUOTE=egodust]
I know?
[/quote]
Gee, that's great. But if you do, why make bogus claimes in the first place?

---

### Post by egodust on 2006-02-20
[QUOTE=SuperDiscoMachine V.5.7-3]No, I didn't. And you should really ask if you think make.conf only makes sense when it comes to performance.
[/QUOTE]

I said
> Gentoo is faster default install, thats because gentoo has been developed to be fastest

And you jumped in with:
> 
No, it hasn't. But if I'm wrong, maybe you could provide a document where drobins states that this was the primary purpose of gentoo.


So it **hasn't** been developed to be faster?, even if the founder of the gentoo project states that he wanted it to be "blazing" and this isn't a design goal in your eyes? WTF?  -- I even provided a direct quote from Gentoo but that isnt' good enough.

I am not stating it's not the ONLY goal, and now other devs have joined and the whole project is different, but it's still a major design goal.

MAKE.CONF, aptly named for it's purpose now has a wider meaning than when it was first created, yes I know -- so what?

[QUOTE=SuperDiscoMachine V.5.7-3]
But you implied it. Otherwise all you wrote about the kernel didn't make any sense.
[/QUOTE]

Actually no, I said gentoo had a better kernel than Ubuntu does out of the box, that doesn't mean they don't patch it, there is a patch set applied, but it lacks certain performance patches, and so on.

[QUOTE=SuperDiscoMachine V.5.7-3]
Gee, that's great. But if you do, why make bogus claimes in the first place?[/QUOTE]

I haven't said anything BOGUS, it is you who haven't read what I said properly, I said something about prelink in the context of what I change in Ubuntu and certain things about gentoo are in it's own section, this has nothing to do with Ubuntu or Gentoo's use of prelink and if prelink is default or not.

The question of the thread was is Gentoo really that much faster than Ubuntu? and the answer is maybe not and a bunch of tweaks I have done and how they compare to Gentoo's total optimisation of a system. Why wait for Gentoo when you can get near enough?

It isn't an answer to "Is Gentoo a better system for learning Linux hardcore?" Apt v.s. portage, source vs. bin, design goals.

---

### Post by SuperDiscoMachine V.5.7-3 on 2006-02-20
[QUOTE=egodust]
So it hasn't been developed to be faster?[/quote]
And I quote:
> Daniel wanted Enoch to be a blazingly fast distro with capabilities to completely automate the package creation and upgrading process.
So no, it wasn't.

[QUOTE=egodust]
MAKE.CONF, aptly named for it's purpose now has a wider meaning than when it was first created, yes I know -- so what?
[/quote]
Refering to gentoo being designed to be faster you wrote and I quote:
> I thought that was obvious, otherwise what's the point of make.conf? and reading info gcc?
??????

[QUOTE=egodust]
Actually no, I said gentoo had a better kernel than Ubuntu does out of the box, that doesn't mean they don't patch it, there is a patch set applied, but it lacks certain performance patches, and so on.
[/quote]
Actually no, you said and I quote:
> 1. default kernel compiles with the CK patchset, which improves system responsiveness even under heavy load
Now this is first off simply incorrect as we have found out now (That is, there is no default kernel and even the recomended one isn't a ck kernel). Second, it doesn't mean that ubuntu doesn't use also use performance enhancing patches, does it, though you clearly implied it didn't. However, I'd really like you to be specific about this issue.

[QUOTE=egodust]
I haven't said anything BOGUS, it is you who haven't read what I said properly, I said something about prelink in the context of what I change in Ubuntu and certain things about gentoo are in it's own section, this has nothing to do with Ubuntu or Gentoo's use of prelink and if prelink is default or not.
[/quote]
And again I quote:
> 6. prelink, all your binaries are prelinked to load faster: i.e. system relocation is done once and then it's trivial to load a binary without fixing up all the relative addresses

And after it was pointed out to you, that prelink wasn't a default in gentoo you wrote and I quote:
> However the user finds out about it, the difference between Ubuntu and Gentoo regarding prelink is pretty much USE flag "pic"
And I pointed out that it wasn't any harder to get prelink to automatically work on Ubuntu, to which you replied you knew this. So your point was????

---

### Post by egodust on 2006-02-20
[QUOTE=SuperDiscoMachine V.5.7-3]So no, it wasn't. [/QUOTE]

> 
Daniel **wanted** Enoch to be a **blazingly fast distro** [COLOR="Red"]with[/COLOR] capabilities to _completely automate the package creation and upgrading process_


How is the above so far away from "designed to be faster default" to elicit a respone of "No it wasn't" from you? 

It was his project and what he wanted fell into the design goals of that project, it doesn't say he wanted a meta distro or something you could cross compile, compile on modern software for lesser processors, apply stack protection, heap canary support or SELinux.. 

[QUOTE=SuperDiscoMachine V.5.7-3]
Now this is first off simply incorrect as we have found out now (That is, there is no default kernel and even the recomended one isn't a ck kernel). Second, it doesn't mean that ubuntu doesn't use also use performance enhancing patches, does it, though you clearly implied it didn't. However, I'd really like you to be specific about this issue.
[/QUOTE]

The difference here is minor because there is no "default" kernel and you are given a chance to install whatever kernel you want and at your choice told about a bunch of kernels that you MIGHT want, is not a long way from a default and the language used in the handbook isn't that far off from my point either:

> 
vanilla-sources (the default kernel source as developed by the linux-kernel developers) 
gentoo-sources (kernel source patched with **performance-enhancing** features) AND the Wiki says:

Nowadays, gentoo-sources contains 2.6.x series kernels. This is the kernel **most** people will want to use.


So fine, gentoo has the option for CK patchset but doesn't have it by default, yet you argue gentoo has no default, so how can I be wrong? :P -- gentoo has _a_ ck patchset and the documentation says that gentoo sources has various performance patches, even if they aren't CK set, they have their own  merit.  I didn't have any explicit point about prelink in the good or bad camp, just that it was worthy of use!

As for Ubuntu, most of it's kernel patchset (linux-image-2.6.12-10-386) seems to be from Debian, and doesn't mention enough for me to gleen an answer, and even though it's 31MB uncompress that includes a huge changelog -- 
Debian not really known for performance, v.s. stability though.

---

### Post by Arc Owner on 2006-02-20
[QUOTE=prattrs]LordHunter:

I wanted to try and speak to some of your questions, even though I'm not the OP.  As a bit of background, I've run Gentoo and Ubuntu both for a bit, but I'm running Gentoo right now.

What you learn with Gentoo: 

You get a basic sense of how a linux system is laid out, what fstab is, how grub.conf (menu.lst in debian/Ubuntu IIRC) works, how to use fdisk, how to compile your kernel, configure X, add users, where your system logs are, what a cron daemon is...  you know, all those things we take for granted after a while?  I think the only way to dismiss the value of learning these things is to not realize what a mystery they are to a linux newbie.

Why people like it:

-The init system: It's nice to be able to say /etc/init.d/service_name restart.  I'm led to believe that this scheme is uncommon in linux, but it's very convenient.

-The ease with which you can re-compile your kernel: While I was using Ubuntu, I was frustrated when I wanted to re-compile my kernel with PREEMPT and a few other options in it.  Yes, I RTFM'd on the wiki, but from 10,000 ft the directions look like a PITA compared to Gentoo - I think mostly because the sources aren't there by default, and the directions I read seemed to imply that making a deb package out of your new kernel was the way to go, which seemed annoying to me at the time.  YMMV.

-Gentoo has niceties, to include:
  gentoo-syntax for editors (for config files and such)
  a nice console environment with FB and so forth, very easily
  emul-linux-x86-java for things like open-office
  java-config (I like it better than alternatives-config, YMMV)
  it will update cedega for me

I'm sure there are other things, and to each their own, but I wanted to put in a response to defend my beloved distro :)

BTW, I don't think anyone in the Gentoo community cares to much about what instructions the compiler emits, or is deluded into thinking it makes much of a difference.  For the most part, we like the control, the convenience and the niceities.  And the community. YMMV :)

Sandy[/QUOTE]

Just too bad they took away stage 1 installs, I was hoping I could do one, 
but sadly, they took them away :cry:

---

### Post by LordHunter317 on 2006-02-20
[QUOTE=bjweeks]Lordhunter I normally agree with you but emerge is more powerful apt-get. [/quote]No, it isn't.  It's feature deficent.  It's lacking **basic** features.

> USE flags are the best thing about gentoo no binary distro can offer what USE flags can.Yes, they can, and they already do in the overwhelming majority of cases.

>  About -D many users don't use or recommend  it.Many Gentoo users are simply incompetent then.  The fact portage doesn't always do a full dependency tree walk for all effected packages saddens me greately.  Even RPM and it's various front-ends get this right, and even the BSD packagers get this right,

> Gentoo has less shit installed no cups, no hp printer service, etc. Wonderful.  They do nothing but lengthen your startup time if you're not using them.

---

### Post by LordHunter317 on 2006-02-20
[QUOTE=midwinter]Okay, this is interesting to me because i've heard and read several things that contradict with this.  I'd be happy if you are right though, so enlighten me further.  I am at least certain I read that upgrading without a *-desktop package is not officially suported.[/quote]It's not.  If you don't have the -desktop package when you upgrade, all you'll miss is anyhting new that was added as a dep to the -desktop.  You can simply add it to the install, then re-kill the dependencies you don't want.
 
> If I do a minimal server install, install X, and a few other things (maybe a base gnome package.. if ubuntu has one of these..), you mean if I do a dist-ugpgrade after this, I will just have updated packages of what I currently have installed? I wont have to deal with a whole ubuntu-desktop or whatever?   And it wont break?  This is certainly good news if true.I've been doing it on Debian for literally years, so...

[quote=egodust]1. default kernel compiles with the CK patchset, which improves system responsiveness even under heavy load
[/quote]Gentoo has no default kernel.

> 2. during installation you are encouraged to setup hdparm settings properly, not only including DMA but IO and suchThe kernel does this for you in the overwhelming majority of cases, since 2.4.  Where it doesn't, *all* distros do it for you automatically.  This isn't rocket science.  There's nothing difficult to tune there.

> 3. hardware detection is non existant, you are encouraged to compile the kernel and remove all the things you don't need and then auto load all the modules your hardware needs yourself.How can a unloaded module make a difference?  Oh wait, it can't.  But don't let logic stop your fanboi cheering.

> 4. during installation you are encouraged to explore different partitions and settings, e.g. ext3 with dir_index, full logging and removing root partition reservations, etc..And?  Exploration doesn't lead to performance increases or even necessarily any knowledge of value.

> 5. packages are compiled for target CPU, this only really has a impact on glibc, X, kernel, gnome, etc..Try glibc and the kernel.  As I suspected, you know nothing about compiling. **Go benchmark.**

> 6. prelink, all your binaries are prelinked to load faster: i.e. system relocation is done once and then it's trivial to load a binary without fixing up all the relative addressesPrelink helps start up times only, it's easy to setup by default, and it doesn't do what you say it does.

---

### Post by piedamaro on 2006-02-20
One word: [http://funroll-loops.org/](http://funroll-loops.org/)

---

### Post by LordHunter317 on 2006-02-20
[QUOTE=egodust]I thought that was obvious, otherwise what's the point of make.conf?[/quote]So you can globally set configuration parameters, just like in BSD ports they copied? (Which is an almost universal bad, but that's besides the point)

>  and reading info gcc?Your own potential gratification at reading something and not comprehending it?  Most programmers don't understand the GCC documentation very well.

> So it hasn't been developed to be faster?,No, because any competent engineer knows that's damn well impossible in any meanigful sense.

He wanted a source-built distro.  End of story.

> Actually no, I said gentoo had a better kernel than Ubuntu does out of the box, that doesn't mean they don't patch it, there is a patch set applied, but it lacks certain performance patches, and so on.Actually, in terms of stability, they both suck (both have had serious data-corruption problems I've witnessed).  In terms of featureset, Ubuntu is a clear winner.

> How is the above so far away from "designed to be faster default" to elicit a respone of "No it wasn't" from you?Because that's not waht that sentence says.  A course in reading comprehension would do you well.  "Blazingly fast" just means that.  It doesn't mean "faster than anyone else"  You're creating a comparsion that simply does not exist.  IOW, Fanboy logic.

> The difference here is minor because there is no "default" kernelIt's quite substantial because it renders a large portion of your argument invalid.  Fanboy defense.

> So fine, gentoo has the option for CK patchset but doesn't have it by default, yet you argue gentoo has no default, so how can I be wrong? :P Because your statement is contradictory with those two.  A course in basic logic would help you understand this, since you seem to be running clearly afoul of it.  Such details are important here.

> As for Ubuntu, most of it's kernel patchset (linux-image-2.6.12-10-386) seems to be from Debian,Yes, but they're extended it quite thoroughly.  I counted for hoary while looking for bugs, and it's substantial in terms of size and patches, though I forget the exact numbers.

---

### Post by GreyFox503 on 2006-02-20
Well, if you want opinions and/or experiences, I have one.

Regardless of why it happened, my Gentoo install was much faster than my Ubuntu install. I have the default install of Ubuntu 5.10, with a few other applications, but nothing significant. My boot time/speed of Ubuntu hasn't changed since installation.

I installed the Gentoo base system, then X.org, then Gnome.  And then a few other misc. packages.

Gentoo boots in half the time, and applications on the system seem to load a smidge faster (although that might just be my imagination).

And I do believe you will learn something from installing it. I had to learn about and edit a few key config files about networking, xorg.conf, and /etc/fstab, among others. Sure, you can do that with any distro, but there's usually no need to.

---

### Post by prattrs on 2006-02-20
> 
And I do believe you will learn something from installing it. I had to learn about and edit a few key config files about networking, xorg.conf, and /etc/fstab, among others. Sure, you can do that with any distro, but there's usually no need to.

Ding!

Folks, why is there any controversy about the fact that lots of people like to f*ck with their systems?  And, I might add, learn from their mistakes.  Where is the mystery?

And FFS, enough with the "compiling is BS" stuff.  It's enough that people want to know how the build environment can be affected by things like +/- gtk or QT, NPTL, and so forth.  If they want to f*ck with it, for no better reason than curiousity, more power to them.

Please try to remember that your average Gentoo user is someone who knows his knowledge is limited and whose curiousity is big.  There might not be a technical reason for doing things the Gentoo way, but then again, there doesn't need to be.  It's an end in itself.

(And for the record I like (K|U)buntu a great deal, and discussions like this keep tempting me to install Dapper and take it for a spin.)

EDIT: Just wanted to add an analogy - it's possible to use Ubuntu for a year and still assume that certain things might as well happen by magic or fairy dust.  There's less fairy dust in Gentoo (somewhat less, at least).

Sandy

---

### Post by LordHunter317 on 2006-02-20
[QUOTE=GreyFox503]Gentoo boots in half the time,[/quote]You probably have half the services running, too.  If you trim out everything you don't need, Ubuntu will load in comparable time.

>  Sure, you can do that with any distro, but there's usually no need to.If there is no need, why bother learning it?

[quote=prattrs]Folks, why is there any controversy about the fact that lots of people like to f*ck with their systems? And, I might add, learn from their mistakes. Where is the mystery?[/quote]There isn't, but suggesting Gentoo is prerequisite to that path (or even a good way to go down it) is foolishness.

---

### Post by Jessehk on 2006-02-20
I think I've gotten a good sense of Gentoo users from this thread...

Oh! The quoting! ;)

---

### Post by prattrs on 2006-02-20
> There isn't, but suggesting Gentoo is prerequisite to that path (or even a good way to go down it) is foolishness.

Is God killing kittens or something?

---

### Post by bjweeks on 2006-02-21
[QUOTE=prattrs]Is God killing kittens or something?[/QUOTE]

Everbody install Gentoo for the kittens sake!!! lol

---

### Post by Mikecore on 2006-02-21
Gentoo was my first and only Distro for three years. I really liked it. From the stand point of learning more aboout linux, Gentoo is a great Distro. You will learn alot and in a short time. Im sure that if your goal was to produce a faster distro on a  particular system you could do just that. No two Gentoo installs are the same. First you choose your files system, Second you build a custom kernel for your hardware without any added or unwanted opptions, I could go on and on the point is everything is a custom. So building a small fast distro is somthing you could do.
How much faster I don't know or care, And Im sure if you really know what you are doing you could do the same thing with Ubuntu.  IMHO the main thing is just use the Distro that you like or makes your life the easiest. ( I can tell you this Gentoo is not about easy its about learning ) I could have installed Gentoo on my new laptop I choose Ubuntu instead because lack of time and the fact that Ubuntu installed in about an hour with everything working out of the box.  my 1280x768 native screen res, my Intel  PRO/Wireless 2200BG wireless nic, and just about everything else. My point is Im happy with Ubuntu.

---

### Post by dbw on 2006-02-23
Maybe [linux-from-scratch]("http://www.linuxfromscratch.org/lfs/index.html") is faster?  ;)

---

### Post by Cyfr on 2006-02-24
Wow theres certainly a lot of action in this thread lol..

I'm an advanced windows user, and I consider myself a good learner when it comes to computers.

Ubuntu is a brilliant distro, the only thing I could possibly say about it is for linux in general, some applications that I can run in windows (such as Messenger Live) there is simply no decent alternative on linux. (Unless you just want to message each other, then theres plenty of decent alternatives, however I usualy webcam and neither aMSN or mercury seem to be able to handle webcam without severe system lag).

Installing gentoo and running it may be pointless, there might not be much performance gain, and that might only be due to less things running... but coming from a 'a year ago I didn't know shit about linux' guy, I've learnt SO much because Gentoo MADE me learn it.

I could do all the things i've done in gentoo, in ubuntu, I could recompile the kernel, I could trim down all additional processes which I dont use etc...
but because I have a complete working system without doing that, I lack the motivation to learn... where as Gentoo makes me do it and then I feel i've learnt something when it comes to having a working system.
For once im my life, it seems easier and better to work *forward* on gentoo, rather than working *backwards* on ubuntu to try and learn the same sort of things and have less crap running..

---

### Post by Kurt` on 2006-02-24
I ran Gentoo for about 6 months (it was my first distro ever).

Recently, I did a stage 1 install + all possible optimizations for fun. I was pretty impressed with the speed.

Then, one of my friends suggested that I try Slackware. He said I could install it in less than 10 minutes.

20 minutes later (had to download the ISO ;)), my jaw almost hit the floor. Slackware, with its "not-optimized binary installation", was faster out of the box than a Stage 1 Gentoo install!

Needless to say, I stopped using Gentoo that day. ;) Also, I had grown tired of everything on the system breaking if I upgraded Perl/Python through portage.

Now, Slackware = server PC, Kubuntu = desktop

---

### Post by polo_step on 2006-02-24
[FONT="Fixedsys"]Gentoo?  Sorry, but I can't see getting involved with a distro from people who [don't know the difference between a cow and a bull]("http://www.gentoo.org/main/en/about.xml").

Sorry.

[/FONT]

---

### Post by plb on 2006-02-24
Faster? By default sure. With Identical setups? Possibly, but the difference is probably so small there is no reason to even argue over it. The best attibute gentoo has imho are USE flags.

---

### Post by magomago on 2006-02-24
No offense, but unless you want to control exactly what packages are on your system from the BASE (and don't want to be jigdo Debian...) then Gentoo is the distro you can use.

I've used it before as a learning experience to learn more about Linux and its filestructure and how to do a few things (great documentation they have, someof the best)

but you wll end up compiling your life away.  Don't waste your time with it.  Please...think of the Penguins ;)  You will spend SOOOOOOOOOOOOO much time compling and things are faster by miliseconds at most.  I would say its <5% (both by experience and benchmarks) but errs closer to negligble.  PCs today are pretty beefy and this is not the days of 233Mhz P1 with 32 megabytes of ram that we have to talk about optimization that would make it run faster.  

anyways stick with the binaries...

---

### Post by LordHunter317 on 2006-02-24
[QUOTE=magomago]No offense, but unless you want to control exactly what packages are on your system from the BASE (and don't want to be jigdo Debian...) then Gentoo is the distro you can use.[/quote]I have perfect control under Debian.  I don't know what you're taking about.

I have arguably less control under Gentoo because I can't remove software once it's installed safely, for example.

---

### Post by Cashel on 2006-02-24
[QUOTE=CaptainTux]Hence why a gentoo linux system is usually faster than most other distros.  

Look, at the end of the day, gentoo is whatever you want it to be.  It can be as fast, bloated, stable, or bleeding edge as you want more-so than any other distro.  It is also not for the feint of heart to install and configure, but once you get there, emerge is simple amazing.

It is a control freaks dream distro...pretty much one step shy of rolling your own distro.[/QUOTE]

What Cpt Tux said. In addition, I'd say you can control the key aspects of Ubuntu well enough with a bit of knowledge to trim it down. 

I'm running x86_64 based Ubuntu. I always compile my own kernel (it didnt change much from the Breezy default), and remove services and the largest of the unused apps and libs... As for compiling things to make them run fast, the few applications in which the extra compiler flags may make a difference, are easier to compile in an Ubuntu then in Gentoo IMHO.. I say this mostly because in Gentoo your first two days are consumed just installing the thing (for a first timer) as where Ubuntu installed in just over 20 minutes for me.

Why compile everything? Some stuff you'll hardly ever use anyways... For example, who's played Four-in-a-Row? 

Have fun! 
Cashel

---

### Post by dtfinch on 2006-02-25
I tried gentoo for a few weeks. After I got finally got 3d acceleration (x11-drm) working about a week ago, I blew it away and moved on. It was fun, but all I wound up doing was building a system that was not unlike all the other distros I've used, and x11-drm was the last big milestone before reaching that level of functionality.

I was attracted by the concept of everything being in source packages, but when I need to customize something, it seems easier just to download tarballs and build them manually then download the source package with emerge, untar the package, make my source changes, retar the package, rebuild the hashes, and tell emerge to recompile and reinstall it. I'm sure there's a better way to do it without straying from emerge/ebuild/portage, but I didn't find any such documentation.

I eventually found myself downloading several packages from the source rather than using emerge for everything, partly because of the hassle of unmasking newer package versions, the pain of repackaging emerged source to make changes, and also because Gentoo (like all other distros) never has the newest packages I want. Since I do this on every other distro anyway, and just as easily, I just wasn't seeing the benefits of Gentoo, though it was fun for a while.

The performance was good. But when something is fast enough, it's hard to tell if it gets faster short of running a benchmark. My CFLAGS were "-Os -march=pentium4 -fomit-frame-pointer -pipe", because I have a celeron. My root filesystem was JFS, because I hadn't used JFS before and have never heard anything bad about it.

When I was done with Gentoo, I decided to give Arch a try. I stopped using Arch about 2 hours later when I decided to let pacman (the package manager) update my system. It prompted me with the message "ttf-bitstream-vera conflicts with xorg. Remove xorg? [Y/n]". And a lot of other packages it simply refused to install, because they contained files that were already installed by other packages. Maybe 0.7.1 just wasn't their best release. I know I could have made it work, but I had the feeling there'd be a lot more of these sorts of troubles ahead. At least Gentoo worked from the beginning. Sure I had to edit a couple lines of x11-drm, but all the configuration, compiling, and installation before that was rather uneventful and error-free, though time consuming.

I installed Dapper flight 4 next, because it was released that same night and was finally into the feature-freeze stage.

---

### Post by bvc on 2006-02-25
speed_smeed...it's all in your head
The only distro I ever noticed any diff on was LFS and while it was probably in my head because of what is involved in building it, I still thought it was faster. Benchmarks probably wouldn't have shown much of a diff though.

---

### Post by briancurtin on 2006-02-25
[QUOTE=Cashel]Why compile everything? Some stuff you'll hardly ever use anyways... For example, who's played Four-in-a-Row?[/QUOTE]
that is the precise reason you dont compile it...

if you arent going to use something, why on earth would you compile it?

---

### Post by tameritoke on 2006-02-26
I had Gentoo 2005.1 on my machine. I am using a AMD Athlon 2000 with 1.5 GB RAM. I see no difference. I guess all ubuntu packages for x86 are compiled with i686. From the speed it is allmost the same like the AMD optimized flags. 

Tamer

---

### Post by solafide on 2006-03-03
Yes, Gentoo is absolutely faster than Ubuntu. It isn't that hard, just time-consuming, and it's easier to configure than Ubuntu. The manual walks you right through the necessary steps, and with a graphical installer now there is nothing to fear.

---

### Post by dermotti on 2006-03-04
Hmmm, in my point of view Ubuntu is faster.

Gentoo LAMP install took me about a week. 
Ubuntu LAMP install took me 4 hours.

Gentoo should be able to make up that 164 hours in processing in about 10 years.


Ubuntu is faster.

---

### Post by GreyFox503 on 2006-03-04
lol, very true, man.

For me,

Ubuntu install:  < 1 hour
Gentoo install: ~20 hours with GNOME and OpenOffice.  (Only about 2-3 hours of actual human involvement.)

Finally booting and seeing that GNOME login screen:  priceless.

There's some things time can't buy.

For everything else, there's Knoppix.

---

### Post by incubus on 2006-03-04
If you have some extra space in your hard drive, I **highly** recommend trying out other distributions (as long as you feel confident enough for that). I tried many and regret none.

That experience is priceless. Even if at the end of the day you reach the same conclusions above, it's going to be your own, custom-made.

Just remember, a distribution comes not only with a bunch of packages, but also with a philosophy behind it.

incubus

---

### Post by bjweeks on 2006-03-04
Gentoo takes me a 2 hours to install.

Time to install ubuntu and remove all the shit I never needed a day.

The key to gentoo is sleep, compile overnight so no wasted time.

emerge -e system && emerge -e world && emerge -e world && emerge xorg-x11 && emerge kde-meta 

Anybody?? ;)

---

### Post by GreyFox503 on 2006-03-04
I should mention my roughly 20 hour time was from stage 1.  I believe it took me about 4 hours to progress to where stage 3 is, if I understand it correctly.

---

### Post by bjweeks on 2006-03-04
Doing a stage 3 and the emerge -e system && emerge -e world && emerge -e world are alot better.

---

### Post by Sirin on 2006-03-04
Gentoo took me 4 days (with the computer on, constantly) to install. I am never going back that way again. :evil:

---

### Post by bjweeks on 2006-03-04
[QUOTE=Sirin]Gentoo took me 4 days (with the computer on, constantly) to install. I am never going back that way again. :evil:[/QUOTE]

Get a better computer?

---

### Post by asimon on 2006-03-04
The main problem with Gentoo is not the initial install time but the expensive maintance (which among others is the result of bad package quality, childish developers, missing update paths, lack of good tools, and such things).

---

### Post by Mikecore on 2006-03-04
@asimon 

You hit it right on the spot! Thats the reason I left Gentoo.  I tried to speak to the Dev's about some of the problems Alot of people were having and was flatly ignored.

I would also caution the Ubuntu Dev team (one person) That being the guy who pretty much decided by himself not to include the "build-essential" 

I read the e-mails that went back and forth between the Dev's on this subject and this guy is really stuborn. Not including this package was a Big mistake ( just my oppion)

---

### Post by tseliot on 2006-03-04
If you want a distro which is bleeding edge, fast, optimised for 686 WITHOUT compilation times try "Arch Linux".

You can also compile and manage ports a la Gentoo but it's NOT required.

It's a wonderful distro (I think Gentoo users might like it)

---

### Post by blubaustin on 2010-03-12
As for the whole "benchmark arch and ubuntu" well here you go:
[http://www.phoronix.com/scan.php?page=article&item=arch_200908_benchmarks&num=1]("http://www.phoronix.com/scan.php?page=article&item=arch_200908_benchmarks&num=1")

---

### Post by leandromartinez98 on 2010-03-12
> **lordhunter317 said:**
> no, it isn't.  It's placebo effect.  Anyone who tells you otherwise understands nothing about compilers, save for a few small, corner cases.  And ubuntu ships optimized packages for nearly all of those cases, as well.

+1

---

### Post by cariboo on 2010-03-12
This thread is just about 4 years old, things have changed. Closed

---

