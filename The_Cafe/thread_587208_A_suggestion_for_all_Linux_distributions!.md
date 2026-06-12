---
title: "A suggestion for all Linux distributions!"
date: 2007-10-22
forum: The Cafe
---

### Post by Martial-law on 2007-10-22
Hi,



Since there are a LOT of Linux distributions each using different type of environments and settings like some Gnome some KDE, some are Debian based and some are based on other and many other differences between them it is not very easy and beneficial for Software and Game developers to create native Linux software and Games due to the lack of a single platform. Having a single platform is the advantage Windows has and therefore it is easy and comfortable for developers for creating Software and Games for Windows only. I would like to suggest all Linux distributions to get together and remove this hurdle in order to pave way for developers to create software and games for Linux too. For this I would suggest them to create a single native Linux Emulator which could run on any  Linux distribution and run native Linux software and games. It should also be easier for the community to run the native Linux software and games on that Emulator. If that is made possible it would really be a boon for the entire Linux community for it would provide a single platform to Linux and developers would seriously consider to create software and games for Linux too. For LInux and its future it would be a far better option than Wine or Cedega the presently available emulators which only run Windows software and games giving further boost to the idea of developing just native Windows software and games to the developers. :)

---

### Post by DeadSuperHero on 2007-10-22
My suggestion is to be apt-based. It's just sensible to me. And easy for the user.

EDIT: I meant this as just a suggestion for Linux distros in general. But about your idea: why exactly an emulator? if it can already run Linux apps, why does it need to pretend to run linux apps (with the exception of a virtual test environment)

---

### Post by machoo02 on 2007-10-22
I think you are just slightly missing the point of emulators.  Emulators are designed to allow software from one operating system to be run on a *completely different one*.  When you say "Native Linux Emulator", it's basically an oxymoron: if an application is native to an operating system, then no emulator is required to run it!  Under the hood, virtually all Linux distributions are the same...the major difference among them all is really in the package management system.  What would be a better idea is the development of system-agnostic packages (like [autopackage]("http://www.autopackage.org/")) that would remove the hurdle of designing packages for X different distributions.

---

### Post by igknighted on 2007-10-22
> **Martial-law said:**
> Hi,



Since there are a LOT of Linux distributions each using different type of environments and settings like some Gnome some KDE, some are Debian based and some are based on other and many other differences between them it is not very easy and beneficial for Software and Game developers to create native Linux software and Games due to the lack of a single platform. Having a single platform is the advantage Windows has and therefore it is easy and comfortable for developers for creating Software and Games for Windows only. I would like to suggest all Linux distributions to get together and remove this hurdle in order to pave way for developers to create software and games for Linux too. For this I would suggest them to create a single native Linux Emulator which could run on any  Linux distribution and run native Linux software and games. It should also be easier for the community to run the native Linux software and games on that Emulator. If that is made possible it would really be a boon for the entire Linux community for it would provide a single platform to Linux and developers would seriously consider to create software and games for Linux too. For LInux and its future it would be a far better option than Wine or Cedega the presently available emulators which only run Windows software and games giving further boost to the idea of developing just native Windows software and games to the developers. :)

**cough** cygwin **cough**

---

### Post by Fbot1 on 2007-10-22
I think a standardized ABI would be easier.

---

### Post by Dimitriid on 2007-10-22
Well you don't even have to use GTK or QT if you dont want to use that "desktop integrations" in fact few games do.

As for installation and all, im sure many distros would be willing to work with closed source developers to create binaries for all different managers.  By "working with" id mean "Yes we will give you permission so you to do all the work and create a distro specific installer for our game"

---

### Post by frup on 2007-10-22
Not an emulator but a way to make QT apps and GTK apps work and look properly on the other DE with out it's libs installed.

---

### Post by -grubby on 2007-10-22
That would be nice but, it's like running an emulator of an OS on the native OS. Also, could you please use paragraphs, that's hard to read

---

### Post by Darkhack on 2007-10-22
> **Martial-law said:**
> it is not very easy and beneficial for Software and Game developers to create native Linux software and Games due to the lack of a single platform.

There are differences between distributions but all software should work just fine.

> **Martial-law said:**
> I would like to suggest all Linux distributions to get together and remove this hurdle in order to pave way for developers to create software and games for Linux too.

We have that.  It's called the [Linux Standards Base]("http://en.wikipedia.org/wiki/Linux_Standards_Base").  

> **Martial-law said:**
> For this I would suggest them to create a single native Linux Emulator which could run on any  Linux distribution and run native Linux software and games.

An emulator is used to run software on other platforms.  This topic can become confusing though because there is a lot of terminology and only slight differences between them.  An emulator translates the actual CPU calls into different ones.  Virtualization is the abstraction of hardware which makes the software think that it is running on its own machine.  The CPU calls are not translated, they are already native.  This just separates the computers resources so that it can run multiple operating systems.

> **Martial-law said:**
> For LInux and its future it would be a far better option than Wine or Cedega the presently available emulators which only run Windows software

If I were a WINE developer I would slap you silly.  Be thankful I'm not.  WINE is an acronym which stands for "Wine Is Not an Emulator".  WINE is actually just a port of the Windows API to Linux.  Cedega is the same thing.

---

