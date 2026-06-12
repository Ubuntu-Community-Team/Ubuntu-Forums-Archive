---
title: "Debian packages."
date: 2010-01-24
forum: The Cafe
---

### Post by markinf on 2010-01-24
I mean I know that when you divide packages you make them more scalable and more flexible. For example when you divide ffmpeg into various packages, if one of these package have a problem it won't effect the others. But that makes packaging a hell. Because you need to divide them and it needs a lot bureaucracy so that people don't package the same software with different packages.

However when you don't divide packages you lose this functionality but it's way more clean, since you don't have to look for the dozen -dev, -data, -dbg, -headers, libFoo-headers. And so on.

Arch/Gentoo packages don't share this view, they are whole packages, For example when you install ffmpeg, you really "install" ffmpeg, you don't need to search for libffmpeg, ffmpeg-*. IMO is so much better this way.

I know that Ubuntu can't change this because of the Debian "roots", oh how much I hate Debian !!!, but if it could woudn't that be a lot better?

---

### Post by Xbehave on 2010-01-24
meh go troll elsewhere dude. This has nothing to do with bureaucracy.

> However when you don't divide packages you lose this functionality but it's way more clean, since you don't have to look for the dozen -dev, -data, -dbg, -headers, libFoo-headers. And so on.
You don't usually need -dev (dev is generally the headers btw) or -dbg, so why waste space on them, so unless you need the dev/dbg you don't need to worry about anything you posted about (as usual) because you just install the program name and it will pull the -data and libs that it needs. If you are compiling stuff you don't need to worry about -dev either (you just install the build-deps for the package your compiling). The only time you need to think about -* is for debuging data, but as i doubt you have the cognitive capacity to read a backtrace that doesn't affect you anyway, nor is it particularly hard.

**tl;dr** * off and troll elsewhere, this is the third useless troll post you've started this week.

---

### Post by mcduck on 2010-01-24
No, it wouldn't. I only want the part of a program that's actually usefull for me, I don't need all the source code, development libraries and debug stuff that's completely irrelevant on any normal use.

(besides, I've never had to search for separate libraries of some program manually anyway. Just install the app itself and all the required extra packages will be installed automatically for you. I don't see any problems there..)

---

### Post by RiceMonster on 2010-01-24
They do this on fedora as well, and it gets kind of annoying when I want to build a package. However, it does make the packages smaller, which is nice.

> **Xbehave said:**
> meh go troll elsewhere dude. This has nothing to do with bureaucracy.


You don't usually need -dev (dev is generally the headers btw) or -dbg, so why waste space on them, so unless you need the dev/dbg you don't need to worry about anything you posted about (as usual) because you just install the program name and it will pull the -data and libs that it needs.

**tl;dr** * off and troll elsewhere, this is the third useless troll post you've started this week.

You don't think this is a legitimate topic to discuss? Plus, if this really is a troll, all you're doing is feeding ;).

---

### Post by Xbehave on 2010-01-24
> **RiceMonster said:**
> You don't think this is a legitimate topic to discuss? Plus, if this really is a troll, all you're doing is feeding ;).
It's not, -data/-dev/-dbg exist for damn good reasons and you never need to worry about them. markinf is definitely a troll, look at his previous threads. I prefer to show the troll for the idiot that he is, because otherwise people might thing there is a spark of truth to his accusations (which there is not).

---

### Post by Xbehave on 2010-01-24
> **RiceMonster said:**
> They do this on fedora as well, and it gets kind of annoying when I want to build a package. However, it does make the packages smaller, which is nice.
Instead of falling for BS like this read the manual, I'm sure yum will have yum install build-deps (or something like that) that pulls in all the header files you need to compile your program. yum has a nice command for installing debuging info too, debuginfo-install (or something like that) will pull in all the dbg that your program needs (apt might have an equivalent, but when doing debugging I usually guess the dbg's that are needed, because they usually make sense)

edit:
to do something like apt-get build-dep in yum you need yum-utils which provides yum-builddep, apparently because redhat don't have as much "bureaucracy" as debian, it is a bit harder to use (you need to know the name of the srpm for a package, which isn't always the same (this is being worked on so in fedora 13 there will probably be smarter logic to avoid this being an important issue)), however it's still easy and it will work for most cases.

---

### Post by RiceMonster on 2010-01-24
> **Xbehave said:**
> It's not, -data/-dev/-dbg exist for damn good reasons and you never need to worry about them. markinf is definitely a troll, look at his previous threads. I prefer to show the troll for the idiot that he is, because otherwise people might thing there is a spark of truth to his accusations (which there is not).

My point was, you're calling markinf a troll, yet you continue to argue with them. If markinf is a troll, then don't respond.

