---
title: "missing wavpack support in the current xinelib for edgy."
date: 2007-03-26
forum: Repositories &amp; Backports
---

### Post by enaut on 2007-03-26
My Question is Why is in the current xinelib version of feist the wavpack support disabled? - I was so exitet to hear wavpack with Amarok. but what a disappointment it is still not working.

meanwhile i fixed the problem by simply recompiling xinelib with the required wavpack support.

but i think it is essential to support a format like wavepack in an open source system. 

so please if any paketmaintainer is reading this post please add the support to the xinelib packet. - I would be really greatfull. - if this is the wrong place please say where i can claim. and where i can find the responsible persons.

---

### Post by ilia on 2007-04-28
The better place for such requests is a launchpad. Go to [http://launchpad.net](http://launchpad.net)  and submit a bug on libxine package or something similar.

---

### Post by ksaid on 2007-04-28
> i fixed the problem by simply recompiling xinelib with the required wavpack support
how can i do this?

---

### Post by enaut on 2007-04-30
Hello,

Compiling is in general not to esy because you have to fix all dependencies before... but there is a good tutarial about how to compile [here https://help.ubuntu.com/community/CompilingEasyHowTo?highlight=%28compiling%29]("https://help.ubuntu.com/community/CompilingEasyHowTo?highlight=%28compiling%29")

The sources you can get from the [Xinelib Homepage http://prdownloads.sourceforge.net/xine/xine-lib-1.1.4.tar.bz2]("http://prdownloads.sourceforge.net/xine/xine-lib-1.1.4.tar.bz2")

unpack the source and execute the following commands

```
./configure --with-wavpack --prefix=/usr
make
make install
```

ask if you have any problems...
and happy listening ;)

---

### Post by ksaid on 2007-04-30
perfect.. thanks!!! you know if there is a way to play also monkey's audio files with xine?

---

### Post by enaut on 2007-05-01
Sorry I have no idea about that...

you may look if there is a hidden support too by looking through the list of ```
./configure --help
``` or so but I really don't know...

---

### Post by john__80 on 2007-09-26
Hello i have a problem compiling xinelib for listening wavpack files with amarok.  When i run: 
```
./configure --with-wavpack --prefix=/usr/local/src/bin

```

i got a message like this:

checking for LIBMODPLUG... checking for WAVPACK... configure: error: Package requirements (wavpack) were not met:

No package 'wavpack' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables WAVPACK_CFLAGS
and WAVPACK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

and i actualy have installed wavpack 4.41 in /usr/local/src/bin, i have  tried installing wavpack with sudo apt-get install wavpack too...

What i'm doing wrong...?


ask if you have any problems...
and happy listening ;)[/QUOTE]

---

### Post by cygnl7 on 2007-10-03
I posted some instructions on this topic on my [blog]("http://www.davtar.org/blog/?p=41").  The post is specifically for gutsy but should be fairly similar for edgy.

---

