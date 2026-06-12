---
title: "ffmpeg/make/checkinstall?"
date: 2009-10-18
forum: Server Platforms
---

### Post by adman4054 on 2009-10-18
I received this error message "Unable for find a suitable output format for '0'"
after reinstalling ffmpeg. I googled it and found that I was missing some codecs and should install a version from Mediabuntu. So I added mediabuntu as a repository. I uninstalled ffmpeg and downloaded the new version:
[code]

The following NEW packages will be installed:
  ffmpeg
0 upgraded, 1 newly installed, 0 to remove and 297 not upgraded.
Need to get 195kB of archives.
After this operation, 664kB of additional disk space will be used.
Get:1 http://packages.medibuntu.org hardy/free ffmpeg 3:0.cvs20070307-5ubuntu7.3           +medibuntu1 [195kB]
Fetched 195kB in 1s (150kB/s)
Selecting previously deselected package ffmpeg.
(Reading database ... 157309 files and directories currently installed.)
Unpacking ffmpeg (from .../ffmpeg_3%3a0.cvs20070307-5ubuntu7.3+medibuntu1_i386.d           eb) ...
Setting up ffmpeg (3:0.cvs20070307-5ubuntu7.3+medibuntu1) ...

I followed these instructions:
C. Installing the ubuntu-restricted-extras package
Another option for Jaunty and Ibex is to install the ubuntu-restricted-extras package. This is a metapackage, which means that it will install multiple packages including the "unstripped" FFmpeg libraries. This is a sledgehammer approach, especially if you are bandwidth limited, and will install a large amount of other packages that you may not want. To install this package, open up Terminal (Applications -> Accessories -> Terminal) and enter:


Code:
sudo apt-get install ffmpeg ubuntu-restricted-extrasD. Installing FFmpeg from Medibuntu
This option is only available for Ubuntu Hardy Heron 8.04 and Ubuntu Gutsy Gibbon 7.10. Medibuntu is a third-party repository that contains a number of packages that are unable to be included in the official Ubuntu repositories. To install FFmpeg from Medibuntu open Terminal (Applications -> Accessories -> Terminal) and run the following:


Code:
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q updateThis huge command will install the repository information to your computer then update and authenticate the new repository. Now install FFmpeg:


Code:
sudo apt-get install ffmpeg

That's as far as the instructions go, so do I need to do make, check install and configure? If I have to ./configure, how do i know what I'm configuring. This is my forth attempt at trying to make ffmpeg work and the other instructions I followed always gave me what I needed to configure. I assume that there would be a different configuration if there are more files with this download.



From Apache log:
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 17 2009 21:37:49, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/xxxxxxxx/Public/xxxxxxxx/admin/../movies/AANQ11.mov':
  Duration: 00:02:06.1, start: 0.000000, bitrate: 731 kb/s
  Stream #0.0(eng): Audio: mp4a / 0x6134706D, 44100 Hz, stereo
  Stream #0.1(eng): Video: svq3, yuv420p, 360x240, 29.97 fps(r)
Unable for find a suitable output format for '0'
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 17 2009 21:37:49, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/xxxxxxxx/Public/xxxxxxxx/admin/../movies/AANQ11.mov':
  Duration: 00:02:06.1, start: 0.000000, bitrate: 731 kb/s
  Stream #0.0(eng): Audio: mp4a / 0x6134706D, 44100 Hz, stereo
  Stream #0.1(eng): Video: svq3, yuv420p, 360x240, 29.97 fps(r)
PIX_FMT_YUV420P will be used as an intermediate format for rescaling
Output #0, rawvideo, to '/home/xxxxxxxx/Public/xxxxxxxx/admin/../flvfiles/245277.png':
  Stream #0.0: Video: png, rgb24, 110x90, q=2-31, 200 kb/s, 29.97 fps(c)
Stream mapping:
  Stream #0.1 -> #0.0
Press [q] to stop encoding
frame=    1 q=0.0 Lsize=       9kB time=0.0 bitrate=2319.9kbits/s

Thanks for taking a look!

---

### Post by laceration on 2009-10-18
There is no make, check install and configure (compiling) to be done.  Adding repositories is adding more sources for programs that you can install with the apt system.  The whole idea of apt is to install programs without having to compile them.  All you need to do is

sudo apt-get install ffmpeg

You might open synaptic, which is basically an apt gui and search for ffmpeg and install from there.  If you add all those repositories you may have some different versions of ffmpeg to choose from.

---

### Post by adman4054 on 2009-10-18
> **laceration said:**
> There is no make, check install and configure (compiling) to be done.  Adding repositories is adding more sources for programs that you can install with the apt system.  The whole idea of apt is to install programs without having to compile them.  All you need to do is

sudo apt-get install ffmpeg

You might open synaptic, which is basically an apt gui and search for ffmpeg and install from there.  If you add all those repositories you may have some different versions of ffmpeg to choose from.

Thanks for the reply, so I added some codecs after the install, do they just work or do I need to uninstall/install
Thanks again!

---

### Post by laceration on 2009-10-18
I can't say for sure because I do not know the details, but they probably just work.  Try them out.

---

### Post by andrew.46 on 2009-10-18
Hi adman,

> **adman4054 said:**
> I received this error message "Unable for find a suitable output format for '0'"

Can you give the full *commandline* as well as the full terminal output for this error as I suspect there could be an error in your syntax.

All the best,

Andrew

---

### Post by adman4054 on 2009-10-18
> **andrew.46 said:**
> Hi adman,



Can you give the full *commandline* as well as the full terminal output for this error as I suspect there could be an error in your syntax.

All the best,

Andrew

Thanks for the reply Andrew, I think you will find both here:
[http://ubuntuforums.org/showthread.php?t=1294568](http://ubuntuforums.org/showthread.php?t=1294568)

---

### Post by andrew.46 on 2009-10-18
Hi adman,

> **adman4054 said:**
> Thanks for the reply Andrew, I think you will find both here:
[http://ubuntuforums.org/showthread.php?t=1294568](http://ubuntuforums.org/showthread.php?t=1294568)

I see you have the FakeOutdoorsman on the job there and he is by far the best one to give advice on FFmpeg on these forums :).

Andrew

---

