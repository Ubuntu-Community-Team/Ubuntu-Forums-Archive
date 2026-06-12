---
title: "Why don't some developers provide installers?"
date: 2010-05-14
forum: The Cafe
---

### Post by mamamia88 on 2010-05-14
and just leave tar archives?  just curious seeing how much easier it is to istall games from sh, bin, or deb.

---

### Post by jrothwell97 on 2010-05-14
Because tar archives work on every system. You unpack, compile and go.

If you throw a .deb file onto, say, a Fedora system, it won't work. A .run or .bin file won't run on Windows except under Cygwin. A Mac OS X .pkg file won't work on Ubuntu.

Put simply, it's because it's the most consistently reliable fallback option, and, while inconvenient, is flexible and works. :D

---

### Post by mamamia88 on 2010-05-14
are you saying a  run file or bin file won't run on other distros? im just complaining because when i pay for software i want an easy way to install it

---

### Post by Bachstelze on 2010-05-14
> **mamamia88 said:**
> when i pay for software i want an easy way to install it

Examples, please. There are many kinds of software around, and not all of them can be distributed as binaries, for various reasons.

---

### Post by mamamia88 on 2010-05-14
example bought sleeps as death yesterday.  came as a tar package.  extracted it.  ran the run to build file and it wouldn't compile right.  now i'm stuck with a bunch of useless files running the windows version in wine.

---

### Post by murderslastcrow on 2010-05-14
Lol, I used to install stuff in Wine that had dependency/compilation issues in Ubuntu (PCSX2, for example).

He was saying that a bin or run file won't install in WINDOWS, not other distributions. tar/tar.gz can be compiled on OS X, Windows, Linux, FreeBSD, whatever, so long as the dependencies are met.

It's not TOO difficult to make a deb, then use alien to make an RPM, etc. etc. It's just easier to plop the source down and make the user take care of dependencies than looking around trying to make sure the dependencies are met for each distribution they wanna' get it on.

It'd be cool if there were a cross-platform automatic installation format besides tar archives. A file you can just double click in any OS. Wow, the possibilities.

Some projects are in beta or have minimal Linux support, and think that's good enough support, so they just leave it to sit rather than maintaining packages.

---

### Post by NightwishFan on 2010-05-14
I prefer repositories, more secure and manageable.

---

### Post by murderslastcrow on 2010-05-14
Oh, certainly, and I hope the Ubuntu Software Center includes commercial software soon to ease installation for users who purchase games like World of Goo, Penumbra, and the like. No reason why commercial vendors shouldn't be able to take advantage of the repository system.

---

### Post by madjr on 2010-05-14
> **mamamia88 said:**
> example bought sleeps as death yesterday.  came as a tar package.  extracted it.  ran the run to build file and it wouldn't compile right.  now i'm stuck with a bunch of useless files running the windows version in wine.

