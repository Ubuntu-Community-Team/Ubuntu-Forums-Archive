---
title: "Imagination, a simple and lightweight DVD slideshow"
date: 2009-01-22
forum: Ubuntu Dev Link Forum
---

### Post by colossus73 on 2009-01-22
Hi,

I've developed a simple and lightweight interface in GTK+2 to produce DVD slideshow from a set of pictures: Imagination. The code for the transition between the images uses cairo and it's developed a plugins loadable with GModule. The current code is available only with SVN and no encoding yet is developed, just the transition effects. I would like to receive any patch/feedback/help for improving it and developing new eye candy plugins; they are found in the directory transitions.

The code can be fetched with:

$ svn co [http://imagination.svn.sourceforge.net/svnroot/imagination](http://imagination.svn.sourceforge.net/svnroot/imagination)

I need an original and fresh logo for Imagination. If you aren't a developer but can help for creating a new logo I will appreciate your help. Also there is no website yet for Imagination. Any contribution too is appreciated. The web site should be simple but impressive.

Thanks,

---

### Post by colossus73 on 2009-02-26
> **colossus73 said:**
> Hi,
The code can be fetched with:
$ svn co [http://imagination.svn.sourceforge.net/svnroot/imagination](http://imagination.svn.sourceforge.net/svnroot/imagination)


Ok, today I released the first release of Imagination. You can download it from here:

[http://sourceforge.net/project/showfiles.php?group_id=244319](http://sourceforge.net/project/showfiles.php?group_id=244319)

[IMG]http://imagination.sourceforge.net/screenshots/circular_blind_from_center.png[/IMG]

---

### Post by castrojo on 2009-02-26
This looks great, I've always wanted one of these, I'll try it later this afternoon!

---

### Post by colossus73 on 2009-02-27
> **whiprush said:**
> This looks great, I've always wanted one of these, I'll try it later this afternoon!

Me too I've always wanted one of these. There is a huge lack of user-friendly apps like this on Linux and for this reason I coded Imagination.

---

### Post by rockin_goliath on 2009-02-27
Can I add music to the slide show? Can I export it as a simple movie file, like Theora?

---

### Post by colossus73 on 2009-03-02
> **rockin_goliath said:**
> Can I add music to the slide show? Can I export it as a simple movie file, like Theora?

They are all planned for next release; ffmpeg can export to Theora if it's compiled with such support. Stay tuned! Counsel/feedback are appreciated.

Bye,

---

### Post by ace214 on 2009-03-06
Looking good. Will look forward to you adding Ken Burns and such.

The one time I needed to make a DVD slideshow I had used [slcreator]("http://slcreator.sourceforge.net/") but it's very outdated.

---

### Post by colossus73 on 2009-03-07
> **ace214 said:**
> Looking good. Will look forward to you adding Ken Burns and such.


Sound will be added in the next release for sure since we're working on it. I'm in doubt for Ken Burns but in the third Imagination release they will be. In the mean time in the development version we added new transitions respect to the 1.0 one and also Ogg (Theora/Vorbis) slideshow export.

Bye,

---

### Post by theDaveTheRave on 2009-03-25
This is just what I've been looking for.

One reallys good addition would be to be able to include "short" video also. then you will have a brilliant peice of kit.

I will try it out in the next few months (hopefully you will have added sound  also by then) when I put together my next set of "baby" photo's.

I haven't looked at your sourceforge page, but do plan (or allready have) a windows version? then I will be able to share the same stuff with my wife. 

My colleagues at work create films from timelapse photography stuff, I guess you can change the "speed" between frames?

I must tag this page and try it out really soon.

David

---

### Post by colossus73 on 2009-03-25
> **theDaveTheRave said:**
> This is just what I've been looking for.
One reallys good addition would be to be able to include "short" video also. then you will have a brilliant peice of kit.


I have no idea how to do this, as far as I know switching to GSstreamer in a future release this is possible.

> 
I haven't looked at your sourceforge page, but do plan (or allready have) a windows version? then I will be able to share the same stuff with my wife. 


No, it's not planned at the moment, but it's very easy to compile a binary for windows, just adapting the Makefile.

> 
My colleagues at work create films from timelapse photography stuff, I guess you can change the "speed" between frames?


If you mean the transition speed yes it's. Also you can decide how long a slide should stay before the next effect.

Thanks for using Imagination,

---

### Post by theDaveTheRave on 2009-03-27
I've not been back to the office yet,

but changing the slide transistion speed, and time a slide stays on screen sound exactly like what my colleagues need.

I'm going to test and report back (hopefully I'll even be able to post a few resulting "films").

It's good to hear about the "windows compatiblity", I'm not much good with c programming but I'll have a look as and when I get the chance (in between all the other DBase and scripting I am doing for my research!).

David

---

### Post by Derol on 2009-04-30
package for 9.04 i386 :)


[http://www.easy-share.com/1904875497/imagination_1.0-1_i386.deb](http://www.easy-share.com/1904875497/imagination_1.0-1_i386.deb)

---

### Post by hernando on 2009-05-11
Sweet app!!!

@colossus73

I'm a video editor who really likes GNU/Linux and is nice have a simple app like this one to do quick slideshows.

Definitely a simple way to apply the ken burns effect to the slides will be a grate addition to the program.

Thank you for your effort in the development and please keep on going.

Congratulations.
Hernando Ramos.

---

### Post by colossus73 on 2009-06-24
> **rockin_goliath said:**
> Can I add music to the slide show? Can I export it as a simple movie file, like Theora?

Now, with the release 1.5 you can do both! Please try it and spread the word, thanks!

[IMG]http://imagination.sourceforge.net/images/imagination_perspective.png[/IMG]

---

### Post by mlkovacs on 2009-06-25
Here is Imagination 1.5 compiled and packaged with checkinstall for Jaunty 9.04:

[http://www.mediafire.com/?m4q3znyzgz9]("http://www.mediafire.com/?m4q3znyzgz9")

---

### Post by colossus73 on 2009-06-26
> **mlkovacs said:**
> Here is Imagination 1.5 compiled and packaged with checkinstall for Jaunty 9.04:

[http://www.mediafire.com/?m4q3znyzgz9]("http://www.mediafire.com/?m4q3znyzgz9")

Thank you.

---

### Post by colossus73 on 2009-09-27
Imagination 2.0 released with more audio management. The audio files are now concatenated, trimmed at video length and a fade-out of 5 seconds is applied to the end. Enjoy it and please report bugs and feature request at sf.net.

Thank you
colossus73

---

### Post by linuxmart on 2009-10-02
I am trying to install this in Ubuntu 9.04, but when running ```
./configure
```

I get this:
```
checking for PACKAGE... yes
checking for SOX... configure: error: Package requirements (sox >= 14.2.0) were not met:

No package 'sox' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables SOX_CFLAGS
and SOX_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I have SOX installed in synaptic, but still get the same results. How can I fix this?
Is there a deb package for Imagination 2.0 stable?

Thanks.

---

### Post by colossus73 on 2009-10-02
> **linuxmart said:**
> 
I have SOX installed in synaptic, but still get the same results. How can I fix this?
Is there a deb package for Imagination 2.0 stable?
Thanks.

You have to install the development files of libsox:

libsox-dev 14.2.0-1 Development files for the SoX library

Regarding the package I think packagers should do it soon.

Bye,

---

### Post by Specks on 2009-10-07
I just downloaded the source for 2.0 and I'm trying to compile it but I'm running into an error on configure. I'm using 9.10 beta.

```

checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.14.0 gthread-2.0) were not met:

No package 'gtk+-2.0' found
No package 'gthread-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I see /usr/lib/gthread-2.0.so.0 and /usr/lib/gtk-2.0/ which I'm pretty sure is the standard location, so I'm not sure what to do to fix the error.

---

### Post by colossus73 on 2009-10-08
> **Specks said:**
> I just downloaded the source for 2.0 and I'm trying to compile it but I'm running into an error on configure. I'm using 9.10 beta.

```

checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.14.0 gthread-2.0) were not met:

No package 'gtk+-2.0' found
No package 'gthread-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I see /usr/lib/gthread-2.0.so.0 and /usr/lib/gtk-2.0/ which I'm pretty sure is the standard location, so I'm not sure what to do to fix the error.

Hi,

you have to install the development packages of gtk and also sox. They are not installed by default:

libgtk2.0-dev
libsox-dev

Bye
colossus73

---

### Post by Specks on 2009-10-08
> **colossus73 said:**
> Hi,

you have to install the development packages of gtk and also sox. They are not installed by default:

libgtk2.0-dev
libsox-dev

Bye
colossus73

Thanks so much. After installing those packages, configure finished successfully.

Ran into another problem though when compiling.

```
I/O error : Attempt to load network entity http://docbook.sourceforge.net/release/xsl/current/html/onechunk.xsl
warning: failed to load external entity "http://docbook.sourceforge.net/release/xsl/current/html/onechunk.xsl"
compilation error: file ./../imagination.xsl line 7 element import
xsl:import : unable to load http://docbook.sourceforge.net/release/xsl/current/html/onechunk.xsl
make[3]: *** [html-build.stamp] Error 5
make[3]: Leaving directory `/home/brian/src/imagination-2.0/doc/en'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/brian/src/imagination-2.0/doc/en'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/brian/src/imagination-2.0/doc'
make: *** [all-recursive] Error 1

```

I'm not sure what the problem is since I can bring up the xsl file on docbook.sourceforge.net in a browser. Pretty much got the same thing on make install. Since I think this is only dealing with the documentation, it doesn't effect the application. I am able to start the application, so it appears to be working.

---

### Post by colossus73 on 2009-10-09
> **Specks said:**
> Thanks so much. After installing those packages, configure finished successfully.

I'm not sure what the problem is since I can bring up the xsl file on docbook.sourceforge.net in a browser. Pretty much got the same thing on make install. Since I think this is only dealing with the documentation, it doesn't effect the application. I am able to start the application, so it appears to be working.

You have to install docbook-xsl

Bye,

---

### Post by colossus73 on 2009-10-14
Imagination 2.1 released, it follows the changelog:

Added a new transition family named Rochade.
Added 3GP export for mobile phones.
Fixed seg-fault when using Imagination with GTK 2.18
Fixed crash when playing with Ken Burns and slide text after closing the project.
Added a Slides Transitions Report Dialog. Please give feedback on this.
Added Japanese translation.
Fixed display of music duration after loading the slideshow.
Fixed seg-fault when exporting with more audio files.
Image rotation is now stored inside project file.

[https://sourceforge.net/projects/imagination/files/imagination/2.1/imagination-2.1.tar.gz/download](https://sourceforge.net/projects/imagination/files/imagination/2.1/imagination-2.1.tar.gz/download)

Have fun with Imagination,

---

### Post by cbnation on 2009-10-15
With the help of this thread, I could install Imagination. So thanks for that.

Now if I use the program, the dropdown to choose a transition is empty. The only entry is "none". Is there some extra step needed?

---

### Post by Specks on 2009-10-15
Same thing happened to me when I compiled and installed 2.1. I went back to 2.0 and the transition drop down was repopulated. Not sure why they were missing in 2.1.

---

### Post by colossus73 on 2009-10-16
> **cbnation said:**
> With the help of this thread, I could install Imagination. So thanks for that.

Now if I use the program, the dropdown to choose a transition is empty. The only entry is "none". Is there some extra step needed?

Sorry my mistake. I forgot to change line 23 in src/support.c from this:

#define PLUGINS_INSTALLED 0

to this:

#define PLUGINS_INSTALLED 1

Please do it and recompile; you will see the transitions.

Bye,

---

### Post by Ruhani04 on 2009-10-19
Thx sooo much. Besides some minor install problems which were addressed in the previous posts it works wonderfully.
Highly recommended for everyone who likes software that works "out of the box."
=D>

---

### Post by celem on 2009-10-27
I have tried everything else with mixed results. Imagination is perfect - just what I have been looking for. Now - to get it included into Ubuntu!

---

### Post by wich on 2009-10-29
thanks for this information. i like this posting very much. thanks for this.

---

### Post by 831photo on 2009-11-23
Maybe I'm missing something, but it seems like when you zoom, it always has to "hold" at the stop points.

Is there a way to have a zoom/pan that can be continuous, then transition to the next slide? (have a zero hold time, for example)

Also, you have random transitions, I think it would be a good idea to have random zoom points. It would give a quick and easy starting point to creating a dynamic slide show. Of course, we could manually edit the points, but by having a random "zoom-in/zoom-out/pan" we'd just be tweaking, rather than creating everything from scratch.

Also, using a music and motion "template" would be really cool. Have a preset timing and motion xml file that goes with the music, then we could use any images. It's extremely useful for professional photographers, and makes for really, really fast slideshow creations. You could even create your own and share templates.

Check out [www.showitfast.com](www.showitfast.com) for an example. We use this on windows, but still haven't found anything as quick for linux.

This is a great start, nice clean interface! Thanks so much!

Shan

---

### Post by silvertuna on 2009-12-06
When i export to vob, it exports only the 3 min 31 seconds of slides that coincide with the first music track.  The rest of the show does not export.  So i tried combining the 5 music tracks into one using the cat command and import one piece of music that covered the whole length of the slide show.  It still only exported the 3 min 31 seconds.  What am i missing?  My version is 1.5 from the Ubuntu Karmic repository.

---

### Post by silvertuna on 2009-12-06
Work around - converted my ogg's to mp3's, cat the mp3's, import to Imagination and then the export worked fine. Hat-tip - 
[http://sourceforge.net/tracker/?func=detail&aid=2853360&group_id=244319&atid=1125540](http://sourceforge.net/tracker/?func=detail&aid=2853360&group_id=244319&atid=1125540)

---

### Post by ainsaur on 2009-12-07
Hi,

I've been reading this thread and would like to try out Imagination.  The problem that I've found is that I just purchased a new computer (now using 64 bit Ubuntu) and there is no record of "Imagination" in the Add/Remove Software application.  It DOES show up in the software center (using my old computer, which is running 32 bit Ubuntu).  Any suggestions (or explanation for why this is happening)?

Thanks

---

### Post by Ruhani04 on 2009-12-12
Just start reading the thread from beginning or go to page 3 for version 2.1 and it should answer your question. The repos only show version 1.5 using Synaptic. For 2.1 you need to do a manual install. 

Good luck !  ;)

---

### Post by coyotepod on 2009-12-24
i dont compile programs often and usually look in repos and for debs :-/ so the other posts about the specific dependencies where very helpful thus far. i really want this to work as I haven't found a slide show programs i really like yet in Ubuntu.

this is part of output when doing  make check not sure how essential the missing "po" is.


----

make[1]: Leaving directory `/home/tux2/Public/imagination-2.1/transitions'
Making check in po
make[1]: Entering directory `/home/tux2/Public/imagination-2.1/po'
rm -f missing notexist
srcdir=. /usr/bin/intltool-update -m
The following files contain translations and are currently not in use. Please
consider adding these to the POTFILES.in file, located in the po/ directory.

imagination.desktop.in
src/subtitles.c

If some of these files are left out on purpose then please add them to
POTFILES.skip instead of POTFILES.in. A file 'missing' containing this list
of left out files has been written in the current directory.
Please report to [http://sourceforge.net/tracker/?group_id=244319&atid=1125540](http://sourceforge.net/tracker/?group_id=244319&atid=1125540)
if [ -r missing -o -r notexist ]; then \
	  exit 1; \
	fi
make[1]: *** [check] Error 1
make[1]: Leaving directory `/home/tux2/Public/imagination-2.1/po'
make: *** [check-recursive] Error 1
tux2@tux2-desktop:~/Public/imagination-2.1$

---

### Post by JackD on 2010-01-01
Almost have Imagination working. So close. I've installed from the 2.1x source code (making the changes for the transitions list) and everything works well, except one thing. Export fails. VOB, FLV both create a null file.

So, then I uninstalled the 2.1x release, and tried the 1.5 (GetDeb has a package) release, calling it from the command prompt. When it comes time to export, here's what happens:

> ffmpeg -f image2pipe -vcodec ppm -i pipe: -r 30.00 -aspect 4:3 -s 720x480 -an -y -bf 2 -target ntsc-dvd "/home/jack/Desktop/8th.vob"
FFmpeg version git-91be88c, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-nonfree --enable-shared --enable-pthreads --enable-libx264 --enable-libfaac --enable-libtheora
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.32. 0 / 52.20. 0
  libavformat   52.36. 0 / 52.31. 0
  libavdevice   52. 2. 0 / 52. 1. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on Jul 24 2009 21:22:03, gcc: 4.3.3
Input #0, image2pipe, from 'pipe:':
  Duration: N/A, bitrate: N/A
    Stream #0.0, 1/25: Video: ppm, rgb24, 720x480, 1/25, 25 tbr, 25 tbn, 25 tbc
Output #0, dvd, to '/home/jack/Desktop/8th.vob':
    Stream #0.0, 1/90000: Video: mpeg2video, yuv420p, 720x480 [PAR 8:9 DAR 4:3], 1001/30000, q=2-31, 6000 kb/s, 90k tbn, 29.97 tbc
Stream mapping:
  Stream #0.0 -> #0.0
ffmpeg: symbol lookup error: ffmpeg: undefined symbol: avcodec_decode_video2

(imagination:8926): Gtk-CRITICAL **: gtk_list_store_iter_next: assertion `GTK_LIST_STORE (tree_model)->stamp == iter->stamp' failed

My initial impressions with Imagination is that it is an extraordinarily powerful tool. The combination of text, "Ken Burns" transitions, and sound is very impressive. 

I'm hoping that the export function can be remedied. Obviously, not everyone has this problem, some do, but not everyone. So, there is a configuration or missing library to be addressed, as my best guess. 

Fingers crossed.

---

### Post by colossus73 on 2010-01-02
> **JackD said:**
> I'm hoping that the export function can be remedied. Obviously, not everyone has this problem, some do, but not everyone. So, there is a configuration or missing library to be addressed, as my best guess.Fingers crossed.

JackD,

your ffmpeg installation is broken. Please reinstall it with libavcodec and see it will work. The export function works. Also about audio problems they have been corrected with 2.1.

---

### Post by colossus73 on 2010-01-02
> **silvertuna said:**
> When i export to vob, it exports only the 3 min 31 seconds of slides that coincide with the first music track.  The rest of the show does not export.  So i tried combining the 5 music tracks into one using the cat command and import one piece of music that covered the whole length of the slide show.  It still only exported the 3 min 31 seconds.  What am i missing?  My version is 1.5 from the Ubuntu Karmic repository.

Please update to 2.1 thank you.

---

### Post by JackD on 2010-01-02
> **colossus73 said:**
> JackD,

your ffmpeg installation is broken. Please reinstall it with libavcodec and see it will work. The export function works. Also about audio problems they have been corrected with 2.1.

Interesting ! And weird.

When I checked the library dependencies for ffmpeg, I see some avcodec ambiguities. 

Looking further, I see that I have TWO different libavcodec.so.52 installed, each in a different directory:

1. /usr/lib/
2. /usr/local/lib/

> jack@jack-laptop:~$ which ffmpeg
/usr/local/bin/ffmpeg
jack@jack-laptop:~$ ldd -r /usr/local/bin/ffmpeg
	linux-gate.so.1 =>  (0xb7811000)
	libavdevice.so.52 => /usr/lib/i686/cmov/libavdevice.so.52 (0xb77e9000)
	libavformat.so.52 => /usr/lib/i686/cmov/libavformat.so.52 (0xb76ee000)
	libavcodec.so.52 => /usr/lib/i686/cmov/libavcodec.so.52 (0xb6eaa000)
	libavutil.so.50 => /usr/local/lib/libavutil.so.50 (0xb6e97000)
	libswscale.so.0 => /usr/lib/i686/cmov/libswscale.so.0 (0xb6e6a000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb6e44000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb6e2b000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb6ce6000)
	libavutil.so.49 => /usr/lib/i686/cmov/libavutil.so.49 (0xb6cd5000)
	libdc1394.so.22 => /usr/lib/libdc1394.so.22 (0xb6c62000)
	libasound.so.2 => /usr/lib/libasound.so.2 (0xb6b9b000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0xb6a6c000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0xb6a5c000)
	libz.so.1 => /lib/libz.so.1 (0xb6a45000)
	libbz2.so.1.0 => /lib/libbz2.so.1.0 (0xb6a33000)
	libamrnb.so.3 => /usr/lib/libamrnb.so.3 (0xb69f5000)
	libamrwb.so.3 => /usr/lib/libamrwb.so.3 (0xb69c8000)
	libdirac_encoder.so.0 => /usr/lib/libdirac_encoder.so.0 (0xb6934000)
	libfaac.so.0 => /usr/local/lib/libfaac.so.0 (0xb6921000)
	libfaad.so.0 => /usr/lib/libfaad.so.0 (0xb68e1000)
	libgsm.so.1 => /usr/lib/libgsm.so.1 (0xb68d3000)
	libmp3lame.so.0 => /usr/lib/libmp3lame.so.0 (0xb6860000)
	libopenjpeg.so.2 => /usr/lib/libopenjpeg.so.2 (0xb6841000)
	libschroedinger-1.0.so.0 => /usr/lib/libschroedinger-1.0.so.0 (0xb67bf000)
	libspeex.so.1 => /usr/lib/sse2/libspeex.so.1 (0xb67a2000)
	libtheora.so.0 => /usr/lib/libtheora.so.0 (0xb674c000)
	libvorbisenc.so.2 => /usr/lib/libvorbisenc.so.2 (0xb6650000)
	libvorbis.so.0 => /usr/lib/libvorbis.so.0 (0xb6627000)
	libx264.so.67 => /usr/lib/libx264.so.67 (0xb6585000)
	libxvidcore.so.4 => /usr/lib/libxvidcore.so.4 (0xb6471000)
	/lib/ld-linux.so.2 (0xb7812000)
	libraw1394.so.11 => /usr/lib/libraw1394.so.11 (0xb6461000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb645d000)
	librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0xb6454000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0xb6436000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0xb6431000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb633f000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb6321000)
	liboil-0.3.so.0 => /usr/lib/liboil-0.3.so.0 (0xb62a6000)
	libogg.so.0 => /usr/lib/libogg.so.0 (0xb629f000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb6299000)
undefined symbol: avcodec_channel_layout_num_channels	(/usr/local/bin/ffmpeg)
undefined symbol: avcodec_decode_audio3	(/usr/local/bin/ffmpeg)
undefined symbol: avcodec_decode_subtitle2	(/usr/local/bin/ffmpeg)
undefined symbol: avcodec_decode_video2	(/usr/local/bin/ffmpeg)
undefined symbol: av_free_packet	(/usr/local/bin/ffmpeg)
jack@jack-laptop:~$ ls -al /usr/lib/libavco*
lrwxrwxrwx 1 root root      21 2010-01-02 09:56 /usr/lib/libavcodec.so.52 -> libavcodec.so.52.20.0
-rw-r--r-- 1 root root 5461104 2009-12-04 15:37 /usr/lib/libavcodec.so.52.20.0
jack@jack-laptop:~$ ls -al /usr/local/lib/libavc*
-rw-r--r-- 1 jack jack 25788058 2009-07-24 22:22 /usr/local/lib/libavcodec.a
lrwxrwxrwx 1 jack jack       21 2009-08-29 08:56 /usr/local/lib/libavcodec.so -> libavcodec.so.52.32.0
lrwxrwxrwx 1 jack jack       21 2009-08-29 08:56 /usr/local/lib/libavcodec.so.52 -> libavcodec.so.52.32.0
-rwxr-xr-x 1 jack jack  5157652 2009-07-24 22:22 /usr/local/lib/libavcodec.so.52.32.0

Synaptic only shows one installed library, in the /usr/lib directory, which is the older one. Unfortunately, I can't simply uninstall it, as many programs are dependent on it.

I'll open up another thread on how to address this problem, as I don't see this as specific to Imagination.

_______________________________________________________________

What a pain to get ffmpeg to work correctly. Not the fault of Giuseppe Torelli, Tadej Borov&#353;ak and their amazing team.

In the end, I added export LD_LIBRARY_PATH=/usr/local/lib to my .bashrc and call Imagination from a terminal.

I did check that /etc/ld.so.config.d and libc.conf includes the correct path. Running ldconfig didn't fix anything, which is why I gave up and did the export hack into .bashrc

However, I do have everything working !

---

### Post by redenex on 2010-04-04
> **Ruhani04 said:**
> Just start reading the thread from beginning or go to page 3 for version 2.1 and it should answer your question. The repos only show version 1.5 using Synaptic. For 2.1 you need to do a manual install. 

Good luck !  ;)

Can someone help me with the howto-manual install? Thank you.

---

### Post by redenex on 2010-04-05
:confused::mrgreen:

---

### Post by ridelnx on 2010-04-18
> **redenex said:**
> Can someone help me with the howto-manual install? Thank you.

If you can wait for 10.04, version 2.1 is available in the repos.

---

### Post by redenex on 2010-05-01
Yup, I got it! But still gives problem when I try to add mp3. I can add an audio file, but it is not playing! Wonders what am I doing wrong :)

---

### Post by colossus73 on 2010-05-02
> **redenex said:**
> Yup, I got it! But still gives problem when I try to add mp3. I can add an audio file, but it is not playing! Wonders what am I doing wrong :)

The audio in the preview is not availble. If you want to play your file switch to the "Audio" tab, select your mp3 file and click on the Play button.

---

### Post by maupec on 2010-06-06
I've installed Imagination 2.1 in Ubuntu 9.04, from .deb in the site, and all go right, except for exporting video: every codec result in a zero file lenght. I've tried the same installation on Ubuntu 10.04 and the export go well, producing files normally. How is it possible to fix the problem in 9.04?

Thank you!

mauro

---

### Post by colossus73 on 2010-06-06
> **maupec said:**
> I've installed Imagination 2.1 in Ubuntu 9.04, from .deb in the site, and all go right, except for exporting video: every codec result in a zero file lenght. I've tried the same installation on Ubuntu 10.04 and the export go well, producing files normally. How is it possible to fix the problem in 9.04?
mauro

Hi Mauro,

as I replied you via email you have to install all ffmpeg dependencies or ffmpeg itself.

Have a nice day,
Giuseppe

---

### Post by mcsenna on 2010-06-15
Hi, I have a quick question. I created a slideshow and the vob file and it all went well, problem arises when Igo to open the original file toedit it the progam closes down. Any ideas? By the way I found the program easy to use and exactly what I was looking for except for this weird problem.

---

### Post by colossus73 on 2010-06-15
> **mcsenna said:**
> Hi, I have a quick question. I created a slideshow and the vob file and it all went well, problem arises when Igo to open the original file toedit it the progam closes down. Any ideas? By the way I found the program easy to use and exactly what I was looking for except for this weird problem.

Hi,
it's a known bug but unfortunately it's hard to be discovered. Open your slideshow file (it's a text file) and be sure that the total number of the slides matches with the **last one at the end of the file**:

#Imagination 2.0 Slideshow Project - [http://imagination.sf.net](http://imagination.sf.net)

[slideshow settings]
video format=576
background color=0;0;0;
distort images=true
**number of slides=6**

[slide 1]
filename=/home/gt/Documents/Pictures/Landscapes/3d_landscape_6.jpg
angle=0
duration=3
transition_id=45
speed=4
no_points=0
anim id=0
anim duration=1
text pos=4
placing=0
font=Sans 12
font color=0;0;0;1;

[slide 2]
filename=/home/gt/Documents/Pictures/Landscapes/1107wallpaper-7_1280.jpg
angle=0
duration=3
transition_id=19
speed=4
no_points=0
anim id=0
anim duration=1
text pos=4
placing=0
font=Sans 12
font color=0;0;0;1;

[slide 3]
filename=/home/gt/Documents/Pictures/Landscapes/1107wallpaper-17_1280.jpg
angle=0
duration=3
transition_id=39
speed=4
no_points=0
anim id=0
anim duration=1
text pos=4
placing=0
font=Sans 12
font color=0;0;0;1;

[slide 4]
filename=/home/gt/Documents/Pictures/Landscapes/IMG_6637 sugar bowl cold snow clouds landscape.JPG
angle=0
duration=3
transition_id=49
speed=4
no_points=0
anim id=0
anim duration=1
text pos=4
placing=0
font=Sans 12
font color=0;0;0;1;

[slide 5]
filename=/home/gt/Documents/Pictures/Landscapes/living_landscape_screensaver_28769.jpeg
angle=0
duration=3
transition_id=14
speed=4
no_points=0
anim id=0
anim duration=1
text pos=4
placing=0
font=Sans 12
font color=0;0;0;1;

[slide 6]
filename=/home/gt/Documents/Pictures/Landscapes/waterfall_desktop_background-1600x1200.jpg
angle=0
duration=3
transition_id=39
speed=4
no_points=0
anim id=0
anim duration=1
text pos=4
placing=0
font=Sans 12
font color=0;0;0;1;

If it doesnt match adjust the number in the above bold words and reload it inside Imagination.

Please, try if you can reproduce the bug by starting a new slideshow file and writing down the steps you perform on it, maybe I can fix this @"£! bug!

Thank you,
Giuseppe

---

### Post by subaudible on 2010-06-21
Hi,

I've got Imagination 2.1 installed on Lucid and I can export to .VOB and .FLV, but when I try to export to .3gp, I get nothing, no errors, and no files created also... any ideas?

Thanks!
Moe

---

### Post by colossus73 on 2010-06-21
> **subaudible said:**
> Hi,

I've got Imagination 2.1 installed on Lucid and I can export to .VOB and .FLV, but when I try to export to .3gp, I get nothing, no errors, and no files created also... any ideas?

Thanks!
Moe

Most probably you are missing one of the (many) ffmpeg libraries. Sorry I can't tell the one right now.

Bye,

---

### Post by BriannNL on 2010-06-30
> **colossus73 said:**
> The audio in the preview is not availble. If you want to play your file switch to the "Audio" tab, select your mp3 file and click on the Play button.

Same problem over here. I can understand (though it would be very useful!) that the audio doesn't work in the preview. But I can't even get a MP3 file loaded. So I decided to convert it to an OGG file. That one actually loads, but it won't play as described.

Any ideas? I will try 2.0 in a few minutes, to see if it'll resolve my problem.

---

### Post by coyotepod on 2010-07-23
I had tried earlier versions and had some headaches. So far I am really liking Imagination ver 2.1!


In some instances when I export the video the transitions and image time adjust to the length of the music. In other exports, the slideshow timing is consistent and the music fades out (or drops out if the song is too short) -- this is the one that happens most often. I can trim long songs or add more songs manually when needed, but some times it would be nice to have pictures change according to the song length such as when only using 1 song for a show.

Is there a setting for total time = images time OR total time = audio time?



Thanks

---

### Post by coyotepod on 2010-07-23
I sort of found the answer to my total time mystery. When I export as OGV it uses the total time of the music, when I export as VOB the total time is determined by the image and transition time. I don't know if this is a feature or a bug, but I like having the options for setting total time :-)

---

### Post by iguest on 2010-10-25
BriannNL,

Problem with preview audio not playing...  I figured out that you need SOX installed.  Not just libsox-fmt-whatever, but SOX too.  It seems that SOX (The swiss army knife of sound processing) is not one of the dependencies that is required by the imagination 2.1 install, but it looks as though its absolutely necessary to use the audio preview play button. (on the audio tab)  In addition there are no error messages posted at the console when running the app from a terminal window.   For reference, I'm running Lucid (10.04) 64-bit.  What an excellent DVD slide-show app!!   

Kind regards,

- Iestyn Guest -

---

### Post by colossus73 on 2010-10-26
> **iguest said:**
> BriannNL,
What an excellent DVD slide-show app!!   


An execellent DVD slide-show app whose development is stopped. I'm looking for GTK/Cairo developers that could help me to give Imagination HD export.

Anyone interested or anyone who can spread the voice in the Ubuntu developers community please?

Thank you,

---

### Post by colossus73 on 2011-03-06
Hi guys,

please spread the word Imagination 3.0 with HD support is out thanks to Robert Cheramy. Download it:

[http://sourceforge.net/projects/imagination/files/imagination/3.0/imagination-3.0.tar.gz/download](http://sourceforge.net/projects/imagination/files/imagination/3.0/imagination-3.0.tar.gz/download)

Please test it intensively and give us suggestions on how to improve.

Bye,

---

### Post by stratojaune on 2011-06-17
Hi colossus73,

is it no more possible to export in flash with 3.0 ?

---

### Post by colossus73 on 2011-06-17
> **stratojaune said:**
> Hi colossus73,

is it no more possible to export in flash with 3.0 ?

As far as I know yes. Which problem do you face?

---

### Post by stratojaune on 2011-06-18
when choose "export" no choice except VOB, and 4/3 or 16/9 to clic

---

### Post by stratojaune on 2011-06-18
OUPS !!

it's ok I found the "project properties" in the main menu

sorry for the noise

---

### Post by stratojaune on 2011-06-18
hum, me again proscratinizing...

impossible to export in flash, have tried many settings and all the times it do "export" but the file is not create.

when export in vob, winFF can convert in flash, so it's ok for me, but you said that you like comments ?

debian squeeze run the machine, and except imagination 3.0-r1 almost everything comes from the stable repo (libmp3lame0 comes from the christian marillat repo)

---

### Post by stratojaune on 2011-06-18
ok,

when compile ffmpeg from svn, and recompile imagination against it, export to flash works if don't choose some video size (800*600 in properties and 640*360 in export popup for exemple gives nice image effects w/zoom is on the diapo, something like echo in the image, cool seeing but not wanted !)

here the output from the console :

FFmpeg version SVN-r26402, Copyright (c) 2000-2011 the FFmpeg developers
  built on Jun 18 2011 13:13:39 with gcc 4.4.5
  configuration: --enable-libmp3lame --enable-libtheora --enable-postproc --enable-libxvid --enable-pthreads --enable-libvorbis --enable-gpl --enable-x11grab --enable-nonfree
  libavutil     50.36. 0 / 50.36. 0
  libavcore      0.16. 1 /  0.16. 1
  libavcodec    52.108. 0 / 52.108. 0
  libavformat   52.93. 0 / 52.93. 0
  libavdevice   52. 2. 3 / 52. 2. 3
  libavfilter    1.74. 0 /  1.74. 0
  libswscale     0.12. 0 /  0.12. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[image2pipe @ 0x9dba4e0] Estimating duration from bitrate, this may be inaccurate
Input #0, image2pipe, from 'pipe:':
  Duration: N/A, bitrate: N/A
    Stream #0.0: Video: ppm, rgb24, 640x480, 30 fps, 30 tbr, 30 tbn, 30 tbc
[flac @ 0x9dc3ba0] max_analyze_duration reached
Input #1, flac, from '/tmp/img_audio_fifo':
  Duration: 00:04:43.42, bitrate: N/A
    Stream #1.0: Audio: flac, 44100 Hz, 2 channels, s16
[buffer @ 0x9dfa4c0] w:640 h:480 pixfmt:rgb24
[scale @ 0x9e0eb20] w:640 h:480 fmt:rgb24 -> w:320 h:240 fmt:yuv420p flags:0xa0000004
Output #0, flv, to '/media/store/lesZembiers.flv':
  Metadata:
    encoder         : Lavf52.93.0
    Stream #0.0: Video: flv, yuv420p, 320x240, q=2-31, 1536 kb/s, 1k tbn, 30 tbc
    Stream #0.1: Audio: libmp3lame, 22050 Hz, 1 channels, s16, 56 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #1.0 -> #0.1
[ppm @ 0x9dc5280] [IMGUTILS @ 0xbfe7f1f4] Picture size 6x0 is invalidits/s    
    Last message repeated 1 times  4981kB time=54.57 bitrate= 747.7kbits/s    
[ppm @ 0x9dc5280] [IMGUTILS @ 0xbfe7f1f4] Picture size 64x0 is invalid
    Last message repeated 1 times  7739kB time=63.63 bitrate= 996.3kbits/s    
[ppm @ 0x9dc5280] [IMGUTILS @ 0xbfe7f1f4] Picture size 640x0 is invalid
    Last message repeated 3 times 11703kB time=81.60 bitrate=1174.9kbits/s    
[ppm @ 0x9dc5280] Invalid maxval: 0
    Last message repeated 7 times 29949kB time=181.94 bitrate=1348.5kbits/s    
[ppm @ 0x9dc5280] [IMGUTILS @ 0xbfe7f1f4] Picture size 6x0 is invalid
    Last message repeated 1 times 30936kB time=191.10 bitrate=1326.2kbits/s    
[ppm @ 0x9dc5280] [IMGUTILS @ 0xbfe7f1f4] Picture size 64x0 is invalid
    Last message repeated 1 times 31743kB time=200.10 bitrate=1299.5kbits/s    
[ppm @ 0x9dc5280] [IMGUTILS @ 0xbfe7f1f4] Picture size 640x0 is invalid
    Last message repeated 3 times 34268kB time=218.18 bitrate=1286.7kbits/s    
[ppm @ 0x9dc5280] Invalid maxval: 0
    Last message repeated 7 times 45353kB time=281.81 bitrate=1318.4kbits/s    
frame= 8460 fps= 13 q=2.0 Lsize=   45376kB time=282.00 bitrate=1318.2kbits/s    
video:43146kB audio:1928kB global headers:0kB muxing overhead 0.668265%
Received signal 2: terminating.

---

### Post by colossus73 on 2011-06-19
> **stratojaune said:**
> ok,

when compile ffmpeg from svn, and recompile imagination against it, export to flash works if don't choose some video size (800*600 in properties and 640*360 in export popup for exemple gives nice image effects w/zoom is on the diapo, something like echo in the image, cool seeing but not wanted !)

Glad you solved the problem ,thank you for using Imagination.

---

### Post by stratojaune on 2011-06-20
Thanks for doing it !!

Cheers --fred

---