### Post by rsambuca on 2007-10-22
Sorry to sound a little blunt here, but I really don't think you understand the basics of the linux operating system.  Basically, all of the current distros can run linux software, because they are all linux.

---

### Post by init1 on 2007-10-22
> **Martial-law said:**
> Hi,



Since there are a LOT of Linux distributions each using different type of environments and settings like some Gnome some KDE, some are Debian based and some are based on other and many other differences between them it is not very easy and beneficial for Software and Game developers to create native Linux software and Games due to the lack of a single platform. Having a single platform is the advantage Windows has and therefore it is easy and comfortable for developers for creating Software and Games for Windows only. I would like to suggest all Linux distributions to get together and remove this hurdle in order to pave way for developers to create software and games for Linux too. For this I would suggest them to create a single native Linux Emulator which could run on any  Linux distribution and run native Linux software and games. It should also be easier for the community to run the native Linux software and games on that Emulator. If that is made possible it would really be a boon for the entire Linux community for it would provide a single platform to Linux and developers would seriously consider to create software and games for Linux too. For LInux and its future it would be a far better option than Wine or Cedega the presently available emulators which only run Windows software and games giving further boost to the idea of developing just native Windows software and games to the developers. :)
Emulator? Emulator of what? I don't really understand. And also, Linux binaries usually run on all current Linux kernels. I could compile a game in Debian Gnome, and have it be played in Slackware KDE.

---

### Post by Frak on 2007-10-22
Cygwin and MinGW are good for developing and running Linux native apps in a Win32 based environment.

As for Linux, bridges can be made instead of emulators. Real software is faster than fake software.

You can run RPM's in Ubuntu, via [alien]("apt:alien"), and vice versa. KDE apps can be run in Gnome using QT and K libraries, while Gnome apps can be run in KDE environments using GTK and GTK+ libraries, or follow Firefox and use XUL.

If its a modern GNU/Linux Operating System, it can run modern Linux software.

---

### Post by Fbot1 on 2007-10-22
> **rsambuca said:**
> Sorry to sound a little blunt here, but I really don't think you understand the basics of the linux operating system.  Basically, all of the current distros can run linux software, because they are all linux.

...No, that's not quite right. Distros can't alway use other distro's executables.

---

### Post by rsambuca on 2007-10-22
> **Fbot1 said:**
> ...No, that's not quite right. Distros can't alway use other distro's executables.

You are right, but I was thinking more in terms of application software, which can be compiled on virtually any system.

---

### Post by Fbot1 on 2007-10-22
> **rsambuca said:**
> You are right, but I was thinking more in terms of application software, which can be compiled on virtually any system.

I guess but, I don't think there going to sell their source code.

---

### Post by Frak on 2007-10-22
> **Fbot1 said:**
> I guess but, I don't think there going to sell their source code.
Most will sell a binary compiler though.

---

### Post by Crashmaxx on 2007-10-23
> **Frak said:**
> Most will sell a binary compiler though.

Can you explain what you are referring to by 'binary compiler'?

---

### Post by cogadh on 2007-10-23
Okay, there are a few misunderstandings going on here:
[LIST=1]
[*]*Emulator* - An emulator does not just emulate an OS, it creates an entire virtual environment, right down to virtual representation of hardware devices to "fool" a particular piece of software into thinking it is running in its native environment. Examples of emulators would be MAME (arcade machine emulator), Mupen64 (Commodore 64 emulator) or Gens (Sega Genesis emulator).
[*]*Software can't be installed across distros* - This is just flat out wrong. If a piece of Linux software is in RPM format, it can be installed on virtually any Linux distro, including Ubuntu. If a piece of software is in DEB format, it can be installed on any Debian based distro. If a piece of software is available in neither, then it is likely source code instead of an install package, which can be compiled and installed on *every* Linux distro.
EDIT - Forgot about the occasional installation that comes as a ".run" file, these can also be installed on every Linux distro.
[*]*Availability of source code* - Practically every Linux-based software is free and open source, meaning you can download the source code and compile the application yourself. There are exceptions, but they are rare.
[/LIST]
There is absolutely no need for a Linux emulator to run Linux software in Linux, that's just silly.

---

### Post by avik on 2007-10-23
> **cogadh said:**
> Mupen64 (Commodore 64 emulator) 

Actually, Mupen64 is an N64 emulator.  But I agree with all your points.  I don't understand the OP's use of emulator.

Also, most software, even if it doesn't come with the source  code, will have a binary for the different architecture (i386, amd64, etc., which is necessary for Windows as well), as well as specific packages for the different distributions.  The specific packages are not required, and many commercial programs, especially games like Wolfenstein: Enemy Territory don't come packaged this way.

The distribution-specific packages, in addition to being unnecessary, can also be created with anyone with access to the binaries.  So there is absolutely no hurdle to creating software for GNU/Linux in terms of packaging and distribution.

---

### Post by bikeboy on 2007-10-23
Everyone has already covered most points, LSB etc., but I have one to add. We also have the [Portland Project](http://portland.freedesktop.org/wiki/) which is aiming to be the solution to the problem of different APIs and libs across different Linux environments.

---

### Post by Frak on 2007-10-23
> **Crashmaxx said:**
> Can you explain what you are referring to by 'binary compiler'?
.run files are precompiled binaries that recompile later for different platforms.

---

