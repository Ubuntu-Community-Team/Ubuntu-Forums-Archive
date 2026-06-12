---
title: "Would anyone be interested in helping to write this program?"
date: 2010-08-05
forum: The Cafe
---

### Post by Dustin2128 on 2010-08-05
The repositories have gotten better over the years, but still you'll run across that odd piece that you have to install via compiling. I used gentoo recently and liked the way they install software- it's all compiling. So, why not write this piece of software that's a GUI tool for compiling and installing programs? Basically you start the program, specify the directory of the package, set your compiling options (something gentoo-like, e.g. not having kde support if you don't use it), then choose user or root install. It decompresses the archive, puts a shell script for compilation (is that a word?) in the new directory and executes it. Do you think it would be a good idea, or has it already been done? If so, shouldn't it be in a default install?

---

### Post by theraje on 2010-08-05
Sounds like you want an IDE... there are plenty of those.

Or am I misunderstanding something?

---

### Post by aidenscool09 on 2010-08-05
I could have a try at making a shell script that asks where the directory is, goes there and starts compiling.

---

### Post by Cuddles McKitten on 2010-08-05
My only thought is that most people who would be interested in specifying very exact compiling instructions would be the types who can already compile their own programs and would be willing to do so the normal way.  It seems like anyone who'd use the graphical interface would just rather download something from Synaptic and be done with it rather than optimize the speed of the program by 1.2%.

The important thing is more whether or not you'd get something out of the project whether it be fun or learn something new.

---

### Post by Dustin2128 on 2010-08-05
> **Cuddles McKitten said:**
> My only thought is that most people who would be interested in specifying very exact compiling instructions would be the types who can already compile their own programs and would be willing to do so the normal way.  It seems like anyone who'd use the graphical interface would just rather download something from Synaptic and be done with it rather than optimize the speed of the program by 1.2%.

The important thing is more whether or not you'd get something out of the project whether it be fun or learn something new.
well the specifications of the compiling instructions would be under an advanced tab, the main thing about this program is that it would treat tarballs as software installation packages, which would be convenient for newbies.

---

### Post by Bachstelze on 2010-08-05
> **Dustin2128 said:**
> well the specifications of the compiling instructions would be under an advanced tab, the main thing about this program is that it would treat tarballs as software installation packages, which would be convenient for newbies.

It wouldn't work, because 1) you need to figure out the build dependencies, and 2) a lot of packages require non-standard compilation instructions.

I don't know how you think Gentoo's portage works, but it's probably more complicated than that.  For starters, each and every package has its own "building recipe" in a separate text file.  Adapting those to Ubuntu would not be trivial.

---

### Post by phrostbyte on 2010-08-05
That's exactly what portage (gentoo's package manager) is already. :) Well not a GUI, but it encapsulates the specifics of compiling a piece of software.

---

### Post by phrostbyte on 2010-08-05
> **Bachstelze said:**
> It wouldn't work, because 1) you need to figure out the build dependencies, and 2) a lot of packages require non-standard compilation instructions.

I don't know how you think Gentoo's portage works, but it's probably more complicated than that.  For starters, each and every package has its own "building recipe" in a separate text file.  Adapting those to Ubuntu would not be trivial.

Ubuntu (Debian) has that already, it's called the debian/rules file. :) debian/rules is simply a Makefile that describes how to build a package in an automated fashion.

---

### Post by Bachstelze on 2010-08-05
> **phrostbyte said:**
> Ubuntu (Debian) has that already, it's called the debian/rules file. :)

And someone has to write it.  What would be the point of making such a program if it could only build packages for which a rules files exists, meaning that the package in question probably exists as a DEB already?

---

### Post by phrostbyte on 2010-08-05
> **Dustin2128 said:**
> well the specifications of the compiling instructions would be under an advanced tab, the main thing about this program is that it would treat tarballs as software installation packages, which would be convenient for newbies.

It could work in all actuality. Because many (most?) FOSS packages use a very small number of build systems. You'd have to be able to sense autotools, cmake, plain Makefile, etc. Perhaps being able to scrape the dependencies from build system and alert the user and/or attempt to find them somehow.

Note: this would work for most tarballs out there, but there will always be people using exotic build systems that will confuse it. Dependency management is nontrivial as it is, scraping dependencies from a configure script and somehow finding them, well, good luck. :)

