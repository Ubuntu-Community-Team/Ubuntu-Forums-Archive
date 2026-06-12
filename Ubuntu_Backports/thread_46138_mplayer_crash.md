---
title: "mplayer crash"
date: 2005-07-03
forum: Ubuntu Backports
---

### Post by comadreja on 2005-07-03
Hello all,

my problem was I installed mplayer-586 on my hp pavilion dv1250ea, everything seemed to work fine until I tried to watch a dvd.

Then I got this:

---------------------->cut<--------------------------
Starting playback...


MPlayer interrupted by signal 11 in module: decode_audio
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
alsa-uninit: pcm closed

---------------------->cut<--------------------------

xine-totem, and xine-gstreamer also die. I downloaded the sources from mplayerhq and compiled and everything worked then.

Seems an audio problem, if I set -ao none it doesn't crash

Let me know how can I help.

Thanks !

Jorge

---

### Post by tempest on 2005-07-15
I have the exact same problem with mplayer and if I set the audio output to OSS instead of ALSA it tells me there will be no audio and plays the dvd fine (minus the sound).

I have also tried ogle and totem, they both freeze. I tried VLC and it plays the dvd with sound, but the video is choppy. DMA is not enabled,but when I try to enable it with "hdparm -d1 /dev/dvd" , i get the message 

/dev/dvd:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Permission denied
 using_dma    =  0 (off)

---

### Post by pacoman on 2005-07-15
I get the same Mplayer crash when trying to play a dvd:

**MPlayer interrupted by signal 11 in module: decode_audio **

But mplayer works perfect for all other files, and my dvds play perfect in all other applications and evertything in gstreamer works perfect...

btw to get the hdparm to work you must be a superuser i.e. use sudo. and instead of using /dev/dvd use /.dev/cdrom

so the command is as follows:

sudo hdparm -d1 /.dev/cdrom

---

### Post by pacoman on 2005-07-15
I found a possible solution to the Mplayer crash:

