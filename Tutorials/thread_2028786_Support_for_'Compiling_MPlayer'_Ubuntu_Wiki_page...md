---
title: "Support for 'Compiling MPlayer' Ubuntu Wiki page...."
date: 2012-07-18
forum: Tutorials
---

### Post by andrew.46 on 2012-07-18
This thread is intended for support, discussion and development of the Ubuntu Community Wiki page:

Compiling MPlayer
[https://help.ubuntu.com/community/Compiling%20MPlayer](https://help.ubuntu.com/community/Compiling%20MPlayer)

I would encourage people to not only use this wiki page but also log on and edit + improve the page. I will be stepping back a little from upkeep of the page but perhaps some suggested updates could be:

[LIST=1]
[*]Make a link from the wiki page to this thread
[*]Add a section on compiling MPlayer2
[*]Add some details for compiling MEncoder
[*]Sort out the live555 mess, it no longer compiles with MPlayer :(
[*]Add in some useful links
[/LIST]

and whatever people feel is necessary. I will be interested to see if greater community involvement in the wiki version of this guide will yield a better MPlayer experience!

---

### Post by andrew.46 on 2012-07-26
Updated mpg123 version to 1.14.4:

```

andrew@skamandros~$ **[COLOR="Red"]mpg123 --version[/COLOR]**
mpg123 1.14.4

```

Good idea to spend a little time on the commandline with this great mp3 player.

---

### Post by mc4man on 2012-08-04
Andrew - 
don't see any issue on a 64 bit install (though using gcc 4.7.1), shortcut-ed past the blue-ray stuff, git of x264 as of the time of this post(don't know how to get version of in this instance, mplayer - 35058.
> ============ Checking for x264 ============

#include <inttypes.h>
#include <x264.h>
#if !(X264_BUILD >= 118)
#error We do not support old versions of x264. Get the latest from git.
#endif
int main(void) { x264_encoder_open((void*)0); return 0; }

cc -Wundef  -Wstrict-prototypes -Wmissing-prototypes -Wdisabled-optimization -Wno-pointer-sign -Wdeclaration-after-statement -std=gnu99  -I/home/doug/mplayer_build/mplayer_deps/usr/include -fno-tree-vectorize /tmp/mplayer-configure--14203/tmp.c -Ilibdvdread4 -I. -Iffmpeg  -I/home/doug/mplayer_build/mplayer_deps/usr/include  -D_REENTRANT -I/usr/include/directfb -I/usr/include/     -D_REENTRANT    -I/usr/include/freetype2 -I/usr/include/opus   -I/usr/include/bs2b    -lm  -L/home/doug/mplayer_build/mplayer_deps/usr/lib   -lncurses -lsmbclient -lpng -lz -ljpeg -lungif -lasound -ldl -lpthread -lcdda_interface -lcdda_paranoia -L/usr/lib/x86_64-linux-gnu -lfreetype -lz -lfontconfig  -lfribidi -lass -lenca -lz -lbz2 -lmad -lspeex -lgsm -ltheoradec -logg -lmpg123 -la52 -lfaad -lopus   -lbs2b   -lliveMedia -lgroupsock -lBasicUsageEnvironment -lUsageEnvironment -lstdc++ -lrtmp -lopencore-amrnb -lopencore-amrwb -ldv -lxvidcore  -ldirectfb  -lXext -lX11 -lpthread -lXv -lvdpau -lXinerama -lXxf86vm -lXxf86dga -lggi -laa -L/usr/lib/x86_64-linux-gnu -lcaca -lvga -lSDL -lGL -ldl -lesd   -lpulse   -ljack -lopenal -lfaac  -ltwolame -lfaac -o /tmp/mplayer-configure--14203/tmp -lx264 -lpthread


Result is: yes (in FFmpeg: yes)
##########################################
Do have a 32 bit install that I'll try on in a bit
(you decided it's best to to use a shared libx264 for mencoder?

---

### Post by mc4man on 2012-08-05
For some reason on my 32 bit install get this error unless I just build 'as usual' or build with mencoder/libx264 with libx264 installed normally
```
mp3lib/dct64_sse.c: In function 'dct64_sse':
mp3lib/dct64_sse.c:59:13: error: can't find a register in class 'GENERAL_REGS' while reloading 'asm'
mp3lib/dct64_sse.c:59:13: error: 'asm' operand has impossible constraints
make: *** [mp3lib/dct64_sse.o] Error 1
```

Otherwise on my current 64bit 12.10 the how-to works but one would need to link at runtime...

You may just consider using the repo libx264-120 or possibly just build the git as shared to /usr/local (though that could conflict with FO's guide..

---

### Post by ron999 on 2012-08-05
> **mc4man said:**
> ... build the git as shared to /usr/local (though that could conflict with FO's guide..
Hi
That's what I did. Posts #2176-2183 here ---> [http://ubuntuforums.org/showthread.php?t=786095&highlight=ron999&page=218]("http://ubuntuforums.org/showthread.php?t=786095&highlight=ron999&page=218")

---

### Post by mc4man on 2012-08-05
> **ron999 said:**
> Hi
That's what I did. Posts #2176-2183 here ---> [http://ubuntuforums.org/showthread.php?t=786095&highlight=ron999&page=218]("http://ubuntuforums.org/showthread.php?t=786095&highlight=ron999&page=218")
shows you how good my memory is...
In any event for a Wiki method the building of a shared libx264 to somewhere not in default path may not be suitable as mplayer/mencoder would need to be linked to libx264.so at runtime which is easy thru an alias for cli but would be likely a bit more involved for an app that called the mencoder binary directly. (binary redirect ..
 (though maybe Andrew has a good one there...

---

### Post by mc4man on 2012-08-05
So here the best 'solution' for a mplayer/mencoder build would be to statically link.

*removed* - static linking for gcc > 4,4 fixed in mplayer - 
> r35060 | cehoyos | 2012-08-06 11:39:04 -0400 (Mon, 06 Aug 2012) | 1 line

Second try to fix auto-detection of static libraries.


Side note - as to actual value you can enable opus thru ffmpeg, 12.04 doesn't have the opus libs, 12.10 does
Selected audio codec: [fflibopus] afm: ffmpeg (FFmpeg libopus)

---

### Post by ron999 on 2012-08-09
> **mc4man said:**
> ... you can enable opus thru ffmpeg, 12.04 doesn't have the opus libs, 12.10 does...
Hi mc4man

I compiled opus. :P
(And libogg and opus-tools)
(See attachment)
So opusdec and opusenc and opusinfo are OK.
And FFmpeg compiles with "--enable-libopus".
Also mPlayer ./config found libopus automatically.
> "Checking for libopus decoding support ... yes"

mPlayer ./config found x264 because I compiled it "shared" and removed libx264-dev.
It did not find vpx, so maybe I will compile it "shared" too next time.
Though I don't think that I'll ever need to use vpx with MEncoder.

Perhaps your MEncoder compile suggestions will be added to the mPlayer wiki sometime.
(But there isn't much interest in MEncoder these days).

> @ubuntu:~$ mplayer
MPlayer SVN-r35066-4.5.2 (C) 2000-2012 MPlayer Team 

> Enabled... 
Codecs: libschroedinger libdirac x264 xvid libdv libopencore_amrwb libopencore_amrnb ffmpeg(internal) qtx real xanim win32 libopus faad2 faac libdca libmpeg2(internal) liba52 mpg123 mp3lib(internal) libtheora libgsm speex tremor(internal) twolame libmad liblzo gif OpenJPEG 

Disabled...
Codecs: libvpx crystalhd musepack toolame

---

### Post by ads52 on 2012-08-10
Some details on this web page for compiling libopus that might be useful for the wiki page:

[http://andrews-corner.org/mplayer.html#libopus](http://andrews-corner.org/mplayer.html#libopus)

and another sample file. It will be interesting to see how opus fares, libvpx had a similar fanfare...

---

### Post by ads52 on 2012-08-11
I have synced the Ubuntu Wiki with [the web guide]("http://www.andrews-corner.org/mplayer.html") so quite a few changes now. Important one is that I have added in MEncoder and courtesy of Carl Eugen Hoyos static linking of x264 now works well enough and as per the web guide a truly* local* installation will not interfere with the system x264. I removed directions to compile live555 as the repository version works well enough. Plus added in libopus as mentioned above.

Since it is a wiki I hope that any mistakes I have made will be corrected by others in this thread :).

---

### Post by ads52 on 2012-08-12
I have again synced the wiki page with [the website guide]("http://www.andrews-corner.org/mplayer.html") and added in a section describing how to compile and package MPlayer2. Works well enough on my system. I suspect the next move would be to add in a few libav and MPlayer compile options, the build system is *very* different from stock standard MPlayer...

---

### Post by andrew.46 on 2012-12-08
Updated for Quantal Quetzal.

---

### Post by ron999 on 2012-12-14
Hi
**SMPlayer > Help > About SMPlayer **

Shows:-
**Using MPlayer SVN r35679**

This information is contained in file $HOME/.config/smplayer/smplayer.ini
It says "mplayer_detected_version=35679".

When we update MPlayer, can you suggest a suitable command that can be included so that it updates the "mplayer_detected_version" information too?

---

### Post by andrew.46 on 2012-12-15
Oddly enough the versions seem to match on my system despite regular updates to MPlayer itself. Not sure what to suggest there.... Please feel free to update / change the wiki page as you please, my involvement there will be minimal. The wiki still appears a wasteland after T&T...

---

### Post by ron999 on 2012-12-18
> **andrew.46 said:**
> ... Not sure what to suggest there...
I found help here --->[http://ubuntuforums.org/showthread.php?t=2095757](http://ubuntuforums.org/showthread.php?t=2095757)


```
sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/mplayer_build" \
   --pkgname mplayer --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
   --pkgversion "2:1.0~svn$(LC_ALL=C svn info 2> /dev/null | \
     grep Revision | cut -d' ' -f2)" --provides "mplayer,mencoder" && \
[COLOR="Red"]sed -i "/mplayer_detected_version/ s/=.*$/=$(LC_ALL=C svn info 2> /dev/null | \
     grep Revision | cut -d' ' -f2)/" ~/.config/smplayer/smplayer.ini && \
[/COLOR]make distclean && sudo ldconfig
```

---

### Post by andrew.46 on 2012-12-18
Mind you this might lead to a confusing error message if SMPlayer is *not* already installed...Perhaps consider placing the text as a sidenote or an extra step, out of the actual MPlayer packaging section?

---

### Post by ron999 on 2012-12-18
> **andrew.46 said:**
> Perhaps consider placing the text as a sidenote or an extra step, out of the actual MPlayer packaging section?
Yes,
It would be better to have a 'stand-alone' command to use at any time without reference to SVN.

When I figure out how to isolate version from:- 

@ubuntu:~$ mplayer -h | grep -i "MPlayer SVN-r"
MPlayer SVN-r35695-4.5.2 (C) 2000-2012 MPlayer Team

---

### Post by andrew.46 on 2012-12-18
> **ron999 said:**
> When I figure out how to isolate version from:- 

```
@ubuntu:~$ mplayer -h | grep -i "MPlayer SVN-r"
MPlayer SVN-r35695-4.5.2 (C) 2000-2012 MPlayer Team
```


This is not particularly elegant but should work until the revision numbers reach 100000 :

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -h | grep ^MPlayer | cut -c14-18[/COLOR]**
35687

```

I have not really used the -c option before with cut but definitely a good thing to know...

---

### Post by ron999 on 2012-12-18
> **andrew.46 said:**
> ... should work until the revision numbers reach 100000 ...
That works OK.
But we've introduced something like a Y100K bug, lol. :P

I don't think it's necessary to add this feature to the wiki.

```
sed -i "/mplayer_detected_version/ s/=.*$/=$(mplayer -h | grep ^MPlayer | cut -c14-18)/" ~/.config/smplayer/smplayer.ini
```

---

### Post by qyot27 on 2012-12-25
As a heads up, there is now another fork worth checking out: [mpv](https://github.com/mpv-player/mpv)

I've moved over to using it as my main mplayer variant on both Ubuntu and Windows (because you can actually compile it under MinGW-w64 without applying patches* and whatall, although it does require building the dependencies first).  I also use it as my transcoding solution on OS X, although I don't use OS X nearly as often as the other two.

*slightly untrue, because there is all of **one** necessary patch to apply: to Fribidi2.  But aside from that, there's no patching required.  libbluray and twolame also need some minor patching to build with MinGW or link statically, but unlike Fribidi, those components are completely optional (Fribidi is only optional if you don't want support for subtitles).

Of interest is that:
MPlayer2's vo-lavc (aka encoding) branch is no longer developed (hasn't been since around July or August), because development on that moved to mpv (and is not a separate branch; it's also enabled by default).  This means that a stock build of mpv does both decoding and encoding to any format supported by the libavcodec that was linked against it.

At least on my older graphics card, I seem to be getting better performance with mpv - much less tearing on Ubuntu with -vo xv, anyway (although the age of my computer means I can't really play video on Ubuntu; -vo direct3d under Windows just runs circles around it).  Under Windows, it doesn't have the weird issues dealing with exotic pulldown schemes or playing 29.97fps progressive in MPEG-2 the way MPlayer2 sometimes would have.  This might be partially due to the age of the MPlayer2 build I was comparing it to, though.

Support for FFmpeg's extended y4m format that allows higher bit depths (and even in non-y4m cases: though x264 can't encode 12-bit or 14-bit H.264 files yet, mpv can play such streams back if you actually use *FFmpeg*).

mpv's stated purpose also seems to be to reduce the amount of complexity/cruft in MPlayer/MPlayer2, so some stuff has gotten trimmed out (the win32 binary codec loader is gone, for instance).




I do have my own branch on Github that integrates two changes to mpv itself: one makes it generate a sequential revision number to display in the console readout, the other is a discrete AvxSynth demuxer that was originally posted for MPlayer2 to 0x09's AvxSynth 'osx' branch (since libavformat's AviSynth demuxer doesn't work on Linux and the rewrite posted to ffmpeg-devel that would enable using AvxSynth to do it hasn't gotten all the kinks hammered out of it yet*, a discrete demuxer is really the only solution as of right now).  I haven't done a HEAD catchup for a while though, I'm waiting on one of the alternative branches on the main repo to get merged first.

*read: the most recent version of it causes segfaults whenever you try to load a script.  Also, due to the move to planar audio decoding going on in libavcodec, FFMS2 can't handle audio aside from PCM at the moment (although you could build it against a pre-November 26th FFmpeg so you can decode AAC, MP3, and AC3 at least).  Not that that has anything to do with how well the demuxer works, though - just something to be aware of if you want to try to test it.

---

### Post by ron999 on 2012-12-26
> **qyot27 said:**
> As a heads up, there is now another fork worth checking out: [mpv](https://github.com/mpv-player/mpv)
Hi
I'm very satisfied with MPlayer, but I've compiled mpv and it's working reasonably well from command line.

I use MPlayer with SMPlayer GUI so I tried to set up mpv to use UMPlayer GUI.

But it doesn't work. :cry:

Seems that the fancy command UMPlayer uses has MPlayer option(s) that are unknown to mpv.
In the preferences section of UMPlayer it allows to add extra options to the command.
But I don't know how to edit the command to remove the offending option(s).
Maybe it's hard-wired into the program.

Any idea how to do this?


```
18:40:02:913] Core::startMplayer: command: '/usr/local/bin/mpv -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo x11, -ao alsa, -zoom -nokeepaspect -nodr -double -input nodefault-bindings:conf=/dev/null -stop-xscreensaver -wid 54527660 -monitorpixelaspect 1 -noass -subfont-autoscale 3 -subfont-text-scale 2.5 -subcp UTF-8 -subpos 100 -volume 38 -nocache -osdlevel 0 -vf-add screenshot -noslices -channels 2 -af scaletempo -softvol -softvol-max 110 /home/ron/Desktop/foo.wav '
[18:40:02:919] Playlist::setModified: 0
[18:40:02:919] Playlist::addFiles
[18:40:02:923] Playlist::addItem: '/home/ron/Desktop/foo.wav'
[18:40:02:924] Playlist::updateView
[18:40:02:924] Playlist::updateView: name: 'foo.wav'
[18:40:02:927] Playlist::addFiles: latest_dir: '/home/ron/Desktop'
[18:40:03:249] MplayerProcess::parseLine: 'Terminal type `unknown' is not defined.'
[18:40:03:263] MplayerProcess::parseLine: 'Unknown option on the command line: noquiet'
[18:40:03:263] MplayerProcess::parseLine: 'Exiting... (Fatal error)'
[18:40:03:264] MyProcess::procFinished
[18:40:03:264] MyProcess::procFinished: Bytes available: 0
[18:40:03:264] MplayerProcess::processFinished: exitCode: 1, status: 0
[18:40:03:265] MplayerLayer::playingStopped
[18:40:03:268] Core::processFinished
[18:40:03:268] Core::processFinished: we_are_restarting: 0
[18:40:03:268] Core::processFinished: play has finished!
[18:40:03:268] Core::processFinished: exit_code: 1
[18:40:03:268] BaseGui::showExitCodeFromMplayer: 1
[18:40:10:585] BaseGui::showLog
```

---

### Post by qyot27 on 2012-12-26
> **ron999 said:**
> Hi
I'm very satisfied with MPlayer, but I've compiled mpv and it's working reasonably well from command line.

I use MPlayer with SMPlayer GUI so I tried to set up mpv to use UMPlayer GUI.

But it doesn't work. :cry:

Seems that the fancy command UMPlayer uses has MPlayer option(s) that are unknown to mpv.
In the preferences section of UMPlayer it allows to add extra options to the command.
But I don't know how to edit the command to remove the offending option(s).
Maybe it's hard-wired into the program.

Any idea how to do this?
It does seem to be hard-coded in.  If you run a grep on the UMPlayer source code, the options that that code block shows that it was trying to use are located in umplayer/trunk/src/core.cpp.  They're defined like this: ```
proc->addArgument("-msglevel");
```
but otherwise look to not be wrapped in more complex code.  It might be possible to just replace the options that can be replaced with their mpv equivalents, and comment out the ones that can't.  Then you'd have to compile UMPlayer again (I've never tried building any of the GUIs for mplayer, so I don't know what's involved there).

Of course, that sort of change will make UMPlayer incompatible with MPlayer/MPlayer2.  To make it compatible with all three, the mpv options would have to be defined separately and ifdeffed to code that detects the GUI is using mpv instead of one of the other two.

---

### Post by ron999 on 2012-12-26
> **qyot27 said:**
> It does seem to be hard-coded in...
Thanks qyot27
That may be the way to do it.
But I'm not a pathfinder.;)

I will sit tight for now.
Somebody will come up with a GUI solution when mpv is further developed.

---

### Post by andrew.46 on 2012-12-27
> **ron999 said:**
> 
But I'm not a pathfinder.;)

You underestimate yourself....

---

