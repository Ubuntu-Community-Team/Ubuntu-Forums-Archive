---
title: "What the heck is lipo!?!? (compiling darwin)"
date: 2009-10-24
forum: The Cafe
---

### Post by dragos240 on 2009-10-24
harley@linux:~/darwin$ ./archs.sh 
./archs.sh: 7: lipo: not found
./archs.sh: 8: lipo: not found
./archs.sh: 9: lipo: not found
./archs.sh: 10: lipo: not found

 make
*** Making all in darwinbuild ***
../archs.sh: 7: lipo: not found
../archs.sh: 8: lipo: not found
../archs.sh: 9: lipo: not found
../archs.sh: 10: lipo: not found
make[1]: Entering directory `/home/harley/darwin/darwinbuild'

Anyone know what this is?

---

### Post by schauerlich on 2009-10-24
You're trying to compile Darwin?

Oh dear...

---

### Post by dragos240 on 2009-10-24
Heheh. I like to compile stuff. Anyone know where I can get this "lipo" program?

---

### Post by schauerlich on 2009-10-24
Also:

[http://www.google.com/search?client=safari&rls=en&q=lipo+darwin&ie=UTF-8&oe=UTF-8](http://www.google.com/search?client=safari&rls=en&q=lipo+darwin&ie=UTF-8&oe=UTF-8)

---

### Post by Bachstelze on 2009-10-24
> **EDavidBurg said:**
> You're trying to compile Darwin **on Linux**?

Oh dear...

Fixed that for you.

---

### Post by dragos240 on 2009-10-24
Anyone know where I can get it??

---

### Post by Bachstelze on 2009-10-24
> **dragos240 said:**
> Anyone know where I can get it??

Do you honestly think you can build Darwin on Linux? Of course you can't, just like you can't build FreeBSD, or Windows.

---

### Post by schauerlich on 2009-10-24
1) Download PureDarwin
2) Install PureDarwin
3) Retain your sanity
4) ???
5) PROFIT

---

### Post by -grubby on 2009-10-24
> **dragos240 said:**
> Heheh. I like to compile stuff.

That hobby could get painful fast.

---

### Post by dragos240 on 2009-10-24
> **EDavidBurg said:**
> 1) Download PureDarwin
2) Install PureDarwin
3) Retain your sanity
4) ???
5) PROFIT

I've been trying to do that for ages. It says I need a working darwin system.

---

### Post by dragos240 on 2009-10-25
Ohai. Move to the general support. It's now a support question. I asked 'what is lipo?'. But now I need to find out how to get it.

---

### Post by Warpnow on 2009-10-25
Just download the PureDarwin ISO.

Not that I can see why you'd want to. Would be much more fun to toy with HURD imo, as it has a slightly better chance of ever being usable day to day.

---

### Post by dragos240 on 2009-10-25
> **Warpnow said:**
> Just download the PureDarwin ISO.

Not that I can see why you'd want to. Would be much more fun to toy with HURD imo, as it has a slightly better chance of ever being usable day to day.

Even Stallman said that he doesn't think that'll be going anywhere. I should know. I asked him at software freedom day.

---

### Post by The Toxic Mite on 2009-10-25
[quote=Wikipedia]**lipo** is a [Mac OS X]("http://en.wikipedia.org/wiki/Mac_OS_X") [command line]("http://en.wikipedia.org/wiki/Command_line") utility for the manipulation of [Mach-O]("http://en.wikipedia.org/wiki/Mach-O") [universal binary]("http://en.wikipedia.org/wiki/Universal_binary") [object files]("http://en.wikipedia.org/wiki/Object_file"). lipo performs [nondestructive]("http://en.wikipedia.org/w/index.php?title=Nondestructive&action=edit&redlink=1") manipulations of the file. It can show info on the file or extract a particular [executable]("http://en.wikipedia.org/wiki/Executable") format into a new file.[/quote]

That should answer your question ;)

---

### Post by Bachstelze on 2009-10-25
> **dragos240 said:**
> Ohai. Move to the general support. It's now a support question. I asked 'what is lipo?'. But now I need to find out how to get it.

/facepalm

I told you you can't build Darwin on Linux.

---

### Post by crazedgremlin on 2009-10-25
> **Bachstelze said:**
> /facepalm

I told you you can't build Darwin on Linux.

Why can't you build Darwin on Linux?

---

### Post by Tipped OuT on 2009-10-25
> **dragos240 said:**
> Even Stallman said that he doesn't think that'll be going anywhere. I should know. I asked him at software freedom day.

Wow, you've actually talked to Stallman? Cool.

---

### Post by Bachstelze on 2009-10-25
> **crazedgremlin said:**
> Why can't you build Darwin on Linux?

Because Darwin is Darwin, and Linux is Linux. You can't build FreeBSD or Windows in Linux, either. As the thread demonstrates, the build process relies on Darwin-specific command and functions.

---

### Post by RATM_Owns on 2009-10-25
What is lipo?

Well, it's when people feel that they're too overweight.
It's a special procedure that can remove fat from many different parts of the body.

---

### Post by dragos240 on 2009-10-25
> **Bachstelze said:**
> /facepalm

I told you you can't build Darwin on Linux.

Nothing is impossible. You think I can find the source to the tools needed to build darwin. I think it can be done with a few headaches.

---

### Post by Jesus_Valdez on 2009-10-25
Some things are impossible.

---

### Post by CJ Master on 2009-10-25
Do it in a virtual machine. That way you are technically compiling it while using Linux.

---

### Post by schauerlich on 2009-10-25
> **dragos240 said:**
> Nothing is impossible. You think I can find the source to the tools needed to build darwin. I think it can be done with a few headaches.

Good luck. You'll need it.

> **CJ Master said:**
> Do it in a virtual machine. That way you are technically compiling it while using Linux.

A virtual machine of what?

---

### Post by Tipped OuT on 2009-10-25
> **CJ Master said:**
> Do it in a virtual machine. That way you are technically compiling it while using Linux.

/fail

---

### Post by forrestcupp on 2009-10-25
> **CJ Master said:**
> Do it in a virtual machine. That way you are technically compiling it while using Linux.

I don't think you can run MacOS in a vm.

Hey, if dragos thinks he can do it, let him try.

---

### Post by schauerlich on 2009-10-25
> **forrestcupp said:**
> I don't think you can run MacOS in a vm.

I suppose if he wanted to, he could try installing PureDarwin Nano in a VM. I'm not sure just how Nano it is, though. It may not include all of the build tools needed.

---

### Post by dragos240 on 2009-10-25
> **Tipped OuT said:**
> /fail

Win ;)

---

### Post by jaxxstorm on 2009-10-25
> **dragos240 said:**
> Nothing is impossible. You think I can find the source to the tools needed to build darwin. I think it can be done with a few headaches.

Forgive me if I'm wrong, but you're trying to build a kernel *on* a kernel?

That just won't work.

---

### Post by schauerlich on 2009-10-25
> **jaxxstorm said:**
> Forgive me if I'm wrong, but you're trying to build a kernel *on* a kernel?

Darwin is more than just a kernel. It's more similar to the base system of *BSD.

---

### Post by dragos240 on 2009-10-25
> **jaxxstorm said:**
> Forgive me if I'm wrong, but you're trying to build a kernel *on* a kernel?

That just won't work.

Come again? Do you mean I am building a the darwin kernel while using the linux kernel? If so, how could that not work??

---

### Post by jaxxstorm on 2009-10-25
> **EDavidBurg said:**
> Darwin is more than just a kernel. It's more similar to the base system of *BSD.

Well yeah but it includes a Kernel.

> **dragos240 said:**
> Come again? Do you mean I am building a the darwin kernel while using the linux kernel? If so, how could that not work??


Well you're building them on top of each other. the kernel has access to parts of your hardware. What you're essentially doing is

[CENTER]Darwin Kernel + OS
       |
Linux Kernel + OS
       |
Hardware[/CENTER]

Which as far as I'm aware just won't work. The kernel will need direct access to your hardware components, it provides device drivers and all other manner of wizardry

---

### Post by schauerlich on 2009-10-25
> **jaxxstorm said:**
> The kernel will need direct access to your hardware components, it provides device drivers and all other manner of wizardry

I don't think that's what he's trying to do. He wants to compile Darwin, and then install it on another partition. The problem is, Linux doesn't have the build tools necessary to compile Darwin to start with. It pretty much needs to be built from OS X or an already existing existing Darwin install.

---

### Post by dragos240 on 2009-10-25
> **EDavidBurg said:**
> I don't think that's what he's trying to do. He wants to compile Darwin, and then install it on another partition. The problem is, Linux doesn't have the build tools necessary to compile Darwin to start with. It pretty much needs to be built from OS X or an already existing existing Darwin install.

Are the tools needed to build darwin open source? A large part of osx is.

---

### Post by Skripka on 2009-10-25
> **dragos240 said:**
> Nothing is impossible. You think I can find the source to the tools needed to build darwin. I think it can be done with a few headaches.

Isn't this how most Darwin Awards start?


PS-WAM!  Pun unintentional!

---

### Post by dragos240 on 2009-10-25
> **Skripka said:**
> Isn't this how most Darwin Awards start?


PS-WAM!  Pun unintentional!

Ah. The darwin awards. People helping to improve the gene pool........ by removing themselves from it.

---

### Post by schauerlich on 2009-10-25
> **dragos240 said:**
> Are the tools needed to build darwin open source? A large part of osx is.

These are all good questions for google. As I said: Happy hacking.

---

### Post by renkinjutsu on 2009-10-25
> **dragos240 said:**
> harley@linux:~/darwin$ ./archs.sh 
./archs.sh: 7: lipo: not found
./archs.sh: 8: lipo: not found
./archs.sh: 9: lipo: not found
./archs.sh: 10: lipo: not found

 make
*** Making all in darwinbuild ***
../archs.sh: 7: lipo: not found
../archs.sh: 8: lipo: not found
../archs.sh: 9: lipo: not found
../archs.sh: 10: lipo: not found
make[1]: Entering directory `/home/harley/darwin/darwinbuild'

