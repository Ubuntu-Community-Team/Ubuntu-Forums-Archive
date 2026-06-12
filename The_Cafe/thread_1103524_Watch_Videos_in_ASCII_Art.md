---
title: "Watch Videos in ASCII Art"
date: 2009-03-22
forum: The Cafe
---

### Post by Dr Small on 2009-03-22
I know mplayer is capable of this, but I was wondering if VLC or some other specialized lightweight player could do this. Do you know of any, or a simpler way to watch a video in a console with framebuffer?

---

### Post by Mehall on 2009-03-22
> **Dr Small said:**
> I know mplayer is capable of this, but I was wondering if VLC or some other specialized lightweight player could do this. Do you know of any, or a simpler way to watch a video in a console with framebuffer?

Yes, vlc has the capability.

Dunno if I rememvber right how to use it in a console, but there's a flag you use. I thinks it's -caca or -aa (colour ascii and ascii art respectively)

---

### Post by Dr Small on 2009-03-22
> **Mehall said:**
> Yes, vlc has the capability.

Dunno if I rememvber right how to use it in a console, but there's a flag you use. I thinks it's -caca or -aa (colour ascii and ascii art respectively)
Since VLC no longer has a man page, that's annoying. But I did `vlc --help` and the string `caca` or `aa` were found anywhere. Hmm. Guess I'll have to keep looking.

---

### Post by smartboyathome on 2009-03-22
> **Dr Small said:**
> Since VLC no longer has a man page, that's annoying. But I did `vlc --help` and the string `caca` or `aa` were found anywhere. Hmm. Guess I'll have to keep looking.

[Here you are]("http://wiki.videolan.org/Video_Output"). Remember, the Wiki is your friend. ;)

---

### Post by sisco311 on 2009-03-22
i'm confused. you can watch videos with mplayer in ascii without framebuffer.

you can use vlc, xine and mplayer to watch vids with framebuffer.

[http://ubuntuforums.org/showthread.php?t=882596]("http://ubuntuforums.org/showthread.php?t=882596")

---

### Post by Dr Small on 2009-03-22
> **smartboyathome said:**
> [Here you are]("http://wiki.videolan.org/Video_Output"). Remember, the Wiki is your friend. ;)
I was having a difficult time finding the wiki, only the docs. But I'm going to recompile vlc with caca and aa enabled, as it looks like the package from the repository didn't have that enabled.

---

### Post by TBOL3 on 2009-03-22
Awsome, do any of you know if there's any way to export this?

---

### Post by Dr Small on 2009-03-22
Well, even after recompiling vlc to enable caca and aa, it still won't work, yet mplayer will. So, I guess I'll just be sticking to mplayer :S

---

### Post by TBOL3 on 2009-03-22
The command is vlc <whatever file you want there, or none if you want to find it in vlc> -V aa.

Or

vlc <your file> -V caca

Hope that helps.  I'm just using the standard version that comes with Ubuntu 8.04.

---

### Post by andrew.46 on 2009-03-23
Hi Dr Small,

> **Dr Small said:**
> I know mplayer is capable of this, but I was wondering if VLC or some other specialized lightweight player could do this.

My own copy of vlc is capable of outputting ascii art and I attach 2 screenshots of Rammstein playing 'Mutter' in ascii art using aalib and libcaca. My eyes have a little trouble with this output but you can see the singer looking up through bars? The compile flag is, as you probably already know:

```
--enable-caca --enable-aa
```

with 0.9.8a. Mind you the option is a little hidden in the gui:

Tools ---> Preferences ---> Video ---> Output ---> ASCII-art video output (or Color ASCII-art video output)

I will admit that I compiled vlc on my 'other' distro which has aalib-1.4rc5 and libcaca-0.99.beta11 *fully* installed as part of its base installation, but of course it *should* work just as well under Ubuntu after the installation of the appropriate -dev files.

All the best,

Andrew (from BT)

---

### Post by Dr Small on 2009-03-23
> **andrew.46 said:**
> Hi Dr Small,



My own copy of vlc is capable of outputting ascii art and I attach 2 screenshots of Rammstein playing 'Mutter' in ascii art using aalib and libcaca. My eyes have a little trouble with this output but you can see the singer looking up through bars? The compile flag is, as you probably already know:

