---
title: "Where are ffmpeg's header files?"
date: 2008-12-27
forum: Ubuntu Studio
---

### Post by resander on 2008-12-27
I am using Ubuntu 8.10 and installed ffmpeg via Synaptic. 
After cd /usr/bin and ffmpeg -version I get:

ken@ken-desktop:/usr/bin$ ffmpeg -version
FFmpeg version UNKNOWN-svn15824+3:0.svn20081115-1ubuntu1~ppa1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn15824+3:0.svn20081115-1ubuntu1~ppa1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.12. 0 / 49.12. 0
  libavcodec    52. 3. 0 / 52. 3. 0
  libavformat   52.23. 1 / 52.23. 1
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 1. 0 /  0. 1. 0
  libswscale     0. 6. 1 /  0. 6. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Dec 15 2008 18:22:40, gcc: 4.3.2
FFmpeg UNKNOWN-svn15824+3:0.svn20081115-1ubuntu1~ppa1
libavutil     49.12. 0 / 49.12. 0
libavcodec    52. 3. 0 / 52. 3. 0
libavformat   52.23. 1 / 52.23. 1
libavdevice   52. 1. 0 / 52. 1. 0
libavfilter    0. 1. 0 /  0. 1. 0
libswscale     0. 6. 1 /  0. 6. 1
libpostproc   51. 2. 0 / 51. 2. 0

which shows that ffmpeg reacts and libraries are installed.
I want to go through a tutorial written in C that uses include files 

#include <ffmpeg/avcodec.h>
#include <ffmpeg/avformat.h>

I cannot find avcodec.h, avformat.h, avutil.h or any other ffmpeg include file.
Where are they?

---

### Post by lensman3 on 2008-12-27
Libraries are installed with the program automatically.  The header files ususally are installed with the "development" source.

When the source file you have says 

#include <ffmpeg/avcodec.h>

then ffmpeg/avcodec.h is installed under "/usr/include" OR /usr/local/include".  The second one is considered a temporary or secondary location. 

From the command line use "locate avcodec.h" or "find / -name "avcodec.h"" to discover a file's location on the file system.  The second command can take a while since the "/" does the search from the root file system.  The command can also give lots of errors if you don't have permission to read or go into a directory.  The quotes around avocodec.h in this case can be dropped.  Use quotes if you want to wild card a file name.

In your case you will have to install the ffmpeg development suite of files.  But it will have the header files with it.

Hope this helps.

---

### Post by resander on 2008-12-28
Thanks for the advice.

It would appear the synaptic install did not put any ffmpeg header files into directories. I searched using Places->SearchForFiles via the GUI and the find command from the command line and visually inspected usr/include.

So, decided to install from source following FakeOutdoorsman's tutorial HOWTO: Compile the latest ffmpeg and x264 from source  ([http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)).
The install process put a ffmpeg directory in my home directory. Subdirectories in ffmpeg contained libavcodec, libavformat directories that in turn contained header files. There are also copies of libavcodec and libavformat directories in /usr/local/include.

---