Anyone know what this is?

how are you building Darwin on linux?
I thought Darwin needed it's build environment to be on a UFS volume, and the linux kernel only has read-only support for it?


edit: [pureDarwin on vm]("http://7447233378926839072-a-puredarwin-org-s-sites.googlegroups.com/a/puredarwin.org/puredarwin/screenshots/pd-vmwareplayer.png?attachauth=ANoY7cqm071Egg7Kq12ikVr0BZvoxPSosxE78ylp4o-9wjDGChz2MJQFRw2ckEg9zqkphfIaBH3dDX-Ii7EgboP0qHXXkt2negmi13gzpH9764z-7aQYA5soH2QHNLV4QcQ4EIBXZvuTztmJYrqAw7NGlrDEqsumKdVblKGbjz1FAtL8C2mZ40JnPt_-y82fdHsmFpSuE9KPKB0EkCKBKkR3WnxEqrJBDOonOU5sKnkBcrorAgPrmWI%3D&attredirects=0")
So, what are you going to do exactly, after you compile?

---

### Post by forrestcupp on 2009-10-26
> **EDavidBurg said:**
> It pretty much needs to be built from OS X or an already existing existing Darwin install.

How did they compile it the first time? :)

---

### Post by schauerlich on 2009-10-26
> **forrestcupp said:**
> How did they compile it the first time? :)

