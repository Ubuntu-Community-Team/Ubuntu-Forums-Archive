---
title: "How to install / uninstall new version of JACK."
date: 2009-03-25
forum: Ubuntu Studio
---

### Post by jonobo on 2009-03-25
Hi everyone,

i need to compile a new version of JACK/jackd for the new Ardour (ardour.org) .

I already compiled a new version, but i need an even newer version because mine is buggy.

I know how to compile stuff by now, but i don't know if i have to uninstall old versions before i install new versions, and how to uninstall old version, if that is necessary.

In this case i want to install:
JACK 0.116.2 

I got installed:
jackd version 0.112.0

So - what's the right way to do it (i thought i'd better ask BEFORE i screw it)?

:guitar:

---

### Post by thorgal on 2009-03-25
since your old version was already a custom compilation, no problem, just uninstall it:

sudo make uninstall

from the old source directory where you compiled it.

---

### Post by jonobo on 2009-03-25
Thanks. Gonna try that and report back.

Just realised that i installed from svn last time, gonna do that again now - i guess uninstalling is necessary anyway... ...correct me if i'm wrong ;)

---

### Post by thorgal on 2009-03-25
ah, it was an svn check out ? same thing here, just go ahead:

```

cd jack_svn # or wherever it was
sudo make uninstall
make distclean
svn update
./configure --prefix=/usr # using /usr/local may have drawbacks due to LD_LIBRARY_PATH, it's up to you
make && sudo make install

```

WARNING: the new jack svn has something called "sanity checks" ... you may be surprised when you try your newly compiled jackd ... ;)

---

### Post by jonobo on 2009-03-25
Okay - thanks for the advice - just found out about "svn update" before i read your posting, but that made it clear to me.

Last time i configured with these Options (maybe that was the reason for the buggy behaviour), i don't know anymore why i used these options, but i guess there was a reason (i might get into trouble with the sanity check @ jack ;) ) :
```
./configure --enable-capabilities --with-default-tmpdir=/mnt/ramfs
```

Your advice confuses me "just a little", but enough to ask, again ;)
> ./configure --prefix=/usr # using /usr/local may have drawbacks due to LD_LIBRARY_PATH, it's up to you

What is the LD_LIBRARY_PATH?

What is --prefix=/usr or --prefix=/usr/local for?

What if i don't give any --prefix option at all, ah, i guess there is a default setting somewhere.

So which --prefix would you suggest?

Update:
Okay, i tried to configure, but i got some errors about no install or install.sh in /config subdirectory, so i deleted the whole jack directory (after uninstalling and cleaning) and re-ordered JACK fresh from svn, but that only got me a new error-message if i try to configure: 
./configure: No such file or directory

Mmh... okay there is no configure-file, so what now?

---

### Post by thorgal on 2009-03-25
hehe, lots of questions :)

LD_LIBRARY_PATH is a so-called environment variable, something that was needed if you had non standard locations for runtime libraries. Indeed, programs (binaries) are dynamically linked to some libraries (*.so files). Most of the time, these libs live in /usr/lib or /lib. But if you compiled some yourself, the default installation will put them in /usr/local/lib, which is a non standard place in general. So if you program depends on it at run time, and LD_LIBRARY_PATH does not point to it, the program will complain that it cannot run because it cannot find the run time lib it needs.

This is a bit tricky, there are more modern ways to go around this. But for jack, it can be a real pain in the butt. So the advice (and that even comes from Paul Davis, the author of jack) is to install in /usr so that libjack.so goes into the standard /usr/lib directory.


As far as options are concerned:

./configure --help will show you the default. 

--enable-optimize is there by default I think. Just add it as you did if not. 

--enable-capabilities ? never used it ...
 what was it for ?

The tmpfs thingy (--with-default-tmpdir) is something of the past, you can  ignore it as nowadays, you most likely have a /dev/shm directory where shared memory segments can be used. So you most likely don't need this option any longer. Maybe the README file has not been updated for years (I remember seeing this stuff almost 6 years ago ...).

so something like:
```

./configure --enable-optimize --prefix=/usr

```

would do I think. Check the default with --help.

---

### Post by jonobo on 2009-03-25
Okay. Cool. Thanks for the Enlightment. Free :popcorn: for everyone ;)

I confused the Thread by updating my old posting, sanity check not passed.

Okay - ready to configure - but no configure-file there anymore :confused:

```

jobo@ybox:/media/sda1/jazztop/kos/progz-zipz-tarballz/jack-svn/jack$ ls
acinclude.m4                   config        COPYING.LGPL     jack          libjack      README.developers
authors                        configure.ac  doc              jackd         Makefile.am  todo
autogen.sh                     copying       drivers          jack.pc.in    man          tools
BUILDING-FOR-LINUX-2.4-KERNEL  copying.gpl   example-clients  jack.spec.in  readme

```

```

jobo@ybox:/media/sda1/jazztop/kos/progz-zipz-tarballz/jack-svn/jack$ ./configure --enable-optimize --prefix=/usr
bash: ./configure: No such file or directory

```

I start to feel guilty for using your braintime on my problems - free :popcorn: and your very own personal :KS for you.

---

### Post by thorgal on 2009-03-25
I improve my karma, so it's not for free :D

use
```

./autogen.sh

```

it will regenerate the configure script.

looks like you did a fresh checkout again ... next time, just update your svn tree. If you really want to clean the whole tree, use
```

make maintainer-clean

```

this will remove EVERYTHING, even configure. So autogen.sh will be required again.

---

### Post by jonobo on 2009-03-25
Okay - so one free Karma-Shawarma for you.

That seems to work... :guitar:

I'll be back to confirm completion.

Thanks,

;j

---

### Post by thorgal on 2009-03-25
haha, shawarma ... have not eaten that for ages ... pretty disgusting when I think ot if :lol:
your gratitude is the only food that counts :guitar:
(jeeze, I am almost reaching the point where I should think about shaving my long hair ...:lol: )

---

### Post by jonobo on 2009-03-25
YEAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAH!

It rrrrrrrrrrrrrrrrrrrrrrrrrrrrrruuuuuuuuuuuuns.

And is no longer buggy (at least i can enter the connections-window again, which was *sic* not possible for the last months and forced me to do all the routing from inside ardour which was okay for me, but not forever):]

So i'm gonna go for Ardour 3.0 Alpha now and when the MIDI works and i can finally programm MIDI-Rolls in Ardour and have the sound coming out of fluidsynth/qsynth i'm gonna celebrate like THERE'S A TOMORROW :)

Keep the hair growing 'til all studios run on Ardour :guitar:

So over and out for now and thanks for the fish,

;j

---

