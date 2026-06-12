---
title: "compiling vs aptitude"
date: 2010-09-13
forum: The Cafe
---

### Post by timbosity on 2010-09-13
Im only curious really but if someone with the know could comment on advantages/disadvantages of compiling programs from source vs simply installing from aptitude repos I would be most grateful.
Im looking for technical reasons more than ease of use and other useability issues (ie it _is_ much simpler/easier to install things with apt-get).
What kinds of situations would make compiling from source be worth the trouble?

cheers

---

### Post by juancarlospaco on 2010-09-13
*Compiling got Placebo Effect*

---

### Post by v1ad on 2010-09-13
apt-get will also keep u updated.

---

### Post by timbosity on 2010-09-13
so, its not usually advisable to compile things and it all comes down to aptitude management and updates etc...

---

### Post by snowpine on 2010-09-13
A Linux distrubution is not just software; it is also community.

Ubuntu is a community of people who, for the most part, enjoy installing pre-compiled binaries. The tools and how-tos that have grown up around Ubuntu support this trend.

This does not mean you cannot compile from source in Ubuntu! :)

---

### Post by v1ad on 2010-09-13
oh yes always advisable.

---

### Post by wojox on 2010-09-13
I really only compile if I want different options or maybe there are patches.

---

### Post by wojox on 2010-09-13
> **timbosity said:**
> so, its not usually advisable to compile things and it all comes down to aptitude management and updates etc...

It's a lot easier, simpler and quicker. ;)

---

### Post by odiseo77 on 2010-09-13
There are some cases when people has to compile to add extra functionality for some application, some function not enabled by default, etc. Take for instance the kernel, in some cases people must compile in order to either add some extra functionality, or to add support for a given hardware. Other than that, it's preferable to install stuff directly from binary packages.

---

### Post by toupeiro on 2010-09-13
FUD alert:  Most open source projects with frequent updating have subversion checkout systems.  Nothing wrong with compiling, its a matter of preference!  Compiling is the most distribution agnostic way to distribute software.

---

### Post by oldos2er on 2010-09-13
I started compiling because I wanted to learn how, and I'm still compiling and learning. Sometimes source code for a given version of a program is available long before a deb file of the same version is, so that's one reason you might want to compile something. You can use the app checkinstall to allow the package management system to keep track of your compiled and installed software. [https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by Ralob on 2010-09-14
If I use the program often, I compile it from source merely to have the bleeding-edge version. If I encounter issues then I generate a report and give it to the devs. However, most repositories have have a recent enough version for apps and libs that I don't worry about getting the source. For apps I use daily and keep track of the source code, I compile when changes are introduced that I view as beneficial. At the moment, the main programs I compile from source are Calibre and XBMC along with some of the dependencies like ffmpeg, xvid, podofo, etc.

---

