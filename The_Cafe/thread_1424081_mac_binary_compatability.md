---
title: "mac binary compatability"
date: 2010-03-07
forum: The Cafe
---

### Post by chris200x9 on 2010-03-07
Hi, I'm just wondering could I achieve mac binary compatability by running pure darwin with GNUstep? There is no real reason for this, I am just wondering, I would try it myself but I do not have a free partition.

---

### Post by RiceMonster on 2010-03-07
I don't think it will work. You need Aqua or whatever the Mac window system is called.

---

### Post by DeadSuperHero on 2010-03-07
This has been discussed before on UF, but the short answer is: no, unfortunately it doesn't work that way. 

While GNUStep maintains compatibility with the old NEXTSTEP libraries, and Darwin is the lower level of the Mac OSX platform, there are some proprietary bits missing still. Quartz, CoreAnimation, components of Cocoa, to name a few.

In theory, enough reverse engineering could give way to something akin to the WINE project, but for the time being such a task is impossible.

Furthermore, another problem is that Apple tethers MacOSX to their platform in interesting legal ways. While you can run OSX on a PC via OSX86, the fact of the matter is that you cannot legally run specific MacOSX applications on a non-Apple computer and on a non-Apple operating system.

---

