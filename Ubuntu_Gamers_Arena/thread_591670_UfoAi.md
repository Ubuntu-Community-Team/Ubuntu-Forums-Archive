---
title: "UfoAi"
date: 2007-10-25
forum: Ubuntu Gamers Arena
---

### Post by Doctor J. on 2007-10-25
Okeh, i've been dying to get this game going.  [http://ufoai.sourceforge.net/](http://ufoai.sourceforge.net/)
Note that this requires a version of libSDL higher than what's available to me through Synaptic [On Dapper x86_64 i only see 1.2.9 with backports, etc. all turned on.]  I downloaded and installed libSDL and all splitoffs:

```
./configure--prefix=/usr
make
make install
```

So i go to run the program and get: 

```
dave@ubuntu:~/ufoai$ ./ufoai
./ufo: error while loading shared libraries: libSDL_ttf-2.0.so.0: cannot open shared object file: No such file or directory
```

Here is my sdl installation:

```
dave@ubuntu:/usr/lib$ ls libSDL_*
libSDL_image-1.2.so.0      libSDL_mixer-1.2.so.0      libSDL_net-1.2.so.0      libSDL_ttf-2.0.so.0
libSDL_image-1.2.so.0.1.5  libSDL_mixer-1.2.so.0.2.6  libSDL_net-1.2.so.0.0.7  libSDL_ttf-2.0.so.0.6.3
libSDL_image.a             libSDL_mixer.a             libSDL_net.a             libSDL_ttf.a
libSDL_image.la            libSDL_mixer.la            libSDL_net.la            libSDL_ttf.la
libSDL_image.so            libSDL_mixer.so            libSDL_net.so
```

Can somebody point in a proper direction to troubleshoot this thing?

---

### Post by gumigutas on 2008-01-23
Just instal them with:

> 
 sudo apt-get install libsdl-ttf2.0
 sudo apt-get install libsdl-mixer1.2


For me it works ubuntu 7.10 ;)

---

### Post by Perfect Storm on 2008-01-24
> **gumigutas said:**
> Just instal them with:



For me it works ubuntu 7.10 ;)

Yeah, but he said he have Dapper - which have "old" libs/devs. That's why it doesn't working.

---

### Post by davidpodhola on 2008-03-16
It should be

sudo apt-get install libsdl-ttf2.0-0

for today at 7.10

---

### Post by emix101 on 2009-04-29
Hi there guys!

Is there anyway I could download first and then compile the map...
because I only have limited connection to internet...


Any suggestion?

Thx

---

### Post by Doctor J. on 2009-05-04
Sorry emix101, but you are going to be disappointed by what i say.  Even the binary compiled version does not include compiled maps nor compiled documentation.  This is just always going to be a fat download due to the amount of media included [3D objects, music, etc.].  Perhaps you can have a friend get it for you?

Another warning: the game won't even run unless you are in a screenmode with a minimum of 24 bits per pixel, so make sure you've got the latest video card drivers [and hopefully you don't have video by Intel].

---

