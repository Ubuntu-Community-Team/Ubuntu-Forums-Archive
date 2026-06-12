---
title: "ffmpeg unstripped dev packages?"
date: 2009-07-24
forum: Ubuntu Studio
---

### Post by akos.maroy on 2009-07-24
Hi,

I needed to get mpeg4 support for ffmpeg unto my box, so I installed the 'unstripped' ffmpeg packages. but, these removed my previously installed -dev packages related to ffmpeg - and I can't find any -dev packages for these 'unstripped' anywhere.

might it be the case that they don't exist?


Akos

---

### Post by SteveDee on 2009-07-24
> **akos.maroy said:**
> Hi,

I needed to get mpeg4 support for ffmpeg unto my box, so I installed the 'unstripped' ffmpeg packages. but, these removed my previously installed -dev packages related to ffmpeg - and I can't find any -dev packages for these 'unstripped' anywhere.

might it be the case that they don't exist?


Akos

You may find an answer here: [http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by Grishka on 2009-07-24
[https://launchpad.net/~freshmedia/+archive/ppa](https://launchpad.net/~freshmedia/+archive/ppa)

---

### Post by andrew.46 on 2009-07-24
Hi akos,

> **akos.maroy said:**
> I needed to get mpeg4 support for ffmpeg unto my box, so I installed the 'unstripped' ffmpeg packages.

Can I ask what sort of encoding/transcoding are you trying to do?

Andrew

---

### Post by akos.maroy on 2009-07-25
> **SteveDee said:**
> You may find an answer here: [http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

hm, I'm not finding references to unstripped -dev packages on this page. it seems that one can either install ffmpeg-related -dev packages, or unstripped packages - but not both.

this is sad, as one can't develop for ffmpeg if he has the unstripped packages installed :(

---

### Post by akos.maroy on 2009-07-25
> **andrew.46 said:**
> Hi akos,



Can I ask what sort of encoding/transcoding are you trying to do?

Andrew

sure:

```

ffmpeg -i video.mp4 -s 480x320 -vcodec mpeg4 -acodec libfaac -ac 1 -ar 16000 -r 13 -ab 32000 -aspect 3:2 output-video.G1.mp4

```

basically transcoding a video so that it can be watched on a google android phone

---

### Post by SteveDee on 2009-07-25
No sure if you are developing software or just trying to use the conversion features of ffmpeg. If the latter, then you might want to look at this: [http://winff.org/html_new/](http://winff.org/html_new/) which is reckoned to support any translation/conversion that ffmpeg supports.

---

### Post by akos.maroy on 2009-07-25
> **SteveDee said:**
> No sure if you are developing software or just trying to use the conversion features of ffmpeg. If the latter, then you might want to look at this: [http://winff.org/html_new/](http://winff.org/html_new/) which is reckoned to support any translation/conversion that ffmpeg supports.

I'm trying to do both - use it for conversion & develop using ffmpeg.

---

### Post by andrew.46 on 2009-07-25
Hi akos,

> **akos.maroy said:**
> sure:

```

ffmpeg -i video.mp4 -s 480x320 -vcodec mpeg4 -acodec libfaac -ac 1 -ar 16000 -r 13 -ab 32000 -aspect 3:2 output-video.G1.mp4

```

basically transcoding a video so that it can be watched on a google android phone

You are obviously no beginner with FFmpeg, why not go the full distance and start running the svn FFmpeg? Details for Ubuntu are here:

HOWTO: Install and use the latest FFmpeg and x264 
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

This might be better than grappling with dev files and the results will almost always be better.

Andrew

---

### Post by akos.maroy on 2009-07-25
> **andrew.46 said:**
> Hi akos,



You are obviously no beginner with FFmpeg, why not go the full distance and start running the svn FFmpeg? Details for Ubuntu are here:

HOWTO: Install and use the latest FFmpeg and x264 
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

This might be better than grappling with dev files and the results will almost always be better.

Andrew

I could - but what's the point of packages then? :)

also, then what I develop is not guaranteed to work on other machines which just have the stop ffmpeg packages installed.

but: is there a place to file a ticket for this packaging issue?

---

### Post by mc4man on 2009-07-25
I think any of 3 or 4 ways may serve your needs which could be the determining factor. ([COLOR="Blue"]the edit may be better for you[/COLOR]

The ppa mentioned will give you ffmpeg, the shared libs, and -devs as current as the ppa updates and enabled to the extent chosen and configured
(info below

Or you could build ffmpeg as static, with ffmpeg enabled and configured to your choosing and for the shared libs use the repo unstripped versions to the extent they're enabled and configured.  (noting that apps that use the ffmpeg libs will use the repo libs for better or worse even if built off of your static svn headers (same as -devs

Because the version #'s are the same for most of the ffmpeg libs in jaunty/karmic as in the svn, I'd avoid building a svn as shared unless you do them as debian packages. 

If you want/ need more than the repo's unstripped offer, or want to build apps that depend on ffmpeg shared libs and don't want to use the ppa or need a different configure, then do it for yourself (very easy once set up.

I did a quick debuild of the ppa's source on hardy, here is basically how it's configured, enabled.
(I prefer the diff/configure/patches of  Christian Marillat (debian-multimedia) to the above mentioned ppa's, plus i add wmapro to it

((though the ppa's configure could be easily edited to suit


The ppa, snippet of build log (the formats list is more revealing but a bit large to post
> yasm                      yes
MMX enabled               yes
MMX2 enabled              yes
3DNow! enabled            yes
3DNow! extended enabled   yes
SSE enabled               yes
SSSE3 enabled             yes
CMOV enabled              no
CMOV is fast              no
EBX available             yes
EBP available             yes
10 operands supported     yes
gprof enabled             no
debug symbols             yes
strip symbols             no
optimizations             yes
static                    no
shared                    yes
postprocessing support    yes
new filter support        yes
filters using lavformat   yes
network support           yes
IPv6 support              yes
threading support         pthreads
SDL support               yes
Sun medialib support      no
AVISynth enabled          no
libdc1394 support         yes
libdirac enabled          no
libfaac enabled           yes
libfaad enabled           yes
libfaad dlopened          no
libgsm enabled            yes
libmp3lame enabled        yes
libnut enabled            no
libopencore-amrnb support no
libopencore-amrwb support no
libopenjpeg enabled       no
libschroedinger enabled   yes
libspeex enabled          yes
libtheora enabled         yes
libvorbis enabled         yes
libx264 enabled           yes
libxvid enabled           yes
zlib enabled              yes
bzlib enabled             yes

screen shows what the ppa offers or what you'd get from building it's source

This is basically the configure using the debian-multimedia diff a few days ago (built and installed as packages to /usr, (ffmpeg, libs and -devs

> FFmpeg version SVN-r19468, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --prefix=/usr --extra-cflags='-Wall -g ' --libdir='${prefix}/lib' --shlibdir='${prefix}/lib' --bindir='${prefix}/bin' --incdir='${prefix}/include/ffmpeg' --enable-shared --enable-libmp3lame --enable-gpl --enable-libfaad --mandir='${prefix}/share/man' --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-x11grab --enable-libgsm --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libtheora --enable-libdc1394 --enable-libspeex --enable-nonfree -[COLOR="Blue"]-disable-stripping [/COLOR]--enable-avfilter --enable-libdirac --disable-decoder=libdirac --enable-libschroedinger --disable-encoder=libschroedinger --enable-avfilter-lavf --enable-libopenjpeg --enable-version3 --disable-altivec --disable-armv5te --disable-armv6 --disable-vis


(takes about 15 min. start to finish once setup with needed build-deps and package deps (on core2duo

edit
> also, then what I develop is not guaranteed to work on other machines which just have the stop ffmpeg packages installed.

Just saw that, if you think it may cause a problem. what you could also do then is just apt-get  the ubuntu repo's build-deps for ffmpeg, apt-get the ffmpeg source and build a package set (probably just use "fakeroot debian/rules binary"

That will give you the exact same packages as you have now with the exception that they'll be unstripped with matching -devs ( note they won't say 'unstripped' but they will be

you may need a small edit or 2 in the debian folder, nothing too much if at all

---

### Post by mc4man on 2009-07-25
happened to boot up to a live jaunty cd for something so gave building the repo source a try (never used one before, on a 64 bit live cd, but no different if 32 bit

pretty easy, from terminal history
1  sudo apt-get build-dep ffmpeg
    2  sudo apt-get install fakeroot
    3 mkdir ffmpeg && cd ffmpeg
    4 apt-get source ffmpeg
    5  cd ffmpeg-debian-0.svn20090303
    6  fakeroot debian/rules binary
    7  sudo dpkg -i *.deb
....................................... some quick tests
    8  ffplay  mummers.m4a 
    9  ffplay 1.mp3
    10 ffplay w2.wma

between 5 and 6 went in to the debian folder -> control and edited so packages would be named .....-unstripped (may or may not matter, when building apps - depends on apps should be the unstripped if building your apps as .deb's

ubuntu@ubuntu:~$ ffmpeg
> FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Jul 25 2009 08:48:29, gcc: 4.3.3


this is the default confflags (shows config

>  Common configuration flags; comment out following line for LGPL versions of
# the libraries
confflags += $(gpl_confflags)
confflags += --extra-version='svn$(SVNREVISION)+$(DEB_VERSION)'
confflags += --prefix=/usr
confflags += --enable-avfilter
confflags += --enable-avfilter-lavf
confflags += --enable-libgsm
confflags += --enable-libschroedinger
confflags += --enable-libspeex
confflags += --enable-libtheora
confflags += --enable-libvorbis
confflags += --enable-pthreads
confflags += --disable-stripping
confflags += --disable-vhook

# this part below is intended for the 'ffmpeg' package in ubuntu/multiverse
confflags += $(call cond_enable,/usr/include/xvid.h,libxvid)
confflags += $(call cond_enable,/usr/include/lame/lame.h,libmp3lame)
confflags += $(call cond_enable,/usr/include/faac.h,libfaac)
confflags += $(call cond_enable,/usr/include/x264.h,libx264)
confflags += $(call cond_enable,/usr/include/vdpau/vdpau.h,vdpau)

# Enable IEEE 1394 (FireWire) support on Linux only
ifneq (,$(findstring linux,$(DEB_HOST_GNU_TYPE)))
  confflags += --enable-libdc1394
  lib1394-dev += libraw1394-dev, libdc1394-22-dev
endif

(( you could add/remove a few  things if wanted, may not be needed/desired , may require some small edits in debian folder, this is the repo one exactly (unstripped

note that ffmpeg and the lib...... -unstripped, while seen as same version as repo ones will be upgraded by apt if allowed, so lock versions

(you could append the versions with lib......-1 but you may be better off just locking

If you wish to try out and need edited confflags file I'll post

(note screenshot truncates full name, but the are as they should be

---

### Post by paul.gevers on 2009-07-27
> **akos.maroy said:**
> but: is there a place to file a ticket for this packaging issue?

There is already a long standing issue about this, which just has been solved (in Karmic).

See: [http://bugs.launchpad.net/ubuntu/+source/ffmpeg-debian/+bug/312898]("https://bugs.launchpad.net/ubuntu/+source/ffmpeg-debian/+bug/312898")

---

### Post by akos.maroy on 2009-07-27
> **paul.gevers said:**
> There is already a long standing issue about this, which just has been solved (in Karmic).

See: [http://bugs.launchpad.net/ubuntu/+source/ffmpeg-debian/+bug/312898]("https://bugs.launchpad.net/ubuntu/+source/ffmpeg-debian/+bug/312898")

great! how long until this fix makes it into ubutnu 8.10?

---

### Post by paul.gevers on 2009-07-27
> **akos.maroy said:**
> great! how long until this fix makes it into Ubuntu 8.10?

It is most likely NOT going to make it into 8.10. Please see the before mentioned bug report. The packager of ffmpeg doesn't believe this is important enough for back porting (as he only introduced to "fix" this bug because so many people requested this feature).

OT most bugs which are not of the "this program crashes" or "data is lost" type are not solved in the current versions of Ubuntu, unless specifically requested and justified.

---

