---
title: "Jack/Youtube/Chromium"
date: 2011-03-29
forum: Ubuntu Studio
---

### Post by riffey#4 on 2011-03-29
I started using Ubuntu Studio some 2 weeks ago (I tried different Linuxes over the years). As a *cough* musician I like the features of Ubuntu Studio. 
So far, I got most things up and running, at least the things that are important to me. 

Jack is running, I can play music over Jack with QMMP, I can play VLC video over Jack, Audacity is running over Jack, and even Pidgin notifies me of on/offline buddies over Jack.

There's one thing I can't get to work: Chromium and YouTube videos over Jack. 
I have a short attention span :P so every now and then I want to see a Youtube video (how do they do it? What does that sound like).

Could somebody point me how to get Youtube working over Jack? I tried searching, but apparently somebody already used the name Jack for a plug, a whiskey, a movie, a few actors, a radio station and some egocentric sexual activity.

---

### Post by Pablo_F on 2011-03-29
Hi,

There are at least two approaches to solve this issue.

1. Use pulseaudio through jack. Archers have a nice manual:

 [https://wiki.archlinux.org/index.php/PulseAudio#Pulseaudio_through_JACK](https://wiki.archlinux.org/index.php/PulseAudio#Pulseaudio_through_JACK)

2. "Jackify" the flash player, as explained here:

[http://www.linuxmusicians.com/viewtopic.php?f=4&t=2323](http://www.linuxmusicians.com/viewtopic.php?f=4&t=2323)

Cheers! Pablo

---

### Post by riffey#4 on 2011-03-30
Thanks Pablo.
If I understand correctly, your first suggestion makes every application that uses Pulseaudio use Jack.
That looks like the best solution. 

The first step says:  just try PA on top of jack you can have PA load the necessary modules on start:
```
pulseaudio -L module-jack-sink -L module-jack-source
```

I started Jack and then: 
```
me@box:~$ pulseaudio -L module-jack-sink -L module-jack-source
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
```

It doesn't say on the site what I should get, but this doesn't look good.
So before I start editing things: what should the output be?

---

### Post by Pablo_F on 2011-03-30
Hi, 

Admiteddly, I use the second method so I am not familiar with PA through jack. 

Anyway, in ubuntu, PA is started as the default sound daemon but you need to start PA _after_ jack so will need to kill PA and, probably, avoid PA autospawn, start jackd, start PA and load the module(s). If you want playback only, you only need the sink, IIRC. Ah, and you need pulseaudio-module-jack package.  

Cheers, Pablo

---

### Post by riffey#4 on 2011-03-30
Fine with me, I'll use all the help I can get ;)

If I use the second method and do sh bootstrap.sh I get:

```
+ [ x = xam ]
+ rm -rf autom4te.cache
+ rm -f config.cache
+ test x = x
+ LIBTOOLIZE=libtoolize
+ libtoolize -c --force
libtoolize: putting auxiliary files in `.'.
libtoolize: copying file `./ltmain.sh'
libtoolize: You should add the contents of the following files to `aclocal.m4':
libtoolize:   `/usr/share/aclocal/libtool.m4'
libtoolize:   `/usr/share/aclocal/ltoptions.m4'
libtoolize:   `/usr/share/aclocal/ltversion.m4'
libtoolize:   `/usr/share/aclocal/ltsugar.m4'
libtoolize:   `/usr/share/aclocal/lt~obsolete.m4'
libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.ac and
libtoolize: rerunning libtoolize, to keep the correct libtool macros in-tree.
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
+ run_versioned aclocal 1.9
+ local P
+ local V
+ echo 1.9
+ sed -e s,\.,,g
+ V=19
+ which aclocal19
+ [ -e  ]
+ which aclocal-1.9
+ [ -e  ]
+ P=aclocal
+ shift 2
+ aclocal
bootstrap.sh: 1: aclocal: not found
```

After that, my make returns: 
```
make: *** No targets specified and no makefile found.  Stop.
```

Any suggestions?

---

### Post by Pablo_F on 2011-03-30
You need automake, libtool, autoconf... see the instructions.

Cheers, Pablo

---

### Post by sawtdk on 2011-03-30
the easiest way to do this is to run pulseaudio through jack.

With jack and pulseaudio running (doesn't matter what was first) run this command in terminal:
pactl load-module module-jack-sink


Then to set the output to the jack sink run this (you can also do this in sound preferences):
echo "set-default-sink jack_out" |pacmd

edit: you must have pulseaudio-module-jack package installed

---

### Post by riffey#4 on 2011-03-30
@Pablo: doh... I was following all the steps one at a time.. Should have read the whole article, my bad.

I installed it and I think all commands completed without any errors, but I still didn't have sound. 
Maybe I should have done the last step, but (still being new) I'm not on Lucid, and my Firefox version is 3.6.16 I didn't try that yet.

So I followed Sawtdk's instructions and they worked right away! 

Thanks both for helping!

---

