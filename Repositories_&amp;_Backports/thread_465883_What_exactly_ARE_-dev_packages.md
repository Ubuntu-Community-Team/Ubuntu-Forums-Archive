---
title: "What exactly ARE -dev packages?"
date: 2007-06-06
forum: Repositories &amp; Backports
---

### Post by vertigo1980 on 2007-06-06
Hi all,

i want to compile the x264 encoder, and for that i obviously need libx264-dev.

there is several months difference between the date of the latest x264 source (from the official site), and the dev package in the repositories. i want to make sure it is compiled properly with the latest code, so i'd like to know what exactly the -dev packages do? what if i wanted to compile my own build of a program, but the repositories only have a -dev package from a year ago? how can i make my own -dev package? should i ever need to make my own?

thanks! :)

---

### Post by uberushaximus on 2007-06-06
> **vertigo1980 said:**
> Hi all,

i want to compile the x264 encoder, and for that i obviously need libx264-dev.

there is several months difference between the date of the latest x264 source (from the official site), and the dev package in the repositories. i want to make sure it is compiled properly with the latest code, so i'd like to know what exactly the -dev packages do? what if i wanted to compile my own build of a program, but the repositories only have a -dev package from a year ago? how can i make my own -dev package? should i ever need to make my own?

thanks! :)

The dev packages contain the static libraries needed to build packages. These are seperated because average users do not need the packages. Simply compiling the full source code of the program in question (i.e. libx264) should give you the proper libraries needed for whatever you plan to compile that depends in this lib.

---

