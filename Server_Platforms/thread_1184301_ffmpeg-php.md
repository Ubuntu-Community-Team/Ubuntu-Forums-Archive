---
title: "ffmpeg-php"
date: 2009-06-11
forum: Server Platforms
---

### Post by jo282 on 2009-06-11
Hi,

I`m trying to install ffmpeg-php (and all is requirements) on a ubuntu 9.04 sever using this guide : [GUIDE HERE]("http://www.imyun.net/2008/10/installing-ffmpeg-and-ffmpeg-php-on-a-cpanel-server.html") and at the last step (compiling/installing ffmpeg-php), i get (make: *** [ffmpeg_frame.lo] Error 1).
 
 The guide mention that i can have this error and tell me to rename ffmpeg_frame.loT to ffmpeg_frame.lo (cp ffmpeg_frame.loT ffmpeg_frame.lo) but when i do that, it tell me that the file does not exist :o. 

Here`s the content of my ffmpeg-php-0.5.3.1 folder :

> acinclude.m4         config.nice                 ffmpeg_frame.c        INSTALL                  mkinstalldirs
aclocal.m4      config.status          ffmpeg_frame.h   install-sh          modules
autom4te.cache  config.sub             ffmpeg_movie.c   libtool             php_ffmpeg.h
build           configure              ffmpeg_movie.h   LICENSE             run-tests.php
ChangeLog       configure.in           ffmpeg_movie.lo  ltmain.sh           test_ffmpeg.php
config.guess    CREDITS                ffmpeg-php.c     Makefile            tests
config.h        EXPERIMENTAL           ffmpeg-php.lo    Makefile.fragments  tmp.png
config.h.in     ffmpeg_animated_gif.c  gd.h             Makefile.global     TODO
config.log      ffmpeg_animated_gif.h  gd_io.h          Makefile.objects
config.m4       ffmpeg_errorhandler.c  include          missing


I also tryed with version 0.6.0 but i got the same error.

While searching for a way to fix it i see the command (apt-get install ffmpeg-php) but it was on an old thread and the command does not work with my sources.

So please help me to fix it. P.S : Im not very pro with linux so please tell me the command i need to do.

Thanks very very much.

---

### Post by FakeOutdoorsman on 2009-06-11
No need to compile ffmpeg-php.  It's in the repository:
```
sudo apt-get install php5-ffmpeg
```
You may need to undo some of the steps you followed in that outdated tutorial.

---