How was the first compiler compiled? :)

This is pure conjecture, but I'm guessing they built on on a NeXTSTEP system (since Darwin was based off of that). What was NeXTSTEP built on? No idea.

---

### Post by koenn on 2009-10-26
> **EDavidBurg said:**
> How was the first compiler compiled? :)

it was build, with an assembler

---

### Post by tuahaa on 2009-10-26
I thought this was a debate on evolution.

---

### Post by schauerlich on 2009-10-26
> **koenn said:**
> it was build, with an assembler

I know, it was a joke. Hence the smiley. :)

---

### Post by RiceMonster on 2009-10-26
> **tuahaa said:**
> I thought this was a debate on evolution.

Ba-doom-chsssss

---

### Post by nubimax on 2009-10-26
Dragos 240 you are a constant delight to me in my declining years.
Best regards M.

---

### Post by dragos240 on 2009-10-26
> **nubimax said:**
> Dragos 240 you are a constant delight to me in my declining years.
Best regards M.

Eh? How am I a delight? ;)

---

### Post by Excedio on 2009-10-26
> **dragos240 said:**
> Eh? How am I a delight? ;)
 
Isn't it enough that you are. :-)

---

### Post by dragos240 on 2009-10-26
> **Excedio said:**
> Isn't it enough that you are. :-)