---

### Post by phrostbyte on 2010-08-05
> **Bachstelze said:**
> And someone has to write it.  What would be the point of making such a program if it could only build packages for which a rules files exists, meaning that the package in question probably exists as a DEB already?

Yes, it's almost impossible to make this work 100% of the time. Computer would have to be able do some extremely complex analysis to figure out how to build some things. It's rapidly degenerates into a general artificial intelligence problem. Kind of like the Linux kernel driver generator. :D

---

### Post by phrostbyte on 2010-08-05
Here is my first attempt:

```

#! /bin/sh

zenity --info --text "I am a friendly GUI doing friendly things."
./configure
make
make install
zenity --info --text "I have finished doing the things I was doing."

```

But really, I'm almost positive something like this (except 1000x better) exists. I vaguely remember some tool that could autogenerate a *.deb from a arbitrary tarball in many circumstances.

---

### Post by Dustin2128 on 2010-08-05
> **phrostbyte said:**
> Here is my first attempt:

```

#! /bin/sh

zenity --info --text "I am a friendly GUI doing friendly things."
./configure
make
make install
zenity --info --text "I have finished doing the things I was doing."

```
mm, the problem with this would be dependency resolution. Most tarballs do have a dependency list in the readme though, I suppose you might add
```
wget http://dependency1
``` of course the main problem with that is that you have to have an algorithm or something to search for the dependency list which adds a good bit of code. Or maybe you could have a readme reader that displays it in the program so you can wget the dependencies (also from within the program).

---

### Post by Bachstelze on 2010-08-05
> **Dustin2128 said:**
> mm, the problem with this would be dependency resolution. Most tarballs do have a dependency list in the readme though, I suppose you might add
```
wget http://dependency1
``` of course the main problem with that is that you have to have an algorithm or something to search for the dependency list which adds a good bit of code. Or maybe you could have a readme reader that displays it in the program so you can wget the dependencies (also from within the program).

This is simply not possible.  If it were, Gentoo wouldn't have so many people writing and maintaining ebuilds.

---

### Post by Shining Arcanine on 2010-08-05
> **Dustin2128 said:**
> The repositories have gotten better over the years, but still you'll run across that odd piece that you have to install via compiling. I used gentoo recently and liked the way they install software- it's all compiling. So, why not write this piece of software that's a GUI tool for compiling and installing programs? Basically you start the program, specify the directory of the package, set your compiling options (something gentoo-like, e.g. not having kde support if you don't use it), then choose user or root install. It decompresses the archive, puts a shell script for compilation (is that a word?) in the new directory and executes it. Do you think it would be a good idea, or has it already been done? If so, shouldn't it be in a default install?

Software is usually only installed according to the Filesystem Hierarchy Standard, which usually requires root privileges. While it is possible to install software without any root privileges, there is no standard for doing that, so making a distinction between "user installations" and "root installations" makes little sense. If you insist on doing things in a non-standard way, you will need to specify exactly what that non-standard way is.

Creating a package manager with the ability to arbitrarily install software in a manner in-compliant with the Filesystem Hierarchy Standard would be a non-trivial task, because it would likely require a custom repository. If you could find some way to adapt Gentoo's portage tree to this, then your job would immediately become much easier, but that likely would not be possible without support from Gentoo's developers, because the entire tree would likely need to be modified to support such a thing. To be realistic, I find it unlikely that they would want to do that, because while Gentoo is about flexibility, all of the people that want that level of customization would likely be compiling things on their own because user-installed software is outside of the scope of a the system package manager.

If you would be willing to give up such a feature, you could switch to Gentoo Linux. There are graphical front-ends available for its package manager:

[http://porthole.sourceforge.net/](http://porthole.sourceforge.net/)

> **theraje said:**
> Sounds like you want an IDE... there are plenty of those.

Or am I misunderstanding something?

He wants a GUI-based package manager that compiles everything from source. That is different than an IDE.

> **phrostbyte said:**
> That's exactly what portage (gentoo's package manager) is already. :) Well not a GUI, but it encapsulates the specifics of compiling a piece of software.

[http://porthole.sourceforge.net/](http://porthole.sourceforge.net/)

---