[http://sleepisdeath.net/](http://sleepisdeath.net/)

wow from reviews seems to be one heck of a game, pay what you want model and went open source too!

how the heck did this go almost unnoticed !!!?

anyway any insight am not sure how to play it, seems to be unique

OP, since you payed for the game why dont you ask for a .deb on their site?

---

### Post by mamamia88 on 2010-05-14
you think they would actually listen?   and since there is already a mac and windows installer file why does it need to be it a tarball?

---

### Post by ssj6akshat on 2010-05-15
Some come as .tar.gz but do not need to be compiled.Just extract and play like Gish.Can you PM me the linux archive?

---

### Post by 3rdalbum on 2010-05-15
If I compile a program on my x86 computer on Linux, I can't run that precompiled version on a computer that uses an ARM CPU, or a PowerPC CPU, or anything except an x86 CPU.

Source code is the lowest-common-denominator - you can compile source code to run on any CPU that Linux supports. But a binary, a precompiled package - forget it.

---

### Post by handy on 2010-05-15
Some distros have a repository with the binaries & for source, for both x86 / x86_64 & more.

I don't want installers though, as a good package manager is just that & more.

---

### Post by m4tic on 2010-05-15
you bought a 2d game. Nice

---

### Post by steveneddy on 2010-05-15
That game is worse than Facebook.

---

### Post by madjr on 2010-05-16
> **steveneddy said:**
> That game is worse than Facebook.

why so, i see good reviews

anyway the op should at least open a thread in their forums

---

### Post by -grubby on 2010-05-16
Honestly, they probably didn't have the time/will/whatever to make the packages, so they just give you the source and let you compile it.

---

### Post by lisati on 2010-05-16
> **murderslastcrow said:**
>  It's just easier to plop the source down and make the user take care of dependencies than looking around trying to make sure the dependencies are met for each distribution they wanna' get it on.


> **-grubby said:**
> Honestly, they probably didn't have the time/will/whatever to make the packages, so they just give you the source and let you compile it.

+1 to both the above! 

There's also the possibility that the developer is happy that they've got the program up and running, and is keen to get onto the next project.

---

### Post by Old Marcus on 2010-05-16
Since they could be bothered to compile for Windows, why couldn't they compile for Linux? ok, you might have to do it twice for deb/rpm, but it's not that bad, surely? Not all of us are CLI ninjas these days.

---

### Post by snova on 2010-05-16
Because packaging is a different skill than programming, and not every developer has it. The odds of a project having someone who is able to package for the distro you happen to use goes down with the size of the project, especially if your distro is anything less than common.

> **mamamia88 said:**
> and just leave tar archives?  just curious seeing how much easier it is to istall games from **sh, bin**, or deb.

Also, installers suck...

> **Old Marcus said:**
> Since they could be <snip> to compile for Windows, why couldn't they compile for Linux? ok, you might have to do it twice for deb/rpm, but it's not that bad, surely? Not all of us are CLI ninjas these days.

... and binaries are easily made incompatible and unusable from the slightest difference between two distros, or even two releases. And that goes up with the complexity of the project (or the number of shared libraries it links against).

---

### Post by Old Marcus on 2010-05-16
Google had no problems with Google Earth as .bin as far as I know. Every Linux system I installed it on took it fine.

Perhaps they could at the very least provide locations for the 500,000 packages required to install the game?

---

### Post by 3rdalbum on 2010-05-16
> **snova said:**
> Because packaging is a different skill than programming, and not every developer has it.

Debian packaging is easy* if you just use the command-line, and there are GUI tools that make it as easy as falling off a log.

I don't know about RPM packaging, but I'm sure it's no rocket science either.

*Making one that would be accepted into the Debian or Ubuntu repositories is beyond my abilities, but anyone can make a package that is functionally correct.

---

### Post by aysiu on 2010-05-16
> **snova said:**
> Because packaging is a different skill than programming, and not every developer has it. So the developer expects users to do something she herself is incapable of doing? If packaging is so difficult, why would an end user be expected to do it instead of the developer? Checkinstall isn't rocket science for someone who can program... or shouldn't be.

---

### Post by snova on 2010-05-16
> **3rdalbum said:**
> Debian packaging is easy* if you just use the command-line, and there are GUI tools that make it as easy as falling off a log.

I don't know about RPM packaging, but I'm sure it's no rocket science either.

*Making one that would be accepted into the Debian or Ubuntu repositories is beyond my abilities, but anyone can make a package that is functionally correct.

There are graphical tools to build packages? That's new to me.

For something so simple, though, it seems to be surrounded by a mass of policies, rules, overlapping tools and guidelines that make no sense from where I stand. Granted, when I tried a basic Python package it wasn't particularly hard- CDBS practically built it for me- but I always felt like I was missing something, or that it was somehow inferior to a "real" package.

> **aysiu said:**
> So the developer expects users to do something she herself is incapable of doing? If packaging is so difficult, why would an end user be expected to do it instead of the developer? Checkinstall isn't rocket science for someone who can program... or shouldn't be.

I think it would be somewhat pretentious for a developer to "expect" the users to do anything.

This is my perspective on things, as someone who simply likes to play: there are people who understand the art of .deb's well, and I am not one of them. I also think the group who does is vastly outnumbered by the group who doesn't. For a project to build their own packages, for every release made, for every package format supported, someone has to take the time to maintain the files necessary for the system to work, test them, and upload them in synchrony with the rest of the project's release. Ideally there might also be repositories available to improve the update process for the end user; this is yet another set of tools to learn and more server space to maintain.

The original question appears to refer to a game called [Sleep Is Death]("http://sleepisdeath.net/"). Judging by its home page, it has one developer, who supports three varied major platforms already.

Someone who is more familiar with this kind of thing can probably see my exaggeration, but my point is: it's more work for a package to exist. And I'm lazy.

---

### Post by aysiu on 2010-05-16
> **snova said:**
> 
This is my perspective on things, as someone who simply likes to play: there are people who understand the art of .deb's well, and I am not one of them. I also think the group who does is vastly outnumbered by the group who doesn't. For a project to build their own packages, for every release made, for every package format supported, someone has to take the time to maintain the files necessary for the system to work, test them, and upload them in synchrony with the rest of the project's release. Ideally there might also be repositories available to improve the update process for the end user; this is yet another set of tools to learn and more server space to maintain. There are more than just two options (1. no packages at all and 2. well-maintained and properly packaged packages).

You can also have developers just occasionally create packages. They don't have to be maintained for every release or follow packaging standards meticulously. I'm sure a lot of end-users would appreciate *any* package to *no* package.

---

