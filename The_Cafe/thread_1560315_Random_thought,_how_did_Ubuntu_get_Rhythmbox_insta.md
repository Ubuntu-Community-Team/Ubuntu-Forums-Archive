---
title: "Random thought, how did Ubuntu get Rhythmbox installed anyway?"
date: 2010-08-24
forum: The Cafe
---

### Post by LinuxFox on 2010-08-24
I was just bored so I downloaded Rhythmbox (same version included) and tried to compile it to my home folder (so I don't overwrite it).  Oddly enough, I was missing dependencies when I tried to compile it.

It just kind of makes me wonder, how did the player get on Ubuntu with those missing dependencies.

Just a thought, not a tech question since I'm having no trouble at all.  It just made me think.

---

### Post by Austin25 on 2010-08-24
Well, maybe it uninstalled something(s) only it depended on when you uninstalled it the first time.

---

### Post by bunburya on 2010-08-24
I had the same thing recently... I can't remember which packages they were, but a few days ago I decided to try and download the source of a few packages I already have installed and compile them, just to get myself used to compiling from source. Oddly enough the compiling seemed to fail for lack of dependencies.

I'm guessing it's just looking in the wrong place for the dependencies? But then I know nothing about compiling, so...

---

### Post by Austin25 on 2010-08-24
I know! You had runtime libraries when you needed development libraries.

---

### Post by LinuxFox on 2010-08-24
> **Austin25 said:**
> I know! You had runtime libraries when you needed development libraries.Then maybe I guess the people working on Ubuntu must remove them after the software is compiled.  It's only a guess.

---

### Post by FuturePilot on 2010-08-24
The dependencies you were missing when you tried to compile it were the -dev packages which contain header files and such needed to compile stuff. They are not needed to actually run the program.

---

### Post by LinuxFox on 2010-08-24
> **FuturePilot said:**
> The dependencies you were missing when you tried to compile it were the -dev packages which contain header files and such needed to compile stuff. They are not needed to actually run the program.Yeah, a post before mentioned that.  It makes me wonder if Ubuntu uses the -dev dependencies to compile it and then remove them afterwards.

Anyway, thanks for the answers, it just had me thinking.

---

### Post by FuturePilot on 2010-08-24
> **LinuxFox said:**
> Yeah, a post before mentioned that.  It makes me wonder if Ubuntu uses the -dev dependencies to compile it and then remove them afterwards.

Anyway, thanks for the answers, it just had me thinking.

When a package is compiled it is compiled on a [buildd]("http://www.debian.org/devel/buildd/"). All of the necessary build-depends are installed on the buidd and then removed afterwards.

---

### Post by LinuxFox on 2010-08-24
> **FuturePilot said:**
> When a package is compiled it is compiled on a [buildd]("http://www.debian.org/devel/buildd/"). All of the necessary build-depends are installed on the buidd and then removed afterwards.Then that answers my question.  Thanks.

---

### Post by phrostbyte on 2010-08-24
There is more then one kind of dependency in the software world:

Runtime dependencies - What everyone using the software needs installed.

Build dependencies - Dependencies only needed to compile the program.

Test dependencies - Dependencies needed in automated tests.

When you make a Debian package, you have to specify the build dependencies, but these are invisible to the end user unless they do (apt-get builddep <package name>).

---

