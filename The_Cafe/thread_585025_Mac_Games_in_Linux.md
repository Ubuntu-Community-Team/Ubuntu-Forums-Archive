---
title: "Mac Games in Linux?"
date: 2007-10-21
forum: The Cafe
---

### Post by Martial-law on 2007-10-21
Hi,



Just wish to know if Mac games could be played in Linux. You may think that this is a stupid question but I am asking this because since both Mac and Linux are based on Unix may be its possible to run Mac games in Linux. Is that possible? Kindly confirm. Thanks:)

---

### Post by hessiess on 2007-10-21
mac softwere will only run on mac

---

### Post by jwhiz on 2008-10-13
This is NOT a stupid question.
One of the reasons people consider making Linux their main OS is that they can continue to run many apps, either with open source versions, virtual machines/other OS or emulators.
I would love to play the games I bought for my G4 PowerBook. However, it runs so damn hot that I just stopped. 
How cool (ha!) would it be to either have a fast emulator, something like Darwin that ran on Linux or a fast virtual machine to play Myst, Lego Star Wars (Mac), Blizzard's cool games, old Titanic (with functioning disks!) etc. etc. etc. on a x86 tower that I already own, or another cheap one, instead of putting everything away and hoping there will always be a way to run OS9/OSX 1-3.9 on the expensive Apple tower I want to have some day?!...
Forums are for questions.
:popcorn:

---

### Post by jimi_hendrix on 2008-10-13
semi on topic question

theres a game everyone at my school plays that i believe is a binary file.  will this compile under linux since they are both unix?

---

### Post by zmjjmz on 2008-10-13
In short: No.
In length: While it's possible to run BSD binaries on Linux (and vice-versa), Apple uses a proprietary graphics interface which would make it impossible to display properly.

---

### Post by jimi_hendrix on 2008-10-13
ok thanks

---

### Post by MaxIBoy on 2008-10-13
> **zmjjmz said:**
> In short: No.
In length: While it's possible to run BSD binaries on Linux (and vice-versa), Apple uses a proprietary graphics interface which would make it impossible to display properly.

It's the DarwinBSD equivalent of Gtk+ or Qt, as far as I know (could be wrong about that though.)

There's no reason why a WINE-like project wouldn't be started to get the programs to work under Linux, except for the hilarious reason that Macs don't have enough of a market share to make it worthwhile.

---

### Post by zmjjmz on 2008-10-13
> **MaxIBoy said:**
> It's the DarwinBSD equivalent of Gtk+ or Qt, as far as I know (could be wrong about that though.)

There's no reason why a WINE-like project wouldn't be started to get the programs to work under Linux, except for the hilarious reason that Macs don't have enough of a market share to make it worthwhile.

