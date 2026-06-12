---
title: "Trouble installing Non-sequencer"
date: 2010-06-29
forum: Ubuntu Studio
---

### Post by elsrkite on 2010-06-29
Hi, I'm pretty new to Ubuntu, and linux in general. Trying to install Non-sequencer has been pretty challenging because I've mostly stuck to pre-compiled software until now.

After jumping through a dozen hoops, I found one that Google couldn't help me solve. It is telling me that JACK is not installed.

Here are the results of "make" for Non-sequencer:
> Checking sanity...-e          ok 
--- Configuration required
:: Installation prefix? [/usr/local] 
:: Use the LASH Audio Session Handler? [yes] 
:: Build for debugging? [no] 
Checking for FLTK...-e        ok (1.1.9)
Checking for FLUID...-e       ok 
Checking for JACK...failed!
Required package JACK doesn't appear to be installed.
make: *** No rule to make target `.config', needed by `all'.  Stop.JACK is definitely installed, I use qjackctl all the time.
> dpkg -s jack
Package: jack
Status: install ok installed
Priority: optional
Section: sound
Installed-Size: 660
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 3.1.1+cvs20050801-25build1...etc.

I'm using 9.04. Any ideas would be really appreciated! Even if you haven't used Non-sequencer before. I just don't know how to attack the problem.

Thanks!

---

### Post by Pablo_F on 2010-06-30
To build programs from source, you need the development libraries. You find these in synaptic. Usually, if package A depends on package B, compiling the sources of A will require package libB-dev. In you case, for non-sequencer, you need, afaict:

libjack-dev
libfltk1.1-dev
libsigc++-2.0-dev

In addition, in this case, before running make you need to run:

$ ./configure

But before this, run:

$ make clean

To sum up, install the -dev packages, make clean, configure, make and sudo make install.

Cheers! Pablo

---