[http://www.archivum.info/ubuntu-users@lists.ubuntu.com/2005-06/msg01909.html](http://www.archivum.info/ubuntu-users@lists.ubuntu.com/2005-06/msg01909.html)

---

### Post by manicka on 2005-07-15
[QUOTE=tempest]I have the exact same problem with mplayer and if I set the audio output to OSS instead of ALSA it tells me there will be no audio and plays the dvd fine (minus the sound).

I have also tried ogle and totem, they both freeze. I tried VLC and it plays the dvd with sound, but the video is choppy. DMA is not enabled,but when I try to enable it with "hdparm -d1 /dev/dvd" , i get the message 

/dev/dvd:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Permission denied
 using_dma    =  0 (off)[/QUOTE]
 [http://www.ubuntuforums.org/showthread.php?p=93238#post93238](http://www.ubuntuforums.org/showthread.php?p=93238#post93238)

---

### Post by Simon K on 2005-07-18
Hello, 

I'm new to Ubuntu, having switched from Debian just yesterday. After a mostly enjoyable install, I decided to sit and vegetate in front of some mind-numbing movie for a while. My fresh new Linux distribution had some helpful advice to offer about that decision:

*MPlayer interrupted by signal 11 in module: decode_audio*

Highly annoying. So after a little well-intentioned cursing and muttering to myself, I *strace*'d it, and found that liba52 was poking around weird memory addresses (I hear there's a big party for misbehaving audio codecs at 0x0). An *apt-get build-dep mplayer; apt-get source mplayer* later, I try to see if I can get it to behave. After a little experimentation, I find that if I compile mplayer with the regular *./configure; make* we all know and love, it results in a working mplayer that'll play anything I throw at it; whereas if I do a *debian/rules binary*, I get the segfaulting audio decoder. Obviously, something in the packaging is going wrong. 

Now, I don't like having an application the size of *mplayer* outside my package management, so I checked out the contents of debian/patches -- and sure enough, in *debian/patches/03_configure.dpatch*, I spot these interesting lines:

```
@@ -1267,7 +1267,7 @@
 # GOTCHA: the variables below defines the default behavior for autodetection
 # and have - unless stated otherwise - at least 2 states : yes no
 # If autodetection is available then the third state is: auto
-_libavcodec=auto
+_libavcodec=no
 _libavcodecso=auto
 _libavformat=auto
 _fame=auto
```

Oho! We're telling mplayer to not go with its own libavcodec, since we're using the one in Ubuntu. There's an easy "solution", though: After removing this block, mplayer can compile with *debian/rules binary*, so we get working mplayer-custom packages that can be managed using apt. It's not as good as fixing the broken libavcodec, but it'll work for now.

There's a patch for it at the bottom of this post. To apply the patch, put it in a file, hop into the mplayer source directory and *patch -p1 < patchfilename*

NOTE: You might need to *export DEB_BUILD_OPTIONS="custom"* before you do the build. Otherwise, you get a bunch of empty .debs.

Cheers,
Simon

Here's the patch: 
```

diff -ruN mplayer-1.0-pre6/debian/patches/03_configure.dpatch mplayer-1.0-pre6-fixed/debian/patches/03_configure.dpatch
--- mplayer-1.0-pre6/debian/patches/03_configure.dpatch 2005-07-19 00:33:31.974622320 +0200
+++ mplayer-1.0-pre6-fixed/debian/patches/03_configure.dpatch   2005-07-19 01:25:51.772300520 +0200
@@ -15,15 +15,6 @@

 --- configure.orig 2004-12-25 10:53:30.000000000 +0100
 +++ configure  2004-12-25 10:57:24.000000000 +0100
-@@ -1267,7 +1267,7 @@
- # GOTCHA: the variables below defines the default behavior for autodetection
- # and have - unless stated otherwise - at least 2 states : yes no
- # If autodetection is available then the third state is: auto
--_libavcodec=auto
-+_libavcodec=no
- _libavcodecso=auto
- _libavformat=auto
- _fame=auto
 @@ -5563,16 +5563,16 @@
    echores "yes (using $_livelibdir)"
    _def_live='#define STREAMING_LIVE_DOT_COM 1'

```

---

### Post by sjmorgan on 2005-07-19
[QUOTE=Simon K]
*MPlayer interrupted by signal 11 in module: decode_audio*
[/QUOTE]
Excellent work! This has been bugging me for ages and now it seems to be finally fixed. I tried a bunch of things but never really nailed it. Building a package using the official pre7 release fixed the crash but the rules file that comes with it generates a  package that doesn't work too well on my system.

I also got the same crash with certain non-dvd video files so time will tell whether this fixes those as well (I can't remember any specific ones off the top of my head).

Thanks again.

EDIT: I just realised it must be ones that have the audio encoded as AC3 so I found some and they work. Hooray!

---

### Post by kalle314 on 2005-08-08
I am getting another kind of mplayer crash:

* I have installed mplayer (using synaptic).
* I have installed the multimedia codecs ([http://ubuntuguide.org/#codecs)](http://ubuntuguide.org/#codecs)).
* I have rebooted the computer.
* I use the MediaPlayerConnectivity plugin to have quicktime trailers play in mplayer.

When I go to apple.com and try to watch a trailer (in quicktime format), mplayer and firefox crashes. (mplayer plays avi and mpeg without problem.)
This is the output I got four times (different trailers.)

```
  
18:24:50 $  MPlayer 1.0pre6-3.3.5 (C) 2000-2004 MPlayer Team
CPU: Advanced Micro Devices Athlon MP/XP Thoroughbred (Family: 6, Stepping: 1)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled for Debian.


Linux RTC init error in ioctl (rtc_irqp_set 1024): [Access denied.]
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : [This file or directory does not exist.]
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: [This file or directory does not exist.]
Failed to open LIRC support.
You will not be able to use your remote control.


MPlayer interrupted by signal 1 in module: unknown
- MPlayer crashed. This shouldn't happen.

``` 

(some output in swedish translated to english, marked by [].).

---

### Post by phewner on 2005-09-04
[QUOTE=Simon K]

 There's an easy "solution", though: After removing this block, mplayer can compile with *debian/rules binary*, so we get working mplayer-custom packages that can be managed using apt. It's not as good as fixing the broken libavcodec, but it'll work for now.

[/QUOTE]

If you're unsure exactly what is meant by "compile with *debian/rules binary*" (I was).  This website may help: [http://lyre.mit.edu/~powell/debian-howto/build-source.html](http://lyre.mit.edu/~powell/debian-howto/build-source.html) although the good news is that is really is as easy as typing *debian/rules binary* for the most part.

Also, the patch file didn't quite work for me but I don't know how to fix it.  The intention seems pretty obvious though...just remove these lines from the file debian/patches/03_configure.dpatch:

```
@@ -1267,7 +1267,7 @@
 # GOTCHA: the variables below defines the default behavior for autodetection
 # and have - unless stated otherwise - at least 2 states : yes no
 # If autodetection is available then the third state is: auto
-_libavcodec=auto
+_libavcodec=no
 _libavcodecso=auto
 _libavformat=auto
 _fame=auto
```

Then after you build install the packages like this:

 sudo dpkg -i ../*.deb

---

### Post by Cashel on 2005-09-05
Hello,

 Having had this error myself with none of the related fixes working, I discovered an incredibly easy fix... change from OSS for ESD sound system under mplayer's preferences... it causes this same error.. probably should have looked there first but hey :) 

 So try that first folks! 


.. now if I could just get it working fullscreen, hehe

---

### Post by Name on 2005-09-08
could someone translate this into noob for me. I have no clue how to fix this error. Ive been using linux all of 5 days.

plop the code into what file in what folder? I got no clue what the source directory for mplayer is.

---

### Post by Sharebear on 2005-09-16
This patch has been available for 2 months now, any chance someone could apply it to the official backports repo? I really don't want to install a compiler on my stable desktop system just so that I can play/rip DVDs :-(

Thanks in advance

Jon

---

### Post by ernestohs on 2005-12-09
Thanks, this works fine.

But some notes about this issue:

[LIST=1]
[*] Get the code
```
$ sudo apt-get build-dep mplayer; sudo apt-get source mplayer
```
[*] unpack
```
$ tar -xzf  mplayer_1.0-pre6.orig.tar.gz
```
[*] Copy the ubuntu patch to MPlayer source code dir
```
$ cp mplayer_1.0-pre6-0.3ubuntu6.diff.gz MPlayer_1.0-pre6/ 
```
[*] Go to MPlayer dir
```
$ cd MPlayer_1.0-pre6/ 
```
[*] Apply the patch
```
$ zcat mplayer_1.0-pre6-0.3ubuntu6.diff.gz | patch -p1 
```
[*] Do the magic
```
$ cat > SimonK.patch 
```
Then copy the Simon patch and paste, then press ^D (CTRL+D)

[*] Compile
```
$ ./configure; make 
```
[*] Enjoy
```
$ mplayer dvd:// 
```
Get fun :D
[/LIST]

Once again, thanks to Simon for his help...

---

### Post by renebe on 2006-05-10
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
E: De vereiste Build-Depends van pakket mplayer kan niet voldaan worden omdat er geen beschikbare versies zijn van pakket debhelper die aan de versievereisten voldoen
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
Moet 7723kB aan bronarchieven ophalen.
Ophalen:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse mplayer 1:1.0-pre6-0.3ubuntu6 (dsc) [2241B]
Ophalen:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse mplayer 1:1.0-pre6-0.3ubuntu6 (tar) [7450kB]
Ophalen:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse mplayer 1:1.0-pre6-0.3ubuntu6 (diff) [271kB]
7723kB opgehaald in 31s (248kB/s)
sh: dpkg-source: command not found
Uitpakopdracht 'dpkg-source -x mplayer_1.0-pre6-0.3ubuntu6.dsc' is mislukt.
E: Dochterproces is mislukt

Oops... that's in Dutch off course :)

What it's saying is that there's a problem with depends because there are no debhelper versions available (whatever that means).
And that dpkg-source cannot be found (I'm the noobest noob, so I haven't got a clue)
And finally that a child process had failed.

Any ideas? I'm trying to get a dvd player working for almost two months now, without any luck :(

Sincerely,
René.

---

### Post by WADemosthenes on 2006-06-16
> **ernestohs]Thanks, this works fine.

But some notes about this issue:

[LIST=1]
[*] Get the code
```
$ sudo apt-get build-dep mplayer said:**
>  unpack
```
$ tar -xzf  mplayer_1.0-pre6.orig.tar.gz
```
[*] Copy the ubuntu patch to MPlayer source code dir
```
$ cp mplayer_1.0-pre6-0.3ubuntu6.diff.gz MPlayer_1.0-pre6/ 
```
[*] Go to MPlayer dir
```
$ cd MPlayer_1.0-pre6/ 
```
[*] Apply the patch
```
$ zcat mplayer_1.0-pre6-0.3ubuntu6.diff.gz | patch -p1 
```
[*] Do the magic
```
$ cat > SimonK.patch 
```
Then copy the Simon patch and paste, then press ^D (CTRL+D)

[*] Compile
```
$ ./configure; make 
```
[*] Enjoy
```
$ mplayer dvd:// 
```
Get fun :D
[/LIST]

Once again, thanks to Simon for his help...
After "sudo apt-get build-dep mplayer; sudo apt-get source mplayer" I get the message: 

"Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for mplayer
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for mplayer"

What do I need to add to my source list? I uncommented everything alread.

---

### Post by strikeforce on 2006-06-16
[QUOTE=WADemosthenes]After "sudo apt-get build-dep mplayer; sudo apt-get source mplayer" I get the message: 

"Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for mplayer
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for mplayer"

What do I need to add to my source list? I uncommented everything alread.[/QUOTE]

You need to edit your apt/sources.list and uncomment the additional sources.

sudo gedit /etc/apt/sources.list

When that loads up uncomment the additional sources.

---

### Post by bobp0303 on 2006-07-08
Hoping I'm sending this to the right folks -- I noticed there was a "please send bug report", so here it is.

Extremely premature exit when attempting to play Fantasia DVD "Special 60th Anniversary Edition" using mplayer -- the Walt Disney splash screen came up, two measures of music played, and mplayer exited.

I have the -xine options installed, and the movie plays fine under Totem.

(begin terminal session screen dump)

DapperDrake:~$ mplayer dvd://1 -dvd-device /dev/hdc
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium 4/Celeron 4 Northwood; Pentium 4 EE/Xeon Prestonia,Gallatin (Family: 15, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing dvd://1.
libdvdread: Using libdvdcss version 1.2.9 for DVD access
Reading disc structure, please wait...
There are 9 titles on this DVD.
There are 2 chapters in this DVD title.
There are 1 angles in this DVD title.
Please send bug report - no VTS_TMAPT ??

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00001250
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000012c5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x000012db
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000012e0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00001fce
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x000020c1
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x000020c6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00002b65
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x0000c201
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x0031ce6f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x003ee153
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003ee1b8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x003f089a
libdvdread: Elapsed time 0
libdvdread: Found 8 VTS's
libdvdread: Elapsed time 0
DVD successfully opened.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  9800.0 kbps (1225.0 kbyte/s)
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
AC3: 2.0 (stereo)  48000 Hz  192.0 kbit/s
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12
A:   6.7 V:   6.7 A-V: -0.004 ct:  0.045 197/197 15%  1%  1.2% 1 0
alsa-uninit: pcm closed

Exiting... (End of file)
DapperDrake:~$


(end terminal session screendump)

---

