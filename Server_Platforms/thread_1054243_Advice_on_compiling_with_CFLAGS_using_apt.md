---
title: "Advice on compiling with CFLAGS using apt"
date: 2009-01-29
forum: Server Platforms
---

### Post by eimermusic on 2009-01-29
Hi, I have been doing some internet research and could use some feedback.

I really want the same support for large files in php on my Ubuntu server (8.04) as I have on my laptop. But under Linux php does not compile with this support by default. 

I am no hard-core Lunix guru. I have used compiled php's in the past and have found that a quick package update makes updating the system a lot simpler so i try to stay away from manual compiles. This time I'd like to find a middle-ground using Ubuntu's ability to compile from "source-packages".

I could use some advice on how to go about this. It may not be possible to get my dream setup but I'd like to try.

(Dream) Objective:
• Recompiling php5 adding a "CFLAGS" to the distro configuration.
• php5 should afterwards function as the distro package (cli and apache module, update to apache etc. should not break php as manual compile often can).
• The process should be scriptable so it can be run alongside normal package updates. 

Configuration for a normal compile of php with the desired "large file" support would look like:
CFLAGS="-D_FILE_OFFSET_BITS=64" ./configure ...


This as I understand it is the basic steps (all two of them) needed to create and install a package of php.
> sudo apt-get build-dep php5
> sudo apt-build install php5

This will, as I understand it, not use the distro compile settings?
> sudo apt-get -b source php5

What I don't know is where to put the CFLAGS definition to get it to be part of the compilation. I have read som (old) posts and messages that stated that apt-build could not take CFLAGS, so this may not even be posible?

Then I also found this version of the procedure:
> sudo apt-get source php5
> cd php5-version
> fakeroot ./debian/rules binary CFLAGS...

And also info that this would not work and that I need to edit the rules file to set the CFLAGS.

I don't know which way to go here which is mainly why I ask... before I wreck my server :)

/Martin

---

### Post by electrogeist on 2009-01-29
I'm far from a programmer and have not compiled anything on ubuntu yet

and this prob isn't the proper way, but as a last resort I would think you could find a CFLAGS line in the Makefile and add your option to it... maybe make a backup copy of the Makefile first.

---

### Post by eimermusic on 2009-01-30
Thanks for replying.

Looking at debian/rules I notice that around line 40 it reads:
ifneq (yes,$(PHP5_COMPAT))
  CFLAGS += $(shell getconf LFS_CFLAGS)
endif

PHP5_COMPAT is set to "no" above in the file and the return from getconf LFS_CFLAGS is:
-D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64

So everything should be ok, right? I would just like some suggestions as to which way to compile a "package" I should use. "apt-build" or "apt-get -b source"? Anyone with experience and opinion on the subject?

/Martin

---