I suppose. :D

---

### Post by forrestcupp on 2009-10-26
> **dragos240 said:**
> Eh? How am I a delight? ;)

We get a good laugh out of you. :)

---

### Post by dragos240 on 2009-10-26
> **forrestcupp said:**
> We get a good laugh out of you. 
:)

Well. That makes sense!

---

### Post by sliketymo on 2009-10-26
> **dragos240 said:**
> harley@linux:~/darwin$ ./archs.sh 
./archs.sh: 7: lipo: not found
./archs.sh: 8: lipo: not found
./archs.sh: 9: lipo: not found
./archs.sh: 10: lipo: not found

 make
*** Making all in darwinbuild ***
../archs.sh: 7: lipo: not found
../archs.sh: 8: lipo: not found
../archs.sh: 9: lipo: not found
../archs.sh: 10: lipo: not found
make[1]: Entering directory `/home/harley/darwin/darwinbuild'

Anyone know what this is?

:popcorn:liposuction-suction

---

### Post by dragos240 on 2009-10-26
> **sliketymo said:**
> :popcorn:liposuction-suction
>.>

---

### Post by stinger30au on 2009-10-26
lipo

lithium polymer batteries

if not charged correctly the explode and catch on fire

very spectacular to watch

many videos on youtube of this

---

### Post by Machnikowski on 2009-10-26
Trying is the first step toward failure.

The lesson: Don't try.

---

### Post by CJ Master on 2009-10-26
Lipo SUCKS!


[/cornyjoke]

---

### Post by Frak on 2009-10-26
> **EDavidBurg said:**
> How was the first compiler compiled? :)

This is pure conjecture, but I'm guessing they built on on a NeXTSTEP system (since Darwin was based off of that). What was NeXTSTEP built on? No idea.

I know the first C compiler was a mini compiler that could only compile enough C to create a compiler written in C.

For your question on NeXTSTEP, it was compiled on BSD. In the development builds, you can get your hands on some build notes that describe the build process. EDIT: Just checked, development builds of Rhapsody also say they were built on BSD.

As for the OP:
Why do you need lipo?

To answer your question, lipo involves a multitude of tools that Linux doesn't *have*.

---

### Post by Skripka on 2009-10-26
> **Frak said:**
> I know the first C compiler was a mini compiler that could only compile enough C to create a compiler written in C.

For your question on NeXTSTEP, it was compiled on BSD. In the development builds, you can get your hands on some build notes that describe the build process. EDIT: Just checked, development builds of Rhapsody also say they were built on BSD.

As for the OP:
Why do you need lipo?

To answer your question, lipo involves a multitude of tools that Linux doesn't *have*.

Party Pooper.  Nothing is impossible! ;)

---

### Post by Frak on 2009-10-26
> **Skripka said:**
> Party Pooper.  Nothing is impossible! ;)
It is possible. All the tools needed are open source and able to be ported. It's just... well...

Why spend years to compile tools to compile tools in able to compile an OS. :P

---

### Post by forrestcupp on 2009-10-27
> **Frak said:**
> It is possible. All the tools needed are open source and able to be ported. It's just... well...
dragos, it looks like you'd better get to work and start porting it to work with Linux.

---

### Post by KiwiNZ on 2009-10-27
@dragos240

As many have counseled this will not work using the methods you are using. I suggest you jump over to any Darwin Forums to discuss this.

I am closing this thread

---

