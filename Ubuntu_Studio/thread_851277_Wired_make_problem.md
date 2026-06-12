---
title: "Wired make problem??"
date: 2008-07-06
forum: Ubuntu Studio
---

### Post by ixlam on 2008-07-06
I've already posted in "General help" section, but maybe this is the appropriate place for my question.

I'm trying to Install "Wired 0.6" from source. 
I have Ubuntu Studio 8.04 and all my updates and dependencies installed.

Everything goes well up to when I run > make

here's the error message 
```
make: *** No rule to make target `all-recursive', needed by `all'.  Stop.
```

any help is appreciated.

---

### Post by Stochastic on 2008-07-07
Is make the first command you attempted to run after unzipping the source code files?  If so, take a read through the INSTALL file that came inside the source code - it provides some fairly direct instructions.  But if you did follow those instructions, make sure there are no errors in the output of the other commands before running make.

---

### Post by ixlam on 2008-07-07
Hi.. 
No its not the the first command I run.
heres what the install file says to do 

./autogen.sh
./configure
make
make install

./autogen.sh and ./configure go smooth, then at "make" i get the problem.

PS. it seems the when it enters the /intl directory thet the error occurs 
```
make[1]: Entering directory `/home/ixlam/wired-0.6/intl'
make[1]: *** No rule to make target `all'.  Stop. 
```

I'm also curious why Wired is not included in Ubuntu Studio any more..
It was with previous versions (6 I believe) also there is a .deb file 
but it its an old version> wired.0.3

---

### Post by ixlam on 2008-07-07
Interestingly enough.. 
I re-downloaded the source files and tried again from the beginning.
This time arround im getting further but am still getting an error during "make"
```
 /test/paqa_devs.c  lib/.libs/libportaudio.so /usr/lib/libasound.so /usr/lib/libjack.so -ldl -lrt -lm -lpthread
lib/.libs/libportaudio.so: undefined reference to `jack_port_lock'
lib/.libs/libportaudio.so: undefined reference to `jack_port_unlock'
collect2: ld returned 1 exit status
make[1]: *** [bin/paqa_devs] Error 1
make[1]: Leaving directory `/home/ixlam/Desktop/wired-0.6/src/portaudio'
make: *** [all-recursive] Error 1

```

---

### Post by theblackkat on 2008-08-11
i'm having the same problem here... anyone?
:(

EDIT: this might help:
[http://sourceforge.net/forum/forum.php?thread_id=1917952&forum_id=409329](http://sourceforge.net/forum/forum.php?thread_id=1917952&forum_id=409329)
and this:
[http://ubuntuforums.org/archive/index.php/t-614744.html](http://ubuntuforums.org/archive/index.php/t-614744.html)

---

### Post by ghostandmachine on 2008-08-11
I think I'm getting a different but on the same make session.

```

../dssi/dssi.h:310: error: ‘snd_seq_event_t’ has not been declared
../dssi/dssi.h:324: error: ‘snd_seq_event_t’ has not been declared
../dssi/dssi.h:362: error: ‘snd_seq_event_t’ has not been declared
../dssi/dssi.h:378: error: ‘snd_seq_event_t’ has not been declared
make[2]: *** [MainWindow.o] Error 1
make[2]: Leaving directory `/home/eric/Desktop/wired-0.6/src/gui'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/eric/Desktop/wired-0.6/src'
make: *** [install-recursive] Error 1

```

I'm sure this won't help anyone but it's nice to know that there's more than just one person stuck in the boat without a paddle. :)

---

### Post by oliviajohn on 2008-08-12
Yes, make the first command, take a read through the INSTALL file that came inside the source code, it may provides some fairly direct instructions..,

---

### Post by ghostandmachine on 2008-08-17
I've been following the source instructions line for line. downloaded and installed all of dependences and check to make sure they are installed correctly. I've followed all of the directions for installing wired and I'm still getting the errors. the only thing I can think of is it's something wrong with the program itself. Has anyone tried to compile and install an older version of wired on Hardy?

---

### Post by killstheweak on 2008-12-18
To get rid of that error you have to add --disable-portaudio to configure.

---

