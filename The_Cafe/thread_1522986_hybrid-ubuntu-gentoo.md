---
title: "hybrid-ubuntu-gentoo"
date: 2010-07-02
forum: The Cafe
---

### Post by sandyd on 2010-07-02
I recently installed Gentoo, and I actually found it more stable and faster than ubuntu due to the fact that the entire system was configured for my computer. However, Gentoo itself is not exactly the most newbie friendly distro around.

I thought, and had an idea for a "hybrid" system - a system that could install applications both from source, and from binary.

The core parts of the system (i.e, the "stage 3" section of gentoo) would encompass a larger range of software, but just enough software to get you going (i.e. X, standard system utils, .etc .etc). At this time, users can then choose  wether to compile from source, or from binary. The source code will be compiled with features from programs that are already installed, or are in the install queue (or from a standard set if needed). Once you get the main DE compiled, the rest of the programs do not actually take much time to compile at all and are quite fast.

We can then offer an alternative to simply use the binaries that are on the cd (or must be downloaded as well).

Also alternatively, we can just provide them with a fully functioning DE, then everything from then on is compiled.

what do you think?

---

### Post by earthpigg on 2010-07-02
i think you can already do a command line install, and compile from source everything else, in ubuntu :P

would your proposal, then, boil down to adding an ncurses interface for that?

---

### Post by sandyd on 2010-07-02
> **earthpigg said:**
> i think you can already do a command line install, and compile from source everything else, in ubuntu :P

would your proposal, then, boil down to adding an ncurses interface for that?
yup. typically it would be kinda gentoo with an ncurses install interface.

---

### Post by earthpigg on 2010-07-02
sounds good. get on it. :D

actually, all we really need is a way for synaptic to install from source. then, carly's idea could be implimented very easily... and graphically.

---

### Post by marshmallow1304 on 2010-07-02
I like it.  I enjoyed my brief forays into Gentoo, but I was somewhat overwhelmed with the sheer number of compiler flags available.  Also, I couldn't be bothered to research my hardware for proper kernel compilation.  Maybe something that attempts to autodetect hardware and select the proper kernel options.

---