```
--enable-caca --enable-aa
```

with 0.9.8a. Mind you the option is a little hidden in the gui:

Tools ---> Preferences ---> Video ---> Output ---> ASCII-art video output (or Color ASCII-art video output)

I will admit that I compiled vlc on my 'other' distro which has aalib-1.4rc5 and libcaca-0.99.beta11 *fully* installed as part of its base installation, but of course it *should* work just as well under Ubuntu after the installation of the appropriate -dev files.

All the best,

Andrew (from BT)
Following your suggestion works, but only for `aa`, as Color ASCII-art Video is not found in the options, even though I compiled it with --enable-caca, along with everything else. Not sure why it doesn't work though. Even when launching VLC it says:
```
[00000001] main libvlc debug: libvlc was configured with
 ./configure  '--prefix=/usr' '--enable-dvdread' '--enable-dvdnav'
 '--enable-madi' '--enable-ffmpeg' '--disable-rpath' '--enable-qt4'
 '--enable-alsa' '--enable-skins2' '--enable-dvb' '--enable-dmo'
 '--with-ffmpeg-faac' '--with-ffmpeg-vorbis' '--with-ffmpeg-dts'
 '--with-ffmpeg-ogg' '--with-ffmpeg-theora' '--enable-v4l' '--enable-theora'
 '--enable-flac' '--enable-snapshot' '--enable-hal' '--enable-dbus'
 '--enable-ogg' **'--enable-caca' '--enable-aa'** '--enable-dbus-control'
 '--enable-shared' '--enable-nls' '--enable-lirc' '--enable-shout'
 '--enable-pvr' '--enable-release' '--program-suffix=' '--with-dv-raw1394=/usr/include/libraw1394' '--enable-loader' '--enable-live555'
 '--with-live555-tree=/usr/lib/live-media' 'CFLAGS=-march=i686 -mtune=generic -O2 -pipe'
 'CXXFLAGS=-march=i686 -mtune=generic -O2 -pipe'
```

So that's just weird. I know it has nothing to do with cacalibs, as mplayer works with it, along with cacaview.

---

### Post by duendetuc on 2009-04-05
same problem here

---

### Post by JoshuaRL on 2009-04-05
Hey doc.  I know this is still in the process of being fixed, but I have a question.  After looking at the screenshots, what is the pull of playing video in ASCII?  I tried to look at that and it gave me a headache.  I mean, I understand the geek-cred, especially for color, but I can't see the need honestly.  If you could enlighten me, I'd appreciate it.

---

### Post by Dr Small on 2009-04-05
> **JoshuaRL said:**
> Hey doc.  I know this is still in the process of being fixed, but I have a question.  After looking at the screenshots, what is the pull of playing video in ASCII?  I tried to look at that and it gave me a headache.  I mean, I understand the geek-cred, especially for color, but I can't see the need honestly.  If you could enlighten me, I'd appreciate it.
Basically, it was my desire to do it just for the fun of it. I had just recently got caca-view and was able to see images from the command line, and then remembered about video's through mplayer with it.

But watching videos through the command line in ASCII color is possible, but you need to sit about 15 feet away, so you don't get a headache :D

---

### Post by andrew.46 on 2009-04-06
Hi,

Still no luck with vlc? I can claim no glory for getting my own copy going with these outputs as I used a fairly amazing slackware script:

[http://www.slackware.com/~alien/slackbuilds/vlc/build/](http://www.slackware.com/~alien/slackbuilds/vlc/build/)

but the vital libraries are actually a standard part of a full slackware install, installed in full rather than split in the debian / ubuntu fashion. If it is any help I give the slackware versions and configure options:

==============
libcaca-0.99.beta11
==============

```
./configure \
  --prefix=/usr \
  --sysconfdir=/etc \
  --mandir=/usr/man \
  --program-prefix= \
  --program-suffix= \
  --disable-imlib2 \
  --enable-slang \
  --enable-ncurses \
  --enable-x11 \
  --build=$ARCH-slackware-linux
```

and:

===============
aalib-1.4rc5
===============

```

./configure \
  --prefix=/usr \
  --sysconfdir=/etc \
  --mandir=/usr/man \
  --program-prefix= \
  --program-suffix= \
  --build=$ARCH-slackware-linux

```

All the best,

Andrew

---

