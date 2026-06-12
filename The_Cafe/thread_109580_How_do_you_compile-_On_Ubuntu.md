---
title: "How do you compile- On Ubuntu?"
date: 2005-12-28
forum: The Cafe
---

### Post by erikpiper on 2005-12-28
What do I need to apt-get? Thanks. (Here is what I get when I ./configure)

loading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... no
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking for c++... no
checking for g++... no
checking for gcc... gcc
checking whether the C++ compiler (gcc  ) works... no
configure: error: installation or configuration problem: C++ compiler cannot create executables.


----------------------------------------------------------
After uninstalling my 3 versions of gcc (But not base libs):
loading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... no
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... no
checking for cc... no
configure: error: no acceptable cc found in $PATH

---

### Post by darth_vector on 2005-12-28
sudo apt-get install build-essential

---

### Post by eriqk on 2005-12-28
What have you apt-getted (apt-gotten?) until now?
I have build-essentials, automake and gcc3.4 (maybe other bits and pieces).
./configure
make
sudo make install 
usually just works. Sometimes I need to automake, but I haven't had any problems with that, either.

You could try and apt-get everything configure says is missing.

Groet, Erik

---

### Post by erikpiper on 2005-12-28
Thanks!

New install, apt getted GGC4.0
Uninstalled, and followed your instructions.
(I am new to this.. Bear with me!)

Now, I get error 1 after make AND make install while trying to compile: "TUXEDO  T. PENGUIN:  A  QUEST FOR  HERRING. "

---

### Post by eriqk on 2005-12-28
Before make gives you error 1, you'll see one or more errors. The line above those will probably tell you there's a file missing. Is this correct?

Groet, Erik

---

### Post by erikpiper on 2005-12-29
Ok.. What is a known good file I can test compiling?


Thanks!

---

### Post by shin on 2005-12-29
Test compiling? What for?
There is no such thing.

If something doesn't compile - check error log. It provides useful informations. For real. Probably some lib is missing.

And please use search function. There is like 1 question about compiling per hour.

---

### Post by xequence on 2005-12-29
[QUOTE=shin]Test compiling? What for?
There is no such thing.

If something doesn't compile - check error log. It provides useful informations. For real. Probably some lib is missing.

And please use search function. There is like 1 question about compiling per hour.[/QUOTE]


They mean where can they get a good working program they can test their compiling ability on.

---