Actually it's more like 
X = Quartz
WM = Quartz (it's built in)
Toolkit = Cocoa

All proprietary mind you, so it would be really hard to get it running.

---

### Post by eragon100 on 2008-10-13
> **zmjjmz said:**
> Actually it's more like 
X = Quartz
WM = Quartz (it's built in)
Toolkit = Cocoa

All proprietary mind you, so it would be really hard to get it running.

But Mac users have always been able to run linux / UNIX apps by installing X11, right?

Also, terminal programs do often work on linux, don't they? (like shell scripts, because terminal commands are the same.)

---

### Post by zmjjmz on 2008-10-13
> **eragon100 said:**
> But Mac users have always been able to run linux / UNIX apps by installing X11, right?

Also, terminal programs do often work on linux, don't they? (like shell scripts, because terminal commands are the same.)

X11 is OSS, so they can do that.

And terminal scripts would work providing that the script doesn't call on any unavailable programs.

---

### Post by aeiah on 2008-10-13
> **MaxIBoy said:**
> 
There's no reason why a WINE-like project wouldn't be started to get the programs to work under Linux, except for the hilarious reason that Macs don't have enough of a market share to make it worthwhile.

that and apple habit of suing and censoring everything it wishes

---

### Post by zmjjmz on 2008-10-13
> **aeiah said:**
> that and apple habit of suing and censoring everything it wishes

Not that that would matter.
Apple would have no real case against them, and neither does MS.

---

### Post by MaxIBoy on 2008-10-13
Microsoft has tried more than once to sue WINE, and both times they failed.

Actually, Apple has tried more than once to sue Microsoft, and it only won once.

---

### Post by smartboyathome on 2008-10-13
There is GNUStep which can emulate some Cocoa code, but not Quartz. It would not be much profit for it, since the only things which run on a mac that don't on windows (generalization here, yes, I know it isn't a rule) is graphics/movie production software, and even those are sparse.

---

### Post by Sinkingships7 on 2008-10-13
> **MaxIBoy said:**
> Microsoft has tried more than once to sue WINE, and both times they failed.

Which is a stupid attempt in the first place. WINE is pure reverse engineering. They didn't steal anything. Not much of a case there ;)

---

### Post by bashveank on 2008-10-13
> **zmjjmz said:**
> In short: No.
In length: While it's possible to run BSD binaries on Linux (and vice-versa), Apple uses a proprietary graphics interface which would make it impossible to display properly.

If it calls X11 than it'll be fine as X is installed by default in Leopard.

---

### Post by zmjjmz on 2008-10-13
> **bashveank said:**
> If it calls X11 than it'll be fine as X is installed by default in Leopard.

We're talking about running them in Linux.

---

### Post by Frak on 2008-10-13
OpenGL - Possible, very possible, in fact, can be done
Quartz - No game uses Quartz; it would be like using a toaster to cook an egg.
Quartz Extreme - Look above
Cocoa - As soon as somebody gets complete reverse-engineering, we get the next part completed.
Carbon - Mainly used only for legacy apps; not needed for newer games
X - We have X
AppleScript - Parts of the source are on the internet. The rest could be R-E.

All I can think of ATM. The only way I can think of is using mac-on-linux to create a passthrough (meaning direct access to graphics). Only works on PPC machines though (G3 and G4).

---

### Post by FlyingIsFun1217 on 2008-10-13
> **Sinkingships7 said:**
> Which is a stupid attempt in the first place. WINE is pure reverse engineering. They didn't steal anything. Not much of a case there ;)

Unless there's something in an EULA that prohibits reverse-engineering, no? I would think that would protect it (the program in question), but maybe I'm wrong.

FlyingIsFun1217

---

### Post by DeadSuperHero on 2008-10-13
@Frak:

Actually, Quartz and Quartz Extreme are sort of like the OpenGL layers as well. Although I assume 3D is possible without them, the compositors also work with OpenGL rendering and shading. There are some differences, such as the Mac version of OpenArena 0.8.0, which looks alot smoother than the Linux counterpart (although this can be debatable, after all, one can always crack open Linux's calls to OpenGL and tweak various things)

---

### Post by MaxIBoy on 2008-10-14
> **FlyingIsFun1217 said:**
> Unless there's something in an EULA that prohibits reverse-engineering, no? I would think that would protect it (the program in question), but maybe I'm wrong.

FlyingIsFun1217

The way it works is, one person figures out what each part of the API is *supposed* to do, trying as hard as possible to avoid figuring out *how* it's done. Then the person writes out a complete specification, detailing the kind of input that piece of code takes and the kind of output it's liable to give. Then an entirely seperate group of programmers write code that does the same thing, but often works differently "under the hood." People in this group of programmers usually haven't agreed to the EULA or installed Windows. 

This is called "clean room" reverse engineering.


I bet I got at least one crucial detail horribly wrong, but you get the idea.

---

### Post by Frak on 2008-10-14
> **Mr. Psychopath said:**
> @Frak:

Actually, Quartz and Quartz Extreme are sort of like the OpenGL layers as well. Although I assume 3D is possible without them, the compositors also work with OpenGL rendering and shading. There are some differences, such as the Mac version of OpenArena 0.8.0, which looks alot smoother than the Linux counterpart (although this can be debatable, after all, one can always crack open Linux's calls to OpenGL and tweak various things)
I am aware. Though, like I said before, it is like frying an egg in a toaster. It makes more sense to just run a game via OpenGL and some simple window functions (maximize, restore, full-screen).

---

### Post by MetaDark on 2010-09-11
If they made a Wine-like emulator for Mac they should call it Mace
( **Mac** **E***mulator* )

---

### Post by Sutekh849 on 2010-09-11
> **MetaDark said:**
> If they made a Wine-like emulator for Mac they should call it Mace
( **Mac** **E***mulator* )
**W**INE **I**s **N**ot an **E**mulator
and neither would the project described be.

---

### Post by Naiki Muliaina on 2010-09-11
[IMG]http://cdn3.knowyourmeme.com/i/28424/original/thread_necromancer.png?1259372109[/IMG]

2 years since last post, good goins ;)

---

### Post by Someone uk on 2010-09-11
hmm maybe mac compatibility should be added to the unified kernel imagine an os that runs all 3 os applications

---

### Post by DeadSuperHero on 2010-09-11
People seem to always make the mistake of thinking that just because an app uses OpenGL, it can easily be ported to Linux.

But nobody ever accounts for the sheer amount of Objective-C code a lot of these native apps are using through Cocoa APIs, and Apples various libraries they've developed to facilitate Mac-native game development.

To even port an OpenGL game over, it requires much more than just OpenGL. :P

---

### Post by MetaDark on 2010-09-11
> **Sutekh849 said:**
> **W**INE **I**s **N**ot an **E**mulator
and neither would the project described be.

Wine was actually initially called **WIN***dows* **E***mulator*

I also do not see how it is not an emulator, An emulator in computer sciences duplicates (provides an emulation of) the functions of one system using a different system, so that the second system behaves like (and appears to be) the first system.

That is exactly what Wine does and that is what "Mace" could be.

---

### Post by QwUo173Hy on 2010-09-11
Isn't there an open-sourced Mac OS available? Maybe some of the older games would run on that. It would be another OS on your system of course.

---

### Post by DeadSuperHero on 2010-09-11
> **jarlath said:**
> Isn't there an open-sourced Mac OS available? Maybe some of the older games would run on that. It would be another OS on your system of course.

Darwin is only the lower half of the system; it does not account for the proprietary API's such as Cocoa. There's been some interesting work on Darwin done such as [PureDarwin]("http://www.puredarwin.org/"), but hardware support is somewhat lacking.

On the other side of the coin, you have [NextStep's]("http://en.wikipedia.org/wiki/NextStep") APIs and libraries, which Cocoa is partially based off of. (Objective-C and what have you.) [GnuStep]("http://www.gnustep.org/") and [Etoile]("http://etoileos.com/") are two big contributors to Objective-C and NextStep compatibility in Free Software. In theory, it may one day be possible to at least port a program with Cocoa code from MacOS to Linux, but there's still a lot of preliminary work to be done unfortunately.

I too, would love to see an Open Source project that integrates all of the open code projects started up by Apple.

---

### Post by 3rdalbum on 2010-09-11
> **jarlath said:**
> Isn't there an open-sourced Mac OS available?

You are thinking of Darwin. It does not run Mac OS applications. It doesn't use Mac OS APIs.

The kernel ie not the important part for creating a compatibility layer - the APIs and system services are important. Just because Linux and OS X use some of the same concepts (root, permissions, the forward-slash path delimiter) does not mean that programs are interchangeable. Android runs a Linux kernel but that doesn't mean that you can run Rhythmbox on your phone, because the infrastructure like Gstreamer, Gnome, X11 are missing.

---

### Post by murderslastcrow on 2010-09-11
They do have ffmpeg and gstreamer running in certain applications for Android- the libraries aren't incompatible, but they need to be patched through to the Java applications. So to a degree there is integration in Android, but there are serious limitations compared to, say, MeeGo.

The thing with Mac GAMES is that most games use programming languages and graphics libraries that work on Mac and Linux, as there aren't many typically used languages/libraries that Linux doesn't support but OS X does.

So the real question is how hard it would be for those companies to port their applications to Linux (or how hard it WOULDN'T be). As a software developer, I think that creating software without portability in mind is lazy and unprofessional. I don't get why people are hired to make things that are difficult to move around when everything has become so much better for cross-platform programmers these days.

The largest issue I can see it following several different HIGs for different environments.

---

### Post by 3rdalbum on 2010-09-12
Source compatibility as a best-possible-scenario, though; not binary compatibility. Source compatibility means nothing if the developer won't release the source and won't bother to compile it on Linux.

---

### Post by ringo28 on 2011-12-26
all te emulator a like is not needed.. Linux is like Belgium...., they think the same but talk different. there is too much distribution... no like in every distribution a standard model suitable for a non-geek.. its too diffecult for non-geeks, so there comes not a prograsms on commerciale role.., if al linux has a standard model too work and install programms especially too work with non-geeks.. mayby more people get linux, so more big cooperation makes more drivers voor linux...., first make it easy for all.(not too easy) and then you dont need wine or something else.., you must atract Big-money and people...

---

### Post by jwbrase on 2011-12-26
You realize this thread had been dead for more than a year?

---

### Post by mips on 2011-12-26
> **jwbrase said:**
> You realize this thread had been dead for more than a year?

I don't even have a clue as to what he was trying to say :lolflag:

---

### Post by coffeecat on 2011-12-26
Old thread. Closed.

---