> **Xbehave said:**
> Instead of falling for BS like this read the manual

Right, total BS. There's no valididaty to the other side's argument at all. Don't tell me to read the manual. I know how to use yum, and I know how to make rpms myself.

> to do something like apt-get build-dep in yum you need yum-utils which provides yum-builddep, apparently because redhat don't have as much "bureaucracy" as debian, it is a bit harder to use (you need to know the name of the srpm for a package, which isn't always the same (this is being worked on so in fedora 13 there will probably be smarter logic to avoid this being an important issue)), however it's still easy and it will work for most cases.

I'm talking about making my own rpms. I don't think that will work when building from a spec file, will it?

---

### Post by Xbehave on 2010-01-24
> **RiceMonster said:**
> My point was, you're calling markinf a troll, yet you continue to argue with them. If markinf is a troll, then don't respond.
I don't agree with not feeding the trolls, i'd much rather explain to others why he is wrong, otherwise people might read his post and think that he has a valid point.

> Don't tell me to read the manual. I know how to use yum, and I know how to make rpms myself. 
I'm talking about making my own rpms. I don't think that will work when building from a spec file, will it?
When you want to build a program (say firefox) you need to get the headers of all it's dependencies, that is what ```
apt-get build-dep firefox
yum-builddep firefox
``` do, so you never have to worry about -dev files

debuginfo-install (or the apt equivalent) do the same for debugging info, so you never have to worry about -dbg files

here is a crude script that should work do debuginfo-install for apt (requires apt-rdepends and needs you to set $pacakge, before running it.
```
for PKG in $(apt-rdepends --show=DEPENDS $package | grep Depends: | cut --fields=4 --delimiter=" " | sort -u); do PKGS="$PKGS $PKG-dbg"; done ; sudo apt-get -m install $PKGS $pacakge-dbg
```

So users never need to worry about -data/-dev/-dbg
People looking to compile thier own software (either normally or using check-install or apt-get source/apt-src) don't need to worry about -data/-dev/-dbg
The only people who need to worry about -data/-dev/-dbg are packagers who want to distribute their packages in proper repos and if your contributing to a proper repo learning to package correctly isn't that hard.

---

### Post by tgalati4 on 2010-01-24
Here's an exercise:  statically build everything in a typical Ubuntu system and see how big the OS is.

How much space do we really save with all of these shared libraries?  Especially when we have 2 or 3 versions of each library--to maintain compatibility.

My guess is that it's not that big a difference.

---

### Post by Xbehave on 2010-01-24
> **tgalati4 said:**
> Here's an exercise:  statically build everything in a typical Ubuntu system and see how big the OS is.

How much space do we really save with all of these shared libraries?  Especially when we have 2 or 3 versions of each library--to maintain compatibility.
You realise the savings come into ram usage aswell right?
And updating would become like windows if everything was statically compiled
And do you really have 2/3 versions of libs, i'm looking through /usr/lib and i have just a couple of repeated lib (and they are repeated once none have 3 versions

> My guess is that it's not that big a difference.
MY guess is that updating would become a PITA and well managed libs are probably part of the reason that a standard ubuntu install wont exceed 5G, but a windows install won't fit inside 5

Not that this would really affect the splitting up of headers/debugging info/data into -dev/-dbg/-data.

---

### Post by tgalati4 on 2010-01-24
You make some good points.  And yes the memory footprint would increase because you are no longer sharing libraries.  But again, how big would a statically-compiled Ubuntu be?  How much more RAM would a base boot require?  How much slower would it be?

---

### Post by phrostbyte on 2010-01-24
> **tgalati4 said:**
> You make some good points.  And yes the memory footprint would increase because you are no longer sharing libraries.  But again, how big would a statically-compiled Ubuntu be?  How much more RAM would a base boot require?  How much slower would it be?

Well "how static"?

If you statically compile against GTK+ for every GTK+ app you'll probably have some absurd memory requirements. Do you really want to this? If so .... WHY? If a library is multiple megs it's a little much to statically compile this into an app.

It's worth noting that Arch/Fedora doesn't statically compile everything. Windows apps dynamically link to the Win32 API (largely implemented as shared libraries), otherwise every app might pull hundreds of megs of libraries :D 

Arch bundles -dev into the package, which is mostly the header files for the lib (required for compilation). This is not the same thing as statically compiling everything. I mean, Arch is regularly respected for it's speed!

---

### Post by tgalati4 on 2010-01-25
True.  The header files aren't huge  Yes, gtk has a large footprint.  So there seems to be a tradeoff between package size, number of packages, and installed footprint size.

Look at dsl, tinycore, slitaz for how small a desktop linux can be.

---

