---
title: "Howto: Build the development version of vlc under Ubuntu"
date: 2010-02-04
forum: Tutorials
---

### Post by andrew.46 on 2010-02-04
April 29, 2012.

Due to upcoming changes to this section of the Ubuntu Forums it is with great regret that I have moved this guide to my personal website where development will continue:

Howto: Build the development version of vlc under Ubuntu
[http://www.andrews-corner.org/vlc.html](http://www.andrews-corner.org/vlc.html)

In fact I have just completed an update for Precise Pangolin which I am keen for as many people as possible to test :).

If anybody is keen to use the current material (as of April 09,2012) for Ubuntu Wiki, blog, personal site etc I have attached the guide to this message as *vlc_git_guide.gz*. This contains the full Forums formatting so conversion to any other format should be easy enough...

Have Fun!!

Andrew

---

### Post by andrew.46 on 2010-02-06
I have added in a new dependency *libprojectm-dev* which builds support for libprojectM visualisation within vlc-git. A few details of this Google Summer of Code project here:

Visualisations in VLC
[http://ivoire.dinauz.org/blog/index.php?post/2010/02/01/Visualisations-in-VLC](http://ivoire.dinauz.org/blog/index.php?post/2010/02/01/Visualisations-in-VLC)

It was not hugely impressive on my system but early days yet + I am something of a goom fan still :).

Andrew

---

### Post by SuperSonic4 on 2010-02-06
How I remember this guide from the testing topic XD. May I suggest placing a link to the VLC plugins manager.

[VLC extensions]("http://jpeg.dinauz.org/VideoLAN/patches/extensions/share/lua/extensions/")

To try these extensions **right click** on the .lua file and select **save as** and save to the **Desktop**.

To activate the plugins copy them to **~/.local/share/vlc/lua/extensions/**

```
cd ~/Desktop
cp -v *.lua ~.local/share/vlc/lua/extensions/
```

This will copy the extensions to your VLC extensions folder

[IMG]http://img.photobucket.com/albums/v365/SuperSonic4/Screenshots/snapshot2A.png[/IMG]

^ VLC with the "Hello World" extension, imdb does work (see attached for larger image)

---

### Post by mc4man on 2010-02-06
Andrew - 
while I don't intend to keep or use a 64 bit install, it did bug me that some where building the 1.1 of of a shared ffmpeg install (sooner or later using new shared ffmeg libs will be an issue.

So managed to get vlc to build off of a static ffmpeg, though the means bears a little testing and or refinement.

To make sure ffmpeg itself is still good I built it as normal so I could run ffmpeg  - don't think that itself matters per se.

> doug@doug-laptop:~$ ffmpeg
FFmpeg version SVN-r21659, Copyright (c) 2000-2010 Fabrice Bellard, et al.
  built on Feb  6 2010 18:23:58 with gcc 4.4.1
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-pic
  libavutil     50. 8. 0 / 50. 8. 0
  libavcodec    52.52. 0 / 52.52. 0
  libavformat   52.50. 0 / 52.50. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0.10. 0 /  0.10. 0
  libpostproc   51. 2. 0 / 51. 2. 0

So far the vlc seems fine - ldd showing no libavcodec...

> doug@doug-laptop:~$ ldd /usr/local/lib/vlc/codec/libavcodec_plugin.so
	linux-vdso.so.1 =>  (0x00007fff711ff000)
	libpthread.so.0 => /lib/libpthread.so.0 (0x00007f6b307cc000)
	libz.so.1 => /lib/libz.so.1 (0x00007f6b305b5000)
	libbz2.so.1.0 => /lib/libbz2.so.1.0 (0x00007f6b303a3000)
	libfaac.so.0 => /usr/lib/libfaac.so.0 (0x00007f6b30191000)
	libfaad.so.0 => /usr/lib/libfaad.so.0 (0x00007f6b2ff51000)
	libmp3lame.so.0 => /usr/lib/libmp3lame.so.0 (0x00007f6b2fcd8000)
	libopencore-amrnb.so.0 => /usr/lib/libopencore-amrnb.so.0 (0x00007f6b2fa9e000)
	libopencore-amrwb.so.0 => /usr/lib/libopencore-amrwb.so.0 (0x00007f6b2f882000)
	libdl.so.2 => /lib/libdl.so.2 (0x00007f6b2f67d000)
	libjack.so.0 => /usr/lib/libjack.so.0 (0x00007f6b2f461000)
	libm.so.6 => /lib/libm.so.6 (0x00007f6b2f1dd000)
	libvlccore.so.4 => /usr/local/lib/libvlccore.so.4 (0x00007f6b2eef5000)
	libc.so.6 => /lib/libc.so.6 (0x00007f6b2eb86000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f6b3160b000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00007f6b2e876000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00007f6b2e65e000)
	librt.so.1 => /lib/librt.so.1 (0x00007f6b2e456000)
	libsamplerate.so.0 => /usr/lib/libsamplerate.so.0 (0x00007f6b2e0ea000)
	libcelt.so.0 => /usr/lib/libcelt.so.0 (0x00007f6b2ded6000)
	libdbus-1.so.3 => /lib/libdbus-1.so.3 (0x00007f6b2dc97000)

If you wish to pursue take a look at the slackware ffmpeg amd_64 asm patch, -  not all of it (the one I found) would apply cleanly - made a change to the dsputil.h patch so this resulted
```
#define SINETABLE_CONST
#endif

#ifndef _ATTR_HIDDEN
#define _ATTR_HIDDEN __attribute__((visibility("hidden")))
#endif

#define COSTABLE(size) \
    COSTABLE_CONST DECLARE_ALIGNED_16(FFTSample, _ATTR_HIDDEN ff_cos_##size[size/2])
#define SINTABLE(size) \
    SINTABLE_CONST DECLARE_ALIGNED_16(FFTSample, _ATTR_HIDDEN ff_sin_##size[size/2])
#define SINETABLE(size) \
    SINETABLE_CONST DECLARE_ALIGNED_16(float,  _ATTR_HIDDEN ff_sine_##size)[size]
extern COSTABLE(16);
extern COSTABLE(32);
```

For interests sake the changes I made, full diff in post below, still good thru 02/17

---

### Post by andrew.46 on 2010-02-06
Hi SuperSonic,

> **SuperSonic4 said:**
>  May I suggest placing a link to the VLC plugins manager.

I am holding off just for the moment as the first of the extensions has just appeared in the source tree as share/lua/extensions/imdb.lua. I would imagine that shortly the rest will appear and hopefully will either be available directly or by symlink.

Andrew

---

### Post by andrew.46 on 2010-02-06
Hi mc4man,

> **mc4man said:**
> If you wish to pursue take a look at the slackware ffmpeg amd_64 asm patch, -  not all of it (the one I found) would apply cleanly - made a change to the dsputil.h patch so this resulted [...]

That is indeed a big patch. alienBOB runs the script with a fixed version of FFmpeg thus he can tailor the patch to meet the specific FFmpeg revision. A great pity these changes could not be absorbed into FFmpeg itself ....

Andrew

---

### Post by mc4man on 2010-02-06
> changes could not be absorbed into FFmpeg itself ....

personally don't really know if they belong in ffmpeg itself, though for the static build for a 64 bit vlc seems ok.

Considering not in the scope of this thread think I'll let it go...after this

Anyway for the few that may wish to test on 64 bit, made the few changes to the slackware patch, may be good for a day or 2 or longer - till there is a line change in ffmpeg, though the gist is pretty straightforward and can be adjusted.

Can be applied 2 ways - leave as a .gz, place in vlc_build folder, and run @ ffmpeg source folder prompt
```
zcat ~/vlc_build/amd_asm.diff.gz |patch -p1
```

ex.
> Checked out revision 21665.
doug@doug-laptop:~/vlc_build$ cd ffmpeg
doug@doug-laptop:~/vlc_build/ffmpeg$ zcat ~/vlc_build/amd_asm.diff.gz |patch -p1
patching file libavcodec/dsputil.h
Hunk #1 succeeded at 771 (offset 23 lines).
patching file libavcodec/x86/dsputil_mmx.h
patching file libavcodec/x86/vc1dsp_mmx.c
patching file libswscale/swscale.c
Hunk #1 succeeded at 131 (offset -90 lines).
Hunk #2 succeeded at 160 (offset -90 lines).


or extract to vlc_build folder and run instead at the same ffmpeg prompt
```
patch -p1 < ~/vlc_build/amd_asm.diff
```
otherwise all is the same except adding --enable-pic to both the x264 and ffmpeg configures (and the deal with live555 - I forget the exact...

---

### Post by andrew.46 on 2010-02-07
Hi mc4man,

> **mc4man said:**
> (and the deal with live555 - I forget the exact...

Thanks very much for delving into all that :). The live555 libraries simply needed -fPIC added into the compile options before running *./genMakefiles linux* and the quick way to do this is with sed:

```
sed -i_bak 's/-O2 /-O2 -fPIC /' config.linux
```

This should all serve at the very least as a starting point for 64bit users? I keep waiting for somebody to discard a 64bit system while going after the latest and greatest.....

Andrew

---

### Post by andrew.46 on 2010-02-08
Hi Supersonic,

> **SuperSonic4 said:**
> May I suggest placing a link to the VLC plugins manager.

I have caved in and placed directions for placing the extensions in the correct location. I have streamlined the syntax a little so hopefully installation will be pretty easy...

Andrew

---

### Post by andrew.46 on 2010-02-10
Hi,

If you are having trouble compiling with a 'maemo' skins error compilation can be achieved by adding:

```
--disable-skins2
```

to the ./configure line. Hopefully this will be fixed soon...

**Edit**: Still broken so I have added --disable-skins2 to the main guide. If it is fixed and I don't pick up on it I would be grateful for a poke.

Andrew

---

### Post by mc4man on 2010-02-13
So as far as the wmas thru avcodec - I'd guess that's up to the vlc guys...

I'm using 1.0.5 atm - used this for my .diff

```
--- vlc-1.0.5.orig/modules/codec/avcodec/fourcc.c
+++ vlc-1.0.5/modules/codec/avcodec/fourcc.c
@@ -901,6 +901,13 @@
       AUDIO_ES, "Windows Media Audio Professional" },
 #endif
 
+#if LIBAVCODEC_VERSION_INT >= AV_VERSION_INT( 52, 54, 0 )
+    { VLC_FOURCC('W','M','A','S'), CODEC_ID_WMAVOICE,
+      AUDIO_ES, "Windows Media Audio Speech" },
+    { VLC_FOURCC('w','m','a','s'), CODEC_ID_WMAVOICE,
+      AUDIO_ES, "Windows Media Audio Speech" },
+#endif
+
```

1.1 is a bit different, taking a guess -   maybe just this in same file as above (around line 270 would seem appropriate 

```
#if LIBAVCODEC_VERSION_INT >= AV_VERSION_INT( 52, 54, 0 )
    { VLC_CODEC_WMAS, CODEC_ID_WMAVOICE, AUDIO_ES },
#endif

```

---

### Post by andrew.46 on 2010-02-13
Hi mc4man,

Hmmm.... I must say MPlayer is much more flexible in this regard, such changes can be made from the commandline or configuration file rather than only alteration of the source code. Perhaps I shall leave a pleading note on the vlc forums.

Andrew

---

### Post by mc4man on 2010-02-13
> I must say MPlayer is much more flexible in this regard, such changes can be made from the commandline or configuration file...

To some extent they're similar - though mplayer does provide it's own ffmpeg sources and is much more flexible as to specifying an audio and or video decoder to use.

Vlc tends to default to avcodec if it's defined and version supported if applicable. ( in essense they don't know what version and capabilities of ffmpeg is being provided 

I may try the git tommorrow- I think it's just that simple 3 line edit - the 1.0.5 works fairly well - though on one of those samples - the audio only one, misses about the first 5 sec.s, on the other one and a few I have it works fine.

> Perhaps I shall leave a pleading note on the vlc forums.

I'd think that they will be inclined to add at some point like for wmap, it can't be any worse than what's available now thru dmo, which here means no support since 0.9.9a

---

### Post by andrew.46 on 2010-02-13
Hi mc4man,

> **mc4man said:**
> To some extent they're similar - though mplayer does provide it's own ffmpeg sources and is much more flexible as to specifying an audio and or video decoder to use.

It could of course simply be a matter of familiarity but despite building vlc more than a few times I find MPlayer easier to my hand.

> Vlc tends to default to avcodec if it's defined and version supported if applicable. ( in essense they don't know what version and capabilities of ffmpeg is being provided 

Now that you have pointed out the correct location I can see how the vlc developers have attempted to cover different versions of libavcodec, it must be a nightmare to keep up with the constant changes.

> I may try the git tommorrow- I think it's just that simple 3 line edit - the 1.0.5 works fairly well - though on one of those samples - the audio only one, misses about the first 5 sec.s, on the other one and a few I have it works fine.

Not one to hold back with such things I made a very primitive change with no version checking (since I know what version I have in place) and the result was completely successful with 1.1.0:

```
[0x807bc38] main decoder debug: looking for decoder module: 32 candidates
[0x807bc38] avcodec decoder debug: libavcodec initialized (interface 0x343600)
[0x807bc38] avcodec decoder debug: ffmpeg codec (Windows Media Audio Speech) started
```

So in my fourcc.c wma section was altered to:
```

    /*
     *  Audio Codecs
     */
    /* WMA family */
    { VLC_CODEC_WMA1, CODEC_ID_WMAV1, AUDIO_ES },
    { VLC_CODEC_WMA2, CODEC_ID_WMAV2, AUDIO_ES },
**[COLOR="Red"]    { VLC_CODEC_WMAS, CODEC_ID_WMAVOICE, AUDIO_ES },[/COLOR]**
#if LIBAVCODEC_VERSION_INT >= AV_VERSION_INT( 52, 35, 0 )
    { VLC_CODEC_WMAP, CODEC_ID_WMAPRO, AUDIO_ES },
#endif

```

although the version checking is of course more correct :). Thanks for pointing out this section of the code. Perhaps you could submit a patch?

> I'd think that they will be inclined to add at some point like for wmap, it can't be any worse than what's available now thru dmo, which here means no support since 0.9.9a

I have in fact left a [request on the vlc forums]("http://forum.videolan.org/viewtopic.php?f=13&t=72224"). It might be a little early as the FFmpeg decoder has only just arrived with the first patch posted early in January but as you mentioned the dmo loader is no help with these files...

Andrew

---

### Post by Linuxforall on 2010-02-13
I find building mplayer to be far more easier.

---

### Post by andrew.46 on 2010-02-13
Hi Linuxforall,

> **Linuxforall said:**
> I find building mplayer to be far more easier.

I would agree with you there, but of course that is why I have put this guide together :). It provides at the very least a starting point to building the git vlc and certainly in my own personal usage of this guide updates to x264, FFmpeg and vlc-git can be handled easily by scripts so it becomes a lot easier.

Andrew

---

### Post by mc4man on 2010-02-13
> ...to keep up with the constant changes.

That does point to a chance that the support may break if there is any significant change to ffmpeg's wmas support. It happened to wmap in late august - 1.0.2 got wmap avcodec support and then it was lost till 1.03 in oct. (depending on ffmpeg -r

 The reason why it's fairly easy to enable is like wmap it's already in vlc - look in vlc/modules/codec/dmo/dmo.c, so the lines for 1.0.X and 1.1 are just the vlc id, the ffmpeg id and the vlc description - same thing as wmap and if wmal was ffmpeg supported it could also be switched.

(though how well or long decoding works could be up to vlc to make any changes if needed. 

> with no version checking
That's what I did here also, as noted for one's own use it's a moot point.

> Perhaps you could submit a patch?

It'd pretty simplistic- I'm sure they'll do if inclined - though feel free - they'd want the version ck.

(the last post I had there in a related way was a bit ['odd']("http://forum.videolan.org/viewtopic.php?f=13&t=66047&p=220041&hilit=wma3#p220041"), I think I'll let such things go their own way..

It's probably also not a bad idea to hang on to your previous ffmpeg build if re-building with a new one till you've checked it out.

---

### Post by SuperSonic4 on 2010-02-13
Have you had any luck with enabling testsuite via *--enable-testsuite*? I know it's disabled by default but it's intriguing :p

---

### Post by mc4man on 2010-02-15
Andrew - small unimportant thing to consider...

Had occasion today where I wanted to force a decoder on 2 files for opposite reasons but same idea - video from dmo, audio from avcodec

While I may be missing the way, unlike mplayer, vlc seems to have only have  a single non specific decoding  switch, --codec 

So if both the audio and video have decoders in dmo then --codec dmo forces both to dmo, not exactly what I wanted.

So for the moment (and probably permanently here) I've removed wmap from dmo so it's always decoded in avcodec, this way for example if I used the --codec dmo switch now the video is dmo, the audio avcodec.

modules/codec/dmo/dmo.c - remove 1 line in 1.1, 2 lines in 1.0.X (and backspace if needed, around line 204 in 1.1, 216-217 in 1.0.5

Ex.
> doug@doug-laptop:~$ vlc -vv --codec dmo '/home/doug/Videos/halo2_wmp9_WMV3+audio0x162.wmv'
[0x8663b88] asf stream debug:   - codec[0] audio name:"Windows Media Audio 9 Professional" description:"256 kbps, 48 kHz, 5.1 channel 24 bit 2-pass VBR" information_length:2
[0x8663b88] asf stream debug:   - codec[1] video name:"Windows Media Video 9" description:"" information_length:4
[0x86657f0] avcodec decoder debug: ffmpeg codec (Windows Media Audio Professional) started
[0x8661400] main decoder debug: looking for decoder module: 33 candidates
[0x8661400] dmo decoder debug: DMO codec for WMV3 may work with dll=wmv9dmod.dll


While I lean to always using avcodec if possible - there are a few times dmo is better though not for wmap so no need for it to be in there anymore - may also move wmas out of dmo

---

### Post by andrew.46 on 2010-02-17
Looks like support for wma voice is [now officially in vlc-git]("http://git.videolan.org/?p=vlc.git;a=blobdiff;f=modules/codec/avcodec/fourcc.c;h=08e0443841850596dd0865f293b5f939330bd382;hp=fbec4592ea7ddfeeddbeaea5e70f2ded4a2e16e3;hb=e8d5a49a2633d4a2944827f21774fa8ca1108112;hpb=d9666c8a60e61d63c21b25c6de9b07741bf0b151") :). An excellent reason to compile the development version of vlc against the latest svn FFmpeg!

Andrew

---

### Post by andrew.46 on 2010-02-18
Skins break compilation again so I have once more added:

```
--disable-skins2
```

to the ./configure string. I might leave this option in place, I am pretty sure that anybody keen enough to plough through this quite complex guide should also be knowledgeable enough to remove the option if they so desire, and it seems to break compilation fairly regularly.

Still waiting for this guide to pick up a few more users, might be a bit more widely used when I get my own 64bit system going in a few weeks time and finally come to grips with compiling the 64bit vlc-git. Plus the conversion of the guide to the upcoming Lucid Lynx...

Andrew

---

### Post by andrew.46 on 2010-02-22
Hi mc4man,

> **mc4man said:**
> while I don't intend to keep or use a 64 bit install, it did bug me that some where building the 1.1 of of a shared ffmpeg install (sooner or later using new shared ffmeg libs will be an issue

Looks like I will be getting access to a 64bit system shortly so I will soon be able to attack this myself :). In the mean time could you see if:

```
--disable-asm
```

as an FFmpeg option allows the 64bit vlc-git to build against a static FFmpeg in the manner I have described in the guide? And if so are the results catastrophic in terms of FFmpeg performance...

Thanks yet again :)

Andrew

---

### Post by mc4man on 2010-02-22
> --disable-asm  that should work ok, as far as it's effect, don't know quite enough in that area to say for sure.

I'd guess it shouldn't be an issue at all on the decoding side, though maybe on transcoding.

(edit : this is assuming an ffmpeg build for statically linking to vlc itself

On the 32 bit side I've definitely decided that removing wmap and wmas from dmo is the way to go atm

---

### Post by FakeOutdoorsman on 2010-02-22
> **andrew.46 said:**
> 
```
--disable-asm
```

as an FFmpeg option allows the 64bit vlc-git to build against a static FFmpeg in the manner I have described in the guide? And if so are the results catastrophic in terms of FFmpeg performance...

I believe this option would be the equivalent of:
```
--enable-uberslowness
```
for encoding.  However, it's purely opinion without any real evidence or testing on my non-existent 64-bit machine.

---

### Post by andrew.46 on 2010-02-22
Hi FakeOutdoorsman,

> **FakeOutdoorsman said:**
> I believe this option would be the equivalent of:
```
--enable-uberslowness
```
for encoding.  However, it's purely opinion without any real evidence or testing on my non-existent 64-bit machine.  

I suspect you may very well be right :). I am building a 64bit machine for my wife and I intend to have a small space for 64bit ubuntu and this will be my testing ground. I have a suspicion that I will use alienBOB's strategy and utilise an FFmpeg *snapshot* for the 64bit build combined with the asm patch he has used in his own build (while still advocating the svn FFmpeg for 32bit systems). From there it should be a little easier to build vlc for 64bit, I will just have to look at x264 and live555 as well but I think this will be a little easier. So I think in 3 weeks I should have a guide that caters for 32bit *and* 64bit....

Andrew

---

### Post by Elwro on 2010-02-24
Thank you very much for this guide! Unfortunately, I ran into the same problem as when I tried to build VLC myself: namely, I can't install libqt4-dev.```
The following packages have unmet dependencies:
  libqt4-dev: Depends: libpq-dev but it is not going to be installed
E: Broken packages
```
Then again, just to check:
```

$ sudo apt-get install libpq-dev
The following packages have unmet dependencies:
  libpq-dev: Depends: libpq5 (= 8.4.2-1~intrepid1) but 8.4.2-0ubuntu9.10 is to be installed
E: Broken packages

```
So, again to check:
```

$ sudo apt-get install libpq5
The following packages have unmet dependencies:
  libpq5: Depends: libkrb53 (>= 1.6.dfsg.2) but it is not installable
E: Broken packages

```
And lastly, because I'm wondering WHY it is not installable
```

$sudo apt-get install libkrb53
Package libkrb53 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  krb5-pkinit libkrb5support0 libkrb5-3 libk5crypto3 libgssapi-krb5-2
E: Package libkrb53 has no installation candidate

```
So I decide to choose one of the packages which "replace it":
```
$ sudo apt-get install libk5crypto3
libk5crypto3 is already the newest version.

```
I (as a newbie) don't understand the situation, please help. If there is a package which replaces an obsolete package, should the system point any other packages which depend on the obsolete package to use the "new one"?

I'm desperate to build VLC from source since the version from Ubuntu depositories seems to lack lua scripting! Thanks for the guide again and I hope my issue is easy to resolve for someone with bigger knowledge.

---

### Post by Aleksandar_B on 2010-02-24
I am new on Ubuntu, and have run into the same problem when playing .wmv files where .wmpa codec is missing. 

Like I said, I'm new so I don't have much experience with compiling. Is there way to download a .deb package of Your version of VLC?

---

### Post by andrew.46 on 2010-02-24
Hi Aleksandar,

> **Aleksandar_B said:**
> Like I said, I'm new so I don't have much experience with compiling. Is there way to download a .deb package of Your version of VLC?

There is a PPA:

[https://edge.launchpad.net/~nilarimogard/+archive/webupd8](https://edge.launchpad.net/~nilarimogard/+archive/webupd8)

which I have not personally tried...

All the best,

Andrew

---

### Post by andrew.46 on 2010-02-24
Hi Elwro,

This guide is for Karmic which I presume you are running? Some of the errors seem to suggest you could have a *mixed* sources.list which might be worth having a look at.

Andrew

---

### Post by Elwro on 2010-02-24
> **andrew.46 said:**
> Hi Elwro,

This guide is for Karmic which I presume you are running? Some of the errors seem to suggest you could have a *mixed* sources.list which might be worth having a look at.

AndrewThank you very much! Turned out I had one intrepid-related source left. Commenting it out fixed the issue and vlc 1.1.0 built successfully (yay!)...

...but it still doesn't work for me as it should :-( My main goal is to run CUE + single FLAC combinations. It works nicely in VLC under Windows XP. On Ubuntu, however, it doesn't - VLC can't decipher any CUE files (I make them with EAC). The message log says, for example:

```
main debug: `file:///media/My%20Book/FLAC/Perlman%20Edition%20-%20Kreisleriana/Kreisler%2C%20Fritz%20-%20Itzhak%20Perlman%2C%20Samuel%20Sanders.cue' successfully opened
ps warning: garbage at input, trying to resync...
```
in the same place where the windows build proceeds to the content of the CUE.

This is the issue due to which I decided to try to build vlc from source in the first place. On the official VLC forums one of the devs said "seems that your VLC build lacks LUA scripting". But here I checked that the vlc configure script output contained a "checking for LUA: yes" line... I have no idea what to do now. I'd appreciate any help and I hope you don't mind me not starting a new thread about my issue.

edit: I checked that the problem persists after I REMOVE my installation of VLC and use the package from the [PPA](https://edge.launchpad.net/~nilarimogard/+archive/webupd8) you linked to above. So it seems the problem might be at my end again, but I'm still completely in the dark! Did anyone check whether CUE + FLAC combinations work in VLC on their Karmic systems?

---

### Post by andrew.46 on 2010-02-24
Hi Elwro,

> **Elwro said:**
> Thank you very much! Turned out I had one intrepid-related source left. Commenting it out fixed the issue and vlc 1.1.0 built successfully (yay!)...

Excellent :).

>  I checked that the problem persists after I REMOVE my installation of VLC and use the package from the [PPA](https://edge.launchpad.net/~nilarimogard/+archive/webupd8) you linked to above. So it seems the problem might be at my end again, but I'm still completely in the dark! Did anyone check whether CUE + FLAC combinations work in VLC on their Karmic systems?

Could you post an example somewhere? My knowledge of cue and flac is not huge :(. BTW a simple thing to try is to place quotation marks around the filename, I see you have some spaces in the name... this will probably make no difference mind you :).

Andrew

---

### Post by Elwro on 2010-02-24
Thanks, I managed to solve the problem but in a bit bizarre way, after examining my message log more closely. I simply copied cue.lua from the Windows /lua/playlist directory into my /usr/lib/vlc/lua/playlist and playback now works fine! Is it a bug, should I report it somewhere? The Ubuntu packages (both the "official" and from the PPA you linked to) seem to be lacking the cue.lua script and it also wasn't installed when I followed your guide!

Thank you very much for your help again...

---

### Post by andrew.46 on 2010-02-24
Hi Elwro,

> **Elwro said:**
> Is it a bug, should I report it somewhere?

I have subscribed to your thread on the vlc forums which is certainly the place to report such a problem and I wait with some interest to see any comments from the vlc developers.

Andrew

---

### Post by mc4man on 2010-02-24
I think what you may notice (at least here) is that only the lua scripts that get 'precompiled..?', will end up in the install.

Check in your source before build - /vlc/share/lua/playlist - should be about 23 .lua's
Then after building take a look - only the ones duped as .luac will be installed to /usr/local/lib/vlc/lua/playlist or /usr/lib/vlc/lua/playlist

( vlc also will look in ~./local/share/vlc.... for lua scripts

---

### Post by Elwro on 2010-02-24
Yes, you're right, the cue.lua is there but is not duped into cue.luac 

But why should this be appropriate? If cue.lua was just copied into /usr/lib/vlc/lua/playlist then cue playback would work (at least it does work on my machine)...

---

### Post by mc4man on 2010-02-24
> If cue.lua was just copied into /usr/lib/vlc/lua/playlist then cue playback would work
It's probably just one of those things, there have been a lot of lua changes lately.  
The creation of *.luac is only just a week or two old.

As you've seen just copy the script over or put it (or any other uninstalled script ) in your home folder 

~/.local/share/vlc/lua/playlist/

Ex.
> [0x8394650] lua demux debug: Trying Lua playlist script /home/doug/.local/share/vlc/lua/playlist/cue.lua
[0x8394650] lua demux debug: Lua playlist script /home/doug/.local/share/vlc/lua/playlist/cue.lua's probe() function was successful
[0x8394650] main demux debug: using demux module "lua"


Note that vlc can't use all .cue's, but those from eac  it can

---

### Post by tqft on 2010-02-25
> **andrew.46 said:**
> Hi Elwro,



I have subscribed to your thread on the vlc forums which is certainly the place to report such a problem and I wait with some interest to see any comments from the vlc developers.

Andrew

The other place for immediate feedback is the irc #vlc channel on freenode - log errors like you have copied here posted to pastebin.com can generally get some sort of response.

---

### Post by andrew.46 on 2010-02-25
Hi tqft,

> **tqft said:**
> The other place for immediate feedback is the irc #vlc channel on freenode 

Perhaps #videolan ?

Andrew

---

### Post by tqft on 2010-02-25
> **andrew.46 said:**
> Hi tqft,



Perhaps #videolan ?

Andrew

Yes, I was thinking (or maybe not) of the vlmc channel, sorry.

---

### Post by mc4man on 2010-02-25
Small item - 
what you may want to consider to suggest is to install the qt4 config tool and change the qt gui from default (gtk) to something else - cleanlooks works well.
Under the default it's impossible to save playlists to the various formats vlc can and is very good at (.m3u, .m3u8, ,xspf
Plus overall the gui style should be changed anyway

To test try to save as is, then 
```
sudo apt-get install qt4-qtconfig
```
Found under System - preferences - QT 4 settings

srn 1 - under default (gtk) style - no save poss.
scr 2 under cleanlooks - works fine

---

### Post by andrew.46 on 2010-02-25
Hi Elwro,

> **Elwro said:**
> Yes, you're right, the cue.lua is there but is not duped into cue.luac 

Looks like your post on the vlc forums has born some fruit, on my slackware system:

```
/usr/lib/vlc/lua/playlist/dailymotion.luac
/usr/lib/vlc/lua/playlist/googlevideo.luac
/usr/lib/vlc/lua/playlist/joox.luac
/usr/lib/vlc/lua/playlist/megavideo.luac
/usr/lib/vlc/lua/playlist/break.luac
/usr/lib/vlc/lua/playlist/metacafe.luac
/usr/lib/vlc/lua/playlist/mpora.luac
/usr/lib/vlc/lua/playlist/katsomo.luac
/usr/lib/vlc/lua/playlist/lelombrik.luac
/usr/lib/vlc/lua/playlist/vimeo.luac
/usr/lib/vlc/lua/playlist/anevia_streams.luac
/usr/lib/vlc/lua/playlist/youtube.luac
/usr/lib/vlc/lua/playlist/appletrailers.luac
**[COLOR="Red"]/usr/lib/vlc/lua/playlist/cue.luac[/COLOR]**
/usr/lib/vlc/lua/playlist/france2.luac
/usr/lib/vlc/lua/playlist/youtube_homepage.luac
```

Andrew

---

### Post by andrew.46 on 2010-02-25
Hi mc4man,

> **mc4man said:**
> what you may want to consider to suggest is to install the qt4 config tool and change the qt gui from default (gtk) to something else - cleanlooks works well.

Thanks yet again for your input, I have added the qt4 config tool into the guide.

Andrew

---

### Post by Elwro on 2010-02-26
> **andrew.46 said:**
> Looks like your post on the vlc forums has born some fruitWhoa, that was fast :-)

---

### Post by andrew.46 on 2010-02-26
Hi Elwro,

> **Elwro said:**
> Whoa, that was fast :-)

This is why running the development version of anything is so much fun!!

Andrew

---

### Post by Aleksandar_B on 2010-02-26
Before I install Your version of VLC, do I need to delete the "official" version from my system, will the two confront or can they coexist.

---

### Post by andrew.46 on 2010-02-26
Hi Aleksandar,

> **Aleksandar_B said:**
> Before I install Your version of VLC, do I need to delete the "official" version from my system, will the two confront or can they coexist.

In general it can be problematic to have 2 different versions of the same software installed on the same system. In this particular case you will also find that vlc-git will often fail to compile at all, or certain features will be lost completely for extended periods. My best advice, if you are not sure, is to leave the release version installed to your system but also compile vlc-git ***and don't install it***. Then you can run the git version by navigating to the source code and running *./vlc* while running the release version as normal. I will admit that I do not follow this safe practice myself though, I personally have removed the release version and run only vlc-git but this is a little rash :).

All the best,

Andrew

---

### Post by andrew.46 on 2010-02-28
Success with the 64 bit vlc-git on the 64 bit system I built for my wife :). I shall write it up over the next couple of days!!

Andrew

---

### Post by Linuxforall on 2010-03-01
> **andrew.46 said:**
> Success with the 64 bit vlc-git on the 64 bit system I built for my wife :). I shall write it up over the next couple of days!!

Andrew

Bravo........was waiting for that.

---

### Post by andrew.46 on 2010-03-03
64 bit changes are now in place. Usage of --disable-asm with FFmpeg is obviously not ideal but guarantees compilation with vlc at the moment and is perfectly usable on my own 64 bit system. Nevertheless I will keep working on this one...

Andrew

---

### Post by mc4man on 2010-03-03
a possible edit to new instr.
  > if [ ! "$(uname -m)" = "x86_64" ]; then
  ARCHOPTS="--enable-loader"

"i686"

---

### Post by andrew.46 on 2010-03-03
Hi mc4man,

> **mc4man said:**
> a possible edit to new instr.
  
"i686"

I have done this a little backwards I admit :). To tell the truth I am revising all of this a little when I get off nights as I am not entirely happy with the --disable-asm business. I am moving to the same revision of FFmpeg that alienBOB uses and applying the asm patch...

Andrew

---

### Post by mc4man on 2010-03-03
> I am moving to the same revision of FFmpeg that alienBOB uses and applying the asm patch...
That seems to be best sol. atm (in a semi-static how-to sense

Am actually interested to see how you dl a particular snapshot (vs. a checkout of -rxxxxx, which while it works, always co's the current swscale which may not be appropriate to the ffmpeg -r

Otherwise, somewhat to my surprise, the patch posted earlier in pg.1 is still good - though that could change at any time..

To some extent advances in ffmpeg may not translate to any gain in vlc, certainly it's not a given.

---

### Post by andrew.46 on 2010-03-03
Hi mc4man,

> **mc4man said:**
> Am actually interested to see how you dl a particular snapshot (vs. a checkout of -rxxxxx, which while it works, always co's the current swscale which may not be appropriate to the ffmpeg -r.

Well the technique I have just added to this guide is a little clumsy but seems to work well enough:

```

$ svn co -r {'2009-12-11'} svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg
$ cd ffmpeg/libswscale
$ svn up -r {'2009-12-11'}

```

I suspect this can be done a little more cleanly but it will certainly do for a start...

Andrew

---

### Post by mc4man on 2010-03-04
> seems to work well enough:
That it does, I think I've had this mental block that up=forward rather than up=update to <whatever>

---

### Post by andrew.46 on 2010-03-04
Hi mc4man,

> **mc4man said:**
> That it does, I think I've had this mental block that up=forward rather than up=update to <whatever>

Thanks for having a look at it :). The good news is that I have built both the 64 bit and 32 bit versions in the last hour using my own guide and produced 2 good working copies of vlc-git. So for me the first stage of this guide has been completed and I will admit that I did not realise at the outset what a challenge this guide would be to put together :). And again thanks for your assistance in many aspects of the guide including provoking my interest in building vlc-git in the first place!

All the best,

Andrew

---

### Post by tqft on 2010-03-04
> **andrew.46 said:**
> Hi mc4man,



Well the technique I have just added to this guide is a little clumsy but seems to work well enough:

```

$ svn co -r {'2009-12-11'} svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg
$ cd ffmpeg/libswscale
$ svn up -r {'2009-12-11'}

```

I suspect this can be done a little more cleanly but it will certainly do for a start...

Andrew

You have seen the ffmpeg thread ? [quite possibly some people here are running it]
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)
Apparently there are new presets and stuff in latest version of ffmpeg.

I have given up playing with ffmpeg after the last time video broke.

But if you do need speed, you can do a profile guided optimization build  of ffmpeg and x264 as well I think (It has been a while).  Basically 2 passes, after the first pass you play a movie or whatever to build an execution profile and then compile again with the compiler taking the info do an optimised build. If you really want to do this and can't find the directions, ask me and i will try and find the instructions again.

---

### Post by andrew.46 on 2010-03-04
Hi tqft,

> **tqft said:**
> But if you do need speed, you can do a profile guided optimization build  of ffmpeg and x264 as well I think (It has been a while).  Basically 2 passes, after the first pass you play a movie or whatever to build an execution profile and then compile again with the compiler taking the info do an optimised build. If you really want to do this and can't find the directions, ask me and i will try and find the instructions again.

Thanks for that and I am certainly one of those keen readers of Fakeoutdoorsman's great FFmpeg guides. The aims of compiling FFmpeg are however a little different on this particular thread, rather than produce a great FFmpeg build for commandline encoding the aims are rather to:

[LIST=1]
[*]Provide a *rich* FFmpeg / libavcodec to compile vlc against
[*]Cater for the difficulties of compiling FFmpeg on 64 bit systems and allowing vlc to compile cleanly against it
[*]Interfere as little as possible with system installations of FFmpeg/libavcodec and x264
[/LIST]

So the aims are slightly different and certainly not mutually exclusive with FakeOutdoorsman's methods, in fact I run both :).

All the best,

Andrew

---

### Post by andrew.46 on 2010-03-04
I have added some links to the 'Some Resources...' section that give details on enabling midi playback with this build of vlc-git. Hopefully this will be useful for some?

Andrew

---

### Post by Elwro on 2010-03-05
Did you change the part of the guide regarding Live555? The last line is now ```
$ sudo mv -v $HOME/live /usr/lib
``` Shouldn't it be ```
$ sudo mv -v $HOME/vlc_build/live /usr/lib
```? (Yesterday I tried to build vlc on another computer and ran into some kind of "directory does not exist" error at this point.)

---

### Post by andrew.46 on 2010-03-05
Hi Elwro,

> **Elwro said:**
> Did you change the part of the guide regarding Live555?

Oops :(. Thanks for picking up that error which I have now corrected. You managed to build a working copy nevertheless?

Thanks,

Andrew

---

### Post by Elwro on 2010-03-05
> **andrew.46 said:**
> Oops :(. Thanks for picking up that error which I have now corrected. You managed to build a working copy nevertheless?
I don't remember getting any such errors when I first compiled vlc a few days ago, maybe I just missed it somehow... if the mistake was in back then, then yes, I managed to build a working copy using which I succesfully listened to CD Audio and cue+flacs, and also watched some AVIs.

This time, though, I decided to wait for your reply before continuing :-)

---

### Post by andrew.46 on 2010-03-05
Hi Elwro,

> **Elwro said:**
> I don't remember getting any such errors when I first compiled vlc a few days ago, maybe I just missed it somehow... 

There was a little bit of housekeeping in the meantime to allow all of the downloaded files to sit neatly in $HOME/vlc_build...

All the best,

Andrew

---

### Post by mc4man on 2010-03-08
Too off topic for ffmpeg thread
> I am not running lucid yet
Another thing I'm impressed by is for some sites the performance of the totem-mozilla plugin

screen shows apple trailers, the thing of note is it now buffers the complete stream very quickly (depending on your connection, ect.
I have a fast one and being fairly late - the complete trailer is almost finished buffering about a min. or so in.

(I'd love to see browser plugins available as alternatives, then you could install them all and quickly switch as desired from an "sudo update-alternatives --config <something>"

With vlc I'm still not getting http streaming that requires additional caching to run in 1.0.X and 1.1 quite as good as it did in 0.9.9, which was flawless, - have you had occasion to try a cli with vlc on something like apple trailers?

---

### Post by ViperScull on 2010-03-14
Hi, Andrew. Thanks for this excellent how-to. Vlc build failed. My arch is amd64.

I changed --enable-loader for --disable-loader, then it worked. Don't know if it's only for me, or it could happen to the rest of x64 arch users.

Anyway, after installed I can't watch any video, neither xvid nor x264. But i can hear the sound.

I did everything in the how-to except installing w32codecs, cause there aren't for Lucid in Medibuntu repos.

Viper.

---

### Post by andrew.46 on 2010-03-14
Hi Viper,

It could be that you have missed the 'if' commands throughout the guide which have been designed specifically to cater for 64bit users. For example this:

```

if [ "$(uname -m)" = "x86_64" ]; then
  ARCHOPTS="--enable-pic"
 else
   ARCHOPTS=""
 fi

```

is designed to be copied and pasted as *one* piece of code, a similar arrangement should have omitted the *--enable-loader* option for 64bit usage.

All the best,

Andrew

---

### Post by ViperScull on 2010-03-16
Sorry for the delay in replying, I've been very busy.

I dit it manually. I set ARCHOPTS value to the corresponding option in the how-to, given that my arch is x64.

Cheers. Viper.

---

### Post by qyot27 on 2010-03-25
I attempted to build VLMC from the current repository (git://git.videolan.org/vlmc.git), but it fails at about 61%, and, from what I can remember, it has something to do with what I'm assuming are the mouse pointers.  The final GitHub commit compiles fine, though - it's just three weeks old, and it looks like a lot more development has gone into it since then.

I don't know if this is a problem with the (possibly Qt-related) dependencies or not.  The PPA linked to earlier in the thread ([https://edge.launchpad.net/~nilarimogard/+archive/webupd8](https://edge.launchpad.net/~nilarimogard/+archive/webupd8)) didn't seem to conflict with compiling the GitHub repo checkout, but I don't know if it's the reason the checkout from the main repo doesn't compile successfully.

---

### Post by mc4man on 2010-03-25
no issue building the vlmc git from today (using libvlc-dev, Libvlccore-dev built yesterday..

hits this and just moves right along (maybe where you fail?
 > 62%] Building CXX object src/CMakeFiles/vlmc.dir/Gui/timeline/GraphicsCursorItem.cpp.o

Though probably of no use (cmake isn't too verbose), attached build log if you wish to compare

---

### Post by qyot27 on 2010-03-25
Aye, that is.  So I am now assuming it is the dependencies issue with that PPA.  Wonder what changed on VLMC's side that messes it up, because like I mentioned, the repo in the guide here compiles fine using the vlc-git stuff pulled from the PPA instead of me compiling all of that too.

---

### Post by FakeOutdoorsman on 2010-03-25
> **qyot27 said:**
> Aye, that is.  So I am now assuming it is the dependencies issue with that PPA.  Wonder what changed on VLMC's side that messes it up, because like I mentioned, the repo in the guide here compiles fine using the vlc-git stuff pulled from the PPA instead of me compiling all of that too.

That particular PPA is just trouble.  It's caused a herd of [bug reports](https://bugs.launchpad.net/ubuntu/+source/x264/+bug/526105) (5 duplicates!) all because of the libx264 package in that PPA.

---

### Post by qyot27 on 2010-03-26
> **FakeOutdoorsman said:**
> That particular PPA is just trouble.  It's caused a herd of [bug reports](https://bugs.launchpad.net/ubuntu/+source/x264/+bug/526105) (5 duplicates!) all because of the libx264 package in that PPA.
How do you know that it's that PPA?  I didn't see any part of that PPA's URL (or the filenames for its .deb packages) listed in the comments.  Is there a link somewhere that directly shows the stuff was installed from there?

---

### Post by mc4man on 2010-03-26
> How do you know that it's that PPA?

Wouldn't know here, but ...

One thing about that the ppa you linked -  (noting I'm not using it, nor have reason to, just looking inside the .deb

It does misrepresent the the x264 package - the package installs libx264-83 but the core version (and .so) is 88

This is generally a poor idea, really there is no reason not install the lib for what it is, in this case libx264-88

---

### Post by qyot27 on 2010-03-26
Ok, I see it concerning that now.

I'll condense the guide into a shell script so I don't have to do all of that manually.  I was going to do that before but didn't.

---

### Post by FakeOutdoorsman on 2010-03-26
> **qyot27 said:**
> How do you know that it's that PPA?  I didn't see any part of that PPA's URL (or the filenames for its .deb packages) listed in the comments.  Is there a link somewhere that directly shows the stuff was installed from there?

When attempting to find out where that offending package originated from, a search for *git781d300* found that PPA.  It appears that the libx264 package was removed from that PPA and no longer listed...or so it seems when I took a quick look.

---

### Post by qyot27 on 2010-03-26
Well, I discovered it still messed around with my install and gave me broken packages.  But I was able to Force Version back to Karmic and purge it out of existence along with the VLC stuff.

It also ended up solving one of the problems I'd had the last few days - my icons had screwed up, with the Ubuntu logo next to Applications turning white, and the desktop/appearance icons turning purple.  I don't know if the PPA backported Lucid's icons to Karmic or what, but downgrading brought things back to normal on that front too.



I checked the VLMC git repo and apparently there was a commit 18 hours ago that addresses something about GraphicsCursorItem and Qt 4.5.  Whether that would have fixed the problem I was having I don't know, but I'm currently in the process of running that script to compile everything.

---

### Post by Linuxforall on 2010-03-26
I was actually quite tempted with that ppa but then noticed x264 and other stuf there, since I compile my own x264 via FO's excellent guide, I decided to back off. Well guess I am stuck with old vlc 1.02, even C.Korn has stopped updating his PPA and its stuck in version 1.03, it would be nice if somone sets up a PPA with latest stable vlc releases.

---

### Post by mc4man on 2010-03-27
I normally use vlc 1.0.X (curently 6) and build myself for some added capabilities.

While i use a .diff I made and do as a package set, (works well with a local repo), you could easily use this guide with a few minor changes to build 1.0.5.

Otherwise here is a ppa that has 1.0.5 and is very well done ( not quite like a self built, but that may not even matter depending on one's usage.

[https://launchpad.net/~philip5/+archive/extra](https://launchpad.net/~philip5/+archive/extra)

( As a general rule with ppa's that offer a large number of packages you shouldn't leave enabled if you use the update manager - though a quick glance suggests nothing will get borked from this ppa due to an inadvertent update of other packages

---

### Post by Linuxforall on 2010-03-27
> **mc4man said:**
> I normally use vlc 1.0.X (curently 6) and build myself for some added capabilities.

While i use a .diff I made and do as a package set, (works well with a local repo), you could easily use this guide with a few minor changes to build 1.0.5.

Otherwise here is a ppa that has 1.0.5 and is very well done ( not quite like a self built, but that may not even matter depending on one's usage.

[https://launchpad.net/~philip5/+archive/extra](https://launchpad.net/~philip5/+archive/extra)

( As a general rule with ppa's that offer a large number of packages you shouldn't leave enabled if you use the update manager - though a quick glance suggests nothing will get borked from this ppa due to an inadvertent update of other packages

Thanks mc4man, I would rather build it myself as I did for mplayer, any place there is a clear guide, I would truly appreciate it. That PPA looks tempting but too many other stuff in there and I don't wish to fiddle with those.

---

### Post by qyot27 on 2010-03-27
> **Linuxforall said:**
> I was actually quite tempted with that ppa but then noticed x264 and other stuf there, since I compile my own x264 via FO's excellent guide, I decided to back off. Well guess I am stuck with old vlc 1.02, even C.Korn has stopped updating his PPA and its stuck in version 1.03, it would be nice if somone sets up a PPA with latest stable vlc releases.
The guide here for vlc-git compiles/installs everything to the subdirectory in $HOME.  The only exceptions to that are libtiger and goom and VLC itself, but not x264, ffmpeg, or so on (and some of the outputted .deb packages are placed on the Desktop, but you can delete those).  Everything else is self-contained and won't muck with the system, so you can have the x264 and/or ffmpeg you compile normally as well as this separately.

The script idea worked fine.  I had to wait for about 3½ hours for everything to compile, but that's because my computer is a dinosaur.  I would recommend moving all the sudo apt-get install stuff to the beginning, though, to cut down on the number of times you need to authenticate.  This is what it looked like after I turned it into a shell script (I only changed the VLMC repo to the current one on Videolan's servers):
```
#!/bin/bash -x
sudo apt-get install build-essential subversion git-core checkinstall automake
if [ ! "$(uname -m)" = "x86_64" ]; then
  ARCHOPTS="w32codecs"
 else
   ARCHOPTS=""
 fi
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
--output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update &&
sudo apt-get install -y libdvdcss-dev $ARCHOPTS
sudo apt-get install yasm libfaac-dev libfaad-dev libmp3lame-dev libopencore-amrnb-dev \
libopencore-amrwb-dev zlib1g-dev libqt4-dev libhal-dev lua5.1 liblua5.1-0-dev libdvdread-dev \
libtag1-dev libmad0-dev libdvbpsi5-dev liba52-0.7.4-dev libv4l-dev libcdio-dev \
libvcdinfo-dev libfribidi-dev libfluidsynth-dev libmpeg2-4-dev libschroedinger-dev \
libvorbis-dev libspeex-dev libgcrypt11-dev libcddb2-dev libproxy-dev libnotify-dev \
libebml-dev libmpcdec-dev libcaca-dev libaa1-dev libmatroska-dev xulrunner-dev \
libasound2-dev libass-dev libavahi-client-dev libdca-dev libdvdnav-dev libfaad-dev \
libflac-dev libfreetype6-dev libggi2-dev libgl1-mesa-dev libglib2.0-0 libgnutls-dev \
libid3tag0-dev libjack-dev liblircclient-dev libmodplug-dev libncursesw5-dev \
libogg-dev libpng12-dev libpulse-dev libsdl-image1.2-dev libsdl1.2-dev libshout3-dev \
libsmbclient-dev libsvga1-dev libsysfs-dev libtar-dev libtwolame-dev libudev-dev \
libupnp3-dev libx11-dev libxcb-keysyms1-dev libxext-dev libxml2-dev libxpm-dev \
libxt-dev libxv-dev libxcb-shm0-dev libxcb-xvmc0-dev libx11-xcb-dev \
libmtp-dev libsqlite3-dev libgnomevfs2-dev librsvg2-dev libzvbi-dev libxcb-randr0-dev \
liboggkate-dev libkate-dev libpango1.0-dev libcairo2-dev libprojectm-dev qt4-qtconfig cmake
mkdir -v $HOME/vlc_build && cd $HOME/vlc_build
git clone git://git.videolan.org/x264.git
cd $HOME/vlc_build/x264
if [ "$(uname -m)" = "x86_64" ]; then
  ARCHOPTS="--enable-pic"
 else
   ARCHOPTS=""
 fi
./configure --prefix=$HOME/vlc_build/vlcdeps/usr $ARCHOPTS
make && make install
make distclean
sudo apt-get remove liblivemedia-dev
cd $HOME/vlc_build
wget http://www.live555.com/liveMedia/public/live555-latest.tar.gz
tar xvf live555-latest.tar.gz
cd live
if [ "$(uname -m)" = "x86_64" ]; then
   sed -i_bak 's/-O2 /-O2 -fPIC /' config.linux
 fi
./genMakefiles linux
make
sudo mv -v $HOME/vlc_build/live /usr/lib
cd $HOME/vlc_build
svn co -r {'2009-12-11'} svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg
cd ffmpeg/libswscale
svn up -r {'2009-12-11'}
cd ..
if [ "$(uname -m)" = "x86_64" ]; then
   wget http://andrews-corner.org/patches/ffmpeg_x86_64_asm.patch
   patch -p1 --verbose <ffmpeg_x86_64_asm.patch
   ARCHOPTS="--enable-pic"
  else
   ARCHOPTS=""
 fi
./configure --prefix=$HOME/vlc_build/vlcdeps/usr \
              $ARCHOPTS \
              --enable-gpl \
              --enable-version3 \
              --enable-nonfree \
              --enable-postproc \
              --enable-pthreads \
              --enable-libfaac \
              --enable-libfaad \
              --enable-libmp3lame \
              --enable-libopencore-amrnb \
              --enable-libopencore-amrwb \
              --disable-ffmpeg \
              --disable-ffplay \
              --disable-ffserver \
              --disable-doc
make jobs=4 && make install-libs install-headers
make distclean
cd $HOME/vlc_build
wget http://libtiger.googlecode.com/files/libtiger-0.3.3.tar.gz
tar xvf libtiger-0.3.3.tar.gz
cd libtiger-0.3.3
./configure
make
sudo checkinstall --pakdir "$HOME/Desktop" --backup=no --deldoc=yes \
                    --pkgname libtiger --pkgversion "0.3.3" --deldesc=yes \
                    --delspec=yes --default
make distclean
cd $HOME/vlc_build
wget http://downloads.sourceforge.net/goom/goom-2k4-0-src.tar.gz
tar xvf goom-2k4-0-src.tar.gz
cd goom2k4-0
./configure
make
sudo checkinstall --pakdir "$HOME/Desktop" --backup=no --deldoc=yes \
                    --pkgname goom --pkgversion "2k4-0" --deldesc=yes \
                    --delspec=yes --default
make distclean
cd $HOME/vlc_build
git clone git://git.videolan.org/vlc.git --depth 1
cd vlc
./bootstrap
export PKG_CONFIG_PATH="$HOME/vlc_build/vlcdeps/usr/lib/pkgconfig"
sed -i_bak 's/Icon=vlc/Icon\=\/usr\/local\/share\/vlc\/vlc48x48\.png/' \
       share/vlc.desktop
if [ ! "$(uname -m)" = "x86_64" ]; then
  ARCHOPTS="--enable-loader"
 else
   ARCHOPTS=""
 fi
./configure $ARCHOPTS \
             --with-live555-tree=/usr/lib/live \
             --enable-real \
             --enable-realrtsp \
             --enable-aa \
             --enable-snapshot \
            --enable-merge-ffmpeg              
make jobs=4
sudo checkinstall --pakdir "$HOME/Desktop" --backup=no --deldoc=yes \
                    --pkgname vlc --pkgversion "1.1.0-`date +%Y%m%d`" \
                    --deldesc=yes --delspec=yes --default
make distclean
mv -v share/vlc.desktop_bak share/vlc.desktop
sudo ldconfig
mkdir -pv $HOME/.local/share/vlc/lua/extensions
lftp -c "mirror --verbose \
     http://jpeg.dinauz.org/VideoLAN/patches/extensions/share/lua/extensions \
     $HOME/.local/share/vlc/lua/extensions"
cd $HOME/vlc_build
git clone git://git.videolan.org/vlmc.git --depth 1
cd vlmc
cmake .
make
```
Save the above as a new file, vlc_buildscript.sh, for example, give it execution permission and then run it:

chmod +x vlc_buildscript.sh
./vlc_buildscript.sh


If you don't want the packages saved to the Desktop, I guess you'd just remove the --pakdir "$HOME/Desktop" parameters from the checkinstall steps.

---

### Post by Linuxforall on 2010-03-27
qyot27, many thanks, will give it a spin and get back to you.

---

### Post by dusdus on 2010-03-27
Hi there,

Despite I'm not an expert (using linux for 8 years though), I'm certainly interested in this installation of vlc. 

Question: is it necessary to build it using qt-libs? I saw you're using gnome, so isn't it possible to keep it "as gtk as possible"?

---

### Post by mc4man on 2010-03-27
> Question: is it necessary to build it using qt-libs?
For the typical use of vlc as a player - yes, it uses the qt4 interface, without it your use of vlc is quite limited

---

### Post by dusdus on 2010-03-27
ok, thanks for your answer.
I'll maybe take a look at it later. I'm playing with mplayer with multithread enabled now.

---

### Post by andrew.46 on 2010-03-28
Hi qyot,

> **qyot27 said:**
> The script idea worked fine.  I had to wait for about 3½ hours for everything to compile, but that's because my computer is a dinosaur.  I would recommend moving all the sudo apt-get install stuff to the beginning, though, to cut down on the number of times you need to authenticate. 

If you are keen to script this perhaps you could add a -y option to many of the apt-get commands which will then anticipate a 'yes' answer. Also it might be an idea to add something like:

```
set -e
```

to the beginning of your script so failure at one step will halt the script rather than let it roll onwards... Perhaps also run the script itself as sudo, eliminate all the 'sudo's in the scipt and adjust the permissions at the end. Lots of room for playing around :).

Andrew

---

### Post by andrew.46 on 2010-03-29
After some considerable thought I have decided to not develop this guide further than Karmic Koala. Some of the reasons include:

[LIST]
[*]The development model of vlc is quite different to that of say MPlayer and FFmpeg. With FFmpeg and MPlayer there are very definite gains to be had from compiling a cutting edge version. This is not so true of vlc where I feel that the development version is really intended for developers and those with enough skill to mend breakages. Certainly there is room for the curious but this is a lot of work for curiosity :).
[*]I confess in my own personal computer usage I have always felt more comfortable with MPlayer and I would like to focus my precious spare time in this area.
[*]More than most software I have come across compiling vlc demands access to a 64 bit and 32 bit installation. Although I have setup 2 such installations it has become a logistical nightmare and starting to feel like just plain hard work. Believe it or not I really only write guides because it is fun, and the fun is starting to go a little with this guide.
[/LIST]

Mind you if anybody wishes to plunder this guide and write up future versions for Lucid and beyond please do so with my complete blessing, just copy and paste whatever is useful :).

All the best,

Andrew

---

### Post by Elwro on 2010-03-30
I certainly benefitted from your guide - thank you very much, Andrew!

I'm sticking with VLC since there really seem to be no other CUE+(single)FLAC or CUE+(single)APE players for Gnome. 

Thanks again,

L.

---

### Post by qyot27 on 2010-03-30
> **andrew.46 said:**
> ```
set -e
```

to the beginning of your script so failure at one step will halt the script rather than let it roll onwards... Perhaps also run the script itself as sudo, eliminate all the 'sudo's in the scipt and adjust the permissions at the end. Lots of room for playing around :).

Andrew
Now, would the set -e be on the same line as #!/bin/bash -x, or would it be on a new line?


I prefer to use mplayer as well, my interest in vlc-git was only for testing VLMC, since official packages of it don't exist yet.  I really think it has an immediate advantage over other FOSS NLEs when it comes to users migrating from things like Premiere. In terms of layout and what kinds of stuff it looks like it might become capable of in the future, anyway.  Right now it isn't.

---

### Post by startak on 2010-04-18
Just tried this with Lucid.  I had trouble compiling VLC because it could not find '/usr/lib/libenca.la'

Had to manually install enca (1.9-1) from a debian source package to get that file.

---

### Post by mc4man on 2010-04-18
> because it could not find '/usr/lib/libenca.la'
Don't see that here on lucid, actually lucid has a more recent ver. (1.12

What you may wish to keep in mind is if you get the source from git clone you are now getting 1.2, not 1.1 ( there are now 3 vlc's - 1.0.X, 1.1-pre, 1.2
If you prefer to use the 1.1-pre then best bet is to get a nightly .tar - the ones with versions are what they say, without is 1.2 (don't ./boootstrap the nightlies

[http://nightlies.videolan.org/build/source/?C=M;O=D](http://nightlies.videolan.org/build/source/?C=M;O=D)

You can most definitely consider 1.2 to be unstable - 1.1 appears to be heading towards a release in near? future.

Highly recommended to review your configure, both 1.1 and 1.2 may require some editing (if possible) if something you wish is not configured.

There is always the possibility that libraries may not be found for various reasons, a recent ex. in 1.1, 1,2 is sdl_image.

vlc will only look in /usr/include, on lucid in needs to look in /usr/include/SDL, easily fixed in this case, others may not be so.

---

### Post by andrew.46 on 2010-04-30
After some considerable thought I have decided to do something of a backflip and continue developing this vlc-git guide, but at the expense of the other guides I have been writing for these forums. So *this* guide has been cleaned and spruced for Lucid Lynx and now tracks 1.2.0-git Twoflower. There have been a few miscellaneous cleanups but I guess the only 2 major changes are that goom is gone and the FFmpeg revision + 64bit patch have been updated, again following the lead of alienBOB.

@mc4man You solved the sdl_image problem with a link from /usr/include ? **Edit:** Hmmm.... that does not work...

Andrew

---

### Post by mc4man on 2010-04-30
Andrew - 
am heading out the door and happened to have dumped that lucid install and have not redone vlc 1.X since reinstalling.
(at this point I guess 1.1-pre and 1.2-git are still similar enough..?

Taking a quick look at the 1.2 source I believe it was only needed to edit a line in the configure script - look around line 39307 - editing to this should resolve
 ```
# SDL_image
        if  test "${enable_sdl_image}" != "no"; then :

          for ac_header in "[COLOR="Blue"]SDL/[/COLOR]SDL_image.h"
```

from conf. log
> configure:39310: checking SDL/SDL_image.h presence
configure:39310: gcc -std=gnu99 -E  -DSYS_LINUX conftest.c
configure:39310: $? = 0
configure:39310: result: yes
configure:39310: checking for SDL/SDL_image.h
configure:39310: result: yes
and the term.
> screensaver sdl_image skins2 speex 

Can test properly after work

Edit:
it may be possible to 'tweak' from ubuntu side -- I thought it better to adjust vlc...

---

### Post by andrew.46 on 2010-04-30
I have found [the revision]("http://git.videolan.org/?p=vlc.git;a=commitdiff;h=48ae5b2a99157ce1baec3cdb74e34ada060afc9d") that I believe has caused the problem. I shall have to wait for my next days off before filing a bug report... The relevant sdl FAQ is [here]("http://www.libsdl.org/faq.php?action=listentries&category=2#19").

Andrew

---

### Post by mc4man on 2010-04-30
> I have found..
That is the change - I do remember finding 4 of the 5 area's mentioned  to edit, (the darwin area seemed irrelevant here), I know I did initally change the includes and SDL_IMAGE=, (seemed logical), though wasn't sure if they actually mattered

(at least not for the configure - may have been needed for the build though. - the plugin was built successfully

At least here I also found that *by default sdl was detected fine*, and for sdl_image that I needed to edit the configure script as noted above - configure.ac alone didn't get it done..

(would be interesting if you were to just revert the commit you found and see how the configure goes

My impression was that since vlc isn't designed just for 1 distro, platform, whatnot, that the change was probably the best 'overall' solution on their part.

---

### Post by andrew.46 on 2010-05-01
Hi mc4man,

> **mc4man said:**
> (would be interesting if you were to just revert the commit you found and see how the configure goes

Well I have added some details to remove the problem commit and this compiles and runs well + finds SDL_image.h well enough. I did not delve into reverting with git as I am not so sure how well this will work with a local copy only, and git makes my head spin a little :). I will pretty the patch up a little on my days off...

Andrew

---

### Post by mc4man on 2010-05-01
> git makes my head spin a little
Personally I'm lost in how to get a specific git other than search out a shortlog  and dl a snapshot.

For instance last week for vlc 1.0.6 I wanted to match up with an ffmpeg and x264 from early april, - the ffmpeg source was easy to aquire based on date, x264 I gave up and grabbed from the shortlog.

(did notice here that ffmpeg  from the last week or so does something funny decoding amr - the audio is off a bit.

For myself I think I'm now inclined to remove x264 from vlc ala mplayer, just don't see the use transcoding to h264 with vlc, though for some I guess it's useful

---

### Post by andrew.46 on 2010-05-01
Hi mc4man,

> **mc4man said:**
> For myself I think I'm now inclined to remove x264 from vlc ala mplayer, just don't see the use transcoding to h264 with vlc, though for some I guess it's useful

Certainly a thought I will mull over for the next week. Especially I guess as this is the *development* version of vlc and I would assume that most on these forums who build it will do so for interest and the challenge rather than to build software that will be pivotal to their computing life, thus it would be better to build a solid copy of vlc-git with only *essential* features built.... and we both know that FFmpeg does a better job with transcoding to h264 anyway :).

Andrew

---

### Post by mc4man on 2010-05-01
What you may want to test, (whether used here or just 'because') is I believe the couple of times I did remove x264 in the past that it also needed to be absent from the statically linked ffmpeg build or vlc will at some point fail during the build.

(mentioning I guess because of the 2 variations of same idea - using an ffmpeg built specifically for vlc (preferred) or using a static build that just happened to  already be installed.

---

### Post by Colt45 on 2010-05-05
Does anyone know how to use checkinstall for FFmpeg?

How would you edit "make install-libs install-headers" and use checkinstall instead?

Andrew.46's instructions
```

$ ./configure --prefix=$HOME/vlc_build/vlcdeps/usr \
              $ARCHOPTS \
              --enable-gpl \
              --enable-version3 \
              --enable-nonfree \
              --enable-postproc \
              --enable-pthreads \
              --enable-libfaac \
              --enable-libfaad \
              --enable-libmp3lame \
              --enable-libopencore-amrnb \
              --enable-libopencore-amrwb \
              --disable-ffmpeg \
              --disable-ffplay \
              --disable-ffserver \
              --disable-doc
$ make jobs=4 && make install-libs install-headers
$ make distclean

```

---

### Post by qyot27 on 2010-05-06
> **Colt45 said:**
> Does anyone know how to use checkinstall for FFmpeg?

How would you edit "make install-libs install-headers" and use checkinstall instead?

Andrew.46's instructions
```

$ ./configure --prefix=$HOME/vlc_build/vlcdeps/usr \
              $ARCHOPTS \
              --enable-gpl \
              --enable-version3 \
              --enable-nonfree \
              --enable-postproc \
              --enable-pthreads \
              --enable-libfaac \
              --enable-libfaad \
              --enable-libmp3lame \
              --enable-libopencore-amrnb \
              --enable-libopencore-amrwb \
              --disable-ffmpeg \
              --disable-ffplay \
              --disable-ffserver \
              --disable-doc
$ make jobs=4 && make install-libs install-headers
$ make distclean

```
Not with that FFmpeg.  If you want a regular FFmpeg installed to the system with package manager extras then use [FakeOutdoorsman's guide](http://ubuntuforums.org/showthread.php?t=786095).

The FFmpeg above is built *purely* to meet VLC's dependency requirements, and nothing else.  It's installed to a non-system location, meaning even 'installed', you won't be able to use it (as well you shouldn't, and couldn't, considering the interfaces are disabled).

---

### Post by andrew.46 on 2010-05-06
Hi qyot,

> **qyot27 said:**
> The FFmpeg above is built *purely* to meet VLC's dependency requirements, and nothing else.  It's installed to a non-system location, meaning even 'installed', you won't be able to use it (as well you shouldn't, and couldn't, considering the interfaces are disabled).

Exactly :). The idea is stolen from Slackware but works brilliantly on Ubuntu as it delivers a relatively new version of libavcodec and also sidesteps the morass of conflicts and dependencies that can be the Ubuntu packages of FFmpeg/libavcodec.

Andrew

---

### Post by andrew.46 on 2010-05-07
Hi,

I have removed the x264 encoding after some though, also added a screenshot to hopefully convince people that x264 is not required for h264 playback :). Anybody who is keen to get x264 encoding for vlc-git and cannot get it working themselves just ask in this thread, it is pretty easy to get going...

Andrew

---

### Post by andrew.46 on 2010-05-11
Thanks to alienBOB sdl can again be found :). On my next days off I will alter the sed syntax to match other uses of sed in the guide, I am not so keen on the '#' mark as a delimiter. I will admit that I have not seen the ampersand used to prepend text before or a variable used in this manner for grep... quite ingenious... 

**Edit:** On 2nd thoughts I have kept the '#' delimiters as of course this avoids escaping all the forward slashes. I have reversed the sdl changes at the end to keep the source clean. Altered the FFmpeg syntax a little as well so libswscale is not fetched twice.

Andrew

---

### Post by andrew.46 on 2010-05-16
In the politest thread bump: successful build today:

```

andrew@ilium:~$ **[COLOR="Red"]cvlc --version[/COLOR]**
VLC media player 1.2.0-git Twoflower (revision e161e46)
VLC version 1.2.0-git Twoflower (e161e46)
Compiled by andrew on ilium (**[COLOR="Red"]May 16 2010 15:26:21[/COLOR]**)
Compiler: gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) 
This program comes with NO WARRANTY, to the extent permitted by law.
You may redistribute it under the terms of the GNU General Public License;
see the file named COPYING for details.
Written by the VideoLAN team; see the AUTHORS file.

```

Andrew

---

### Post by andrew.46 on 2010-05-23
Yet another polite bump: a successful build today:

```

andrew@ilium:~$ **[COLOR="Red"]cvlc --version[/COLOR]**
VLC media player 1.2.0-git Twoflower (revision fc5f04d)
VLC version 1.2.0-git Twoflower (fc5f04d)
Compiled by root on ilium (**[COLOR="Red"]May 23 2010 19:33:31[/COLOR]**)
Compiler: gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) 
This program comes with NO WARRANTY, to the extent permitted by law.
You may redistribute it under the terms of the GNU General Public License;
see the file named COPYING for details.
Written by the VideoLAN team; see the AUTHORS file.

```

So far the guide seems to be consistently producing a successful build under lucid. I will admit that I am only building it in a 64 bit virtual machine as the 32 bit build was always the easier one.....

Andrew

---

### Post by Lampi on 2010-06-04
Trying to build today's vlc-git gives me the following compilation errors:

```

/usr/local/src/vlc$ grep error vlc-compile.log
../../../include/vlc_xlib.h:26: error: ‘vlc_xlib_init’ declared as an ‘inline’ variable
../../../include/vlc_xlib.h:26: error: ‘vlc_object_t’ was not declared in this scope
../../../include/vlc_xlib.h:26: error: ‘obj’ was not declared in this scope
../../../include/vlc_xlib.h:27: error: expected ‘,’ or ‘;’ before ‘{’ token
/usr/include/c++/4.4/exception:35: error: expected declaration before end of line
```
What are my options? - revert to an earlier vlc-git? Which one could be working?

---

### Post by mc4man on 2010-06-04
> What are my options?

Well you could look at your libx11 libs (Xlib.h) and see if you can adjust, or
wait for a new git that may fix
or 
grab a snapshot instead of 1.2 or 1.1 
[http://nightlies.videolan.org/build/source/?C=M;O=D](http://nightlies.videolan.org/build/source/?C=M;O=D)
or 
with the source you have - if you don't want or use skins2 then just run a make distclean and add this to your configure
--disable-skins2

That should resolve your current error

---

### Post by Lampi on 2010-06-05
> **mc4man said:**
> --disable-skins2
That should resolve your current error
Indeed it does. Don't know if I ever need skins2.

I had to use another configure switch (--disable-taglib) after that make ran through.

Thanks, mc4man!

---

### Post by Elwro on 2010-06-15
Trying to compile this on Karmic again; no luck. When building vlc, after running ./configure with the suggested options (everything seems to have gone fine), "make jobs=4" ends with the following:

```

make[6]: Leaving directory `/home/leszek/vlc_build/vlc/modules/gui/skins2'
make[5]: Leaving directory `/home/leszek/vlc_build/vlc/modules/gui/skins2'
make[5]: Entering directory `/home/leszek/vlc_build/vlc/modules/gui'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/leszek/vlc_build/vlc/modules/gui'
make[4]: Leaving directory `/home/leszek/vlc_build/vlc/modules/gui'
make[3]: Leaving directory `/home/leszek/vlc_build/vlc/modules/gui'
Making all in meta_engine
make[3]: Entering directory `/home/leszek/vlc_build/vlc/modules/meta_engine'
make  all-am
make[4]: Entering directory `/home/leszek/vlc_build/vlc/modules/meta_engine'
  CXX    libtaglib_plugin_la-taglib.lo
taglib.cpp: In function ‘void ReadMetaFromMP4(TagLib::MP4::Tag*, demux_t*, demux_meta_t*, vlc_meta_t*)’:
taglib.cpp:330: error: ‘CoverArtList’ is not a member of ‘TagLib::MP4’
taglib.cpp:330: error: expected ‘;’ before ‘list’
taglib.cpp:331: error: missing template arguments before ‘[’ token
taglib.cpp:331: error: ‘TagLib::MP4::CoverArt’ has not been declared
taglib.cpp:333: error: missing template arguments before ‘[’ token
taglib.cpp:339: error: missing template arguments before ‘[’ token
taglib.cpp:339: error: missing template arguments before ‘[’ token
make[4]: *** [libtaglib_plugin_la-taglib.lo] Error 1
make[4]: Leaving directory `/home/leszek/vlc_build/vlc/modules/meta_engine'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/leszek/vlc_build/vlc/modules/meta_engine'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/leszek/vlc_build/vlc/modules'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/leszek/vlc_build/vlc'
make: *** [all] Error 2

```
I tried twice.

Could it be because I'm not on Lucid yet?

edit: oh, I see, I'll try configuring with taglib disabled

edit2: worked like a charm. So, the guide still works under Karmic! Thanks! Running 1.2.0 now :D

---

### Post by coolnumber9 on 2010-07-12
Thanks for the tip, Elwro!

---

### Post by andrew.46 on 2010-07-14
I have gone over the guide again and corrected a few small errors, also changed FFmpeg to the release version 0.6. Compiles nicely:

```

andrew@ilium:~$ cvlc --version
VLC media player 1.2.0-git Twoflower (revision 7b337cf)
VLC version 1.2.0-git Twoflower (7b337cf)
Compiled by andrew on ilium (Jul 14 2010 19:49:13)
Compiler: gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) 
This program comes with NO WARRANTY, to the extent permitted by law.
You may redistribute it under the terms of the GNU General Public License;
see the file named COPYING for details.
Written by the VideoLAN team; see the AUTHORS file.

```

Andrew

---

### Post by mc4man on 2010-08-03
Andrew - 
Small little thing for 1.1.X (cur. 1.1.2), you may or may not find useful.

vlc has a bookmark thing that is pretty much useless, they don't get saved.
You can however, during the  course of playback of anything, create bookmarks and save them to a playlist file.
The use of that info in playlists has been disabled for quite some time (EXTVLCOPT) for browser security reasons, though quite safe in a local player.
I'd expect bookmarks to be allowed in 1.2.X at some point.

For 1.1.X (and earlier), it's a simple 1 line patch - I applied manually with tab indent

```
diff --git a/src/libvlc-module.c b/src/libvlc-module.c
index de04ee2..e786ba7 100644
--- a/src/libvlc-module.c
+++ b/src/libvlc-module.c
@@ -1855,6 +1855,7 @@ vlc_module_begin ()

         add_string( "bookmarks", NULL, NULL,
                      BOOKMARKS_TEXT, BOOKMARKS_LONGTEXT, true )
    +        change_safe ()

         set_section( N_( "Default devices") , NULL )


```
As a very simple example, opened a vid, created 2 bookmarks (@28 and 51 sec.'s) and saved to a .m3u
Then when opening the playlist in vlc the bookmaks are added.

> #EXTM3U
#EXTINF:367,AMV - MIX - Studio Ghibli - Memories Dance [Vlad G Pohnert].avi
[COLOR="Blue"]#EXTVLCOPT:bookmarks={name=AMV - MIX - Studio Ghibli - Memories Dance [Vlad G Pohnert].avi0,bytes=7808458,time=28}[/COLOR]
#EXTVLCOPT:bookmarks={name=AMV - MIX - Studio Ghibli - Memories Dance [Vlad G Pohnert].avi0,bytes=7808458,time=28},{name=AMV - MIX - Studio Ghibli - Memories Dance [Vlad G Pohnert].avi1,bytes=14510026,time=51}
file:///home/doug/Desktop/AMV%20-%20MIX%20-%20Studio%20Ghibli%20-%20Memories%20Dance%20%5BVlad%20G%20Pohnert%5D.avi

Edit:
when done with playback and playlist is saved I'd go in and delete all excess lines, in this case with 2 bookmarks - the line in blue - doesn't really matter one way or the other

---

### Post by andrew.46 on 2010-08-03
Hi mc4man,

Thanks for that! I have temporarily lost access to the 64 bit computer that I was running this guide from but I shall certainly patch it in when I regain access in a week or 2...

Andrew

---

### Post by andrew.46 on 2010-08-05
A reasonably comprehensive rewrite of this guide that uses the 'semi-automatic' approach I have used in [my MPlayer guide]("http://ubuntuforums.org/showthread.php?t=1542240"). Again the reason is to provide easier access to complex material for those not used to compiling. Successfully compiled today:

```

andrew@ilium:~$ **[COLOR="Red"]cvlc --version[/COLOR]**
VLC media player 1.2.0-git Twoflower (revision 830905f)
VLC version 1.2.0-git Twoflower (830905f)
Compiled by andrew on ilium (Aug  5 2010 17:15:19)
Compiler: gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) 
This program comes with NO WARRANTY, to the extent permitted by law.
You may redistribute it under the terms of the GNU General Public License;
see the file named COPYING for details.
Written by the VideoLAN team; see the AUTHORS file.

```

I am hoping that this will give new life to a guide that has had a relatively small following so far.

**Edit:** vlc compilation fails against libavcodec with libvpx on a 64 bit system, fPIC errors. Has anybody succeeded with this? Alternative is to bump FFmpeg version so natuve decoder is available...

**Edit again!!** Woo hooo!! Success is mine.... I have managed to get a 64 bit libvpx + FFmpeg 0.6 + vlc-git running. I shall write this up in the morning but screenshot attached for the moment...

Andrew

---

### Post by andrew.46 on 2010-08-08
Hi,

I have managed to get the 64 bit build of vlc-git working with a libvpx-enabled FFmpeg 0.6 but only with a fairly ugly workaround (patching the source and removing the 64 bit optimisations). I would be *very* interested to hear if any 64 bit users have found a better way of doing this?

Andrew

---

### Post by mc4man on 2010-08-08
> have found a better way of doing this?

Don't have a current 64 bit install but on live lucid cd - simply built libvpx as shared (--enable-shared --enable-pic

Works fine as far as decoding, didn't try transcoding
(used the how-to as is with obvious changes to libvpx instr. and slightly edited vlc config.

While possibly not needed made this edit to libvpx source, the configure script, before building it
removed these lines - blue, 408 - 413, backspaced empty line after
```
process_detect() {
    [COLOR="Blue"]if enabled shared; then
        # Can only build shared libs on a subset of platforms. Doing this check
        # here rather than at option parse time because the target auto-detect
        # magic happens after the command line has been parsed.
	enabled linux || die "--enable-shared only supported on ELF for now"
    fi[/COLOR]
    if [ -z "$CC" ]; then
        echo "Bypassing toolchain for environment detection."
```

Another consideration for lucid and certainly maverick would be to use the readily available libvpx packages - in maverick libvpx0 is a dep of gstreamer and libavcodec52

(small note - sdl and sdl_image are configuring fine in lucid and maverick as is.


Edit: the libvpx config 

> ubuntu@ubuntu:~/vlc_build/libvpx-0.9.1$ ./configure --enable-shared --enable-pic
Configuring selected codecs
  enabling vp8_encoder
  enabling vp8_decoder
Configuring for target 'x86_64-linux-gcc'
  enabling x86_64
  enabling runtime_cpu_detect
  enabling mmx
  enabling sse
  enabling sse2
  enabling sse3
  enabling ssse3
  enabling postproc
Creating makefiles for x86_64-linux-gcc libs
Creating makefiles for x86_64-linux-gcc examples
Creating makefiles for x86_64-linux-gcc docs


---

### Post by qyot27 on 2010-08-08
I've been unable to compile VLMC with the 1.2.x branch instructions that were posted in May (although the current state of instructions seem fairly close to those).  The errors complain about EffectsEngine stuff.

The log is below:
```
qyot27@ubuntu-desktop:~/vlmc$ cmake .
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
Setting build type to 'Debug'
-- Found LibVLC include-dir path: /usr/local/include
-- Found LibVLC library path:/usr/local/lib/libvlc.so
-- Found LibVLCcore library path:/usr/local/lib/libvlccore.so
-- Looking for Q_WS_X11
-- Looking for Q_WS_X11 - found
-- Looking for Q_WS_WIN
-- Looking for Q_WS_WIN - not found.
-- Looking for Q_WS_QWS
-- Looking for Q_WS_QWS - not found.
-- Looking for Q_WS_MAC
-- Looking for Q_WS_MAC - not found.
-- Found Qt-Version 4.6.2 (using /usr/bin/qmake-qt4)
-- Looking for _POSIX_TIMERS
-- Looking for _POSIX_TIMERS - found
-- Found rpmbuild : /usr/bin/rpmbuild
-- Found dpkg-deb : /usr/bin/dpkg-deb
-- Configuring done
-- Generating done
-- Build files have been written to: /home/qyot27/vlmc
qyot27@ubuntu-desktop:~/vlmc$ make
Scanning dependencies of target translations
[  0%] Generating vlmc_zh_CN.qm
[  0%] Generating vlmc_ru_RU.qm
[  0%] Generating vlmc_sv.qm
[  0%] Generating vlmc_ro_RO.qm
[  0%] Generating vlmc_pt_BR.qm
[  0%] Generating vlmc_ta_TA.qm
[  0%] Generating vlmc_cs_CZ.qm
[  0%] Generating vlmc_it_IT.qm
[  0%] Generating vlmc_gl_ES.qm
[  0%] Generating vlmc_es_ES.qm
[  0%] Generating vlmc_nl.qm
[  0%] Generating vlmc_tr_TR.qm
[  0%] Generating vlmc_uk_UA.qm
[  0%] Generating vlmc_pl_PL.qm
[  0%] Generating vlmc_sk_SK.qm
[  0%] Generating template.qm
[  0%] Generating vlmc_ca_ES.qm
[  0%] Generating vlmc_fr_FR.qm
[  0%] Generating vlmc_ja_JP.qm
[  5%] Built target translations
[  6%] Generating qrc_resources-ts.cxx
[  6%] Generating EffectsEngine/moc_EffectsEngine.cxx
[  6%] Generating EffectsEngine/moc_Effect.cxx
/home/qyot27/vlmc/src/EffectsEngine/Effect.h:0: Warning: No relevant classes found. No output generated.
[  7%] Generating EffectsEngine/moc_EffectInstance.cxx
/home/qyot27/vlmc/src/EffectsEngine/EffectInstance.h:0: Warning: No relevant classes found. No output generated.
[  7%] Generating Library/moc_Library.cxx
[  7%] Generating Library/moc_MediaContainer.cxx
[  7%] Generating LibVLCpp/moc_VLCInstance.cxx
[  8%] Generating LibVLCpp/moc_VLCMediaPlayer.cxx
[  8%] Generating Media/moc_Clip.cxx
[  8%] Generating Media/moc_Media.cxx
[  9%] Generating Metadata/moc_MetaDataManager.cxx
[  9%] Generating Metadata/moc_MetaDataWorker.cxx
[  9%] Generating Project/moc_ProjectManager.cxx
[ 10%] Generating Project/moc_Workspace.cxx
[ 10%] Generating Project/moc_WorkspaceWorker.cxx
[ 10%] Generating Renderer/moc_ClipRenderer.cxx
[ 10%] Generating Renderer/moc_GenericRenderer.cxx
[ 11%] Generating Renderer/moc_WorkflowFileRenderer.cxx
[ 11%] Generating Renderer/moc_WorkflowRenderer.cxx
[ 11%] Generating Settings/moc_SettingsManager.cxx
[ 12%] Generating Settings/moc_SettingValue.cxx
[ 12%] Generating Tools/moc_ErrorHandler.cxx
/home/qyot27/vlmc/src/Tools/ErrorHandler.h:0: Warning: No relevant classes found. No output generated.
[ 12%] Generating Tools/moc_VlmcDebug.cxx
[ 13%] Generating Workflow/moc_AudioClipWorkflow.cxx
[ 13%] Generating Workflow/moc_ClipWorkflow.cxx
[ 13%] Generating Workflow/moc_ClipHelper.cxx
[ 13%] Generating Workflow/moc_ImageClipWorkflow.cxx
[ 14%] Generating Workflow/moc_MainWorkflow.cxx
[ 14%] Generating Workflow/moc_TrackHandler.cxx
[ 14%] Generating Workflow/moc_TrackWorkflow.cxx
[ 15%] Generating Workflow/moc_Types.cxx
/home/qyot27/vlmc/src/Workflow/Types.h:0: Warning: No relevant classes found. No output generated.
[ 15%] Generating Workflow/moc_VideoClipWorkflow.cxx
[ 15%] Generating Commands/moc_KeyboardShortcutHelper.cxx
[ 16%] Generating Gui/moc_About.cxx
[ 16%] Generating Gui/moc_ClickableLabel.cxx
[ 16%] Generating Gui/moc_ClipProperty.cxx
[ 17%] Generating Gui/moc_DockWidgetManager.cxx
[ 17%] Generating Gui/moc_IntroDialog.cxx
[ 17%] Generating Gui/moc_LanguageHelper.cxx
[ 17%] Generating Gui/moc_MainWindow.cxx
[ 18%] Generating Gui/moc_UndoStack.cxx
[ 18%] Generating Gui/moc_WorkflowFileRendererDialog.cxx
[ 18%] Generating Gui/effectsengine/moc_EffectsList.cxx
[ 19%] Generating Gui/effectsengine/moc_EffectsListView.cxx
[ 19%] Generating Gui/export/moc_RendererSettings.cxx
[ 19%] Generating Gui/export/moc_ShareOnYoutube.cxx
[ 20%] Generating Gui/import/moc_ImportController.cxx
[ 20%] Generating Gui/import/moc_TagWidget.cxx
[ 20%] Generating Gui/library/moc_ListViewController.cxx
[ 20%] Generating Gui/library/moc_MediaCellView.cxx
[ 21%] Generating Gui/library/moc_MediaLibrary.cxx
[ 21%] Generating Gui/library/moc_MediaListView.cxx
[ 21%] Generating Gui/library/moc_StackViewController.cxx
[ 22%] Generating Gui/library/moc_StackViewNavController.cxx
[ 22%] Generating Gui/library/moc_ViewController.cxx
[ 22%] Generating Gui/media/moc_ClipMetadataDisplayer.cxx
[ 23%] Generating Gui/media/moc_GuiMedia.cxx
[ 23%] Generating Gui/preview/moc_LCDTimecode.cxx
[ 23%] Generating Gui/preview/moc_PreviewRuler.cxx
[ 23%] Generating Gui/preview/moc_PreviewWidget.cxx
[ 24%] Generating Gui/project/moc_GuiProjectManager.cxx
[ 24%] Generating Gui/settings/moc_BoolWidget.cxx
[ 24%] Generating Gui/settings/moc_DoubleWidget.cxx
[ 25%] Generating Gui/settings/moc_ISettingsCategoryWidget.cxx
[ 25%] Generating Gui/settings/moc_IntWidget.cxx
[ 25%] Generating Gui/settings/moc_KeyboardShortcut.cxx
[ 26%] Generating Gui/settings/moc_KeyboardShortcutInput.cxx
[ 26%] Generating Gui/settings/moc_LanguageWidget.cxx
[ 26%] Generating Gui/settings/moc_Panel.cxx
[ 26%] Generating Gui/settings/moc_PathWidget.cxx
[ 27%] Generating Gui/settings/moc_PreferenceWidget.cxx
[ 27%] Generating Gui/settings/moc_Settings.cxx
[ 27%] Generating Gui/settings/moc_StringWidget.cxx
[ 28%] Generating Gui/timeline/moc_AbstractGraphicsMediaItem.cxx
[ 28%] Generating Gui/timeline/moc_GraphicsAudioItem.cxx
[ 28%] Generating Gui/timeline/moc_GraphicsCursorItem.cxx
[ 29%] Generating Gui/timeline/moc_GraphicsMovieItem.cxx
[ 29%] Generating Gui/timeline/moc_GraphicsTrack.cxx
[ 29%] Generating Gui/timeline/moc_Timeline.cxx
[ 29%] Generating Gui/timeline/moc_TracksControls.cxx
[ 30%] Generating Gui/timeline/moc_TracksRuler.cxx
[ 30%] Generating Gui/timeline/moc_TracksScene.cxx
[ 30%] Generating Gui/timeline/moc_TracksView.cxx
[ 31%] Generating Gui/widgets/moc_ElidableLabel.cxx
[ 31%] Generating Gui/widgets/moc_FramelessButton.cxx
[ 31%] Generating Gui/widgets/moc_NotificationZone.cxx
[ 32%] Generating Gui/widgets/moc_SearchLineEdit.cxx
[ 32%] Generating Gui/widgets/moc_TrackControls.cxx
[ 32%] Generating Gui/wizard/moc_GeneralPage.cxx
[ 32%] Generating Gui/wizard/moc_OpenPage.cxx
[ 33%] Generating Gui/wizard/moc_ProjectWizard.cxx
[ 33%] Generating Gui/wizard/moc_VideoPage.cxx
[ 33%] Generating Gui/wizard/moc_WelcomePage.cxx
[ 34%] Generating Media/moc_Transcoder.cxx
[ 34%] Generating Gui/widgets/moc_CrashHandler.cxx
[ 34%] Generating ui_EffectsList.h
[ 35%] Generating ui_RendererSettings.h
[ 35%] Generating ui_ShareOnYoutube.h
[ 35%] Generating ui_ImportController.h
[ 35%] Generating ui_TagWidget.h
[ 36%] Generating ui_StackViewNavController.h
[ 36%] Generating ui_MediaCellView.h
[ 36%] Generating ui_MediaLibrary.h
[ 37%] Generating ui_ClipMetadataDisplayer.h
[ 37%] Generating ui_PreviewWidget.h
[ 37%] Generating ui_About.h
[ 38%] Generating ui_ClipProperty.h
[ 38%] Generating ui_IntroDialog.h
[ 38%] Generating ui_MainWindow.h
[ 38%] Generating ui_Timeline.h
[ 39%] Generating ui_WorkflowFileRendererDialog.h
[ 39%] Generating ui_TrackControls.h
[ 39%] Generating ui_NotificationZone.h
[ 40%] Generating ui_GeneralPage.h
[ 40%] Generating ui_OpenPage.h
[ 40%] Generating ui_VideoPage.h
[ 41%] Generating ui_WelcomePage.h
[ 41%] Generating ui_CrashHandler.h
[ 41%] Generating qrc_resources.cxx
Scanning dependencies of target vlmc
[ 42%] Building CXX object src/CMakeFiles/vlmc.dir/Commands/Commands.cpp.o
[ 42%] Building CXX object src/CMakeFiles/vlmc.dir/EffectsEngine/EffectsEngine.cpp.o
In file included from /home/qyot27/vlmc/src/EffectsEngine/EffectsEngine.h:30,
                 from /home/qyot27/vlmc/src/EffectsEngine/EffectsEngine.cpp:23:
/home/qyot27/vlmc/src/EffectsEngine/Effect.h:28:27: error: frei0r/frei0r.h: No such file or directory
In file included from /home/qyot27/vlmc/src/EffectsEngine/EffectsEngine.h:30,
                 from /home/qyot27/vlmc/src/EffectsEngine/EffectsEngine.cpp:23:
/home/qyot27/vlmc/src/EffectsEngine/Effect.h:38: error: ‘F0R_PLUGIN_TYPE_FILTER’ was not declared in this scope
/home/qyot27/vlmc/src/EffectsEngine/Effect.h:39: error: ‘F0R_PLUGIN_TYPE_SOURCE’ was not declared in this scope
/home/qyot27/vlmc/src/EffectsEngine/Effect.h:40: error: ‘F0R_PLUGIN_TYPE_MIXER2’ was not declared in this scope
/home/qyot27/vlmc/src/EffectsEngine/Effect.h:41: error: ‘F0R_PLUGIN_TYPE_MIXER3’ was not declared in this scope
/home/qyot27/vlmc/src/EffectsEngine/Effect.h:46: error: ‘f0r_plugin_info_t’ has not been declared
/home/qyot27/vlmc/src/EffectsEngine/Effect.h:47: error: expected identifier before ‘*’ token
/home/qyot27/vlmc/src/EffectsEngine/Effect.h:47: error: ISO C++ forbids declaration of ‘f0r_instance_t’ with no type
/home/qyot27/vlmc/src/EffectsEngine/Effect.h:47: error: ‘f0r_instance_t’ declared as function returning a function
/home/qyot27/vlmc/src/EffectsEngine/Effect.h:48: error: ‘f0r_instance_t’ has not been declared
/home/qyot27/vlmc/src/EffectsEngine/Effect.h:49: error: ‘f0r_instance_t’ has not been declared
/home/qyot27/vlmc/src/EffectsEngine/Effect.h:73: error: ‘f0r_construct_t’ does not name a type
In file included from /home/qyot27/vlmc/src/EffectsEngine/EffectsEngine.cpp:26:
/home/qyot27/vlmc/src/EffectsEngine/EffectInstance.h:45: error: ‘f0r_instance_t’ does not name a type
make[2]: *** [src/CMakeFiles/vlmc.dir/EffectsEngine/EffectsEngine.cpp.o] Error 1
make[1]: *** [src/CMakeFiles/vlmc.dir/all] Error 2
make: *** [all] Error 2
qyot27@ubuntu-desktop:~/vlmc$ 
```

Hopefully there's just some option I'm missing and can adjust the build parameters to that.  I'd rather not have to regress to 1.1.x just to get VLMC to build again, although I know there may be no other choice.

---

### Post by mc4man on 2010-08-08
I guess one way to address is to clean your source, then  look for the various 
#include "frei0r/frei0r.h" 
and edit to just
#include "frei0r.h"

Effect.h
Effectinstance.h
Effect.cpp


in vlmc/src/EffectsEngine

---

### Post by andrew.46 on 2010-08-09
Hi mc4man,

Thanks for having a look at that. I built libvpx as you described on my 64 bit system and unfortunately still received relocation errors (as described in the patch I am using) that broke compilation. So for the time being I may very well remain with the slightly ugly workaround I have in place and look forward to some maturing in the libvpx code...

Andrew

---

### Post by andrew.46 on 2010-08-09
Hi qyot,

> **qyot27 said:**
> I've been unable to compile VLMC 

I have the same error, perhaps wait a day or so or have a word on #vlmc?

Andrew

---

### Post by mc4man on 2010-08-09
> unfortunately still received relocation errors
Interesting - due to a possible corner case kernel issue w/ my laptop I set it back to lucid and decided to do a 64 bit install.
Experienced no issues building as described - plays vp8 fine
(tried a higher res. sample [from here]("http://erunways.com/html5/WebM_VP8_video/")
(ultimately not an issue as libvpx will be avail. by many means.

> [0x2679670] avcodec decoder debug: ffmpeg codec (Google/On2's VP8 Video) started
[0x2679670] main decoder debug: using decoder module "avcodec"


> have the same error, perhaps wait a day or so or have a word on #vlmc?
Very similar to the sdl_image thing, vlmc is expecting the frei0r header to be in /include/frei0r/, while in many cases it's loose in /include/

---

### Post by qyot27 on 2010-08-09
Part of the issue with the frei0r stuff was that I didn't realize it required apt-getting a couple other packages first, and then doing those amends suggested.

sudo apt-get install frei0r-plugins frei0r-plugins-dev


After that, VLMC built, although I did get a crash on export that I didn't get with builds from a couple months ago.  In any case, yeah, still very alpha, but in some of the parts of the interface there has been clear and visible growth.

---

### Post by andrew.46 on 2010-08-10
Hi mc4man,

> **mc4man said:**
> Interesting - due to a possible corner case kernel issue w/ my laptop I set it back to lucid and decided to do a 64 bit install.
Experienced no issues building as described - plays vp8 fine
(tried a higher res. sample [from here]("http://erunways.com/html5/WebM_VP8_video/")
(ultimately not an issue as libvpx will be avail. by many means.

It is very odd then. I shall start fresh this weekend and see if perhaps I have some problem on my system. I am severely tempted to rework the FFmpeg patch so native vp8 playback (with a later FFmpeg version) is possible and ditch the compilation of libvpx completely. Thanks as always for looking at this issue :).

Andrew

---

### Post by andrew.46 on 2010-08-11
Final solution for my obscure problem building libvpx on 64 bit Ubuntu + FFmpeg and linking to vlc-git: I have admitted failure and added in the GStreamer Developers PPA and installed libvpx from there. This has worked without problem on my 64 bit Lucid and should tide this guide over until Maverick arrives with libvpx-dev in its repository. I might consider still keeping this PPA in place though for the GStreamer packages, obviously not for vlc :). BTW it looks like the man who produced the libvpx package is the Debian maintainer for libvpx so I do not for see any problems...

I think I am finally happy that the vlc produced by this guide is a decent, solid build although I shall continue to tinker with it of course!

Andrew

---

### Post by Henrikx on 2010-08-11
THX for this HowTo!!!

[[IMG]http://img199.imageshack.us/img199/4897/html5videovp8webmvlcmed.th.jpg[/IMG]]("http://img199.imageshack.us/i/html5videovp8webmvlcmed.jpg/")

---

### Post by andrew.46 on 2010-08-11
Hi Henrikx,

> **Henrikx said:**
> THX for this HowTo!!!

My pleasure :). I have only just recently worked the kinks out of it and I have been aided not a little by a relatively long period of stability in vlc-git... I am looking forward to the movie shown in your screenshot BTW, I attach a clip of SMPlayer / MPlayer playing the same clip. Good to see how quickly WebM playback became available.

Andrew

---

### Post by Henrikx on 2010-08-12
ffmpeg build for git VLC

```
FFmpeg version SVN-r24753, Copyright (c) 2000-2010 the FFmpeg developers
  built on Aug 10 2010 08:29:53 with gcc 4.4.3
  
 configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc 

--enable-pthreads --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb 

--enable-libopencore-amrwb --enable-libtheora --enable-libvorbis [B]--enable-libvpx 
[/B] 
--enable-libxvid --enable-x11grab --enable-libdc1394 --enable-libgsm [B]--enable-libx264 
[/B] 
--enable-libspeex --enable-runtime-cpudetect --disable-vdpau
  libavutil     50.23. 0 / 50.23. 0
  libavcore      0. 3. 0 /  0. 3. 0
  libavcodec    52.84. 3 / 52.84. 3
  libavformat   52.78. 1 / 52.78. 1
  libavdevice   52. 2. 1 / 52. 2. 1
  libavfilter    1.31. 0 /  1.31. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0

```For the mozilla  plugin, which settings need. 
How do I create the mozilla plugin.
```
/vlc_build/vlc$ ./configure --help
``````
 --with-wine-sdk-path=PATH path to wine sdk
  --enable-mozilla        build a vlc-based Firefox/Mozilla plugin (default
                          disabled)
  --with-mozilla-sdk-path=PATH path to mozilla sdk
  --with-mozilla-pkg=PKG  look for PKG.pc to build the mozilla plugin.

```

---

### Post by andrew.46 on 2010-08-12
Hi Henrikx,

Many possibilities for FFmpeg when compiling vlc-git, I presume you are compiling against your system FFmpeg? I am a little locked-in with this guide as there are a few problems with the 64 bit installation and the required libavcodec.

About the plugin I am not sure as I have never built it I'm afraid. Should just be a matter of finding the dependencies I imagine and compiling with the options you have mentioned. Not sure about the correct method of naming the package though.

Andrew

---

### Post by mc4man on 2010-08-12
> For the mozilla plugin, which settings need. 

I've never built the plugin in a single package build - the obvious reason being if it worked there would be no clean way to disable.
I find all the browser plugins to be a bit 'finicky', the option to switch from one to the other is useful. 
(that would be one of the advantages of a package set build

I'd try this and see
```
--enable-mozilla --with-mozilla-pkg=libxul

```
Make sure xulrunner-dev is installed and remove your current browser plugin if one is installed

Edit 
you'd want to see this after the configure
libvlc configuration
--------------------
version               : 1.1.2
system                : linux
architecture          : i686 mmx sse sse2
build flavour         : 
vlc aliases           : cvlc rvlc svlc qvlc
[COLOR="Blue"]plugins/bindings      : mozilla[/COLOR]

Re-edit - I'd think your biggest issue would to not building the plugin but having it found and used.
If you take a look at how the package version of the plugin is installed you'll see - 
install
usr/lib/mozilla[COLOR="Silver"]/plugins[/COLOR]

[COLOR="Blue"]links[/COLOR]
/usr/share/doc/vlc /usr/share/doc/mozilla-plugin-vlc
/usr/share/bug/vlc /usr/share/bug/mozilla-plugin-vlc
/usr/lib/mozilla/plugins/libvlcplugin.so /usr/lib/mozilla-firefox/plugins/libvlcplugin.so
/usr/lib/mozilla/plugins/libvlcplugin.so /usr/lib/xulrunner-addons/plugins/libvlcplugin.so

---

### Post by Henrikx on 2010-08-12
THX! THX! THX!

I copied plugins /usr/local/lib/mozilla/plugins to 
/home/**/.mozilla/plugins and everything works!!

```
--with-live555-tree=/home/**/Entwicklung/vlc_build/live \
            --enable-real \
            --enable-realrtsp \
            --enable-aa \
            --enable-snapshot \
            --enable-merge-ffmpeg \
            --enable-mozilla \
            --with-mozilla-pkg=libxul \
            --enable-x264 && \
```[[IMG]http://img341.imageshack.us/img341/410/addons003.th.jpg[/IMG]]("http://img341.imageshack.us/i/addons003.jpg/")

---

### Post by andrew.46 on 2010-08-14
I have spent a bit of time setting up vlc-git on my 'other' linux distro and I will admit that I installed it with my old favourite goom, screenshot attached. Is anybody really interested in seeing goom with their vlc-git? The new kid on the block project-m does not run on my system :(.

Andrew

---

### Post by mc4man on 2010-08-14
Ok - ron999

To try a slimmed down version of this how-to on karmic
(32bit, w/ previous static ffmpeg and x264 builds, enabling dmo loader, ect.

Assuming you have a recent static ffmpeg and x264 builds from FO's guide we'll dispense with doing vlc specific builds as Andrew shows.

Small note on that - I think ulltimately you should aquaint yourself with this guides method of using static linking.
There are advantahes - the least of which is there is no guarantee a current svn of x264 and ffmpeg will work with a previous vlc release.

By using this guide's method, if need be you can specify the ffmpeg, swscale and x264 -r's.

Anyway atm no issue.


So open a terminal and if you haven't done so max out the scrollback - may prove useful 
(edit - profile preferences - scrolling - there is a limit in karmic  so 3500 should do.

Then 
install the build deps on page 1 if not already done so and remove any vlc packages that are installed completely. (removing vlc-data will remove all.
Make sure no ffmpeg dev packages are installed - libavcodec-dev, libavformat-dev, ect. - search ffmpeg in synaptic and scroll down to see - Obviously leave your ffmpeg checkinstall package alone..

```
mkdir -p ~/vlc_build/ && cd vlc_build
```
```
wget http://sourceforge.net/projects/vlc/files/1.1.2/vlc-1.1.2.tar.bz2/download

```
```
tar -xvjf vlc-1.1.2.tar.bz2 && cd  vlc-1.1.2

```

Blue is optional
```
./configure --enable-real --enable-realrtsp  --enable-snapshot \
--enable-merge-ffmpeg  --enable-loader  [COLOR="Blue"]--with-tuning=native[/COLOR]

```

Scroll back after the configure and look for any warning, ect -  there will be some that don't matter at all - if it seems important to you then post

```
make
```

If all goes well then 
```
sudo checkinstall --pakdir "$HOME/vlc_build" --backup=no --deldoc=yes \
                  --pkgname vlc --pkgversion "1.1.2-`date +%Y%m%d`" \
                  --deldesc=yes --delspec=yes --default && \
make distclean && sudo ldconfig
```

If the build goes well and installs then run vlc -vv in terminal, close vlc and scrollback and look for any error line about failure to load a .so

If the build fails, no matter - post the error and about 20 lines previous from terminal

If you have any icon issues also post

---

### Post by ron999 on 2010-08-14
> install the build deps on page 1 if not already done

What does this mean?

---

### Post by mc4man on 2010-08-14
page 1 of this guide - I'll copy here, run both even though the first set may be redundant
At some point review page 1

```
sudo apt-get install build-essential subversion git-core checkinstall automake yasm

```
```
sudo apt-get install libqt4-dev libhal-dev lua5.1 liblua5.1-0-dev libdvdread-dev \
libtag1-dev libmad0-dev libdvbpsi5-dev liba52-0.7.4-dev libv4l-dev libcdio-dev \
libvcdinfo-dev libfribidi-dev libfluidsynth-dev libmpeg2-4-dev libschroedinger-dev \
libvorbis-dev libspeex-dev libgcrypt11-dev libcddb2-dev libproxy-dev libnotify-dev \
libebml-dev libmpcdec-dev libcaca-dev libaa1-dev libmatroska-dev xulrunner-dev \
libasound2-dev libass-dev libavahi-client-dev libdca-dev libdvdnav-dev libfaad-dev \
libflac-dev libfreetype6-dev libggi2-dev libgl1-mesa-dev libglib2.0-0 libgnutls-dev \
libid3tag0-dev libjack-dev liblircclient-dev libmodplug-dev libncursesw5-dev \
libogg-dev libpng12-dev libpulse-dev libsdl-image1.2-dev libsdl1.2-dev libshout3-dev \
libsmbclient-dev libsvga1-dev libsysfs-dev libtar-dev libtwolame-dev libudev-dev \
libupnp3-dev libx11-dev libxcb-keysyms1-dev libxext-dev libxml2-dev libxpm-dev \
libxt-dev libxv-dev libxcb-shm0-dev libxcb-xvmc0-dev libx11-xcb-dev libsdl-image1.2-dev \
libmtp-dev libsqlite3-dev libgnomevfs2-dev librsvg2-dev libzvbi-dev libxcb-randr0-dev \
liboggkate-dev libkate-dev libpango1.0-dev libcairo2-dev qt4-qtconfig

```

---

### Post by ron999 on 2010-08-14
OK
I've entered 'make'.
Watch this space.:)

---

### Post by ron999 on 2010-08-14
It's failed.:(

```
CXX    dialogs/libqt4_plugin_la-errors.lo
  CXX    dialogs/libqt4_plugin_la-external.lo
  CXX    dialogs/libqt4_plugin_la-plugins.lo
  CXX    dialogs/libqt4_plugin_la-sout.lo
  CXX    dialogs/libqt4_plugin_la-convert.lo
  CXX    dialogs/libqt4_plugin_la-help.lo
  CXX    dialogs/libqt4_plugin_la-gototime.lo
  CXX    dialogs/libqt4_plugin_la-toolbar.lo
  CXX    dialogs/libqt4_plugin_la-open.lo
  CXX    dialogs/libqt4_plugin_la-openurl.lo
  CXX    dialogs/libqt4_plugin_la-vlm.lo
  CXX    dialogs/libqt4_plugin_la-firstrun.lo
  CXX    dialogs/libqt4_plugin_la-podcast_configuration.lo
  CXX    dialogs/libqt4_plugin_la-extensions.lo
  CXX    components/libqt4_plugin_la-extended_panels.lo
  CXX    components/libqt4_plugin_la-info_panels.lo
  CXX    components/libqt4_plugin_la-preferences_widgets.lo
  CXX    components/libqt4_plugin_la-complete_preferences.lo
  CXX    components/libqt4_plugin_la-simple_preferences.lo
  CXX    components/libqt4_plugin_la-open_panels.lo
g++-4.4.real: Internal error: Segmentation fault (program as)
Please submit a full bug report.
See <file:///usr/share/doc/gcc-4.4/README.Bugs> for instructions.
make[6]: *** [components/libqt4_plugin_la-open_panels.lo] Error 1
make[6]: Leaving directory `/home/ron/vlc_build/vlc-1.1.2/modules/gui/qt4'
make[5]: *** [all] Error 2
make[5]: Leaving directory `/home/ron/vlc_build/vlc-1.1.2/modules/gui/qt4'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/ron/vlc_build/vlc-1.1.2/modules/gui'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/ron/vlc_build/vlc-1.1.2/modules/gui'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/ron/vlc_build/vlc-1.1.2/modules'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ron/vlc_build/vlc-1.1.2'
make: *** [all] Error 2
ron@ubuntu:~/vlc_build/vlc-1.1.2$ 

```

---

### Post by mc4man on 2010-08-14
> g++-4.4.real: Internal error: Segmentation fault (program as)
That can happen with gcc, nothing to do with your build
(I get it every once and while in karmic and lucid - maverick  has been good so far.
Once in karmic I had it happen twice in a row - 
Also to consider - with long builds make sure your machine isn't overheating...

I know it's disappointing - just run (no need to reconfigure
```
make clean && make
```

---

### Post by ron999 on 2010-08-14
> make clean && make

ok

---

### Post by ron999 on 2010-08-14
Right, it's installed OK :popcorn:

The menu icon appeared when I re-booted.
There's a folder in my home file named **vlc_build**. Is it OK to delete it, or is it necessary to keep it?

[IMG]http://img811.imageshack.us/img811/9532/vlc112.png[/IMG]

> ron@ubuntu:~$ vlc -vv
VLC media player 1.1.2 The Luggage (revision exported)
[0x84fb154] main libvlc debug: VLC media player - 1.1.2 The Luggage
[0x84fb154] main libvlc debug: Copyright © 1996-2010 the VideoLAN team
[0x84fb154] main libvlc debug: revision exported
[0x84fb154] main libvlc debug: configured with ./configure  '--enable-real' '--enable-realrtsp' '--enable-snapshot' '--enable-merge-ffmpeg' '--enable-loader'


---

### Post by mc4man on 2010-08-14
> There's a folder in my home file named vlc_build. Is it OK to delete it, or is it necessary to keep it?
You can delete or leave - if deleting then move your vlc .deb out somewhere else

You could also just delete the vlc-1.1.2 folder and keep the archive in case you want to extract and rebuild at some point

Small note on the dmo loader
At this point ffmpeg has taken over decoding for many of the codecs that previously required w32codecs.

One of the exceptions is wmal (lossless

Since vlc-0.9.X, where dmo worked perfectly, the loader has been in some disrepair.

It works perfectly for me in maverick - I thought they had fixed it - trying on karmic it still seems to be a bit of hit or miss if you get sound.
(there were a few tricks to raise the likelihood of successful playback

---

### Post by ron999 on 2010-08-14
OK mc4man
I understand.
Thanks for all your help.:guitar:

---

### Post by andrew.46 on 2010-08-15
Hi ron,

> **ron999 said:**
> Right, it's installed OK :popcorn:

Congrats :). Since you have configured against the latest svn FFmpeg, the latest x264 and whatever else vlc has picked up on your system (having installed the svn MPlayer you have a reasonable compiling environment now) you should have a better and more fully-featured version than any PPA version.

Andrew

---

### Post by andrew.46 on 2010-08-16
Finally fixed compilation of libvpx / FFmpeg / vlc-git thanks to mc4man, when libvpx hopefully uses pkgconfig with a new release I will convert this to a local installation. 

Andrew

---

### Post by andrew.46 on 2010-08-22
Hmmm..... I could possibly have missed this happening but when did vlc start offering access to the Apple trailers directly from within the playlist options? Screenshot (as always) attached...

Andrew

---

### Post by ron999 on 2010-08-22
The Apple trailers don't seem to be there with my v1.1.3

The options I have in 'Internet' are:-
Podcasts
Free music charts
Freebox tv
Icecast directory
Jamendo selections

Maybe there is a way to 'enable' this Apple feature that I don't know about.

---

### Post by shantiq on 2010-08-22
thank you andrew great how to with the  1.1.3 addendum specially

may i suggest inserting a line at the section codecs

which says     install medibuntu-keyring


since that section will not work if not installed

NOT-SO-KNOWLEDGEABLE folks like myself would benefit from this additional info

 the guide is so good a ten year old could do it
ok maybe 11    :KS:KS:KS:KS:KS:KS

---

### Post by mc4man on 2010-08-22
> Maybe there is a way to 'enable' this Apple feature that I don't know about.
Atm I believe that's only for 1.2+, while some changes/fixes from the 1.2 dev make it into the 1.1.X, it's not always the case. You can make a request that it be included, it may or may not be depending on whether possible or if interest in doing so exists.

Over time I've gotten some things inc. in the ubuntu specific builds and some overall, the process ranges from straightfoward to not so, the last was this one for 1.4
[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/620290](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/620290)

If you glance thru you'll  see why I'm possibly not going to bother anymore. (not the best ex., but in the same vein

You could try to build 1.2 on karmic - you won't know till you try. All you'd need to do different is use a different source and after downloading with git - 
cd to the source folder and run 
./bootstrap
Then pickup as before with your ./configure
If it errors out then post the error and we'll see what needs to be adjusted...

---

### Post by ron999 on 2010-08-22
> **mc4man said:**
> Atm I believe that's only for 1.2+...

You could try to build 1.2 on karmic - you won't know till you try. 

Heck, I didn't know that v1.2+ existed.
I'm happy with my v1.1.3 for now.:guitar:

---

### Post by andrew.46 on 2010-08-22
Hi ron,

> **ron999 said:**
> The Apple trailers don't seem to be there with my v1.1.3

Indeed it looks like the script is in place with the release versions of 1.1.*, I had a look with vlc 1.1.1:
```

root@skamandros/home/andrew# **[COLOR="Red"]find /usr -iname 'appletrailers.luac'[/COLOR]**
/usr/lib/vlc/lua/playlist/appletrailers.luac
```

but it would not work with this version as far as I could see. Looks like full functionality is only with 1.2.0-git where it works pretty well on my system. This will probably be a highly popular feature with vlc I suspect when 1.2.0 Twoflower is released...

Andrew

---

### Post by andrew.46 on 2010-08-22
Hi shantiq,

> **shantiq said:**
> thank you andrew great how to with the  1.1.3 addendum specially

My pleasure :). It has been a great learning experience for me as I am more of an MPlayer man than vlc. The little piece on the release version may not always be there as the guide is really aimed at the development version, but I can sense the frustration of vlc users with the Korn PPA gone...

> 
may i suggest inserting a line at the section codecs

which says     install medibuntu-keyring


since that section will not work if not installed

I have not quite caught your meaning here, should I make it more obvious that the command installs an external repository?

All the best,

Andrew

---

### Post by Linuxforall on 2010-08-22
Even though I have used vlc from time to time, I have always been a mplayer man and now even more so thanks to Andrew's excellent instrucitons on making the latest, every month I just update it and stay current, via smplayer, it works like vlc running everything and anything one can throw at it, the codecs that support vdpau run without any CPU load here. :)

---

### Post by Henrikx on 2010-08-24
@andrew.46
Your update-script works perfectly, including full ffmpeg and vlc-mozilla-plugin!

Great THX!!!!!!!!!

[[IMG]http://img842.imageshack.us/img842/3601/howtobuildthedevelopmen.th.jpg[/IMG]]("http://img842.imageshack.us/i/howtobuildthedevelopmen.jpg/")

---

### Post by shantiq on 2010-08-24
> I have not quite caught your meaning here, should I make it more obvious that the command installs an external repository?

All the best,

hi Andrew no what i mean is tell users that they need medibuntu-keyring at this stage see enclosed screenshot


actually reading back your code it looks as if you ask for that there but it did not on my system and that whole section would not go through had to do it from synaptic
anyway maybe that was just me

---

### Post by andrew.46 on 2010-08-24
Hi Henrikz,

> **Henrikx said:**
> Your update-script works perfectly, including full ffmpeg and vlc-mozilla-plugin!

Great news :).

Andrew

---

### Post by andrew.46 on 2010-08-24
Hi shantiq,

> **shantiq said:**
> ...actually reading back your code it looks as if you ask for that there but it did not on my system and that whole section would not go through had to do it from synaptic
anyway maybe that was just me

Hmmm.... it does sound a little odd, I shall have a closer look at this section...

Andrew

---

### Post by mc4man on 2010-08-24
> Hmmm.... it does sound a little odd, I shall have a closer look at this section...

I don't think there is any issue with the command - there seems to be some intermittent problems with medibuntu.
I don't have it as a source, but adding it the other day to a unused lucid install to check something (using basically that same comm.) did produce some 404/500 errors - took a couple of tries till it worked

---

### Post by mc4man on 2010-08-28
> I am even more wary of PPAs these days after reading the various reports of breakages on these forums. It would be nice to have some sort of 'Rating' system in place for PPAs but who would police this?

I've seen mention of something in the future concerning that, haven't keep up.

Myself rarely use (none on 10.10 atm), though do test once and a while

As far as the daily 1.2 for 10.10, I'd consider it trustworthy solely on whose ppa it is and [whose involved]("https://launchpad.net/~videolan")
Same for the ppa in my sig - maintained by [Sebastian Dröge]("https://launchpad.net/~slomo") who also packages some ubuntu gstreamer stuff among other ubuntu related activities.


For http caching take a look in tools - prefs - show all - input/codecs - access modules

> have a look at the 'Audio' preferences in 'Simple' view...
That it does, though not in the all view

> Although 1.1.4 does not do that much for Linux I guess
May try that over the wk. end - did get the bookmarks thing included, I guess if anyone was inclined they could pose a ? about why the appletrailers script isn't usable in 1.1.X over at videolan

---

### Post by andrew.46 on 2010-08-28
Hi mc4man,

> **mc4man said:**
> For http caching take a look in tools - prefs - show all - input/codecs - access modules

There it is :). Thanks!

Andrew

---

### Post by andrew.46 on 2010-08-29
I have updated the 'release version' section of the guide to build vlc 1.1.4. Builds and runs on my system without any issues....

Andrew

---

### Post by Linuxforall on 2010-08-29
Andrew, as usual, I am tempted to go ahead and install vlc even though mplayer with your directions work like a charm here, question is I already have ffmpeg and x264 installed via FO's guide, would them be picked up by vlc?

---

### Post by andrew.46 on 2010-08-30
Hi Linuxforall,

> **Linuxforall said:**
> Andrew, as usual, I am tempted to go ahead and install vlc even though mplayer with your directions work like a charm here, question is I already have ffmpeg and x264 installed via FO's guide, would them be picked up by vlc?

You can certainly use the system libraries that you already have installed, I run vlc-git on my *other* distro in exactly this way with no great problems. You may however run into problems if you are using *64 bit* Ubuntu as vlc is a little fussy about the way in which x264, FFmpeg and Live555 are compiled on such systems.

An alternative is to strictly follow the guide and you will find that there are less potential system conflicts with Live555, x264 and FFmpeg sequestered in $HOME.

All the best,

Andrew

---

### Post by Linuxforall on 2010-08-30
> **andrew.46 said:**
> Hi Linuxforall,



You can certainly use the system libraries that you already have installed, I run vlc-git on my *other* distro in exactly this way with no great problems. You may however run into problems if you are using *64 bit* Ubuntu as vlc is a little fussy about the way in which x264, FFmpeg and Live555 are compiled on such systems.

An alternative is to strictly follow the guide and you will find that there are less potential system conflicts with Live555, x264 and FFmpeg sequestered in $HOME.

All the best,

Andrew


Thanks again Andrew, will stick to mplayer for now as I already have the ffmpeg and x264 installed via checkinstall to /usr/bin/local via FO's method.

---

### Post by andrew.46 on 2010-08-31
Hi linuxforall,

> **Linuxforall said:**
> Thanks again Andrew, will stick to mplayer for now as I already have the ffmpeg and x264 installed via checkinstall to /usr/bin/local via FO's method.

You can have both of course :).

Andrew

---

### Post by andrew.46 on 2010-09-02
After having briefly lost access to the 64bit machine that I write this guide from my wife has again granted me access :). So I get to test the guide from a fresh installation of Lucid Lynx which is always the best way to find bugs. Some might be interested to know the setup I run this from:

[LIST=1]
[*]AMD Athlon x4 630 Processor 2.80 ghz 4 gigs RAM, Windows 7.
[*]Virtualbox PUEL 2.6.3 allocating 2 gigs RAM + 3 processors to Lucid VM.
[*]1500 /256 ADSL 1 connection.
[/LIST]

I might mention that I built this computer from scratch and presented it to my wife as a gift :). Anyway the main point is that on this platform and with this comparatively modest Internet connection this particular guide installed *very* smoothly and took a total of 45 minutes, although slow times from the vlc git repository was responsible for some of this time.

I place this here as a little benchmark of the typical time taken to build the initial copy if vlc from the beginning, no doubt faster computers running without a VM and a decent internet connection could shave this time in half...

Andrew

---

### Post by andrew.46 on 2010-09-05
Hi,

Some might be interested to know that the development vlc at least plays youtube clips quite nicely. Not sure when this became available, certainly not possible with MPlayer. Only noticed this while building todays git:

```

andrew@skamandros~$ cvlc --version 
VLC media player 1.2.0-git Twoflower (revision 6232433)
VLC version 1.2.0-git Twoflower (6232433)
Compiled by root on skamandros.andrews-corner.org (Sep  4 2010 13:13:19)
Compiler: gcc version 4.4.4 (GCC) 
This program comes with NO WARRANTY, to the extent permitted by law.
You may redistribute it under the terms of the GNU General Public License;
see the file named COPYING for details.
Written by the VideoLAN team; see the AUTHORS file.

```

Andrew

---

### Post by mc4man on 2010-09-06
> plays youtube clips quite nicely. Not sure when this became available
I remember this for a while, but has improved quite a bit.
Formerly if you gave vlc a url to a higher quality vid it would always be switched to the lowest avail.
Now it seems to playback all 'as is' and much better than flash..

---

### Post by shantiq on 2010-09-06
nice trick

and then of course you can capture a higher quality image copy than say you would with video downloadhelper

use hotkeys for capture then it is  real child's play


i set it to f2   and f1 for snapshots


also tried it on HD videos but the capture only yielded audio no picture   i guess that is probably as my computer is not HD ready  would love to know if any of you can capture HD successfully (image and sound)

i ended up with 104 kbps on a normal vid on the audio side and 125kbps on  the HD capture

===============================================
a few simple steps

   Open the youtube page you want to get the vid from
 
 
   Copy url from the url box at top of the youtube page and open media/open capture stream in your VLC
paste the url address
 
now you see your vid playing
 
 
   To capture  set your hotkey for capture   go tools/preferences/hotkeys
 
scroll down to where it says record and see what the hotkey is   you can set it to your key of choice i use F2
 
and F1 for snapshots    save your changes
 
 
  now kid's play start your vid click F2 or whatever you have set it to   and then click again at the end of vid
 
 
your vid is now in you video folder/    snapshots go to images

---

### Post by shantiq on 2010-09-06
as ron (thank you !)pointed there is a quicker route

With VLC click on 'View' and tick 'Advanced Controls'.
This puts extra buttons on the GUI.
Red button is for record.
Camera button is for snapshot.


Also use Media > 'Open location from clipboard' instead of paste URL.

---

### Post by andrew.46 on 2010-09-06
Hi shantiq,

> **shantiq said:**
> 

With VLC click on 'View' and tick 'Advanced Controls'.
This puts extra buttons on the GUI.
Red button is for record.
Camera button is for snapshot.


Thanks for that tip, vlc was failing on my system using the Convert/Save options :). I will admit that deep down I am a commandline sort of guy and for saving such files as I am legally entitled to do so from youtube I always use youtube-dl.

Andrew

---

### Post by shantiq on 2010-09-06
had never heard of youtube-dl    thanx


i usually use [https://addons.mozilla.org/en-US/firefox/addon/3006/](https://addons.mozilla.org/en-US/firefox/addon/3006/)

since it allows one to convert to mp3

but going the vlc route seems wiser for vids as the image is better it seems

_video  downloadhelper_


when vid playing see image attached   go on coloured balls click on arrow and hover above track you want other drop down box will open choose download and convert then set to mp3   (see attached image)
only has to be set once

not sure there is a program which can do that from the command-line


hey maybe there is



ok tried youtube-dl 


```
sudo aptitude install youtube-dl

```

 was not very fast i do not think or maybe that was just me on the day

anyway found you had to add -t to get the title

```
youtube-dl -t -f 35  url
```

the -f stands for youtube formats code 35 is for a 480 vid see chart==> (2nd attached)

so thank you a handy tool

---

### Post by qyot27 on 2010-09-06
> **shantiq said:**
>  was not very fast i do not think or maybe that was just me on the day

anyway found you had to add -t to get the title

```
youtube-dl -t -f 35  url
```

the -f stands for youtube formats code 35 is for a 480 vid see chart==> (2nd attached)

so thank you a handy tool
Actually, the better options are

youtube-dl.py -l --max-quality=FORMAT -w [url]

Which will grab whatever the highest tier copy of the file exists, with the 'literal' name (it preserves spaces and stuff like symbols and CJK characters/punctuation), and no overwrites.

For those options you need the newest version, though:
http://bitbucket.org/rg3/youtube-dl/wiki/Home

Just give it execution permission and copy it to /usr/bin to make it work.

---

### Post by andrew.46 on 2010-09-06
Hi qyot,

> **qyot27 said:**
> Actually, the better options are

youtube-dl.py -l --max-quality=FORMAT -w [url]

Which will grab whatever the highest tier copy of the file exists, with the 'literal' name (it preserves spaces and stuff like symbols and CJK characters/punctuation), and no overwrites.

I use something similar:

```
youtube-dl -o '%(stitle)s.%(ext)s' -w '[url]'
```

which has only 2 differences: by default the newest youtube-dl will attempt to download the highest quality video available which these days seems to be decent quality aac sound and good quality h264 video in a flv container (what happened to mp4?). So I do not regret the loss of the *-b* option or personally feel the need for the *--max-quality* setting. Also I use '%(stitle)s' which strips out the spaces in the filenames amongst other things.

Great little script though and the developer keeps it regularly updated...

Andrew

---

### Post by qyot27 on 2010-09-06
> **andrew.46 said:**
> I use something similar:

```
youtube-dl -o '%(stitle)s.%(ext)s' -w '[url]'
```

which has only 2 differences: by default the newest youtube-dl will attempt to download the highest quality video available which these days seems to be decent quality aac sound and good quality h264 video in a flv container (what happened to mp4?). So I do not regret the loss of the *-b* option or personally feel the need for the *--max-quality* setting. Also I use '%(stitle)s' which strips out the spaces in the filenames amongst other things.
I still regularly get .mp4 files, so I'm not sure.  I still use the --max-quality param out of paranoia, since I can't seem to find any reference that it now defaults to that automatically (and doing so just alleviates the doubt that it might not be).  When using --max-quality=FORMAT (where FORMAT actually is the word FORMAT, not FLV/MP4/WebM), I keep getting a mixture of MP4 and FLV files.

The difference, it seems, is in the resolution.  FLV container use seems to be restricted to 480p and under, whereas virtually all the 720p videos I've snagged have been in MP4 (360p is a random mixture of the two).

I also still regularly come across VP6/MP3-encoded FLV files, so I think it's just that they don't do anything about resynchronizing all their content to new format standards when they adopt them (whether it'll happen when the transition to VP8/Vorbis/MKV is rolled out properly, I don't know).


Not quite striking everything I just said, here's a chart that breaks it down:
[http://en.wikipedia.org/wiki/YouTube#Quality_and_codecs](http://en.wikipedia.org/wiki/YouTube#Quality_and_codecs)

Basically, MP4 is used for 'Medium', 720p, 1080p, and the utterly useless* 4K option they put in a month or two ago.  'Medium' has some overlap with the FLV formats (of which 360p and 480p use H.264+AAC in FLV).  The chart isn't entirely correct, though, as like I said, I still encounter VP6/MP3 encoded stuff at SD resolutions, and I would think that H.263 would show up as H.263 in MediaInfo, not VP6.  Unless of course those VP6 videos are coming from Nico Nico Douga (courtesy of, shock, nicovideo-dl) and not YouTube.  Whatever.


*Note, I'm not calling 4K useless.  I'm calling 4K on YouTube useless.  Especially as the test clips I've seen were just upscaled, and rather badly.

---

### Post by shantiq on 2010-09-07
> well qyot27  if you do not have HD on your machine that trick

```
youtube-dl.py -l --max-quality=FORMAT -w [url]

```

 is not helpful since you end up with a 1080 or a 720 which will stutter.   That is why i gave the other info instead. 480 360 still the highest many people can handle ( my machine is 4 years old )

But thanx probably good for people who have HD


> The difference, it seems, is in the resolution. FLV container use seems to be restricted to 480p and under, whereas virtually all the 720p videos I've snagged have been in MP4 (360p is a random mixture of the two).

and maybe this is where using VLC capture/record is also good i have saved 2 480 and one 720 just to test and they both came out as mp4 which in my experience are always clearer than flv

---

### Post by qyot27 on 2010-09-07
> **shantiq said:**
> well qyot27  if you do not have HD on your machine that trick

```
youtube-dl.py -l --max-quality=FORMAT -w [url]

```

 is not helpful since you end up with a 1080 or a 720 which will stutter.   That is why i gave the other info instead. 480 360 still the highest many people can handle ( my machine is 4 years old )
And mine is 9 years old.  But practically every video that I grab gets converted to DVD-spec MPEG-2, so it doesn't matter what it originally was. I just automatically go for the highest quality copy I can on principle, as I can control the quality level of the converted MPEG-2s better that way.

---

### Post by shantiq on 2010-09-07
> **qyot27 said:**
> And mine is 9 years old.  But practically every video that I grab gets converted to DVD-spec MPEG-2, so it doesn't matter what it originally was. I just automatically go for the highest quality copy I can on principle, as I can control the quality level of the converted MPEG-2s better that way.


YES i suppose you can always scale down after the grab
For my own purposes heading for a format i can handle is probably best


I would still take your route if i wanted to extract the audio
as there indeed i want the highest they can provide which on an HD copy seems to be 125kbps

---

### Post by Elwro on 2010-09-07
> **andrew.46 said:**
> Hi,

Some might be interested to know that the development vlc at least plays youtube clips quite nicely. Not sure when this became available, certainly not possible with MPlayer. Only noticed this while building todays git:

```

andrew@skamandros~$ cvlc --version 
VLC media player 1.2.0-git Twoflower (revision 6232433)
VLC version 1.2.0-git Twoflower (6232433)
Compiled by root on skamandros.andrews-corner.org (Sep  4 2010 13:13:19)
Compiler: gcc version 4.4.4 (GCC) 
This program comes with NO WARRANTY, to the extent permitted by law.
You may redistribute it under the terms of the GNU General Public License;
see the file named COPYING for details.
Written by the VideoLAN team; see the AUTHORS file.

```

Andrew
Renee Fleming? Classy :D

Thanks for the info!

---

### Post by andrew.46 on 2010-09-07
Hi Elwro,

> **Elwro said:**
> Renee Fleming? Classy :D

Indeed! She is singing the 4 last Songs of Strauss and the special bonus of this particular clip is the slumbering flautist from the 30 second mark to about the 55 second mark :).

Andrew

---

### Post by andrew.46 on 2010-09-17
Hi,

I have started building vlc-git under Maverick and the good news is that the guide needs very little change. Having libvpx-dev available from the Ubuntu repository eliminates some compiling which is always a plus :).

The bad news is that although vlc-git compiles and runs fine from the source the actual *installation* under checkinstall is consistently failing  on my 64 bit system with the following error message:

```

make[5]: Entering directory `/home/andrew/vlc_build/vlc/modules'
if test -z "" -a "x86_64-unknown-linux-gnu" = "x86_64-unknown-linux-gnu"; then \
		../bin/vlc-cache-gen "/usr/local/lib/vlc/plugins" ; \
	else \
		echo "Staged installation: cache generation skipped!" ; \
	fi
[0xdc7380] main libvlc error: No modules were found, refusing to start. Check that you properly gave a module path with --plugin-path.
No plugins in /usr/local/lib/vlc/plugins
make[5]: *** [install-exec-hook] Error 1


```

I have battle with this for a while with no success, so I am keen to hear if anybody else is experiencing this problem and better if a fix has been found! Or indeed if it is a transient problem with the vlc source. In the meantime I shall battle on with this exasperating problem...

Andrew

**Edit:** I suspect a vlc problem, I have posted [here]("http://forum.videolan.org/viewtopic.php?f=13&t=82619").

---

### Post by tqft on 2010-09-17
Sorry if you have tried this:

Most obvious thing I can think of with a new distro version - paths.

Did you previously set/add to the paths?

Have the Ubuntu devs changed any default paths?

---

### Post by mc4man on 2010-09-17
Happened to do a new vlc build (10.10) earlier and saw no issues, though it was a debian package set build. (there were 2 new plugins that needed an install define but that's not your issue.

Went ahead and did a checkinstall build/install which also was fine, the main diff being on 32 bit.
So I'd think the problem may only be a 64 bit one. Now that I've fixed a hardware issue on laptop I may re-install maverick for 64 bit and take a look.

The corresponding place to your build failure shows this here
> make  install-exec-hook
make[5]: Entering directory `/home/doug/Desktop/vlc1-2-1/vlc/modules'
if test -z "" -a "i686-pc-linux-gnu" = "i686-pc-linux-gnu"; then \
		../bin/vlc-cache-gen "/usr/local/lib/vlc/plugins" ; \
	else \
		echo "Staged installation: cache generation skipped!" ; \
	fi
make[5]: Leaving directory `/home/doug/Desktop/vlc1-2-1/vlc/modules'

there may be something of interest during the build, if nothing to fix shows up from Videolan then maybe output the build to a log or in 10.10 you can set terminal profile to an 'unlimited' scrollback, then select all and copy to file.

edit:
(I'm sure you know that fstrans has been [re-enabled by default]("https://bugs.launchpad.net/ubuntu/+source/checkinstall/+bug/599163") for 10.10, don't see it being fixed, I've taken to setting preferred options in checkinstallrc

---

### Post by FakeOutdoorsman on 2010-09-17
> **andrew.46 said:**
> 
**FFmpeg...**
```
make [color=#FF0000]jobs=4[/color] && make install-libs install-headers && make distclean
```

Anyone know if there any disadvantage of using *make -j* instead of manually declaring a value?  Some benchmarks of compiling x264 in a 32-bit Karmic VM on Intel i7 860.
```
$ time make
    real	0m25.800s
$ time make -j
    real	0m9.198s
$ time make -j8
    real	0m9.060s
```

---

### Post by tqft on 2010-09-17
> **FakeOutdoorsman said:**
> Anyone know if there any disadvantage of using *make -j* instead of manually declaring a value?  Some benchmarks of compiling x264 in a 32-bit Karmic VM on Intel i7 860.
```
$ time make
    real	0m25.800s
$ time make -j
    real	0m9.198s
$ time make -j8
    real	0m9.060s
```

I think it is a control issue -if you use make -j and you are using the machine as a desktop or whatever, you may have responsive issues as the build grinds away.  If you set it yourself, you know who to blame and can make appropriate adjustments.

 -j [jobs], --jobs[=jobs]
            Specifies the number of jobs (commands) to run simultaneously.  If
            there  is  more than one -j option, the last one is effective.  If
            the -j option is given without an argument, make  will  not  limit
            the number of jobs that can run simultaneously.

---

### Post by mc4man on 2010-09-17
Well, set up a 64 bit install and vlc built and installed fine, so maybe try a new git.
> make[5]: Entering directory `/home/doug/vlc_build/vlc/modules'
if test -z "" -a "x86_64-unknown-linux-gnu" = "x86_64-unknown-linux-gnu"; then \
		../bin/vlc-cache-gen "/usr/local/lib/vlc/plugins" ; \
	else \
		echo "Staged installation: cache generation skipped!" ; \
	fi
make[5]: Leaving directory `/home/doug/vlc_build/vlc/modules'
> vlc_1.2.0-git-20100917-dea4f0a-1_amd64.deb

Small note on ffmpeg in 10.10

Went ahead and used the default shared ffmpeg libs and devs to see how it went.
While I've been using 10.10 since A1, I've always replaced the default packages with a newer, cleaner set (and libx264 & dev), so didn't notice how apparently convoluted ffmpeg is yet again in ubuntu.

Don't even want to try to understand, ect...

There are 2 libx264's available - 
85 - no dev
98 - has dev
the libavcodec extra package depends on the 85 libx264

the libswscale-dev allows the extra version except it deps on libswscale-extra-1 which doesn't exist, it's libswscale-extra-0 in the repo
Possibly more oddities.
( don't even know if there is any value to the extra version of anything but libavcodec, don't particularly care anymore.

It would appear you could use the default shared ffmpeg libs, maybe after release w/ the medibuntu ones, though the libx264 deal is a bit troubling if it matters (transcoding support in vlc

---

### Post by andrew.46 on 2010-09-17
Hi mc4man,

> **mc4man said:**
> (I'm sure you know that fstrans has been [re-enabled by default]("https://bugs.launchpad.net/ubuntu/+source/checkinstall/+bug/599163") for 10.10, don't see it being fixed, I've taken to setting preferred options in checkinstallrc

In fact I was not aware of this and setting *--fstrans=no* fixed the problem. Some small irony in being bitten by this bug that I spent some time trawling the forums to alert people to in earlier versions of Ubuntu :). Thanks for the heads up on this one!

This means the Maverick version of this guide is ready to go, I am just waiting for Medibuntu to open for business and I will place the new version.

Andrew

---

### Post by mc4man on 2010-09-17
> setting --fstrans=no fixed the problem.
I meant to test that to see if that was your exact problem but forgot, had a slight feeling because the error messages with fstrans are different than in the past where tmp was always mentioned.
> Some small irony...

There's irony all around on this one - if you read the bug report you'll see yourself mentioned (LouL post - better known as FakeO..), which lead me to the linked comment and checkinstallrc where for myself have eliminated the need for all the extra options, ect..

---

### Post by andrew.46 on 2010-09-17
Hi mc4man,

> **mc4man said:**
> There's irony all around on this one - if you read the bug report you'll see yourself mentioned (LouL post - better known as FakeO..), which lead me to the linked comment and checkinstallrc where for myself have eliminated the need for all the extra options, ect..

I remember now, I became aware of the problem from Slackware a while back when the problem first came up and checkinstall was removed from the distro and has not returned to this day. Anyway the workaround for the Maverick version of this guide will be *--fstrans=no* regardless of the outcome of the bug-report as I do not want to be caught like that again :(. The checkinstall.rc file certainly liberates you from the commandline, it is a pity there is not such a thing as $HOME/.checkinstall.rc. Otherwise little change to the guide although the instructions for building the release version will be removed as people are again flocking to the PPAs. I have added the following dev files:

```

libvpx-dev libva-dev libprojectm-dev libprojectm-qt-dev

```

and remained with a local installation of FFmpeg, goom and x264 to stay free of the quagmire of libavcodec and x264 variations of Maverick. Don't know much about vaapi but looks like FFmpeg picks up the library automagically, as does vlc and playback works with:

```
cvlc --ffmpeg-hw *filename*
```

but no doubt correct card and drivers are also required? Certainly it does not work in virtualbox and a bit of reading seems to indicate that it is not exactly the holy grail of video acceleration :).

Andrew

---

### Post by mc4man on 2010-09-18
> A bit of reading seems to indicate that it is not exactly the holy grail of video acceleration
I find vaapi to be so-so, though I'm somewhat thinking the actual hardware is a factor.

Atm there is no vaapi support in 10.10 for 64 bit, a crucial lib is mia
 and a quick install, test of it - (vdpau-va-driver), may indicate why, performance was awful though again that could be hardware dependent.
Or at least w/ nvidia which does need that driver installed.

> as people are again flocking to the PPAs

10.10 should prove to be a fairly well enabled by default though 10.04, while not as bad off as 8.04 was, is slightly left behind.
There seem to be a trend now for ppa's to backport libs for lucid, some do a good job, others obviously not.
I guess for the moment it's user beware or check out the guides for a bit of control and learning.

Well Ot
I put a 64 bit install together today w/ new ffmpeg shared libs, vlc and a 32 bit mplayer, though atm no live 555 for mplayer.
Does mplayer just need the live 555 libs just at build time or also available during use?

---

### Post by andrew.46 on 2010-09-18
Hi mc4man,

> **mc4man said:**
> I put a 64 bit install together today w/ new ffmpeg shared libs, vlc and a 32 bit mplayer, though atm no live 555 for mplayer.
Does mplayer just need the live 555 libs just at build time or also available during use?

I have to confess that I am not sure, and in fact I am not entirely clear to what degree the live555 libraries are necessary for streams under MPlayer.

Andrew

---

### Post by gupta_sumesh63 on 2010-09-18
I am a little new to ubuntu.
I am using 10.04 LTS
can I use vlc-git for lucid?
After following all the steps in your tutorial how do I run vlc?
I do not see any vlc mentioned in Applications->Sound and video.
Kindly help








































































/

---

### Post by andrew.46 on 2010-09-18
Hi gupta,

> **gupta_sumesh63 said:**
> I am a little new to ubuntu.
I am using 10.04 LTS
can I use vlc-git for lucid?
After following all the steps in your tutorial how do I run vlc?
I do not see any vlc mentioned in Applications->Sound and video.


You can indeed use vlc-git in lucid lynx but are you after the development, or 'pre-release' version of vlc, which is what this guide deals with? If you are actually after a stable version of a fine media player to simply play some dvds, video files, radio broadcasts, transcode sound and video files you would be better served by the release version available in the Ubuntu repositories. The following command will install this for you:

```
sudo apt-get install vlc
```

All the best,

Andrew

---

### Post by mc4man on 2010-09-18
> I do not see any vlc mentioned in Applications->Sound and video.
It's possible that if you've never had vlc installed that the 'built' version won't show up in the menus.
Best thing to first try is a restart, it may then show up.

If not then several ways to fix - 
you could remove the built package, install the repo one, then install the built package.
Or one could copy the vlc.desktop from /usr/local/applications to ~./local/share/applications though you may end up with 2 menu entries at some point so I'd try the 2 above first.

Was just setting up the new 10.10 so cp .desktops was on the mind -

myself usually have 3 different vlc's in menu and r. click  - 
the default VLC media player
VLC Audio Player - only plays the audio stream, saves resources
VLC Cd Player - properly autoplays audio cd's from any dvd/cd drive or r. click on icon

---

### Post by ron999 on 2010-09-18
> VLC Audio Player - only plays the audio stream, saves resources

What is VLC Audio Player mc4man?
Is it just VLC-1.1.4 built using different config options?

---

### Post by mc4man on 2010-09-18
> What is VLC Audio Player ...built using different..

No, it's simply a new .desktop.
I use it to play videos that have good sound, music ect. without wasting cpu on video

Obviously you could either extract the audio or cli vlc, I find this simpler
To ck. - assuming vlc was installed to /usr/local, otherwise change comm. to just /usr (remove blue

```
cp /usr/[COLOR="Blue"]local/[/COLOR]share/applications/vlc.desktop  ~/.local/share/applications/vlc-audio.desktop
```

```
gedit  ~/.local/share/applications/vlc-audio.desktop
```

When the .desktop opens change the line Name=VLC media player to whatever you wish, I use VLC Audio Player

Scroll down and change the line EXEC=vlc %U to either **one** of these
(I used to use the first one - more correct, but now in maverick I use the 2nd one
vlc would complain slightly if given the chance about 'null', but it provides more resource saving here - feel free to experiment

```
Exec=vlc --vout dummy %f
or
Exec=vlc --vout null %f
```

Ex. from my .desktop - clipped

> [Desktop Entry]
Version=1.0
Name=VLC Audio Player
Comment=Audio only Player
Name[bn]=VLC &#2478;&#2495;&#2465;&#2495;&#2527;&#2494; &#2474;&#2509;&#2482;&#2503;&#2527;&#2494;&#2480;
....clipped
Comment[zh_CN]=&#20026;&#24744;&#35835;&#21462;&#12289;&#25429;&#33719;&#25110;&#21457;&#36865;&#22810;&#23186;&#20307;&#27969;
Exec=vlc --vout null %f
Icon=vlc
....clipped

you'll find it in your menu and from r. click

---

### Post by gupta_sumesh63 on 2010-09-18
Thnx mc4man. I had vlc installed from repos. However I removed it thinking that built version would install and show in applications.
Can u help me by informing me as to how I remove the built ver? I'll follow the first option specified by you then.

---

### Post by ron999 on 2010-09-18
Ah
When I use it to open a video file it just plays the audio.
I understand.:)

---

### Post by mc4man on 2010-09-18
> I had vlc installed from repos. However I removed it thinking that built version would install and show in applications.
Then normally it should be showing up in your menu. 

If you want to keep the built (git) version then first make sure it runs okay. In a terminal - 
vlc

If all is well then ck. in edit menus that it simply hasn't been disabled from showing up
R. click on Applications -> edit menus, scroll down and highlight Sound & Video, look in r. side box for vlc. If there and unchecked then check the little box.

If not there then you could create a new menu item for vlc, give it a name, the command would be
```
vlc %f
```

**Or** just simply run this (assuming you followed this how-to
```
cp /usr/local/share/applications/vlc.desktop ~/.local/share/applications/
```

If you wish to remove the built vlc just search vlc in synaptic and remove

---

### Post by andrew.46 on 2010-09-21
Looks like [libbluray support]("http://git.videolan.org/?p=vlc.git;a=commit;h=8fd093d4130b4e7a5b4ca82f3934b6fdf1a10c8d") has arrived for vlc, I imagine that like MPlayer this will not deal with encryption.

Andrew

---

### Post by rudysuryanto on 2010-09-22
When I type: 
cd $HOME/vlc_build && \ git clone git://git.videolan.org/vlc.git --depth 1 && \ cd $HOME/vlc_build/vlc && ./bootstrap && \ export PKG_CONFIG_PATH="$HOME/vlc_build/vlcdeps/usr/lib/pkgconfig" && \ if [ ! "$(uname -m)" = "x86_64" ]; then  ARCHOPTS="--enable-loader" else   ARCHOPTS="" fi && \ ./configure $ARCHOPTS \             --with-live555-tree=$HOME/vlc_build/live \             --enable-real \             --enable-realrtsp \             --enable-aa \             --enable-snapshot \             --enable-merge-ffmpeg \             --enable-vcdx && \ make jobs=4 && \ sudo checkinstall --pakdir "$HOME/vlc_build" --backup=no --deldoc=yes --pkgname vlc \                   --pkgversion "1.2.0-git-$(date +%Y%m%d)-$(git show --abbrev-commit \                   | grep '^commit' | cut -f2 -d " ")" \                   --deldesc=yes --delspec=yes --default && \ make distclean && sudo ldconfig

then appear :
Initialized empty Git repository in /home/rudy/vlc_build/vlc/.git/
remote: Counting objects: 25740, done.
remote: Compressing objects: 100% (17951/17951), done.
Receiving objects:  28% (7462/25740), 29.52 MiB | 28 KiB/s  

I wait for a long time, it look like stop at 28%, what must I do to make git process continue again?
Thank's.

---

### Post by andrew.46 on 2010-09-22
Hi rudy,

> **rudysuryanto said:**
>  I wait for a long time, it look like stop at 28%, what must I do to make git process continue again?

This can take a while from my side of the world as well an unfortunately has more to do with the vagaries of the internet and speed at the remote side than anything else. I would advise trying at a different time of day and perhaps if this is your first run through this guide delete the $HOME/vlc_build/vlc folder and all of its contents and then run the command again.

Andrew

---

### Post by andrew.46 on 2010-09-23
OK well there actually seems to be a scary amount of time waiting for the git command to work:

```

andrew@skamandros~/source/vlc$ **[COLOR="Red"]time git clone git://git.videolan.org/vlc.git --depth 1[/COLOR]**
Initialized empty Git repository in /home/andrew/source/vlc/vlc/.git/
remote: Counting objects: 34708, done.
remote: Compressing objects: 100% (22498/22498), done.
remote: Total 34708 (delta 25650), reused 18360 (delta 11834)
Receiving objects: 100% (34708/34708), 89.08 MiB | 86 KiB/s, done.
Resolving deltas: 100% (25650/25650), done.

real	28m15.925s
user	0m17.421s
sys	0m6.851s
andrew@skamandros~/source/vlc$

```

One day Australia will have the National Broadband Network and hopefully this will make a difference :(.

Andrew

---

### Post by mc4man on 2010-09-23
I forget how easy broadband makes things (and it felt slow tonight

> time git clone git://git.videolan.org/vlc.git --depth 1
Initialized empty Git repository in /home/doug/Desktop/time/vlc/.git/
remote: Counting objects: 25740, done.
remote: Compressing objects: 100% (17951/17951), done.
remote: Total 25740 (delta 17921), reused 12743 (delta 7476)
Receiving objects: 100% (25740/25740), 66.42 MiB | 1.11 MiB/s, done.
Resolving deltas: 100% (17921/17921), done.

real	1m47.020s
user	0m12.469s
sys	0m3.836s


If rudysuryanto can't get the git it could be worth trying the snapshot, only around 15Mb
[http://nightlies.videolan.org/build/source/?C=M;O=D](http://nightlies.videolan.org/build/source/?C=M;O=D)
They're in tar.* (whatever that is ?), I think I used p7zip to extract last time I tried one

if so, you'd do the same except no bootstrap command used - pick back  up at the configure

---

### Post by andrew.46 on 2010-09-23
Hi mc4man,

I envy your internet speed :). I have posted a query on the vlc forums about those nightlies, looks like they were .tar.bz2 until early August and now of course .tar.* which I could not open with 7zip, tar or any other utility at my disposal. I wonder if the script that generates the files has gone haywire, or perhaps I will look as stupid as I did with my checkinstall query :(.

Andrew

---

### Post by mc4man on 2010-09-23
Be interested to know what you find on the .*
While I thought I did something different this does 'work'?

> $ 7za x /home/doug/Desktop/7p/vlc-snapshot-20100923.tar.* 

7-Zip (A) 9.04 beta  Copyright (c) 1999-2009 Igor Pavlov  2009-05-30
p7zip Version 9.04 (locale=en_US.utf8,Utf16=on,HugeFiles=on,2 CPUs)

Processing archive: /home/doug/Desktop/7p/vlc-snapshot-20100923.tar.*

Extracting  vlc-snapshot-20100923.tar

Everything is Ok

Size:       121815040
Compressed: 15431288

That produces a .tar which can be then extracted

---

### Post by andrew.46 on 2010-09-23
Hi mc4man,

> **mc4man said:**
> 
While I thought I did something different this does 'work'?
```
$ 7za x /home/doug/Desktop/7p/vlc-snapshot-20100923.tar.* 
```

That produces a .tar which can be then extracted

Indeed it does and I guess I have now posted 2 idiot questions to the vlc forums :(.

Andrew

---

### Post by mc4man on 2010-09-23
Just to clarify for any users of the snapshot - there are 2 packages in ubuntu, p7zip and p7zip-full. The command for p7zip is 7zr x 
for p7zip-full it's 7za x 

Overall the git clone should be good for most, though the snapshot is quite small and considerably faster to acquire on slow connects

---

### Post by FakeOutdoorsman on 2010-09-23
> **andrew.46 said:**
> Hi mc4man,



Indeed it does and I guess I have now posted 2 idiot questions to the vlc forums :(.

Andrew

Don't feel bad.  I've asked many questionable questions on #ffmpeg, #ffmpg-devel, and #x264.

---

### Post by qyot27 on 2010-09-23
Those .tar.* files are just LZMA2 compressed, so the * could be either 'xz' or 'lzma' - which explains why using 7za extracted it to a regular tar file (as 7zip can't actually extract to real files from tarred archives).

tar opened it fine here, although I changed the extension to .tar.xz first (I also did it under MSys because I'm not logged into Ubuntu right now, but the version of tar is 1.23).

```
tar -xJvf vlc-snapshot-20100923.tar.xz
```

---

### Post by mc4man on 2010-09-23
> although I changed the extension to .tar.xz first

I knew i had done something different (than 7zip) the first time I saw these - that's what it was..

---

### Post by andrew.46 on 2010-09-23
Hi qyot,

> **qyot27 said:**
> Those .tar.* files are just LZMA2 compressed, so the * could be either 'xz' or 'lzma' - which explains why using 7za extracted it to a regular tar file (as 7zip can't actually extract to real files from tarred archives).

tar opened it fine here, although I changed the extension to .tar.xz first (I also did it under MSys because I'm not logged into Ubuntu right now, but the version of tar is 1.23).

```
tar -xJvf vlc-snapshot-20100923.tar.xz
```

Thank you very much for pointing that out! A bit of further investigation has shown that at least under tar 1.22 renaming and indeed 7zip are *not* required as the following command does it all in one go by using lzma:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]tar --lzma -xvf vlc-snapshot-20100923.tar.\* [/COLOR]**
vlc-1.2.0-git/
vlc-1.2.0-git/m4/
vlc-1.2.0-git/m4/lib-link.m4
vlc-1.2.0-git/m4/inttypes_h.m4
vlc-1.2.0-git/m4/with_pkg.m4
vlc-1.2.0-git/m4/po.m4
vlc-1.2.0-git/m4/lcmessage.m4
[...]

```

which makes me feel a little better, I am not that keen on using programs ported from windows :).

Andrew

---

### Post by qyot27 on 2010-09-23
> **andrew.46 said:**
> Thank you very much for pointing that out! A bit of further investigation has shown that at least under tar 1.22 renaming and indeed 7zip are *not* required as the following command does it all in one go by using lzma:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]tar --lzma -xvf vlc-snapshot-20100923.tar.\* [/COLOR]**
vlc-1.2.0-git/
vlc-1.2.0-git/m4/
vlc-1.2.0-git/m4/lib-link.m4
vlc-1.2.0-git/m4/inttypes_h.m4
vlc-1.2.0-git/m4/with_pkg.m4
vlc-1.2.0-git/m4/po.m4
vlc-1.2.0-git/m4/lcmessage.m4
[...]

```

which makes me feel a little better, I am not that keen on using programs ported from windows :).

Andrew
Well, 7zip is the reference LZMA program, so I don't really see porting it as an issue *per se*, especially since it's under the LGPL (and under Windows 7zip still requires two steps to get .tar.xz, .tar.gz, .tar.lzma, .tar.bz2, etc. stuff unpacked).  .tar.xz and .tar.lzma are simply the tar-based usages of 7zip's algorithm, and don't require p7zip to be there at all anyway (although if you run across .7z files you need it, but those generally aren't tarred).  I'm not sure if there's any significant difference between the two either (considering the command I used - a capital J - refers directly to .xz files, --lzma must be more general).

I didn't think renaming would be required on *nix.  I simply had to do that because the asterisk is an illegal character on Windows (and trying to save it through Firefox on there would replace the * with an underscore anyway).  I just don't know if maybe something in Videolan's pipeline is causing the .xz or .lzma on the end of the file to get replaced by a *.

---

### Post by andrew.46 on 2010-09-23
Hi qyot,

> **qyot27 said:**
> (considering the command I used - a capital J - refers directly to .xz files, --lzma must be more general).

Looks like the short option *-J* is simply an alias for *--lzma*, introduced in tar 1.2.1. Hmmm.... I seem to be getting more obtuse every day :(.

Andrew

---

### Post by cthlhu1987 on 2010-10-03
This sucks, i got the most recent ffmpeg, the most recent x264, the most recent vlc:
```
baruch@baruch-laptop:~/progs/webm$ vlc --version
VLC media player 1.1.4.1 The Luggage (revision exported)
VLC version 1.1.4.1 The Luggage (exported)
Compiled by buildd on seaborgium.ppa (Sep 27 2010 16:13:24)
Compiler: gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5)**[...]**
```
And it still won't play webm-files, but give me the followin msg:
```
baruch@baruch-laptop:~/progs/webm$ vlc legend_guardians.webm 
VLC media player 1.1.4.1 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Warning: call to signal(13, 0x1)
[0x898767c] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb66fe0d4, 0xb66fe048)
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
Warning: call to signal(13, 0x1)
Warning: call to srand(1285896859)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:10947): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
[0xb730209c] main decoder error: no suitable decoder module for fourcc `VP80'. VLC probably does not support this sound or video format.
``` What am i doin wrong ;(

---

### Post by mc4man on 2010-10-03
> What am i doin wrong 
Might be useful to explain what are you doing... like where did you 'get' your ffmpeg and vlc from? (build, ppa, ubuntu repo..?

---

### Post by cthlhu1987 on 2010-10-03
> **mc4man said:**
> Might be useful to explain what are you doing... like where did you 'get' your ffmpeg and vlc from? (build, ppa, ubuntu repo..?
I built ffmpeg and x264 from source (there's a instruction here in the forum),vlc came from a ppa (Ferramosca Roberto).

---

### Post by ron999 on 2010-10-03
...

---

### Post by mc4man on 2010-10-03
> vlc came from a ppa
vlc builds from ppa's either use the system shared ffmpeg lib's or provide new (backported) ones.
In this case your vlc is using the default lucid ffmpeg libs which  don't support vp8

So your options are:
build your own vlc as this thread is about
find a ppa for vlc that replaces your ffmpeg libs - could bork other apps

use another player for vp8 files, like mplayer, either self built or a recent ppa version

add the ppa in my sig (lucid only) and totem will play your vp8 files
(update the gsteamer plugins  - bad, ugly and ffmpeg

upgrade to maverick where vp8 and more is enabled by default

---

### Post by andrew.46 on 2010-10-03
Hi cthlhu,

> **cthlhu1987 said:**
> I built ffmpeg and x264 from source (there's a instruction here in the forum)

Mind you if you built the svn FFmpeg from FakeOutdoorsman's guide you will find that you should be able to play that particular webm file by using ffplay.

Andrew

---

### Post by andrew.46 on 2010-10-09
Looks like the Medibuntu Maverick Repository will be opened with the release of Maverick Meerkat in less than 12 hours so I have converted the guide to Maverick. I have run it under the alpha and beta versions with no trouble but I shall re-test it with the *release* version when I get hold of a copy, in the meantime please let me know if there are any glitches :).

Andrew

---

### Post by mc4man on 2010-10-09
I think(?) you could just go with libdvbpsi-dev instead ( dev of the latest version which  is libdvbpsi6), though not using it can't say for sure 
No issue building with it though and changelog would make it seem a logical choice

---

### Post by andrew.46 on 2010-10-09
Hi mc4man,

> **mc4man said:**
> I think(?) you could just go with libdvbpsi-dev instead 

Indeed, and I have remove the second mention oflibdvbpsi as well, not sure when that crept in:) Thanks for that! I have deleted my 2 Maverick VMs now and I will be keen to install fresh on the release version.

Andrew

---

### Post by andrew.46 on 2010-10-10
Looks like Medibuntu will be taking a while with their Maverick repository so I have eliminated it completely from the guide. Codecs will come directly from MPlayer for 32bit users and libdvdcss will be installed from the usual script which should make the guide a little more robust. I have never been keen on external repositories anyway :).

Andrew

---

### Post by mc4man on 2010-10-10
> libdvdcss will be installed from the usual script

At the end of the day it's the exact same package for karmic thru maverick anyway (pool/free/libd/libdvdcss/libdvdcss-dev_1.2.10-0.3medibuntu1_i386.deb or the 64 bit deb


And in any event that script is bound and determined to provide libdvdcss2 one way or the other.

---

### Post by andrew.46 on 2010-10-11
An interesting announcement on the vlc plugins:

Update on the VLC browser plugins
[http://mailman.videolan.org/pipermail/videolan-announce/2010-October/000158.html](http://mailman.videolan.org/pipermail/videolan-announce/2010-October/000158.html)

Andrew

---

### Post by jacobus77 on 2010-10-17
I'm willing to translate your post for the french ubuntu community at [http://doc.ubuntu-fr.org](http://doc.ubuntu-fr.org)
Just to know if you're ok with it before doing it.
Thanks.

---

### Post by andrew.46 on 2010-10-20
Hi Jacobus,

> **jacobus77 said:**
> I'm willing to translate your post for the french ubuntu community at [http://doc.ubuntu-fr.org](http://doc.ubuntu-fr.org)
Just to know if you're ok with it before doing it.

Feel free to do this :). Bear in mind the guide is somewhat fluid and will change from time to time which is the nature of building the* development* version after all...

Andrew

---

### Post by jackachan on 2010-11-02
I'm still using Ubuntu 9.04 Jaunty. Could anyone provide a guide for building vlc 1.1.4 on 9.04? I have already installed the latest version of ffmpeg and x246 following OF's guide.

---

### Post by mc4man on 2010-11-02
> I'm still using Ubuntu 9.04 Jaunty. Could anyone provide a guide for building vlc 1.1.4 on 9.04
You probably can build 1.1.4 on jaunty though you'd to do a few things.

As far as the build-deps that you may not already have - 
can you install jaunty packages? (either the jaunty repos are still open or you've switched to the archives in your sources list

Some jaunty packages may have slightly different names than the below build-dep, just find the correct name and adjust.

A few packages will be too old, you'd need to update w/ newer .debs or build a newer source and most likely statically link - the libtag libraries is one

Some things will not be available in jaunty - you could forgo, install from lucid or mav. packages or build and install - libvpx is an example (maybe you built that for ffmpeg

Slightly truncated build-dep command, run it and see..
```
sudo apt-get install libqt4-dev libhal-dev lua5.1 liblua5.1-0-dev libdvdread-dev \
libtag1-dev libmad0-dev libdvbpsi5-dev liba52-0.7.4-dev libv4l-dev libcdio-dev \
libvcdinfo-dev libfribidi-dev libfluidsynth-dev libmpeg2-4-dev libschroedinger-dev \
libvorbis-dev libspeex-dev libgcrypt11-dev libcddb2-dev libproxy-dev libnotify-dev \
libebml-dev libmpcdec-dev libcaca-dev libaa1-dev libmatroska-dev xulrunner-dev \
libasound2-dev libass-dev libavahi-client-dev libdca-dev libdvdnav-dev libfaad-dev \
libflac-dev libfreetype6-dev libggi2-dev libgl1-mesa-dev libglib2.0-0 libgnutls-dev \
libid3tag0-dev libjack-dev liblircclient-dev libmodplug-dev libncursesw5-dev \
libogg-dev libpng12-dev libpulse-dev libsdl-image1.2-dev libsdl1.2-dev libshout3-dev \
libsmbclient-dev libsvga1-dev libsysfs-dev libtar-dev libtwolame-dev libudev-dev \
libupnp3-dev libx11-dev libxcb-keysyms1-dev libxext-dev libxml2-dev libxpm-dev \
libxt-dev libxv-dev libxcb-shm0-dev libxcb-xvmc0-dev libx11-xcb-dev libsdl-image1.2-dev \
libmtp-dev libsqlite3-dev libgnomevfs2-dev librsvg2-dev libzvbi-dev libxcb-randr0-dev \
liboggkate-dev libkate-dev libpango1.0-dev libcairo2-dev qt4-qtconfig
```

As far as libtag, you need to update to the 1.6.3 versions - read post #13 here
[http://ubuntuforums.org/showthread.php?p=9719115#post97191](http://ubuntuforums.org/showthread.php?p=9719115#post97191)
If you can satisfy most if not all of these deps/package versions then building would be simple.
(or at least then give it a go and see if it errors

---

### Post by andrew.46 on 2010-11-03
I have to thank FakeOutdoorsman for pointing out that there is a new point release for FFmpeg and I have adjusted the build instructions accordingly. Patch for 64 bit users still applies cleanly and vlc-git compiles against the new version with no problems.

Andrew

---

### Post by andrew.46 on 2010-11-12
An interesting compiling guide for vlc has the official nod from the vlc developers and is well worth a read:

Compiling VLC for linux people
[http://ivoire.dinauz.org/blog/index.php?post/2010/10/01/Compiling-VLC-for-linux-people](http://ivoire.dinauz.org/blog/index.php?post/2010/10/01/Compiling-VLC-for-linux-people)

Note the slightly different usage of *PKG_CONFIG_PATH* although functionally there is no difference in result, otherwise I cannot see anything to appropriate for the guide :).

Andrew

---

### Post by shantiq on 2010-11-21
Cannot remember if i have put this here before to pimp your vlc ride    so here they are 4 extra options

go to icon right-click/properties/click on existing icon then change


can also right-click and resize after :KS   bit of fun

---

### Post by andrew.46 on 2010-11-22
Thanks shantiq :)

Andrew

---

### Post by mc4man on 2010-12-06
As a little add. for the few and far between. While vlc registers as a audio cd player and can autoplay or be started from a r. click on the icon it doesn't do so correctly. 
(at least here in any recent ubuntu
This is for autoplay, r. click on icon when having multiple drives, internal and or external. (max. of 10
For a single drive there's a more direct approach though this is fine.
Same idea works for amarok 1.4 w/ small obvious script change

Assumes a bin in home folder, if wishing to try and you don't have one then this and a restart
mkdir bin
Also assumes a ~/.local/share/applications folder

From a terminal  at normal propmt
```
 gedit vlc-cd.desktop
```
paste this in and save
```
[Desktop Entry]
Version=1.0
Name=VLC Cd Player
Comment=Auto plays audio cd's
Exec=vlccd
Icon=vlc
Terminal=false
Type=Application
Categories=AudioVideo;Player;
MimeType=x-content/audio-cdda;
```

```
mv vlc-cd.desktop ~/.local/share/applications/
```
```
chmod +x ~/.local/share/applications/vlc-cd.desktop
```
```
gedit ~/bin/vlccd
```
paste this in and save
```
#!/bin/bash
CD=/dev/`echo $1|sed -e "s/.*\(sr[0-9]\).*/\\1/"`
vlc cdda://$CD
```
```
chmod +x ~/bin/vlccd
```

To add directly to choices for audio cd
```
gedit  ~/.local/share/applications/mimeapps.list
```
look for this line
x-content/audio-cdda=
if there just add to front of line
vlc-cd.desktop;
ex.
> x-content/audio-cdda=vlc-cd.desktop;rhythmbox.desktop;
if not there just add a new line
```
x-content/audio-cdda=vlc-cd.desktop;
```

( to make use of the places 'audio cd' icon (is set to a usually non-existent soundjuicer
```
gconftool-2 --type string --set /desktop/gnome/url-handlers/cdda/command "vlccd"
```
Or set to something else if desired.

---

### Post by mc4man on 2010-12-24
Andrew - 
if you happen by at some point - am curious if on your slack, if you still have vlc going, can you access this setting?
tools -prefs -  all - Input/Codecs - access modules - HTTP(s)

Been causing a segfault here for quite some time

---

### Post by gillza on 2010-12-28
Hello everybody,

I was wondering if I could get some assistance.
I have just followed this guide to install VLC (1.2.0-git TwoFlower) on a fresh 10.10. VLC was literally the first package i installed on it. Everything went beautifly, no errors. 

Now when I try to play any video and skip back and forth through it audio stops. No sound whatsoever. Searched through this thread but did not find anything useful, or missed it. 

Did anyone have something similar?

Thank you.


P.S.

I have noticed that in the preferences, audio output there was no option for Pulse audio for the development version. 
VLC was killed and instead the one from bleed ppa was installed (v1.1.5). This one had pulse output and no problems while jumping/skipping. Just to check I have changed the output to ALSA, saved, restarted the player and bam, no sound while going to the middle of the video again... So it seems to me that the lack of pulse as an output is an issue here. 
How does one enable it for the development build?

---

### Post by andrew.46 on 2010-12-29
Hi mc4man,

> **mc4man said:**
> if you happen by at some point - am curious if on your slack, if you still have vlc going, can you access this setting?
tools -prefs -  all - Input/Codecs - access modules - HTTP(s)

Been causing a segfault here for quite some time

Been more than a few changes in this end of the world recently, I am again without an Ubuntu distro installed and I do not have vlc installed on Slackware either at the moment :(. So I am afraid that I am little help to you with this matter for the next little while....


Andrew

---

### Post by mc4man on 2010-12-29
> Been more than a few changes in this end of the world recently...
I do fear for some changes here also..., anyway it resolved itself just recently (not a bad thing to raise that buffer, though one one a few changes that can be made directly in vlcrc

---

### Post by andrew.46 on 2011-01-02
Hi mc4man,

> **mc4man said:**
> if you happen by at some point - am curious if on your slack, if you still have vlc going, can you access this setting?
tools -prefs -  all - Input/Codecs - access modules - HTTP(s)

Been causing a segfault here for quite some time

Sorry for the delay, I have installed the development version of Slackware (Slackware -current) and it has taken me some time to tame it and mould it to my needs :). Using alienBOB's amazing script I have installed the development version of vlc and no segfaults with those settings. It feels good to be back in the saddle with vlc-git again, not sure if I can afford the time to run the same on Ubuntu though :(.

Andrew

**Edit:** Oops, just saw in your last post that the issue has already been resolved ....

---

### Post by reign1 on 2011-02-08
When attempting to build vlc-git per this tutorial vlc throws a segmentation fault when I try to load mkv files.  Installing 1.1.4 from the main repository using apt-get or 1.1.7 from a ppa seem to work perfectly fine.  Is anyone else experiencing this issue?

---

### Post by mc4man on 2011-02-11
> When attempting to build vlc-git per this tutorial vlc throws a segmentation fault when I try to load mkv files.
Seems to be an issue w. vlc-1.2+ at times, a git from yesterday does segfault here on a .mkv, a build from  about 10 days ago is fine.
The dev source can be a bit hit or miss at times.

(you should definitely save the checkinstall package from a  build that works well for your usage, then you can downgrade while waiting for a more suitable build

---

### Post by reign1 on 2011-02-12
> **mc4man said:**
> Seems to be an issue w. vlc-1.2+ at times, a git from yesterday does segfault here on a .mkv, a build from  about 10 days ago is fine.
The dev source can be a bit hit or miss at times.

(you should definitely save the checkinstall package from a  build that works well for your usage, then you can downgrade while waiting for a more suitable build

Yeah I hopped on IRC and got it fixed yesterday.

Seems to be an issue with EBML_STRICT_API.

Anyone having this problem can do as follows to fix it:

Comment line 66 in /modules/demux/mkv/demux.cpp
Remove the line containing EBML_STRICT_API from configure.ac

Boostrap, configure, and recompile.

Thanks for the suggestion though, I'll definately start saving a previous build for times like these.

---

### Post by andrew.46 on 2011-02-14
> **reign1 said:**
> Seems to be an issue with EBML_STRICT_API.

Hmmm.... I wonder if the new versions of libebml/libmatroska would have a similar problem? 1.2.0 and 1.1.0 came out not too long ago. As a sidenote to any who are interested these 2 are no longer required as external libraries when building mkvtoolnix, an internal copy is supplied...

---

### Post by reign1 on 2011-02-14
> **andrew.46 said:**
> Hmmm.... I wonder if the new versions of libebml/libmatroska would have a similar problem? 1.2.0 and 1.1.0 came out not too long ago. As a sidenote to any who are interested these 2 are no longer required as external libraries when building mkvtoolnix, an internal copy is supplied...

Funny you should ask that, as compiling against libeml-1.2.0 and  libmatroska-1.1.0 was the first thing I tried to correct the issue.

NOTE: You cannot compile against the libraries included by mkvtoolnix  since they are missing the shared libraries. You must compile libebml  and libmatroska from source with the -fpic compile flag if you want vlc  to compile against them.

In any case, compiling against them didn't fix the problem for me, but  it seems one of the latest revisions in git removes EBML_STRICT_API from  configure.ac, and from a quick recompile with a fresh checkout, it seems  everything is back to normal with no special tweaks needed.

---

### Post by andrew.46 on 2011-02-15
I have neglected this guide of late for which my apologies. To remedy this 3 small points:

[LIST=1]
[*]Unnoticed by me on 2010.07.29 there appeared a makefile aimed at building Live555 on 64bit linux. I have added this into the guide.
[*]There is a substantial problem with the Live555 libraries of 2011.01.10 and vlc, you would be best to update to 2011.01.24 promptly.
[*]There is a new version of the MPlayer codecs that I have added in to the guide, it may not add any functionality to vlc (via the *--enable-loader* option) but it is a worthy upgrade to the codecs anyway :).
[/LIST]

@ reign1: Thanks for looking into that, glad to hear the vlc devs have rectified the issue. Could be [this commit]("http://git.videolan.org/gitweb.cgi?p=vlc.git;a=commit;h=c984067b01d8857bcc7b3e6103f88af415c5cb18").

---

### Post by andrew.46 on 2011-02-26
For people after something completely different I would suggest compiling the git vlc against *libgme-dev* as I have just done. Game_Music_Emu support in vlc means vlc can playback most of the following old game console formats:

 * AY        ZX Spectrum/Amstrad CPC
 * GBS       Nintendo Game Boy
 * GYM       Sega Genesis/Mega Drive
 * HES       NEC TurboGrafx-16/PC Engine
 * KSS       MSX Home Computer/other Z80 systems (doesn't support FM sound)
 * NSF/NSFE  Nintendo NES/Famicom (with VRC 6, Namco 106, and FME-7 sound)
 * SAP       Atari systems using POKEY sound chip
 * SPC       Super Nintendo/Super Famicom
 * VGM/VGZ   Sega Master System/Mark III, Sega Genesis/Mega Drive,BBC Micro

A collection of Atari files can be downloaded [here...]("http://asma.atari.org/bin/asma34.zip") or if you prefer I have attached a single file to this post.

---

### Post by ron999 on 2011-03-05
Hmmm...
I've updated VLC-1.2.0 from git today to revision aff01a3.
It seems that two features are missing since my previous update:-

The AppleTrailers have disappeared from View -> Playlist -> Internet.
The IMDb Movie Database has disappeared from the 'View' menu.


My previous update with those features was revision 2023e0b from February 19 2011.

---

### Post by mc4man on 2011-03-05
> **ron999 said:**
> Hmmm...
I've updated VLC-1.2.0 from git today to revision aff01a3.
It seems that two features are missing since my previous update:-

The AppleTrailers have disappeared from View -> Playlist -> Internet.
The IMDb Movie Database has disappeared from the 'View' menu.


My previous update with those features was revision 2023e0b from February 19 2011.

Will be interested to see what response you get about this over at vlc forum

You could always keep a copy of the last good build around, only takes a few seconds to switch versions

---

### Post by andrew.46 on 2011-03-06
Indeed it has gone, I cannot recall when that vanished, hopefully the vlc developers can sort that one out, they can be a bit testy at times...

---

### Post by andrew.46 on 2011-03-06
> **reign1 said:**
> Funny you should ask that, as compiling against libeml-1.2.0 and  libmatroska-1.1.0 was the first thing I tried to correct the issue.

As a sidenote you may be interested to know that vlc 1.1.7 will not actually compile against the newer libraries. A patch exists for this, courtesy of our gentoo colleagues, which I have attached to this post.

---

### Post by mc4man on 2011-03-06
> Indeed it has gone, I cannot recall when ..
Right about here
[http://git.videolan.org/?p=vlc.git;a=commitdiff;h=377ea4956ae17cdab28720be492cfbf436676fb8;hp=cb98df1ce4b368f94254508c135b66a59d68e1b5](http://git.videolan.org/?p=vlc.git;a=commitdiff;h=377ea4956ae17cdab28720be492cfbf436676fb8;hp=cb98df1ce4b368f94254508c135b66a59d68e1b5)

---

### Post by mc4man on 2011-03-06
Ron - for the moment (and stress ftm), this is just an interface change, the code enabling is still intact and compatible w/ vlc and the sites.

So, if desired you can simply add imdb and apple trailers back into the interface, should  take less than a min. to do, it's only 4 lines total that you add back to /share/Makefile.am  (2 each for imdb and apple trailers

Just go to the file, open in gedit (enable line numbers in gedit so to reference the general area easier), copy the removed line (red) from the commit and paste in appropriate place
Use a tab indent, then paste

Ex. - added first line back for imdb, at line #208 _tonights commit_ (actual line #'s can change day to day
```
if BUILD_LUA
        nobase_vlclib_DATA = \
	lua/extensions/allocine-fr.luac \
	[COLOR="Blue"]lua/extensions/imdb.luac \[/COLOR]
	lua/intf/dummy.luac \
	lua/intf/dumpmeta.luac \
	lua/intf/hotkeys.luac \


```
and 1st. one for apple - at line #224 for _tonights commit_
```
  
        lua/modules/simplexml.luac \
	lua/playlist/anevia_streams.luac \
	lua/playlist/anevia_xml.luac \
	[COLOR="Blue"]lua/playlist/appletrailers.luac \[/COLOR]
	lua/playlist/bbc_co_uk.luac \
```
Then just one more each, quite easy, you'll see

Had to try first, seems fine though at some point may no longer work if the code isn't maintained

---

### Post by andrew.46 on 2011-03-06
BTW has anybody tried this guide under Natty Narwhal? I have a deep suspicion that very few changes will be needed to successfully compile vlc-git for the next Ubuntu release. I will be having a peek at Natty on VBox with Beta 1 which I believe will be in 4 weeks or so...

---

### Post by ron999 on 2011-03-06
Hi mc4man
Thanks for your reply.
I have followed a low-tech path.;)
 
I've extracted the **appletrailers.luac** file from the previous install.

This is the method that I used to put it back:-

Look for an **sd** folder in location 
**.local/share/vlc/lua/sd**
If there isn't one then create a new **sd** folder.

Put the **appletrailers.luac** file in the **sd** folder.

Re-start VLC.


I don't use the IMDb feature because I have it as one of my Firefox search engines.:cool:

---

### Post by mc4man on 2011-03-06
> BTW has anybody tried this guide under Natty Narwhal? 
Well, yes and no
Have been doing fresh installs of 11.04 about once a week so haven't done some of the things I may normally do.
Did build vlc git last night though took a bit of a shortcut by using the system x264, ffmpeg, and live555

Will run a test on next fresh install, don't anticipate much issue

edit: had a few so followed guide , no issues (32bit
(there are probably some build-deps not needed, and a couple that could be added for some uses/users.

---

### Post by andrew.46 on 2011-03-06
> **mc4man said:**
> edit: had a few so followed guide , no issues (32bit
(there are probably some build-deps not needed, and a couple that could be added for some uses/users.

Great news, thanks for that :).

---

### Post by mc4man on 2011-03-09
> vlc developers .......  can be a bit testy at times...
I guess ron's ? didn't fare so well (gone somewhere...

---

### Post by ron999 on 2011-03-09
> **mc4man said:**
> I guess ron's ? didn't fare so well (gone somewhere...
The question went unanswered. :roll:
So I deleted it because you had pointed me to the answer.;)
Here:- [http://ubuntuforums.org/showpost.php?p=10527665&postcount=249]("http://ubuntuforums.org/showpost.php?p=10527665&postcount=249")

---

### Post by mc4man on 2011-03-09
> So I deleted it 
That makes more sense, could see the thread ignored or even locked, but not deleted. Didn't realize one could delete threads

---

### Post by andrew.46 on 2011-03-24
Although this thread deals for the most part with the development version of vlc some might be interested to see that there is a [new release version, 1.1.8]("http://www.videolan.org/vlc/releases/1.1.8.html").Not any huge changes but a worthy upgrade anyway, obligatory screenshot attached of my own build :).

I note that one change has been to allow the release version to compile against the newer libebml/libmatroska libraries without patching...

Andrew

---

### Post by andrew.46 on 2011-04-04
In a last small but reasonably significant change before Natty Narwhal arrives I have changed the FFmpeg version to the rc of the next FFmpeg release. Big changes from the last release. The asm patch has been dropped as well as 64bit installation does not seem to need it any longer as far as I can tell and I admit I have not tested my most recent installation extensively.

Any problems with these changes please let me know, it puzzles me a little that this guide has been viewed almost 30,000 times but I get little feedback about it :(. Hopefully everybody just sails through it with no problems at all.....
[B]
Edit:[/B] Natty version now in place :).

---

### Post by rbrick49 on 2011-04-09
mine doesnt work andrew it appeared to build but when I type vlc in terminal no go
I just tried again now its working

---

### Post by andrew.46 on 2011-04-09
> **rbrick49 said:**
> mine doesnt work andrew it appeared to build but when I type vlc in terminal no go
I just tried again now its working

Thanks for testing the guide out Ronnie :)

---

### Post by shantiq on 2011-04-11
> this guide has been viewed almost 30,000 times but I get little feedback about it :(. Hopefully everybody just sails through it with no problems at all.....



Andrew that is the plight of the one who puts stuff before the nerd community  :KS:KS:KS;   they are not a talkative bunch but no doubt appreciate your efforts here on this site...

I know i do 
often your posts have got me out of a fix
so much info and help.

---

### Post by andrew.46 on 2011-04-11
Thanks shantiq :)

---

### Post by andrew.46 on 2011-04-14
For a bit of fun try reading /doc/fortunes.txt within the vlc-git source code, it gave me a laugh :)

---

### Post by gillza on 2011-04-16
> **gillza said:**
> Hello everybody,

I was wondering if I could get some assistance.
I have just followed this guide to install VLC (1.2.0-git TwoFlower) on a fresh 10.10. VLC was literally the first package i installed on it. Everything went beautifly, no errors. 

Now when I try to play any video and skip back and forth through it audio stops. No sound whatsoever. Searched through this thread but did not find anything useful, or missed it. 

Did anyone have something similar?

Thank you.


P.S.

I have noticed that in the preferences, audio output there was no option for Pulse audio for the development version. 
VLC was killed and instead the one from bleed ppa was installed (v1.1.5). This one had pulse output and no problems while jumping/skipping. Just to check I have changed the output to ALSA, saved, restarted the player and bam, no sound while going to the middle of the video again... So it seems to me that the lack of pulse as an output is an issue here. 
How does one enable it for the development build?

Ok I have a freshly installed 10.10 (due to new HDD in the laptop) and this time there is Pulse present in the output. And yet the same issue, sound disappears if I skip back and forth a few times...  Anyone has a similar problem?

---

### Post by andrew.46 on 2011-04-17
> **gillza said:**
> Ok I have a freshly installed 10.10 (due to new HDD in the laptop) and this time there is Pulse present in the output. And yet the same issue, sound disappears if I skip back and forth a few times...  Anyone has a similar problem?

I will confess that I am Ubuntu-less at the moment, waiting for a new version of VirtualBox that can cope with Natty :(. I wonder if you would be interested in trying to compile and install the release version 1.1.9, using the same build environment established in this guide? This might be the best way to understand if there is a pulse-audio problem with vlc-git...

If you are interested uninstall the vlc package created by the guide and run the following command:

```

cd $HOME/vlc_build && \
wget 'http://download.videolan.org/pub/videolan/vlc/1.1.9/vlc-1.1.9.tar.bz2' && \
tar xjvf vlc-1.1.9.tar.bz2 && cd vlc-1.1.9 && \
export PKG_CONFIG_PATH="$HOME/vlc_build/vlcdeps/usr/lib/pkgconfig" && \
if [ ! "$(uname -m)" = "x86_64" ]; then
 ARCHOPTS="--enable-loader"
else
  ARCHOPTS=""
fi && \
./configure $ARCHOPTS \
            --prefix=/usr/local \
            --with-live555-tree=$HOME/vlc_build/live \
            --enable-real \
            --enable-realrtsp \
            --enable-aa \
            --enable-merge-ffmpeg \
            --enable-vcdx \
            --enable-ncurses && \
make jobs=4 && \
sudo checkinstall --pakdir "$HOME/vlc_build" --backup=no --deldoc=yes --pkgname vlc \
                  --pkgversion "1.1.9" --fstrans=no \
                  --deldesc=yes --delspec=yes --default && \
make distclean && sudo ldconfig

```

It will be very interesting to see if your pulse audio issues are resolved with this or in fact they remain. I should mention again that I have not tested the above on either Maverick or Natty, so please let me know if there are errors. If it all works well enough I shall add it into the main guide :).

BTW some may be interested to see that I have enabled [the ncurses interface ]("http://wiki.videolan.org/Documentation:Modules/ncurses")in the compile options, I attach a screenshot showing this in action, playing the audio cd 'Solaris'.

Andrew

---

### Post by andrew.46 on 2011-04-25
Finally Virtualbox and Natty are working together to produce the Unity Desktop on my system. I have just built the 64bit vlc-git successfully on this setup and had my first proper look at Unity: it looks very swish I will have to admit :). Anyway this means I can support this guide through Natty....... Obligatory over-sized screenshot[ here...]("http://www.andrews-corner.org/images/vlc_natty.png") Looking forward to the ongoing challenges of building the development version of vlc under the new release :).

Andrew

**Edit:** I have added instructions for 1.1.9 into the guide itself, no screenshot this time!!

---

### Post by andrew.46 on 2011-05-02
Updated the FFmpeg version to 0.7-rc1, all builds well on my 64bit system, not tested on 32bit yet but I would be surprised if there is a problem...

---

### Post by andrew.46 on 2011-05-08
I am applying for Ubuntu Membership (again!) based on my work in these Forums and as part of this process I am asking for testimonials from those who know and are happy with my work, and perhaps have benefited from my guides or my assistance on the Forums. I am not entirely comfortable with making this request, I prefer to remain in the background to tell the truth, but this is the way the process runs.

So, if you would like to make a testimonial in support of my application for Ubuntu Membership simple write a couple of words in this thread:

Application for Ubuntu Membership: andrew.46
[http://ubuntuforums.org/showthread.php?t=1750777](http://ubuntuforums.org/showthread.php?t=1750777)

And I thank you for your trouble! I am posting the same message in both MPlayer and vlc guides that I run, this seems to be where my current focus is so hopefully this is not too much like spam :).

Thanks for your trouble,

Andrew

---

### Post by yetiman64 on 2011-05-08
> **andrew.46 said:**
> ....I am posting the same message in both MPlayer and vlc guides that I run, this seems to be where my current focus is so hopefully this is not too much like spam :).....

I'm glad you did post this here where I'm subscribed or I might have missed it otherwise, your guides over the years have been a great help to many. Much appreciated, my vote is registered there now :).

Cheers, yetiman64

P.S. haven't checked out the mplayer guides for a while, has it been updated for natty ? 
Edit: I see it specifically mentions Maverick and I suspect you might be doing a rolling tutorial as such now. (Just saw it below this thread in tutorials and tips :-)) /Edit

I think I used the Karmic guide with adjustments from mc4man to build for Lucid (works really well btw).

---

### Post by andrew.46 on 2011-05-09
Thanks yetiman64!! I am still tossing up with the Natty guide for MPlayer, there is a great PPA now and interest has been fading a little on the Ubuntu Forums in compiling MPlayer. However I finish a major assignment in the next few days so this would be the time to rewrite the guide for Natty. Plus I have access to a nice nice machine now which make compiling less painful (it is my wife's computer but I am allowed to use it from time to time!). I shall have serious think over the next few days...

Thanks again for your support!

Andrew

---

### Post by yetiman64 on 2011-05-09
> **andrew.46 said:**
> Thanks yetiman64!! I am still tossing up with the Natty guide for MPlayer, there is a great PPA now and interest has been fading a little on the Ubuntu Forums in compiling MPlayer. However I finish a major assignment in the next few days so this would be the time to rewrite the guide for Natty. Plus I have access to a nice nice machine now which make compiling less painful (it is my wife's computer but I am allowed to use it from time to time!). I shall have serious think over the next few days...

Thanks again for your support!

Andrew

Must admit I really hope you do keep it up, I actually do a quite strange setup here involving parallel 32 and 64 bit systems, a chroot in the 64 bit system to run, in particular, mplayer and mencoder passed across after being built in the 32 bit install to the 32 bit chroot. 

Think vdpau output + w32codecs + mplayer running integrated into the 64 bit desktop with 8GB RAM etc. :lol: I will look into the ppa and test if it will install and play nice with the chroot setup pretty soon though. 

Here's hoping and [-o<-ing that mplayer survives, ... :biggrin:,

Cheers mate and all the best to you. I'll leave your vlc thread alone now, though must admit I've been enjoying following it since not long after I joined in March last year - haven't taken the plunge with building vlc myself yet though.

yetiman64

---

### Post by andrew.46 on 2011-05-13
> **yetiman64 said:**
> Here's hoping and [-o<-ing that mplayer survives, ... :biggrin:,

Well I have finished my big assignment (ask me about Indian Independence and the Partition!) so I fixed the MPlayer guide up for Natty. In all honesty there were only a few minor changes and it runs well enough on my system although Unity is a little twitchy in a VM. My underpowered laptop fails with Unity and Natty so MPlayer was built on my wife's more robust machine :).

---

### Post by andrew.46 on 2011-05-14
I have adjusted the x264 compilation section to reflect the new build defaults, ie as of the latest revision by default no static library is built... I can almost hear the groans across the Internet as build scripts start failing everywhere :).

---

### Post by shantiq on 2011-05-15
ok may have been answered elsewhere but when i run
the update code on natty 64


```
cd $HOME/vlc_build/vlc && git pull && ./bootstrap && \
export PKG_CONFIG_PATH="$HOME/vlc_build/vlcdeps/usr/lib/pkgconfig" && \
if [ ! "$(uname -m)" = "x86_64" ]; then
 ARCHOPTS="--enable-loader"
else
  ARCHOPTS=""
fi && \
./configure $ARCHOPTS \
            --prefix=/usr/local \
            --with-live555-tree=$HOME/vlc_build/live \
            --enable-real \
            --enable-realrtsp \
            --enable-aa \
            --enable-merge-ffmpeg \
            --enable-vcdx \
            --enable-ncurses && \
make jobs=4 && \
sudo checkinstall --pakdir "$HOME/vlc_build" --backup=no --deldoc=yes --pkgname vlc \
                  --pkgversion "1.2.0-git-$(date +%Y%m%d)-$(git show --abbrev-commit \
                  | grep '^commit' | cut -f2 -d " ")" --fstrans=no \
                  --deldesc=yes --delspec=yes --default && \
make distclean && sudo ldconfig
```



i get this


```

Updating 06ac7b7..da61086
error: Your local changes to the following files would be overwritten by merge:
	po/nl.po
Please, [COLOR="Red"]commit your changes or stash them[/COLOR] before you can merge.
```


how do i do that/? please

---

### Post by andrew.46 on 2011-05-15
Doubtless there is a git command to get over that problem but this solution escaped me when I faced the same problem a while back. My own clumsy solution was to delete the vlc source code completely and go back to the "Building vlc-git......" section and grab a fresh download. Unfortunately I do not know enough about git to untangle the problem properly.

BTW I had to add *--disable-taglib* to the vlc ./configure options to successfully compile today but perhaps that has been fixed by now?

---

### Post by shantiq on 2011-05-15
cool Andrew back to the startline it is then  :KS:KS:KS:KS   thanx for this development version the "normal" 1.1.9 was doing horrible things to my puter

---

### Post by qyot27 on 2011-05-15
> **andrew.46 said:**
> Doubtless there is a git command to get over that problem but this solution escaped me when I faced the same problem a while back. My own clumsy solution was to delete the vlc source code completely and go back to the "Building vlc-git......" section and grab a fresh download. Unfortunately I do not know enough about git to untangle the problem properly.
If I'm understanding the issue correctly, I believe that would be:

```
qit commit -a
```

At least, that's what I had to do when I was messing with the Lagarith branch of FFmpeg and doing the manual work to let it merge with the main branch (I no longer have to do this, as the Lagarith stuff was officially committed to SVN back in January, before the implosion occurred).

---

### Post by mc4man on 2011-05-16
For the few that may want a vlc systray icon in 11.04 unity. Noting that the systray may or may not be available in 11.10

It can be done manually in dconf-editor or thru gsettings.
 man gsettings is quite valuable to see how to find the schema names, the key names for schema's and what the value's can be  for a key.

For this the best is to run the get command and then use what's shown inside the [] in a set command, adding and or removing as desired.  Copy and paste works well.

I've removed many of the default ones and added ones i'd actually use so this is  just an example. (there is a single "all" value but I think better to just do as needed and or possible without issues..

Ex.
```
gsettings get com.canonical.Unity.Panel  systray-whitelist
```
> doug@doug-alienware:~$ gsettings get com.canonical.Unity.Panel  systray-whitelist ['JavaEmbeddedFrame', 'Audacious', 'Opera']

So just adding _, 'Vlc'_ to the end and  enclosing the above copied  [] in quotes

 ```
gsettings set com.canonical.Unity.Panel  systray-whitelist "['JavaEmbeddedFrame', 'Audacious', 'Opera', 'Vlc']"
```

Re-running the get shows vlc added, a log out/in is likely required
> doug@doug-alienware:~$ gsettings get com.canonical.Unity.Panel  systray-whitelist ['JavaEmbeddedFrame', 'Audacious', 'Opera', 'Vlc']

---

### Post by ron999 on 2011-05-21
Hi
With FFmpeg we have commands:-
```
ffmpeg -codecs
```
and
```
ffmpeg -formats
```
to show which de-coders and en-coders are available.

Are there some equivalent commands for VLC?

---

### Post by andrew.46 on 2011-05-21
I will have to admit that I have not delved far into the commandline use of vlc but either *cvlc --list* and *cvlc --list-verbose* would be a start. For example:

```

andrew@skamandros~$ **[COLOR="Red"]cvlc --list | grep -i 264[/COLOR]**
VLC media player 1.2.0-git Twoflower (revision 7813291)
  h264                   H264 video demuxer
  packetizer_h264        H.264 video packetizer
  x264                   H.264/MPEG4 AVC encoder (x264)

```

I have not investigated much further than this but my suspicion is that MPlayer and FFmpeg can be interrogated a little more easily :).

---

### Post by ron999 on 2011-05-21
> **andrew.46 said:**
>  but either *cvlc --list* and *cvlc --list-verbose* would be a start.

Good idea.:P

These commands seem to do the job:-
```
cvlc --list | grep -i encoder
cvlc --list | grep -i decoder
cvlc --list | grep -i " muxer"
cvlc --list | grep -i demuxer
```

The reason why I wanted to know this...
I don't think it's possible to encode MPEG-4 Part 2 video with modern VLCs, 'vcodec=mp4v' doesn't seem to work any more.
But MPEG-4 Part 10 is fine, 'vcodec=x264' works OK.

```
ron@ubuntu:~$ cvlc --list | grep -i encoder
VLC media player 1.2.0-git Twoflower (revision 2023e0b)
  flac                   Flac audio encoder
  t140                   T.140 text encoder
  dvbsub                 DVB subtitles encoder
  vorbis                 Vorbis audio encoder
  dmo                    DirectMedia Object encoder
  avcodec                FFmpeg audio/video encoder
  speex                  Speex audio encoder
  twolame                Libtwolame audio encoder
  theora                 Theora video encoder
  araw                   Raw audio encoder
  x264                   H.264/MPEG4 AVC encoder (x264)
  lpcm                   Linear PCM audio encoder
  stats                  Stats encoder function
  dummy                  Dummy encoder function
```

---

### Post by andrew.46 on 2011-06-07
I have altered the instructions for compiling the release version to the latest release:

```

andrew@corinth:~$**[COLOR="Red"] cvlc --version[/COLOR]**
VLC media player 1.1.10 The Luggage (revision exported)
VLC version 1.1.10 The Luggage (exported)
Compiled by andrew on corinth (Jun  7 2011 20:30:42)
Compiler: gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) 
This program comes with NO WARRANTY, to the extent permitted by law.
You may redistribute it under the terms of the GNU General Public License;
see the file named COPYING for details.
Written by the VideoLAN team; see the AUTHORS file.

```

Not sure how many are compiling the release version from this guide but here it is anyway :). I might add in the vlmc mini guide that I had a while ago over the next week or so as well...

---

### Post by qyot27 on 2011-06-07
> **andrew.46 said:**
> I might add in the vlmc mini guide that I had a while ago over the next week or so as well...
This would help tremendously.  I've been wanting to do another test of VLMC lately and seem to have misplaced the previous guide.

---

### Post by andrew.46 on 2011-06-08
> **qyot27 said:**
> This would help tremendously.  I've been wanting to do another test of VLMC lately and seem to have misplaced the previous guide.

I shall have a good luck at vlmc over the next few days and add it to the guide this weekend. From memory it builds reasonably well with the build environment established by this guide but doubtless there will be a few small issues to be sorted out :).

---

### Post by andrew.46 on 2011-06-08
OK here is a little test install for vlmc:

```

sudo apt-get -y install cmake frei0r-plugins-dev && cd $HOME/vlc_build && \
git clone git://git.videolan.org/vlmc.git --depth 1 && cd vlmc && \
wget -N http://www.andrews-corner.org/patches/vlmc_CMakeLists.diff && \
patch -p1 < vlmc_CMakeLists.diff && \
mkdir $HOME/vlc_build/vlmc/build && cd $HOME/vlc_build/vlmc/build && \
cmake .. && make && cpack -G DEB && \
sudo dpkg -i vlmc-0.2.0git*.deb

```

If this works well enough for a few people I will add it to the main guide on the weekend and add in an 'Update vlmc...' section as well. Comments please!!

---

### Post by qyot27 on 2011-06-10
> **andrew.46 said:**
> OK here is a little test install for vlmc:

```

sudo apt-get -y install cmake frei0r-plugins-dev && cd $HOME/vlc_build && \
git clone git://git.videolan.org/vlmc.git --depth 1 && cd vlmc && \
wget -N http://www.andrews-corner.org/patches/vlmc_CMakeLists.diff && \
patch -p1 < vlmc_CMakeLists.diff && \
mkdir $HOME/vlc_build/vlmc/build && cd $HOME/vlc_build/vlmc/build && \
cmake .. && make && cpack -G DEB && \
sudo dpkg -i vlmc-0.2.0git*.deb

```

If this works well enough for a few people I will add it to the main guide on the weekend and add in an 'Update vlmc...' section as well. Comments please!!
It built fine, but I didn't get much chance to test it.

One other point was that to get VLC itself to build, I had to install libxcb-composite0-dev.  It failed on configure otherwise.

---

### Post by andrew.46 on 2011-06-10
> **qyot27 said:**
> It built fine, but I didn't get much chance to test it.

One other point was that to get VLC itself to build, I had to install libxcb-composite0-dev.  It failed on configure otherwise.

Thanks for looking at this, I am not completely happy with the cmake instructions being patched in this way (should be able to do this by commandline line) and cpack is new to me but it certainly builds a decent package that integrates with the package manager. I shall add in the instructions this afternoon as well as the additional dependency.

Thanks again!

---

### Post by andrew.46 on 2011-06-12
OK the vlmc section has been added in + the missing dependency. Interested to hear if anybody has been using vlmc, I have had a quick look at it only...

---

### Post by pauljayd on 2011-06-21
For Windows ?
Is there some slight variation in this procedure which will generate the Windows production version of vlc?

Thanks,

pauljayd

---

### Post by andrew.46 on 2011-06-22
> **pauljayd said:**
> Is there some slight variation in this procedure which will generate the Windows production version of vlc?

I believe it is possible but my knowledge of crosscompiling vlc is close to zero :(. The starting point is here:

How to compile VLC for Windows 
[http://wiki.videolan.org/Win32Compile](http://wiki.videolan.org/Win32Compile)

But I am afraid I cannot guide you any further than this. Hopefully somebody following this thread can help a little more... I note that there seems to be better documentation for [building vlc as a native windows application using MinGW and MSYS]("http://wiki.videolan.org/Win32CompileMSYSNew"), perhaps this might be a better path. I have used MinGW and MSYS before (with the [newsreader slrn]("http://www.andrews-corner.org/slrn-windows.html")) and it is a fascinating world there!

---

### Post by pauljayd on 2011-06-22
Andrew.46,
Thanks for the quick response. 
I actually realized that what I wanted to do was just change the install process - Always include Mozilla, Not create any file associations, Skip "Do you want to run" query at finish.

So I downloaded the .zip file, installed NSIS, and have modified the .nsi file for my use.

The idea was to provide a downloadable vlc for use on pages, without disturbing users' current media-play environment. I would eventually like to remove all support for anything other than a few specific file-types, thus making the download very fast, but that's another project.

Thanks again for the the attention, links, etc.

PaulJayD

---

### Post by andrew.46 on 2011-06-22
I have upgraded the FFmpeg libraries to the release version FFmpeg 0.8 "Love". Runs well enough on the 64bit Natty but please post any problems here as usual.

```

andrew@corinth:~$ cvlc --version
VLC media player 1.2.0-git Twoflower (revision 2d689e4)
VLC version 1.2.0-git Twoflower (2d689e4)
Compiled by andrew on corinth (Jun 23 2011 10:12:00)
Compiler: gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) 
This program comes with NO WARRANTY, to the extent permitted by law.
You may redistribute it under the terms of the GNU General Public License;
see the file named COPYING for details.
Written by the VideoLAN team; see the AUTHORS file.

```

---

### Post by qyot27 on 2011-06-23
Am I the only one that laughed at the codenames for the releases of 0.8 ("Love") and 0.7.1 ("Peace") appearing together on the Download page?  I can't seem to say those together except in a weird, Japanese Engrish-y accent.

Also, I find those codenames just a tad bit ironic considering all the stuff going on with FFmpeg.

---

### Post by FakeOutdoorsman on 2011-06-23
Makes me think of a particular Pogue's album title.

---

### Post by andrew.46 on 2011-06-23
I am not sure who actually names the releases but in all my reading of the recent FFmpeg soap opera I had not ever suspected that Michael Niedermayer had a sense of humour :).

---

### Post by andrew.46 on 2011-07-05
Actually Ron I seem to have made the apple trailers work by simply copying the share/lua/sd/appletrailers.lua file from the source to ~/.local/share/vlc/lua/sd and all appears to be working. Cover art does not download properly and most of the films are rubbish but otherwise it seems ok :).

---

### Post by mc4man on 2011-07-05
Ron - happen to have a lucid install I'm testing some thing on, there was a vlc 1.1.7 available so installed and - (noting it installs to /usr
In /user/share/vlc/lua there is only a http folder so,
created 2 folders, sd and playlist
Then copied in  appletrailers.lua from the git source from those 2 folders into their respective new folders, make sure they go into the correct folder (the sd one is considerably larger

---

### Post by ron999 on 2011-07-05
> **mc4man said:**
> 
In /user/share/vlc/lua there is only a http folder so,
created 2 folders, sd and playlist
Then copied in  appletrailers.lua from the git source from those 2 folders into their respective new folders, make sure they go into the correct folder (the sd one is considerably larger
Hi
I've created playlist and sd folders in usr/share/vlc/lua folder.
I've copied
appletrailers.lua (3.3KB) from vlc_build/share/lua/playlist
and 
appletrailers.lua (1.8KB) from vlc_build/share/lua/sd

But Apple Trailers doesn't show in the listing.
(Using VLC-v1.1.10)

---

### Post by mc4man on 2011-07-05
> Hi
I've created playlist and sd folders in usr/share/vlc/lua folder.
I've copied
appletrailers.lua (3.3KB) from vlc_build/share/lua/playlist
and
appletrailers.lua (1.8KB) from vlc_build/share/lua/sd

But Apple Trailers doesn't show in the listing.
(Using VLC-v1.1.10)

Went ahead and tried on natty - 
This is the first  time I've tried the copy method, as mentioned worked fine on lucid, though needed to copy both .lua's.

normally the scripts are installed to /usr/lib/vlc... as .luac files though using the .lua script instead should and does work. (somewhat..

First, are you installing to /usr or usr/local? (the .lua's should match location.
If you are copying in the sd/lua then don't edit it in the build, the playlist luac is always installed, doesn't seem to matter one way or the other

As far as natty some inconsistent results, on one install shows up and works fine though the names are truncated. (truncated names seems to be a natty issue here.
This is with a 1.2 I built about a month ago, (didn't edit in the lua).
If I remove it and use either  fresh builds of 1.2 or the repo 1.1.9 it shows but doesn't play. (On a fresh builds, one  where I included the lua's and one without using copy method

On another natty install shows up ok but will not play with the exact same 1 month ago build as above, nor with the repo  or master ppa build.

So went ahead on that install, got a snapshot of the commit prior to the trailers being removed and built it. That install works fine except for truncated names. (uses just the 2 .luac files in /usr/local/lib/vlc/..

So to recap - _is always showing up_ but not always playing, from the terminal everything looks good in those cases except after the file is "successfully opened", nothing happens.
Have not been able to get 1.1.X working on natty, though haven't tried a build, just the repo version

Seems a bit of a mystery here, though natty and the upcoming O are quite prone to inconsistent behavior from what I've seen
A sign here that it will work is while there are truncated names the alt. view will show art. - screen s show on natty, for lucid and I'm sure maverick I get what Andrew shows

Edit: noe trying the default 1.10 in O, all looks goog, full names, art, just don't play - screen 3
maybe can figure out why, maybe not..

---

### Post by ron999 on 2011-07-06
> **mc4man said:**
> 
Edit: noe trying the default 1.10 in O, all looks goog, full names, art, just don't play - screen 3
maybe can figure out why, maybe not..
Perhaps the lua script needs to be 'hard coded' during compilation. As in early versions of VLC-git.

EDIT
Natty Narwhal didn't run very well on my PC.
So I've downgraded to Lucid Lynx.
Using this tutorial VLC-v1.1.8 and VLC-v1.1.9 have compiled OK against FFmpeg-0.7.1.

---

### Post by buana32 on 2011-07-12
Hi all,

I'm trying to compile vlc release 1.1.10 on mythbuntu 10.04 so I can use it to stream I tried to run this on lucid, it fails at the vlc compilation point. I'm trying to compile a 1.1.10 release. The ffmpeg and x264 completed compilation without errors.

The error I keep seeing is below:

[http://pastebin.com/cJ5YEQnq](http://pastebin.com/cJ5YEQnq)

Is there something I'm missing? Thanks in advance

---

### Post by andrew.46 on 2011-07-18
> **buana32 said:**
> I'm trying to compile vlc release 1.1.10 on mythbuntu 10.04 so I can use it to stream I tried to run this on lucid, it fails at the vlc compilation point.

I have to admit that I know nothing of Mythbuntu and my focus is always on compiling under the *latest* Ubuntu release. But perhaps an easy fix would be to add *--disable-pulse* to the ./configure options. But I am not sure why pulse is giving trouble here....

---

### Post by mc4man on 2011-07-18
> i'm trying to compile vlc release 1.1.10 ...
Try with the 1.1.11 source or track down the commit

[http://trac.videolan.org/vlc/ticket/4905](http://trac.videolan.org/vlc/ticket/4905)

---

### Post by buana32 on 2011-07-21
Thanks fellas. I thought maybe there was something I could do about it, but enable pulse didn't work. I then went with 1.1.11, that compiled fine, the graphics are still a bit wonky but it'll do since I primarily want to use it for streaming.

---

### Post by ModusPwnens on 2011-07-22
Hello. I just cloned the main vlc git repo and the mozilla plugin repo. How do I build them such that I won't get the "missing plugin" error on the test.html page?

---

### Post by andrew.46 on 2011-07-22
> **buana32 said:**
> Thanks fellas. I thought maybe there was something I could do about it, but enable pulse didn't work. I then went with 1.1.11, that compiled fine, the graphics are still a bit wonky but it'll do since I primarily want to use it for streaming.

Oops, that was a glorious typo on my behalf :(. Of course I actually meant to write *[COLOR="Red"]--disable-pulse[/COLOR]* .....

---

### Post by andrew.46 on 2011-07-23
> **ModusPwnens said:**
> Hello. I just cloned the main vlc git repo and the mozilla plugin repo. How do I build them such that I won't get the "missing plugin" error on the test.html page?

Unfortunately I have never really built the plugin but hopefully others in this thread can lend a hand.

On a separate note I have upgraded the 'release' version of vlc to 1.1.11, looks like a few people have been using this guide to build the release version so I guess I will still still track it...

---

### Post by mc4man on 2011-07-23
> **andrew.46 said:**
> Unfortunately I have never really built the plugin but hopefully others in this thread can lend a hand.

On a separate note I have upgraded the 'release' version of vlc to 1.1.11, looks like a few people have been using this guide to build the release version so I guess I will still still track it...
The dev version always seems to have something up, better or worse
In 11.10 there have been a few improvement, though it would be nice if they'd do a 1.2 release so they could be refined
Vlc now can show as an indicator instead of systray icon and there's some sound menu support, screen shows both

On neg side in 11.04 & 11.10 can no longer save playlists, nothing happens
There's a new magnifying slider,  how useful ..?

I haven't built, used the mozilla plugin in some time either, it was separated out for lack of dev and because it didn't work well
Not sure that's changed much, if at all.

---

### Post by buana32 on 2011-07-23
Never mind the graphics were fine (my mistake the video display was on by default and squished into 2 pixels or so...) Thanks guys, great guide you have here.

---

### Post by ModusPwnens on 2011-07-25
Sorry to ask again, but has anyone had any luck building the web-plugin?

---

### Post by bananagins on 2011-09-11
ugh... ran into this error during the "Building vlc-git..." stage:


bluray.c: In function ‘blurayInitTitles’:
bluray.c:234: error: too many arguments to function ‘bd_get_titles’
bluray.c:242: error: too many arguments to function ‘bd_get_title_info’
make[5]: *** [liblibbluray_plugin_la-bluray.lo] Error 1
make[5]: Leaving directory `/home/palmtree/vlc_build/vlc/modules/access'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/palmtree/vlc_build/vlc/modules/access'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/palmtree/vlc_build/vlc/modules/access'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/palmtree/vlc_build/vlc/modules'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/palmtree/vlc_build/vlc'
make: *** [all] Error 2

and that ended the operation and went back to prompt. also i saw this at the beginning... is this a problem too?


Initialized empty Git repository in /home/palmtree/vlc_build/vlc/.git/
remote: Counting objects: 27061, done.
remote: Compressing objects: 100% (19229/19229), done.
remote: Total 27061 (delta 18406), reused 13408 (delta 7496)
Receiving objects: 100% (27061/27061), 71.54 MiB | 1.57 MiB/s, done.
Resolving deltas: 100% (18406/18406), done.
NOTE: GNU gettext appears to be missing or out-of-date.
Please install or update GNU gettext.
Also check if you have cvs, a dependency of autopoint.
Otherwise, you will not be able to build a source tarball.


any ideas? mc4man?

---

### Post by bananagins on 2011-09-11
> **bananagins said:**
> ugh... ran into this error during the "Building vlc-git..." stage:


bluray.c: In function ‘blurayInitTitles’:
bluray.c:234: error: too many arguments to function ‘bd_get_titles’
bluray.c:242: error: too many arguments to function ‘bd_get_title_info’
make[5]: *** [liblibbluray_plugin_la-bluray.lo] Error 1
make[5]: Leaving directory `/home/palmtree/vlc_build/vlc/modules/access'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/palmtree/vlc_build/vlc/modules/access'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/palmtree/vlc_build/vlc/modules/access'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/palmtree/vlc_build/vlc/modules'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/palmtree/vlc_build/vlc'
make: *** [all] Error 2

and that ended the operation and went back to prompt. also i saw this at the beginning... is this a problem too?


Initialized empty Git repository in /home/palmtree/vlc_build/vlc/.git/
remote: Counting objects: 27061, done.
remote: Compressing objects: 100% (19229/19229), done.
remote: Total 27061 (delta 18406), reused 13408 (delta 7496)
Receiving objects: 100% (27061/27061), 71.54 MiB | 1.57 MiB/s, done.
Resolving deltas: 100% (18406/18406), done.
NOTE: GNU gettext appears to be missing or out-of-date.
Please install or update GNU gettext.
Also check if you have cvs, a dependency of autopoint.
Otherwise, you will not be able to build a source tarball.


any ideas? mc4man?

ignore this. i had forgotten to delete my ppa version of mplayer.

---

### Post by mc4man on 2011-09-11
Edit:  - didn;t see your repost - not sure where you stand?

> **bananagins said:**
> ugh... ran into this error during the "Building vlc-git..." stage:


bluray.c: In function &#8216;blurayInitTitles&#8217;:
bluray.c:234: error: too many arguments to function &#8216;bd_get_titles&#8217;

and that ended the operation and went back to prompt. also i saw this at the beginning... is this a problem too? 


Just to confirm - this is on maverick?

Several things - 
by default maverick doesn't have libbluray* - how did you install those libs?

Again - like jack, if you don't use something it can be removed from the configure or if the version you have is causing issues you can try to get a different or newer version.
Vlc does a lot of auto detect - so in many cases to remove something from a configure you can simply uninstall the -dev package if installed that way or do so thru the ./configure ie.
--disable-bluray 

[COLOR="Blue"]There are 4 sources that will give a maverick build some issue, without having a maverick install can't quite say if resolvable[/COLOR]
pulseaudio - could be a real issue
schroedinger  - may need to be upgraded or removed in ./configure
bluray - same as above
liborc (maybe needs to be upgraded

[COLOR="Blue"]What you may want to try[/COLOR]  - 
add the videolan ppa, then open synaptic, click on reload
Then click on 'Origin', find the ppa and click on the 'main' entry, you see all of the above, upgrade as possible - you can then disable the ppa

Then try your vlc build again 
For troubleshooting or in general I'd break the vlc build command up into 4 sections (you may want to open your terminal > edit > profile preferences  > scrollback and either enable unlimited if there or up the lines to 3000 or so.

If you are trying again from existing vlc source then
```
cd $HOME/vlc_build/vlc && git pull && ./bootstrap && \
export PKG_CONFIG_PATH="$HOME/vlc_build/vlcdeps/usr/lib/pkgconfig" && \
if [ ! "$(uname -m)" = "x86_64" ]; then
 ARCHOPTS="--enable-loader"
else
  ARCHOPTS=""
fi
```
```
./configure $ARCHOPTS \
            --prefix=/usr/local \
            --with-live555-tree=$HOME/vlc_build/live \
            --enable-real \
            --enable-realrtsp \
            --enable-aa \
            --enable-merge-ffmpeg \
            --enable-vcdx \
            --enable-ncurses
```
This will give you a chance to review the configure and or make changes to  - ex.
```
./configure $ARCHOPTS \
            --prefix=/usr/local \
            --with-live555-tree=$HOME/vlc_build/live \
            --enable-real \
            --enable-realrtsp \
            --enable-aa \
            --enable-merge-ffmpeg \
            --enable-vcdx \
            --enable-ncurses \
            --disable-bluray  
```

Then run either 
make or make jobs=4

If you get a compile error on pulse then that's a bit of an issue - If it were me I'd then just --disable-pulse in the configure (or remove libpulse-dev) and use alsa and a specified device in the audio settings for vlc

If it builds ok then finish w/
```
sudo checkinstall --pakdir "$HOME/vlc_build" --backup=no --deldoc=yes --pkgname vlc \
                  --pkgversion "1.2.0-git-$(date +%Y%m%d)-$(git show --abbrev-commit \
                  | grep '^commit' | cut -f2 -d " ")" --fstrans=no \
                  --deldesc=yes --delspec=yes --default && \
make distclean && sudo ldconfig
```

(again - like mplayer, some consideration could be given to using the newer jack libs as dep's or you can change in synaptic prior to your configure or just --disable-jack in your ./configure (if not using jack

---

### Post by bananagins on 2011-09-11
thanks again for your help mc4man. here's the situation:

first, yes, i am on maverick. 

concerning bluray, before i installed mplayer with andrew.46's guide, i had tried a ppa from here: [https://launchpad.net/~motumedia/+archive/mplayer-daily](https://launchpad.net/~motumedia/+archive/mplayer-daily)

that is where libbluray came from. i had forgotten to remove those packages before compiling mplayer from source. apparently, it causes problems with vlc-git using this guide. so i removed the packages and disabled motumedia since i don't need it anymore and re-compiling vlc-git went off without a hitch.

also, thanks for the info on jack and disabling unnecessary options. next time i have errors during compile, i will try ./configure with --disable to fix the problem.


however... now i have encountered a problem with VLMC. here's the relevant portion of the output:

...
Initialized empty Git repository in /home/palmtree/vlc_build/vlmc/.git/
remote: Counting objects: 1346, done.
remote: Compressing objects: 100% (1015/1015), done.
remote: Total 1346 (delta 868), reused 616 (delta 313)
Receiving objects: 100% (1346/1346), 1.40 MiB | 1019 KiB/s, done.
Resolving deltas: 100% (868/868), done.
--2011-09-11 12:41:09--  [http://www.andrews-corner.org/patches/vlmc_CMakeLists.diff](http://www.andrews-corner.org/patches/vlmc_CMakeLists.diff)
Resolving [www.andrews-corner.org](www.andrews-corner.org)... 69.163.193.141
Connecting to [www.andrews-corner.org|69.163.193.141|:80](www.andrews-corner.org|69.163.193.141|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 815 [text/plain]
Saving to: `vlmc_CMakeLists.diff'

100%[======================================================================================================================>] 815         --.-K/s   in 0s      

2011-09-11 12:41:10 (56.8 MB/s) - `vlmc_CMakeLists.diff' saved [815/815]

Hmm...  Looks like a unified diff to me...
The text leading up to this was:
--------------------------
|diff -Naur a//CMakeLists.txt b//CMakeLists.txt
|--- a//CMakeLists.txt	2011-06-09 11:57:15.000000000 +1000
|+++ b//CMakeLists.txt	2011-06-09 11:49:22.000000000 +1000
--------------------------
Patching file CMakeLists.txt using Plan A...
Hunk #1 FAILED at 79.
Hunk #2 succeeded at 267 (offset -1 lines).
1 out of 2 hunks FAILED -- saving rejects to file CMakeLists.txt.rej
done




... and then back to prompt.

here's the CMakeLists.txt.rej:

--- CMakeLists.txt	2011-06-09 11:57:15.000000000 +1000
+++ CMakeLists.txt	2011-06-09 11:49:22.000000000 +1000
@@ -79,7 +79,8 @@
 
 IF (UNIX)
     SET(WITH_PROFILING FALSE CACHE BOOL "Build with profiling support" )
-    SET(CMAKE_INSTALL_PREFIX /usr)
+    SET(CMAKE_INSTALL_PREFIX /usr/local)
+    SET(CPACK_INSTALL_PREFIX "${CMAKE_INSTALL_PREFIX}")
 ENDIF(UNIX)
 
 SET(WITH_GUI TRUE CACHE BOOL "Enable the VLMC's GUI")


it looks like this line (of the guide in the VLMC section) was where the error happened:
patch --verbose -p1 < vlmc_CMakeLists.diff
any ideas?




EDIT: quick follow-up question concerning ./configure... when i do configure --help to see all the configure options, it says, "Options: [defaults in brackets after descriptions]". do the ones that have "autodetect" in brackets mean that it is automatically enabled? e.g.

--enable-vaapi    enable VAAPI code [autodetect]

does this mean --enable-vaapi is automatically added as an option and so i wouldn't have to include it in the ./configure command? (./configure is the same as ./configure --enable-vaapi)?

---

### Post by mc4man on 2011-09-11
> --enable-vaapi enable VAAPI code [autodetect]

does this mean --enable-vaapi is automatically added as an option and so i wouldn't have to include it in the ./configure command? (./configure is the same as ./configure --enable-vaapi)?
Basically yes - if any/all needed libs are found then it will be enabled

As far as the vlmc patch = 
you could manually patch or here I quickly adjusted

```
diff -Naur a//CMakeLists.txt b//CMakeLists.txt
--- a//CMakeLists.txt	2011-06-09 11:57:15.000000000 +1000
+++ b//CMakeLists.txt	2011-06-09 11:49:22.000000000 +1000
@@ -79,8 +79,8 @@
 
 IF (UNIX)
     SET(WITH_PROFILING FALSE CACHE BOOL "Build with profiling support" )
-    SET(CMAKE_INSTALL_PREFIX /usr)
+    SET(CMAKE_INSTALL_PREFIX /usr/local)
     SET(CPACK_INSTALL_PREFIX ${CMAKE_INSTALL_PREFIX})
 ENDIF(UNIX)
 
 SET(WITH_GUI TRUE CACHE BOOL "Enable the VLMC's GUI")
@@ -267,7 +268,7 @@
     #SET(CPACK_SOURCE_STRIP_FILES "")
 ENDIF(WIN32 AND NOT UNIX)
 
-SET(PACKAGE_REQUIRES "libvlc-dev ( >= 1.1.4 ), frei0r-plugins, libqt4-gui ( >= 4.6 ), libqt4-network ( >= 4.6 ), libqt4-svg ( >= 4.6 ), libqt4-xml ( >= 4.6 )")
+SET(PACKAGE_REQUIRES "")
 
 # RPM packages
 INCLUDE ( ${CMAKE_MODULE_PATH}/RpmBuild.cmake )
```

So if trying again, delete the vlmc folder and break into 2 commands
```
sudo apt-get -y install cmake frei0r-plugins-dev && cd $HOME/vlc_build && \
git clone git://git.videolan.org/vlmc.git --depth 1 && cd vlmc && \
wget -N http://www.andrews-corner.org/patches/vlmc_CMakeLists.diff 
```
Now open the .diff in the vlmc folder in text editor  and replace all with above 
Then finish
```
patch --verbose -p1 < vlmc_CMakeLists.diff && \
mkdir $HOME/vlc_build/vlmc/build && cd $HOME/vlc_build/vlmc/build && \
cmake .. && make && cpack -G DEB && \
sudo dpkg -i vlmc-0.2.0git*.deb && \
cd $HOME/vlc_build/vlmc && patch --verbose -R -p1 < vlmc_CMakeLists.diff
```
edit - decided to test, seems fine, the patch should produce this - 
> Hmm...  Looks like a unified diff to me...
The text leading up to this was:
--------------------------
|diff -Naur a//CMakeLists.txt b//CMakeLists.txt
|--- a//CMakeLists.txt	2011-06-09 11:57:15.000000000 +1000
|+++ b//CMakeLists.txt	2011-06-09 11:49:22.000000000 +1000
--------------------------
Patching file CMakeLists.txt using Plan A...
Hunk #1 succeeded at 79.
Hunk #2 succeeded at 267.
done



---

### Post by Linuxisfast on 2011-09-11
Is hardware acceleration working with this build and ATI cards?

---

### Post by bananagins on 2011-09-11
mc4man: thanks again. it worked perfectly.

NOW, almost done. got one more little question (of course unless the compile fails! knock on wood :) )

i'm about to compile release version of vlc. during installations, i have this obsessive habit of including every possible features and options. so, any harm in enabling these in the configure step?

--enable-wma-fixed
--enable-shine
--enable-id3tag
--enable-faad

or should i just go with what's in the script?

./configure $ARCHOPTS \
            --prefix=/usr/local \
            --with-live555-tree=$HOME/vlc_build/live \
            --enable-real \
            --enable-realrtsp \
            --enable-aa \
            --enable-merge-ffmpeg \
            --enable-vcdx \
            --enable-ncurses && \

---

### Post by bananagins on 2011-09-11
> **Linuxisfast said:**
> Is hardware acceleration working with this build and ATI cards?

i would love to answer that if you could just tell me how to test it.

---

### Post by Linuxisfast on 2011-09-11
> **bananagins said:**
> i would love to answer that if you could just tell me how to test it.

Very simple. play any webM, mp3 file and monitor your CPU usage, make sure GPU acceleration tab is checked under codecs for VLC.

---

### Post by bananagins on 2011-09-11
:( :( :(

uh-oh. looks like i spoke too soon. i have some serious problems with vlc-git. to recap, here is what i did:

- everything before compiling vlc-git was ok.
- first time compiling vlc-git, got errors because of libbluray package.
- deleted libbluray + all other packages from motumedia ppa & disabled repo
- deleted vlc folder in ~/vlc_build/
- recompiled vlc-git, no errors; at this time, i didn't actually test the program. installation was reported as success
- compiled vlmc; first time error, after mc4man's patch, success
- building the release version: ran all commands up till (not including) ./configure

before configuring release version, i tried playing some movies and there are some serious problems:

first of all, what are all the different vlcs? here's what i guessed:
 vlc: GUI
cvlc: CLI
nvlc: ncurses?
qvlc: qt?
rvlc: another CLI?
svlc: no clue

there are issues with svlc. just running 'svlc' gives this:
VLC media player 1.2.0-git Twoflower (revision caa3434)
[0x9fd2270] main interface error: no suitable interface module
[0x9fc0908] main libvlc error: interface "default" initialization failed

'cvlc' gives this:
VLC media player 1.2.0-git Twoflower (revision caa3434)
[0x9de5270] dummy interface: using the dummy interface module...

but the terminal just hangs, doesn't give a prompt like rvlc. ctrl-z quits.

vlc, nvlc, qvlc, rvlc seem to work ok.

now the bigger issue is playing videos. nothing seems to work. i got one mpg file to actually get audio and video. though when i tried to seek, these errors would come up:
[0x8659d70] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
[0x8659d70] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
[0x8659d70] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
[0x8659d70] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
[0x8659d70] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
[0x8659d70] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture


for reasons unknown, trying to play avi files gives this error:
[0x9d26260] main decoder error: no suitable decoder module for fourcc `mp4v'. VLC probably does not support this sound or video format.
[0x9d26260] main decoder error: No suitable decoder module
[0x9d26260] main decoder error: VLC does not support the audio or video format "mp4v". Unfortunately there is no way for you to fix this.

the hex numbers are different each time. i get same error messages in GUIs.

mkv & webm gives this error:
[0x8371f30] mkv demux error: cannot find KaxSegment

mp4 gives this error:
[0xaaa51cf0] main decoder error: no suitable decoder module for fourcc `mp4a'. VLC probably does not support this sound or video format.
[0x862b608] main decoder error: no suitable decoder module for fourcc `h264'. VLC probably does not support this sound or video format.


is there a problem because of the initail failed compile? i wanted to delete and do a new fresh install before tackling the problem but i don't know how to undo all the changes to get my system back to how it was before this guide. i just ran tests with various audio and video files on ffmpeg (installed with fakeoutdoorsman's guide) and mplayer (installed with andrew.46's guide) and both seem to be working ok so at least its not a system wide problem and seems to be something with the VLC installation...

i know you guys must be sick of reading my posts... :) i'm really really close to getting this working. i appreciate everyone's (especially mc4man!) help and patience.

---

### Post by bananagins on 2011-09-11
> **Linuxisfast said:**
> Very simple. play any webM, mp3 file and monitor your CPU usage, make sure GPU acceleration tab is checked under codecs for VLC.

i will get on it as soon as i can get it working :) by monitoring cpu usage, you mean just look at cpu % in system monitor?

---

### Post by mc4man on 2011-09-12
Sounds like something is askew with your git build
(as far as undoing, just open synaptic, search vlc and remove. There should be no other vlc packages installed. If there were I would have removed before building vlc.
 
vlc & qvlc are the same, by default vlc uses the qt interface
cvlc needs something to play in the command, ie.
cvlc /path/to/whatever

What does this show from a terminal, post _complete _terminal output
```
vlc -vvv --list |grep avcodec
```

---

### Post by bananagins on 2011-09-12
> **mc4man said:**
> Sounds like something is askew with your git build
(as far as undoing, just open synaptic, search vlc and remove. There should be no other vlc packages installed. If there were I would have removed before building vlc.
 
vlc & qvlc are the same, by default vlc uses the qt interface
cvlc needs something to play in the command, ie.
cvlc /path/to/whatever

What does this show from a terminal, post _complete _terminal output
```
vlc -vvv --list |grep avcodec
```

hmm.. so just apt-get remove vlc? am i right in assuming that all the other stuff like live555, ffmpeg, goom, etc. is contained in the vlc build?

here's the output by the way:

VLC media player 1.2.0-git Twoflower (revision caa3434)
[0x8d81908] main libvlc debug: VLC media player - 1.2.0-git Twoflower
[0x8d81908] main libvlc debug: Copyright © 1996-2011 the VideoLAN team
[0x8d81908] main libvlc debug: revision caa3434
[0x8d81908] main libvlc debug: configured with ./configure  '--enable-loader' '--prefix=/usr/local' '--with-live555-tree=/home/palmtree/vlc_build/live' '--enable-real' '--enable-realrtsp' '--enable-aa' '--enable-merge-ffmpeg' '--enable-vcdx' '--enable-ncurses' 'PKG_CONFIG_PATH=/home/palmtree/vlc_build/vlcdeps/usr/lib/pkgconfig'
[0x8d81908] main libvlc debug: searching plug-in modules
[0x8d81908] main libvlc debug: loading plugins cache file /usr/local/lib/vlc/plugins/plugins.dat
[0x8d81908] main libvlc debug: recursively browsing `/usr/local/lib/vlc/plugins'
[0x8d81908] main libvlc warning: cannot load module `/usr/local/lib/vlc/plugins/codec/libavcodec_plugin.so' (/usr/local/lib/vlc/plugins/codec/libavcodec_plugin.so: undefined symbol: th_encode_free)
[0x8d81908] main libvlc debug: saving plugins cache /usr/local/lib/vlc/plugins/plugins.dat
[0x8d81908] main libvlc debug: plug-ins loaded: 403 modules
[0x8d81908] main libvlc debug: opening config file (/home/palmtree/.config/vlc/vlcrc)
[0x8d81908] main libvlc debug: translation test: code is "C"

---

### Post by mc4man on 2011-09-12
> **bananagins said:**
> hmm.. so just apt-get remove vlc? am i right in assuming that all the other stuff like live555, ffmpeg, goom, etc. is contained in the vlc build?
Yes & no - 
ffmpeg. live555 & x264 where built just for vlc and only in ~/vlc_build
The rest were installed, no real reason to remove


> **bananagins said:**
>  main libvlc debug: VLC media player - 1.2.0-git Twoflower
[0x8d81908] main libvlc debug: Copyright © 1996-2011 the VideoLAN team
[0x8d81908] main libvlc debug: revision caa3434
[0x8d81908] main libvlc debug: configured with ./configure  '--enable-loader' '--prefix=/usr/local' '--with-live555-tree=/home/palmtree/vlc_build/live' '--enable-real' '--enable-realrtsp' '--enable-aa' '--enable-merge-ffmpeg' '--enable-vcdx' '--enable-ncurses' 'PKG_CONFIG_PATH=/home/palmtree/vlc_build/vlcdeps/usr/lib/pkgconfig'
[0x8d81908] main libvlc debug: searching plug-in modules
[0x8d81908] main libvlc debug: loading plugins cache file /usr/local/lib/vlc/plugins/plugins.dat
[0x8d81908] main libvlc debug: recursively browsing `/usr/local/lib/vlc/plugins'
[COLOR="Red"][0x8d81908] main libvlc warning: cannot load module `/usr/local/lib/vlc/plugins/codec/libavcodec_plugin.so' (/usr/local/lib/vlc/plugins/codec/libavcodec_plugin.so: undefined symbol: th_encode_free)[/COLOR]
[0x8d81908] main libvlc debug: saving plugins cache /usr/local/lib/vlc/plugins/plugins.dat
[0x8d81908] main libvlc debug: plug-ins loaded: 403 modules
[0x8d81908] main libvlc debug: opening config file (/home/palmtree/.config/vlc/vlcrc)
[0x8d81908] main libvlc debug: translation test: code is "C"
The red is your issue, vlc is almost worthless without the libavcodec_plugin

What happened not sure, may be maverick related, may be something in procedure, it may be audio related - are you using the pulseaudio libs from maverick or the videolan ppa?

I did the same build today (on 11.10) - no problems, see below
You could remove vlc in synaptic (& any other vlc packages if there), then maybe just start over (delete in vlc_build - 
vlc
vlcdeps
ffmpeg-0.8
x264
Start how-to from x264 section, do it, the ffmpeg section and the vlc section
Look carefully for any errors in the ffmpeg and or vlc builds
(again maybe break the vlc build command right after the configure and review the terminal output

Or if wished - i dump my 11.10 install every week or so, maybe tommorrow. I could do a quick mav. install before the new 11.10 & see what's up with this.

So here the results of command I asked you to post
> $ vlc -vvv --list |grep avcodec
VLC media player 1.2.0-git Twoflower (revision caa3434)
[0x90a9920] main libvlc debug: VLC media player - 1.2.0-git Twoflower
[0x90a9920] main libvlc debug: Copyright © 1996-2011 the VideoLAN team
[0x90a9920] main libvlc debug: revision caa3434
[0x90a9920] main libvlc debug: configured with ./configure  '--enable-loader' '--prefix=/usr/local' '--with-live555-tree=/home/doug/vlc_build/live' '--enable-real' '--enable-realrtsp' '--enable-aa' '--enable-merge-ffmpeg' '--enable-vcdx' '--enable-ncurses' 'PKG_CONFIG_PATH=/home/doug/vlc_build/vlcdeps/usr/lib/pkgconfig'
[0x90a9920] main libvlc debug: searching plug-in modules
[0x90a9920] main libvlc debug: loading plugins cache file /usr/local/lib/vlc/plugins/plugins.dat
[0x90a9920] main libvlc debug: recursively browsing `/usr/local/lib/vlc/plugins'
[0x90a9920] main libvlc debug: saving plugins cache /usr/local/lib/vlc/plugins/plugins.dat
[0x90a9920] main libvlc debug: plug-ins loaded: 410 modules
[0x90a9920] main libvlc debug: opening config file (/home/doug/.config/vlc/vlcrc)
[0x90a9920] main libvlc debug: translation test: code is "C"
  avcodec                FFmpeg audio/video decoder
  avcodec                FFmpeg access
  avcodec                Avformat muxer
  avcodec                Avformat demuxer
  avcodec                FFmpeg deinterlace video filter
  avcodec                FFmpeg audio/video encoder


---

### Post by Linuxisfast on 2011-09-12
> **bananagins said:**
> i will get on it as soon as i can get it working :) by monitoring cpu usage, you mean just look at cpu % in system monitor?

Yes, do you have a ati card?

---

### Post by bananagins on 2011-09-12
> **Linuxisfast said:**
> Yes, do you have a ati card?

yes, i have ati radeon HD 4670 512mb DDR3... hey do you know if vdpau works with ati if i install xvba? or is it only nvidia?

---

### Post by bananagins on 2011-09-12
mc4man: pulseaudio libs are from maverick... i don't even have the videolan ppa in my repos... since i'm compiling from source, is there any reason i need the ppa? or any packages from it?

the pulseaudio+libs version i have is:
1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu21.1 (maverick-updates)

the version i see at [https://answers.launchpad.net/~videolan](https://answers.launchpad.net/~videolan) is:
1:0.9.22-0ubuntu1~maverick1
i don't need this do i?


concerning libavcodec... wondering if this is related...

i have these installed from maverick repo:
libavcodec-dev
libavdevice-dev
libavformat-dev
libavfilter-dev
libavutil-dev


i also have these installed from medibuntu:
libavcodec-extra-52
libavdevice-extra-52
libavformat-extra-52
libavfilter-extra-1
libavutil-extra-50


and notice these from maverick repo (not installed):
libavcodec52
libavdevice52
libavformat52
libavfilter1
libavutil50


what is the difference between libav***-extra-** and libav***** and could that possibly be what's causing the problem? the libav***-dev seem to be independent and can be installed with either of the 2 groups but i need to choose between regular from maverick and the extra from medibuntu as both can not be installed at the same time.



but anyway, ok, i will try fresh install. so i'll delete vlc package from synaptic. (i had already deleted my other vlc packages before using this guide like vlc-nox, vlc-data, vlc-plugin-***)
also, libvlc5 and libvlccore4 were among the vlc packages i deleted before i undertook building from source with this guide for the first time. i do not see them installed right now. in fact, the only vlc package i see installed is 'vlc'. are libvlc5 and libvlccore4 important by any chance? or are they maybe just for the release version? (which i have not installed yet)


ok, so i will:
1.) remove vlc
2.) delete ~/vlc_build/ffmpeg-0.8
              ~/vlc_build/vlc
              ~/vlc_build/vlcdeps
              ~/vlc_build/x264
3.) build x264
            ffmpeg
            vlc-git
and let you know the result.

---

### Post by mc4man on 2011-09-12
```
in fact, the only vlc package i see installed is 'vlc'. are libvlc5 and libvlccore4 important by any chance?
```
They are for a 'package' build of vlc, ie. from the ubuntu repos or a ppa.
I'd remove them before building a vlc.
I'd also remove any libav* -dev packages before building such as libavcodec-dev, libavformat-dev

I can't say for sure - the videlan ppa uses a newer version of pulseaudio for it's maverick builds

I also see the videolan ppa showing a successful git build for maverick dated aug. 30 - something to consider

I hate to suggest what I can't test first, so while if I had maverick I may add the ppa & update pulseaudio can't rightly suggest you do
Though if you were to add the ppa and install it's vlc packages then you'd get a new pulseaudio, libbluray, orc and schroedinger packages as I noted several posts ago (post 314 - just highlighted in blue

---

### Post by bananagins on 2011-09-12
> **mc4man said:**
> ```
in fact, the only vlc package i see installed is 'vlc'. are libvlc5 and libvlccore4 important by any chance?
```
They are for a 'package' build of vlc, ie. from the ubuntu repos or a ppa.
I'd remove them before building a vlc.
I'd also remove any libav* -dev packages before building such as libavcodec-dev, libavformat-dev

I can't say for sure - the videlan ppa uses a newer version of pulseaudio for it's maverick builds

I also see the videolan ppa showing a successful git build for maverick dated aug. 30 - something to consider

I hate to suggest what I can't test first, so while if I had maverick I may add the ppa & update pulseaudio can't rightly suggest you do
Though if you were to add the ppa and install it's vlc packages then you'd get a new pulseaudio, libbluray, orc and schroedinger packages as I noted several posts ago (post 314 - just highlighted in blue

ok, well i removed the devs tried again but still got the same error. my next plan is to remove vlc again, add the videolan ppa, update pulseaudio, and redo x264, ffmpeg, and vlc-git. but as far as you "hating to suggest what you can't test first", why is that? i mean i understand what you mean but worst case, if it messes up my system, couldn't i always just revert back to the pulseaudio version i had before? or is there a another danger to it besides that that i don't know?

...and anyway if THAT doesn't work, then i'll use the ppa for everything. three questions:

1.) if the problem is libavcodec, why would pulseaudio have anything to do with it? i thought pulseaudio is just audio device layer on top of alsa whereas i seem to have a codec problem within vlc...

2.) what exactly is difference between vlc-git and vlc release version? 

3.) if i install vlc-git and vlc release according to this guide (successfully), how do i differentiate the two? the binary for both is 'vlc' right? so how would i tell the system to run one or the other?

---

### Post by mc4man on 2011-09-12
Don't really think it is a pulse audio issue - the undefined suggests an encoder, just was thinking what you had that was different than from the git vlc on the ppa.
Anyway, am on a live session of mav, added the ppa and vlc-1.2 is installed and running fine - screens
 
> $ vlc
VLC media player 1.2.0-git Twoflower (revision 1.2.0~~git20110830+r828)
[0x9333908] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.

Am going to give a build a try though building vlc on a live session can be a stretch
As far as building/installing the 1.2 git & 1.12 release using the how-to - that's not going to work out so well - they're done as pacckage builds (checkinstall) so it's one or the other
Myself have no use for the 1.1X releases, bugged and not as good

---

### Post by mc4man on 2011-09-12
Even though it was close on ram did the git build on a maverick live session (had only a few MB left from 1400+ @ login before the make distclean
No real issues, built & works fine. I did change a few things from the how-to, mainly to save ram, -   only did live555, x264, ffmpeg and vlc sections

Did use the ppa versions of the mentioned 4 sources and to be a bit safer didn't use multiple Jobs on either the ffmpeg and vlc builds
(a couple of other minor changes, shouldn't matter

So there isn't any reason the build shouldn't work out other than some local issue that could be resolved

> vlc -vv --list |grep avcodec
VLC media player 1.2.0-git Twoflower ([COLOR="Blue"]revision 7fd0bb9[/COLOR])
[0x8d3d908] main libvlc debug: VLC media player - 1.2.0-git Twoflower
[0x8d3d908] main libvlc debug: Copyright © 1996-2011 the VideoLAN team
[0x8d3d908] main libvlc debug: revision 7fd0bb9
[0x8d3d908] main libvlc debug: configured with ./configure  '--enable-loader' '--prefix=/usr/local' '--with-live555-tree=/home/ubuntu/vlc_build/live' '--enable-real' '--enable-realrtsp' '--enable-aa' '--enable-merge-ffmpeg' '--enable-vcdx' '--enable-ncurses' 'PKG_CONFIG_PATH=/home/ubuntu/vlc_build/vlcdeps/usr/lib/pkgconfig'
[0x8d3d908] main libvlc debug: searching plug-in modules
[0x8d3d908] main libvlc debug: loading plugins cache file /usr/local/lib/vlc/plugins/plugins.dat
[0x8d3d908] main libvlc debug: recursively browsing `/usr/local/lib/vlc/plugins'
[0x8d3d908] main libvlc debug: saving plugins cache /usr/local/lib/vlc/plugins/plugins.dat
[0x8d3d908] main libvlc debug: plug-ins loaded: 410 modules
[0x8d3d908] main libvlc debug: opening config file (/home/ubuntu/.config/vlc/vlcrc)
[0x8d3d908] main libvlc debug: translation test: code is "C"
  avcodec                FFmpeg audio/video decoder
  avcodec                FFmpeg access
  avcodec                Avformat muxer
  avcodec                Avformat demuxer
  avcodec                FFmpeg deinterlace video filter
  avcodec                FFmpeg audio/video encoder


---

### Post by bananagins on 2011-09-13
> **mc4man said:**
> Even though it was close on ram did the git build on a maverick live session (had only a few MB left from 1400+ @ login before the make distclean
No real issues, built & works fine. I did change a few things from the how-to, mainly to save ram, -   only did live555, x264, ffmpeg and vlc sections

Did use the ppa versions of the mentioned 4 sources and to be a bit safer didn't use multiple Jobs on either the ffmpeg and vlc builds
(a couple of other minor changes, shouldn't matter

So there isn't any reason the build shouldn't work out other than some local issue that could be resolved

any idea what those local issues may be? :)

well here's the update. 
1.) tried reinstalling vlc-git with updated pulseaudio drivers. same error.
2.) deleted that, installed vlc-git from videolan ppa along with bluray, and upgraded schroedinger and librc. result was better than before but still pretty broken...
   + mkv still gave same error.
   + avi video was ok. audio inconsistent. (sometimes worked, sometimes failed, sometimes partially worked...)  had a REALLY REALLY strange thing happen sometimes where background sound and music would be audible but the dialog wasn't!! bizarre.
   + mp4 seemed ok, flv, webm wouldn't play at all.
   + wmv played ok.
   + choosing audio channels blocked out sometimes. (another strange error)
   + one positive was that an avi video file multiplexed with ac3 audio loaded correctly instead of giving an error (VLC does not support the audio or video format 'undf') like the maverick repo version did. (the whole reason i went about installing dev versions of ffmpeg, mplayer, and vlc)

this libavcodec error seems really strange considering i have no codec trouble with ffmpeg or mplayer... 

seeing as that wasn't really a workable version to have, i ended up deleting that as well. downgrading the packages upgraded through videolan ppa proved to be quite tricky but was able to do it after a little tweaking.

at this point, i was going to redo the relevant parts of this guide (x264, ffmpeg) but try installing the release version... that is unless you have any other ideas to how i can get vlc-git working...

---

### Post by bananagins on 2011-09-13
ok, built the release version... everything seems to be ok except that damn 'undf' error i had with v1.1.4 is still there... but other than that, everything runs perfect. here's the output.


VLC media player 1.1.11 The Luggage (revision exported)
[0x8653914] main libvlc debug: VLC media player - 1.1.11 The Luggage
[0x8653914] main libvlc debug: Copyright © 1996-2011 the VideoLAN team
[0x8653914] main libvlc debug: revision exported
[0x8653914] main libvlc debug: configured with ./configure  '--enable-loader' '--prefix=/usr/local' '--with-live555-tree=/home/palmtree/vlc_build/live' '--enable-real' '--enable-realrtsp' '--enable-aa' '--enable-merge-ffmpeg' '--enable-vcdx' '--enable-ncurses' 'PKG_CONFIG_PATH=/home/palmtree/vlc_build/vlcdeps/usr/lib/pkgconfig'
[0x8653914] main libvlc debug: translation test: code is "C"
[0x8653914] main libvlc debug: checking plugin modules
[0x8653914] main libvlc debug: loading plugins cache file /usr/local/lib/vlc/plugins/plugins-04041e-1f8.dat
[0x8653914] main libvlc debug: recursively browsing `/usr/local/lib/vlc/plugins'
[0x8653914] main libvlc debug: saving plugins cache /usr/local/lib/vlc/plugins/plugins-04041e-1f8.dat
[0x8653914] main libvlc debug: module bank initialized (404 modules)
  avcodec                FFmpeg audio/video decoder
  avcodec                FFmpeg access
  avcodec                FFmpeg muxer
  avcodec                FFmpeg demuxer
  avcodec                FFmpeg deinterlace video filter
  avcodec                FFmpeg audio/video encoder


now why can't the git version install like this? :) very frustrating... i guess there's some conflict between my system's packages/settings and the way vlc-git is compiled?

---

### Post by mc4man on 2011-09-13
> **bananagins said:**
> ok, built the release version... everything seems to be ok except that damn 'undf' error i had with v1.1.4 is still there... but other than that, everything runs perfect. here's the output.
now why can't the git version install like this? :) very frustrating... i guess there's some conflict between my system's packages/settings and the way vlc-git is compiled?
Can't really say, all went well on a live session which was obviously 'pristine' as far as libs, ppa's, ect. vs. what may have been done previously on your install.

As to files that cause you issue, if the opportunity arises to provide a sample or link to a file(s) that cause you issue then others could give them a try to see.
(using 10.10 for a bit I'm reminded how smoothly & quick ubuntu used to be pre 11.04+

---

### Post by andrew.46 on 2011-09-17
> **mc4man said:**
> (using 10.10 for a bit I'm reminded how smoothly & quick ubuntu used to be pre 11.04+

Indeed, the current Ubuntu used to run on my laptop as well but not any more......

---

### Post by FakeOutdoorsman on 2011-09-17
Why is that? Unity?

---

### Post by andrew.46 on 2011-09-18
> **FakeOutdoorsman said:**
> Why is that? Unity?

I suspect a combination of an underpowered laptop + a VM + Unity..... Instead I run Unity etc with VirtualBox on the nice desktop I built for my wife, when she allows me to use it :(.

---

### Post by bananagins on 2011-09-23
andrew.46: you don't by any chance know how to fix this error, do you?

i followed your guide to the letter installing vlc-git on maverick and though there weren't any errors during the installation, it is obvious that it didn't compile correctly as almost all video files fail to play. the output for:

```
vlc -vvv --list |grep avcodec
```

is this:

```
VLC media player 1.2.0-git Twoflower (revision caa3434)
[0x8d81908] main libvlc debug: VLC media player - 1.2.0-git Twoflower
[0x8d81908] main libvlc debug: Copyright © 1996-2011 the VideoLAN team
[0x8d81908] main libvlc debug: revision caa3434
[0x8d81908] main libvlc debug: configured with ./configure '--enable-loader' '--prefix=/usr/local' '--with-live555-tree=/home/palmtree/vlc_build/live' '--enable-real' '--enable-realrtsp' '--enable-aa' '--enable-merge-ffmpeg' '--enable-vcdx' '--enable-ncurses' 'PKG_CONFIG_PATH=/home/palmtree/vlc_build/vlcdeps/usr/lib/pkgconfig'
[0x8d81908] main libvlc debug: searching plug-in modules
[0x8d81908] main libvlc debug: loading plugins cache file /usr/local/lib/vlc/plugins/plugins.dat
[0x8d81908] main libvlc debug: recursively browsing `/usr/local/lib/vlc/plugins'
[COLOR="Red"][0x8d81908] main libvlc warning: cannot load module `/usr/local/lib/vlc/plugins/codec/libavcodec_plugin.so' (/usr/local/lib/vlc/plugins/codec/libavcodec_plugin.so: undefined symbol: th_encode_free)[/COLOR]
[0x8d81908] main libvlc debug: saving plugins cache /usr/local/lib/vlc/plugins/plugins.dat
[0x8d81908] main libvlc debug: plug-ins loaded: 403 modules
[0x8d81908] main libvlc debug: opening config file (/home/palmtree/.config/vlc/vlcrc)
[0x8d81908] main libvlc debug: translation test: code is "C"
```

the red part is obviously the problem but no idea how to fix it. i currently have the release version installed (also using your guide) and that is working ok... the output for the same command gives this:

```
VLC media player 1.1.11 The Luggage (revision exported)
[0x97b0914] main libvlc debug: VLC media player - 1.1.11 The Luggage
[0x97b0914] main libvlc debug: Copyright © 1996-2011 the VideoLAN team
[0x97b0914] main libvlc debug: revision exported
[0x97b0914] main libvlc debug: configured with ./configure  '--enable-loader' '--prefix=/usr/local' '--with-live555-tree=/home/palmtree/vlc_build/live' '--enable-real' '--enable-realrtsp' '--enable-aa' '--enable-merge-ffmpeg' '--enable-vcdx' '--enable-ncurses' 'PKG_CONFIG_PATH=/home/palmtree/vlc_build/vlcdeps/usr/lib/pkgconfig'
[0x97b0914] main libvlc debug: translation test: code is "C"
[0x97b0914] main libvlc debug: checking plugin modules
[COLOR="Red"][0x97b0914] main libvlc debug: loading plugins cache file /usr/local/lib/vlc/plugins/plugins-04041e-1f8.dat[/COLOR]
[0x97b0914] main libvlc debug: recursively browsing `/usr/local/lib/vlc/plugins'
[COLOR="Red"][0x97b0914] main libvlc debug: saving plugins cache /usr/local/lib/vlc/plugins/plugins-04041e-1f8.dat[/COLOR]
[0x97b0914] main libvlc debug: module bank initialized (404 modules)
  avcodec                FFmpeg audio/video decoder
  avcodec                FFmpeg access
  avcodec                FFmpeg muxer
  avcodec                FFmpeg demuxer
  avcodec                FFmpeg deinterlace video filter
  avcodec                FFmpeg audio/video encoder
```

the plugins cache file is plugins-04041e-1f8.dat in the release version as opposed to just plugins.dat in the git versions... maybe i need the git version to somehow point the plugins cache file to plugins-04041e-1f8.dat like the release version??  of course that is just my extremely novice brain thinking.. maybe you have ideas to make this work?

---

### Post by ron999 on 2011-09-23
Hi
I have the same trouble as bananagins with Natty.

When I compile VLC-1.2.0-git I get messages saying:-
"not got mp4a decoder, nothing you can do about it". :o

Also -vvv shows "[0x9e098f0] main libvlc warning: cannot load module `/usr/local/lib/vlc/plugins/codec/libavcodec_plugin.so' (/usr/local/lib/vlc/plugins/codec/libavcodec_plugin.so". :p

I've seen several similar reports when I google, but the things I've tried haven't cured it.
Gave up because it takes best part of an hour to re-compile each time. :p 

Now I've compiled VLC-1.1.12-git using same method and everything's OK. :D

---

### Post by andrew.46 on 2011-09-23
I am caught a little short here as I have deleted my Natty VMs in preparation for testing the vlc and MPlayer guides under Oneiric beta 2. Hopefully I will be up and running soon.....

---

### Post by mc4man on 2011-09-23
> **ron999 said:**
> Hi
I have the same trouble as bananagins with Natty.

When I compile VLC-1.2.0-git I get messages saying:-
"not got mp4a decoder, nothing you can do about it". :o

Also -vvv shows "[0x9e098f0] main libvlc warning: cannot load module `/usr/local/lib/vlc/plugins/codec/libavcodec_plugin.so' (/usr/local/lib/vlc/plugins/codec/libavcodec_plugin.so". :p
 :D
while I haven't used my natty in quite some time booted to it, updated, cleaned out the vlc_build folder & did today's git as per the how-to
See no issues at all...
I might suggest if trying again - when doing the ffmpeg & vlc builds remove the "jobs=4" from the 2 make commands,  - I have seen that on occasion be an issue, - the builds finish but aren't 'complete'
Also when switching from 1.1 to 1.2 probably best to delete the ~/.config/vlc folder 1st.

---

### Post by FakeOutdoorsman on 2011-09-24
> **mc4man said:**
> I might suggest if trying again - when doing the ffmpeg & vlc builds remove the "jobs=4" from the 2 make commands,  - I have seen that on occasion be an issue, - the builds finish but aren't 'complete'
I've also seen a failed make due to the -j option, but only on one occasion and I can't remember the details.

-Mr. Useless Statement

---

### Post by andrew.46 on 2011-09-25
Hmmm.... any difference with the *--jobs* option removed? I am inclined to remove this from the guide as it is not the correct setting for all processors anyway and can have detrimental effect on overall computer function (if other applications running while compiling).

---

### Post by mc4man on 2011-09-25
> **andrew.46 said:**
> Hmmm.... any difference with the *--jobs* option removed? I am inclined to remove this from the guide as it is not the correct setting for all processors anyway and can have detrimental effect on overall computer function (if other applications running while compiling).

I had an issue here once or twice, though can't remember if it was on laptop(core2duo) or desktop (P4 HT) 
I believe it was in the vlc build where it appeared something wasn't built 'on time' or skipped (didn't pay close enough attention
Do remember the build completed but got a run error on <whatever>.so couldn't be loaded, ect.

I guess if Ron is inclined and or gets the chance to try would be interesting. (My desktop is unusable w/ likely a shot power supply

---

### Post by ron999 on 2011-09-25
> **andrew.46 said:**
> Hmmm.... any difference with the *--jobs* option removed? 

Hi
I haven't got a multicore CPU.
So I didn't use the "jobs=4" option.
Instead of:-
```
make jobs=4 && \
```
I used:-
```
make && \
```

(If I had used "jobs=4" my CPU would have ignored it because it can only do one job simultaneously)

---

### Post by andrew.46 on 2011-09-25
Hmmmm..... I have removed the --jobs syntax anyway. Almost finished with the MPlayer guide for Oneiric then I will download a 64bit Oneiric and rerun the vlc one.

---

### Post by mc4man on 2011-09-25
@Ron - don't know why your git build on 11.04 has those issues - if inclined the videolan ppa has started getting successful builds again, you you see how those packages fare...

A somewhat interesting thing on 11.10 for vlc is the semi-sound menu support & more useful the indicator or systray icon

In 11.10 when vlc is started you'll get an indicator icon thru the sni-qt package. It works ok but doesn't respond to a left click to expose or hide vlc.
What I've done for the moment is remove sni-qt & add vlc to the systray-whitelist where the l. click does work.
(haven't yet explored if vlc can be excluded from  sni-qt without removing

vlc can be added to the whitelist thru dconf-editor or gsettings
For gsettings a get command will give you the current string, that can be used in a set command by placing that string inside ""
get command
```
gsettings get com.canonical.Unity.Panel systray-whitelist
```
Ex. here before vlc
> $ gsettings get com.canonical.Unity.Panel systray-whitelist
['JavaEmbeddedFrame', 'Wine', 'scp-dbus-service', 'Audacious']
setting new
```
gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Wine', 'scp-dbus-service', 'Audacious','Vlc' ]"
```
log out/in will complete

---

### Post by andrew.46 on 2011-10-14
Tested under 64bit Oneiric and all is well. Version bump for FFmpeg to release 0.8.5.

```

andrew@corinth:~$**[COLOR="Red"] cvlc --version | head -n 3[/COLOR]**
VLC media player 1.2.0-git Twoflower (revision f728c46)
VLC version 1.2.0-git Twoflower (f728c46)
Compiled by andrew on corinth (Oct 14 2011 20:27:19)
Compiler: gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) 

```

---

### Post by andrew.46 on 2011-11-12
Looks like the end of a long development cycle is on the way:

> 
VLC media player 'Twoflower' 1.2.0-pre1
This is the first pre-version of VLC 1.2.0, aka 'Twoflower'.
This version is intended to developers, packagers and power-users to report important issues and regressions.
It isn't for the average user (yet).
Listing here the number of changes would be quite long, see the NEWS file.
Thanks for the hard work.


Git entry [here]("http://git.videolan.org/?p=vlc.git;a=tag;h=49a6c7ac8d7f5f27196453e9ec582070f68422fc")...

---

### Post by ron999 on 2011-11-19
Hi
There are six git commits concerning live555 (November 14th).
Does the tutorial need to be tweaked?

Gives messages like this:-
> configure: WARNING: unrecognized options: --with-live555-tree
> configure: WARNING: liveMedia is missing or its installed version is too old:
Version 2010.05.29 or later is required to proceed.
You can get an updated one from [http://www.live555.com/liveMedia](http://www.live555.com/liveMedia)

---

### Post by andrew.46 on 2011-11-19
Thanks ron, looks like this is [the relevant change]("http://git.videolan.org/?p=vlc.git;a=commit;h=0f00db90f4ef1f56c000b9d239722fcd38a347a7"). I shall adjust the guide. As for a newer version I have deliberately used the 'live555-latest.tar.gz' version, this changes with every release by the live555 developers.

**Edit:** Should be right now, just delete the live555 archive and any installation in /usr/lib/live and install the newer version. Mind you on my system vlc still refuses to recognise the live555 libraries:

```

checking for live555 version 1275091200 or later... no
configure: WARNING: liveMedia is missing or its installed version is too old:
Version 2010.05.29 or later is required to proceed.
You can get an updated one from http://www.live555.com/liveMedia .

```

The configure log shows the error:

```

configure:27639: checking for live555 version 1275091200 or later
configure:27661: g++ -E  -I/usr/include/liveMedia -I/usr/include/groupsock -I/usr/include/BasicUsageEnvironment -I/usr/include/UsageEnvironment conftest.cpp
conftest.cpp:144:32: fatal error: liveMedia_version.hh: No such file or directory
compilation terminated.

```

although this file exists on my (slackware) system:

```

root@skamandros/home/andrew# find /usr -name 'liveMedia_version.hh'
/usr/lib/live/liveMedia/include/liveMedia_version.hh

```

The joys of the bleeding edge :). Looks like a simple adjustment of the installation directory is required or a symlink to convince the vlc ./configure script, I shall look again after the family BBQ...

---

### Post by mc4man on 2011-11-19
> **andrew.46 said:**
> Thanks ron, looks like this is [the relevant change]("http://git.videolan.org/?p=vlc.git;a=commit;h=0f00db90f4ef1f56c000b9d239722fcd38a347a7"). I shall adjust the guide. As for a newer version I have deliberately used the 'live555-latest.tar.gz' version, this changes with every release by the live555 developers.

**Edit:** Should be right now, just delete the live555 archive and any installation in /usr/lib/live and install the newer version. Mind you on my system vlc still refuses to recognise the live555 libraries:

```

checking for live555 version 1275091200 or later... no
configure: WARNING: liveMedia is missing or its installed version is too old:
Version 2010.05.29 or later is required to proceed.
You can get an updated one from http://www.live555.com/liveMedia .

```

The configure log shows the error:

```

configure:27639: checking for live555 version 1275091200 or later
configure:27661: g++ -E  -I/usr/include/liveMedia -I/usr/include/groupsock -I/usr/include/BasicUsageEnvironment -I/usr/include/UsageEnvironment conftest.cpp
conftest.cpp:144:32: fatal error: liveMedia_version.hh: No such file or directory
compilation terminated.

```

although this file exists on my (slackware) system:

```

root@skamandros/home/andrew# find /usr -name 'liveMedia_version.hh'
/usr/lib/live/liveMedia/include/liveMedia_version.hh

```

The joys of the bleeding edge :). Looks like a simple adjustment of the installation directory is required or a symlink to convince the vlc ./configure script, I shall look again after the family BBQ...

Sorta interesting - appears vlc is looking in wrong place.(for starters

So that, (configure/configure.ac) can be adjusted to reflect actual paths, then this happens
> checking for live555 version 1275091200 or later... yes
checking for live555 usability... no
configure: error: liveMedia lacks patches and is not usable.
Please apply our patches from the VLC contrib (checking for live555 version 1275091200 or later... yes
checking for live555 usability... no
configure: error: liveMedia lacks patches and is not usable.
Please apply our patches from the VLC contrib (contrib/src/live555/).
/).

getting the live source vlc would use (mentioned in the contrib/src/live555/rules.mak), appling the patches & then doing that live source as normal still produces the 'unpatched' error

(no time to pursue any further tonight, maybe live555 should be built in contrib if it can be done separate from the rest ? 
confident you can resolve.. one way or the other

Otherwise the vlc master ppa is failing on the same 'unpatched' error, could see how they resolve (a packaged live installs to where vlc is looking by default

---

### Post by andrew.46 on 2011-11-19
Using contrib looks like an option although I am not keen. I can make it run by using live.2011.11.08.tar.gz and patching with the 4 vlc patches

```

live-uselocale.patch 
live-inet_ntop.patch 
live-intptr.patch
live-cloexec.patch

```

not sure if live-getaddrinfo.patch is required. Then symlinks:

```

ln -sv /usr/lib/live/liveMedia/include /usr/include/liveMedia && \
ln -sv /usr/lib/live/groupsock/include /usr/include/groupsock && \
ln -sv /usr/lib/live/BasicUsageEnvironment/include /usr/include/BasicUsageEnvironment && \
ln -sv /usr/lib/live/UsageEnvironment/include /usr/include/UsageEnvironment

```

A bit cumbersome but it works, I shall look further when BBQ is over and grandchildren are no longer destroying the place :). Can anybody confirm the above works on their system?

---

### Post by mc4man on 2011-11-19
> Using contrib looks like an option although I am not keen
Not a good option, did get contrib to work, as in just build live555, but hardly worth the effort (it does this insane thing of removing the folder containing the patches and then complaining they can't be found.

After some 'misdirection' it worked & vlc configured fine
> checking for live555 version 1275091200 or later... yes
checking for live555 usability... yes
checking for main in -lliveMedia_pic... no
checking for main in -lliveMedia... yes


Not a viable option so will try your method, I didn't link when trying before

As far as that 1 patch, probably not needed, but this edit worked

```
diff -ru live.orig//groupsock/inet.c live//groupsock/inet.c
--- live.orig//groupsock/inet.c	2010-04-09 22:27:39.000000000 +0300
+++ live//groupsock/inet.c	2010-04-17 20:14:07.000000000 +0300
@@ -76,16 +76,6 @@
 #define NULL 0
 #endif
 
-#if !defined(VXWORKS)
-struct hostent* our_gethostbyname(name)
-     char* name;
-{
-	if (!initializeWinsockIfNecessary()) return NULL;
-
-	return (struct hostent*) gethostbyname(name);
-}
-#endif
-
 #[COLOR="Red"]ifdef USE_SYSTEM_RANDOM[/COLOR]
 /* Use the system-supplied "random()" and "srandom()" functions */
 #include <stdlib.h>
```

---

### Post by mc4man on 2011-11-19
> Can anybody confirm the above works on their system?

Works fine - though you need a sudo for each link
```
sudo ln -sv /usr/lib/live/liveMedia/include /usr/include/liveMedia; \
sudo ln -sv /usr/lib/live/groupsock/include /usr/include/groupsock; \
sudo ln -sv /usr/lib/live/BasicUsageEnvironment/include /usr/include/BasicUsageEnvironment; \
sudo ln -sv /usr/lib/live/UsageEnvironment/include /usr/include/UsageEnvironment
```

There also (here) was something about libspeexdsp1 (libspeexdsp-dev

---

### Post by andrew.46 on 2011-11-20
> **mc4man said:**
> Works fine - though you need a sudo for each link
```
sudo ln -sv /usr/lib/live/liveMedia/include /usr/include/liveMedia; \
sudo ln -sv /usr/lib/live/groupsock/include /usr/include/groupsock; \
sudo ln -sv /usr/lib/live/BasicUsageEnvironment/include /usr/include/BasicUsageEnvironment; \
sudo ln -sv /usr/lib/live/UsageEnvironment/include /usr/include/UsageEnvironment
```


Good! I have to admit that I cobbled that together on my slackware system with the controversial (on Ubuntu) advantage of using su :).

> There also (here) was something about libspeexdsp1 (libspeexdsp-dev

The bbq is ended so I have an hour or so to have a proper look at new developments!

---

### Post by mc4man on 2011-11-20
Thinking maybe the mplayer build deps & vlc deps should use the same jack, it's somewhat interchangeable but libjack-jackd2-dev would be fine for both

---

### Post by andrew.46 on 2011-11-20
> **mc4man said:**
> Thinking maybe the mplayer build deps & vlc deps should use the same jack, it's somewhat interchangeable but libjack-jackd2-dev would be fine for both

Sounds good, I have changed this, thanks :). With regard to live555 at least one of the vlc developers has been a little recalcitrant so I am going to break out a little sed magic for that. I am wary of installing such a heavily patched live555 onto the system so I have been experimenting with:

```

  --with-contrib=DIR      search for 3rd party libraries in DIR/include and
                          DIR/lib


```

which might be the safest way...

---

### Post by mc4man on 2011-11-20
> **andrew.46 said:**
> Sounds good, I have changed this, thanks :). With regard to live555 at least one of the vlc developers has been a little recalcitrant .
Nothing new there - bite first, read later if ever.

As far as the 'latest' 555, the line numbers are correct, but that line isn't. (& line numbers many times don't matter, can be patched with offset.

I guess it would come down to whether vlc patches affect other app's use of 555 if deciding to have 1 installed 555

What I did consider was to install a vlc patched live to /usr/lib/live555 & then link, though never looked at what that would do for mplayer, ect. though I'd think mplayer would use /usr/lib/live

? - are the live files only needed during a build but not after? - it did work out fine building live in  /vlc/contrib/src/live555 though it had to be built the 'contrib' way, if not needed after the vlc build that would be ok



Will be curious as always as to what you work out

---

### Post by andrew.46 on 2011-11-20
> **mc4man said:**
> Will be curious as always as to what you work out

You may have noticed that there has been yet another Live555 release which breaks the vlc patches again :). Anyway I have spent the promised time and hopefully I have not needlessly complicated things as I have been accused of in the past. I have:


[LIST=1]
[*]Updated the FFmpeg libraries to 0.8.6
[*]Saved a copy Live555 2011.11.08 on my website. This copy has a folder inside with the vlc patches and a small note to mention that I have altered live-getaddrinfo.patch to work with this version. Left the gpl license stuff in place of course, I have never seen a gpl'd patch before!!
[*]Set up a 'contrib' folder within* $HOME/vlc_build* containing all of the Live555 headers where vlc can find it without any further interventions. I don't like the vlc 'contrib' system in general so would prefer to avoid using it. This may prove useful in the future for those packages that do not use pkgconfig.
[*]Added libspeexdsp-dev which vlc now requires
[/LIST]

Interesting times for vlc and I have enjoyed the challenge of getting it all working again, hopefully in an efficient and easily understood way :).

**Edit: **As a matter of interest I am running the vlc-patched Live555 libraries on my slackware system, installed to /usr/lib/live and so far no misadventures with MPlayer.

---

### Post by mc4man on 2011-11-21
Looks good, will try tomorrow. I'm gathering that the 4 .a files aren't needed, the default contrib build did move them out along with the various .h* files into a ../../i686-linux-gnu/lib dir., the .h* went obviously into a ../../i686-linux-gnu/include dir.

Anyway good of you to host a working live + patches, sounds like vlc or a vlc contributor will need to keep up with the patches (or not

Stellar job as usual.

---

### Post by andrew.46 on 2011-11-21
> **mc4man said:**
> Looks good, will try tomorrow. I'm gathering that the 4 .a files aren't needed, the default contrib build did move them out along with the various .h* files into a ../../i686-linux-gnu/lib dir., the .h* went obviously into a ../../i686-linux-gnu/include dir.

As far as I could see vlc was only looking for the *.h* files and certainly vlc ran all the streams I tested it with. I may very well add the .a files in for the sake of completion but if I build vlc one more time today I may very well have a stroke :). Mind you it would give me the opportunity to put my longest commandline ever into place:

```

mkdir -pv $HOME/vlc_build/contrib/{include/{liveMedia,groupsock,BasicUsageEnvironment,UsageEnvironment},lib/{liveMedia,groupsock,BasicUsageEnvironment,UsageEnvironment}}

```

and that may be enough to make me do it :). **Edit:** Done! And if there ever is a competition about the longest commandline ever given on these Forums.....

> Anyway good of you to host a working live + patches, sounds like vlc or a vlc contributor will need to keep up with the patches (or not

It makes life a little easier for everybody I think and my site has been rock solid hosting for the last few years...

---

### Post by ron999 on 2011-11-21
Hi Andrew
VLC-git has compiled and installed OK using the live555 archive from your website.=D>
Thanks.

---

### Post by andrew.46 on 2011-11-21
> **ron999 said:**
> VLC-git has compiled and installed OK using the live555 archive from your website.

Great news :). An alternative is the vlc 'contrib' scheme but I cannot warm to this...

---

### Post by mc4man on 2011-11-23
Works just fine, (the new how-to) - did notice something - 
The dvd > no dvd menus is a bit broken atm - doubles up on the device. Also the syntax has changed for title nunber - used to be @title number, now it's #title number

Just for info purposes - see that some older live555 tar's are available here
[http://code.google.com/p/live555sourcecontrol/downloads/list](http://code.google.com/p/live555sourcecontrol/downloads/list)

---

### Post by andrew.46 on 2011-11-28
As a side benefit I can now have a rough idea of the numbers of people using this guide for the first time: the live555 archive on my site has now been downloaded 22 times according to the server logs :).

---

### Post by andrew.46 on 2011-11-28
Looks like the long road to 1.3.0 has started:

```

andrew@skamandros~$ cvlc --version | head -n 1
VLC media player 1.3.0-git Rincewind (revision 1.3.0-git-22-g9d759fe)
VLC version 1.3.0-git Rincewind (1.3.0-git-22-g9d759fe)

```

I will update the section of the guide that builds the release version once 1.2.0 hits the ftp sites.

---

### Post by mc4man on 2011-11-29
So I gather 1.2 has released, normally then 12.04 would get it, will be interesting to see if it does & if so  what they do with liblivemedia-dev

---

### Post by andrew.46 on 2011-11-30
> **mc4man said:**
> So I gather 1.2 has released, normally then 12.04 would get it, will be interesting to see if it does & if so  what they do with liblivemedia-dev

Still waiting for the 1.2 release......

---

### Post by nmickuli on 2011-12-07
I followed your guide on 11.10 and was able to build a working VLC. However, the only RTSP module available is the Real one, which doesn't support all RTSP servers. I disabled it using the configure script (--disable-realrtsp) and tried to add the live555 one (--enable-live555). The configure succeeds, but live555 doesn't appear in the installed plugins list (vlc -l) and VLC says there are no available RTSP demux modules. Another thing I don't understand is why -with-live555-tree is no longer an accepted option to the configure script (I thought live555 had to be statically linked), and the live555 libraries don't seem to get installed with vlc. I know the stream plays correctly on the official Ubuntu builds of 1.2, so it's not a VLC compatibility issue. Any ideas?

---

### Post by andrew.46 on 2011-12-07
Interesting. The death of the '*--with-live555-tree*' option came from the vlc developers who wished that the copy of live555 used be suitably patched. Theis copy of live555 they wished either installed to the system or built through their 'contrib' system. I noticed that even with the realrtsp plugin disabled that a 'real' demuxer is still built:

```


andrew@skamandros~$ **[COLOR="Red"]cvlc -l | grep -i demuxer[/COLOR]**
VLC media player 1.3.0-git Rincewind (revision 1.3.0-git-136-g86d9aab)
  avcodec                Avformat demuxer
  rawaud                 Raw audio demuxer
  mkv                    Matroska stream demuxer
  h264                   H264 video demuxer
  au                     AU demuxer
  avi                    AVI demuxer
  mjpeg                  M-JPEG camera demuxer
  mpgv                   MPEG-I/II video demuxer
  ogg                    OGG demuxer
  rawdv                  DV (Digital Video) demuxer
  voc                    VOC demuxer
**[COLOR="Red"]  real                   Real demuxer[/COLOR]**
  pva                    PVA demuxer
  dirac                  Dirac video demuxer
  nuv                    Nuv demuxer
  ps                     MPEG-PS demuxer
  ps                     MPEG-PS demuxer
  xa                     XA demuxer
  demux_cdg              CDG demuxer
  rawvid                 Raw video demuxer
  ts                     MPEG Transport Stream demuxer
  tta                    TTA demuxer
  flacsys                FLAC demuxer
  vc1                    VC1 video demuxer
  wav                    WAV demuxer
  image                  Image demuxer
  mp4                    MP4 stream demuxer
  asf                    ASF/WMV demuxer
  nsv                    NullSoft demuxer
  smf                    SMF demuxer
  aiff                   AIFF demuxer

```

But indeed a 'live555' demuxer does not show. I am at work at the moment so confined to the horrors of Windows XP, what demuxer does vlc show when opening a stream?

BTW when you say the official Ubuntu build of vlc, this is 1.1.11 on Oneiric, you are using a different version?

---

### Post by mc4man on 2011-12-07
Don't use the live555 plugin so configure out but it looks like you need a yes on either of these
> checking for live555 version 1275091200 or later... yes
checking for live555 usability... yes
[COLOR="Red"]checking for main in -lliveMedia_pic... no
checking for main in -lliveMedia... no

[/COLOR]

So it seems no issue when using the tree option or installing as is done in ubuntu.
A quick check taking the live source as used here, patching, then building/installing as is done in ubuntu  (debian/rules, ect.),  would show this

> checking for live555 version 1275091200 or later... yes
checking for live555 usability... yes
checking for main in -lliveMedia_pic... yes


Then as seen in ~/vlc_build/vlc/config.status 
> S["LIBS_live555"]="-lliveMedia_pic -lgroupsock_pic -lBasicUsageEnvironment_pic -lUsageEnvironment_pic "
S["LTLIBlive555"]="liblive555_plugin.la"
S["CXXFLAGS_live555"]=" -I/usr/include/liveMedia -I/usr/include/groupsock -I/usr/include/BasicUsageEnvironment -I/usr/include/UsageEnvironment"

[COLOR="Red"]EDIT:.[/COLOR]
Andrew - put your *.a files loose in /vlc_build/contrib/lib  - this way they will be found & you'll get a yes, ect. - 

> checking for live555 version 1275091200 or later... yes
checking for live555 usability... yes
checking for main in -lliveMedia_pic... no
checking for main in -lliveMedia... yes



And  - the build from above - 
> $ cvlc -l | grep -i demuxer
VLC media player 1.3.0-git Rincewind (revision 2dc2da8)
  avcodec                Avformat demuxer
  vc1                    VC1 video demuxer
  mjpeg                  M-JPEG camera demuxer
  ts                     MPEG Transport Stream demuxer
  avi                    AVI demuxer
  mkv                    Matroska stream demuxer
  flacsys                FLAC demuxer
  nsv                    NullSoft demuxer
  tta                    TTA demuxer
  mod                    MOD demuxer (libmodplug)
  dirac                  Dirac video demuxer
  rawvid                 Raw video demuxer
  live555                RTP/RTSP/SDP demuxer (using Live555)

---

### Post by nmickuli on 2011-12-07
When I try to open a RTSP stream (with Real RTSP disabled), VLC just says no RTSP demux modules available:

```

[0x18d2c08] main input debug: Creating an input for 'rtsp://localhost:1935/live/feed1.stream'
[0x18d2c08] main input debug: using timeshift granularity of 50 MiB, in path '/tmp'
[0x18d2c08] main input debug: `rtsp://localhost:1935/live/feed1.stream' gives access `rtsp' demux `' path `localhost:1935/live/feed1.stream'
[0x18d2c08] main input debug: creating demux: access='rtsp' demux='' location='localhost:1935/live/feed1.stream' file='(null)'
[0x15f6bd8] qt4 interface debug: IM: Setting an input
[0x1c08158] main demux debug: looking for access_demux module: 0 candidates
[0x1c08158] main demux debug: no access_demux module matched "rtsp"
[0x1c08158] main demux debug: TIMER module_need() : 0.336 ms - Total 0.336 ms / 1 intvls (Avg 0.336 ms)
[0x18d2c08] main input debug: creating access 'rtsp' location='localhost:1935/live/feed1.stream', path='(null)'
[0x1ae1da8] main access debug: looking for access module: 0 candidates
[0x1ae1da8] main access debug: no access module matched "rtsp"
[0x1ae1da8] main access debug: TIMER module_need() : 0.344 ms - Total 0.344 ms / 1 intvls (Avg 0.344 ms)
[0x18d2c08] main input error: open of `rtsp://localhost:1935/live/feed1.stream' failed

```

I don't remember the exact error message with Real RTSP, but it was something like "only real/helix servers supported by this module..."

By "official build" I meant the nightly builds PPA maintained by the VLC team: [https://launchpad.net/~videolan/+archive/master-daily](https://launchpad.net/~videolan/+archive/master-daily). The RTSP stream plays correctly using that build.

Thanks for helping me out with this. I hope to get this working so I can start hacking on VLC a bit myself.

---

### Post by andrew.46 on 2011-12-08
Hmmm... it is all getting a little silly :(. In [the thread here]("http://mailman.videolan.org/pipermail/vlc-devel/2011-November/083594.html") it can be seen that patches are no longer necessary, but the check still confounds 'unpatched' building. When the check is disabled vlc will still not build the demuxer, although as always mc4man has seen a solution. I will flail around a little more but increasingly it looks as if the sensible option is to disable live555 until sanity returns...

---

### Post by mc4man on 2011-12-19
Andrew - have a 12.04 install that I thought I'd run post 1 thru - seems to be missing an initial  mkdir  $HOME/vlc_build

Also - while I'm not exactly clear as to use case vlc will now 'use' libsamplerate0 (Secret Rabbit Code), so libsamplerate0-dev could be added

---

### Post by andrew.46 on 2011-12-26
Hmmm... some success:

```
andrew@skamandros~$ cvlc -l | grep 555
VLC media player 1.2.0-pre2 Twoflower (revision 1.2.0-pre2-23-gb275500)
  live555                RTP/RTSP/SDP demuxer (using Live555)
  live555                RTSP/RTP access and demux
```

but I have no Ubuntu vms atm so resolution on Ubuntu may take a while. Slackware build [here]("http://slackware.org.uk/people/alien/slackbuilds/vlcgit/build/vlcgit.SlackBuild").

---

### Post by andrew.46 on 2011-12-28
Success :). Thanks to alienBOB for showing the way as usual...

---

### Post by mc4man on 2012-01-04
Have noticed that 1.3 segfaults on some NeroAacEnc files I did a couple of yr.'s ago. Seem a bit strange as 1.2pre2 & all other players are fine with.
May try some new encodes to recheck.
The error in case it comes up is - 
vlc ASSERT failure in QList<T>::at: "index out of range"

(Wonder if 1.2 is ever going to be a 'release'

---

### Post by faucon50 on 2012-01-10
Hello, 

Thank you for this howto! Some questions: 

1. Can I use the howto as it is if I'm still on ubuntu 10.10?
2. I would like to enable vaapi, the vlc wiki says:
 
[http://wiki.videolan.org/VLC_VAAPI](http://wiki.videolan.org/VLC_VAAPI)

FFmpeg trunk

Get the latest FFmpeg trunk as of 2010-January. Compile it with vaapi hwaccel support.
./configure --enable-gpl --enable-postproc --prefix=/path/to/ --enable-shared --enable-vaapi
make
make install

Is there a difference with your FFmpeg version or can I use your FFmpeg howto section and just add to configure: --enable-gpl enable-shared --enable-vaapi?

3. For the projectM "plugin", does it fonction with only alsa trough vlc? I know that I had to install jackd for the stand alone projectM because it wont work with only alsa but with pulse and jackd it does!?

4. I don't use pulseaudio because of the SC rme Hammerfall 9632, can I just put --disable pulse to the vlc ./configure option?

5. What about this options: --enable-galaktos --enable-goom, would this confilct with projectM? And to enable goom, what do I have to install? 

6. I have tried the night build 1.3 from the PPA and could'nt get any sound with the complain: unknown 12 channel argument wich as to be in the .asoundrc for the rme 9632. So I'm asking myself if after all the compilations if I will not stuck with this problem and do all that for nothing? If somebody as an experience it's wellcome.

Sorry for thoes questions but I prefer to be shure before starting :P

---

### Post by FakeOutdoorsman on 2012-01-10
> **faucon50 said:**
> can I use your FFmpeg howto section and just add to configure: --enable-gpl enable-shared --enable-vaapi?

*--enable-vaapi* is an autodetected option meaning that FFmpeg will automatically enable it if possible without you having to add *--enable-vaapi*:
```

./configure --help
  --enable-vaapi           enable VAAPI code [autodetect]

```

---

### Post by andrew.46 on 2012-01-10
> **faucon50 said:**
> 1. Can I use the howto as it is if I'm still on ubuntu 10.10?

That is a definite maybe :). I don't usually keep track of older Ubuntu releases and I confess at the moment I have actually lost all my current Ubuntu VMs :(.

> 2. I would like to enable vaapi, 

Definitely follow FakePutdoorsman's lead on this one.

> 3. For the projectM "plugin", does it fonction with only alsa trough vlc? I know that I had to install jackd for the stand alone projectM because it wont work with only alsa but with pulse and jackd it does!?

Not sure about this one as my own computer is a little too underpowered to run ProjectM. Hopefully others can answer this...

> 4. I don't use pulseaudio because of the SC rme Hammerfall 9632, can I just put --disable pulse to the vlc ./configure option?

You should be able to enable or disable whatever suits your system.
> 
5. What about this options: --enable-galaktos --enable-goom, would this confilct with projectM? And to enable goom, what do I have to install? 

I don't believe their will be conflict. To enable goom you will have to compile and install the application, I used to have installation instructions with this guide but when the guide was streamlined recently these were dropped. Not hard to compile though...

> 6. I have tried the night build 1.3 from the PPA and could'nt get any sound with the complain: unknown 12 channel argument wich as to be in the .asoundrc for the rme 9632. So I'm asking myself if after all the compilations if I will not stuck with this problem and do all that for nothing? If somebody as an experience it's wellcome.

The development version will always be a moving target and some instability will always be on the cards. Not sure about this specific problem though...

I will be away from this guide for a while hopefully others can keep things rolling along without me:).

---

### Post by nmickuli on 2012-01-10
> **mc4man said:**
> 
Andrew - put your *.a files loose in /vlc_build/contrib/lib  - this way they will be found & you'll get a yes, ect. - 


Thanks a lot. This worked perfectly.

---

### Post by faucon50 on 2012-01-10
@ FakeOutdoorsman: Thanks, so no need to put enable-vaapi, what about multi-thread (cpu) option, is that one autodetected to, I have seen somewhere that it is?

@ andrew.46: Thank you :) I will have a try and see what gona happen and post the result. :o

Once again, thank you for this guide! :D

---

### Post by FakeOutdoorsman on 2012-01-10
> **faucon50 said:**
> what about multi-thread (cpu) option, is that one autodetected to, I have seen somewhere that it is?

Yes, *--enable-pthreads* is now autodetected as well.

---

### Post by watson88 on 2012-01-11
Thanks a lot i was searching for this for very long time, actually i recently join this forum and i hope got lot of such useful information in future.

---

### Post by andrew.46 on 2012-01-12
> **mc4man said:**
> Have noticed that 1.3 segfaults on some NeroAacEnc files I did a couple of yr.'s ago. Seem a bit strange as 1.2pre2 & all other players are fine with.
May try some new encodes to recheck.
The error in case it comes up is - 
vlc ASSERT failure in QList<T>::at: "index out of range"

Sorry for the delay, I have actually repartitioned my drive and for the first time in 2 years or so I have a 20gig partition for Ubuntu instead of wrestling with VMs. It has taken some time to get it all up and running :).

I created an aac file with the most recent neroAacEnc and this played with no errors on the current vlc-git. Perhaps you used an older neroAacEnc at the time? Love to see a sample....

---

### Post by ron999 on 2012-01-12
Hi
I ended up using contribs to build the patched live555 library.
While doing that, it built some other packages.
Among them were **libebml** and **libmatroska**.
So now my VLC will mux into mkv files.:)

This command uses RTMPDump to pipe a video stream through VLC:-
[http://pastebin.com/5k4VTWCa]("http://pastebin.com/5k4VTWCa")

With RTMPDump it's usual to download flv files.:(
But VLC has good muxers.:)

This command uses VLC to mux the stream into an avi file:-
[http://pastebin.com/sFLNnQ2u]("http://pastebin.com/sFLNnQ2u")
And this command uses VLC to mux the stream into an mkv file:-
[http://pastebin.com/6ZTSdncq]("http://pastebin.com/6ZTSdncq")
:cool:

---

### Post by andrew.46 on 2012-01-12
Very nice Ron :). I tested the matroska output and it worked perfectly. Have you tried using FFmpeg for this?

---

### Post by ron999 on 2012-01-12
> **andrew.46 said:**
> Have you tried using FFmpeg for this?
When I mux mkv with -vvv it shows:-
**Couldn't open mux `mkv', trying `ffmpeg{mux=matroska}' instead**

So maybe FFmpeg can do the job on its own without VLC wrapper.
```
| ffmpeg -i - -c copy foo.mkv
```

.... or maybe VLC will help with buffering etc. I dunno.8)

---

### Post by mc4man on 2012-01-13
> **andrew.46 said:**
> Sorry for the delay, I have actually repartitioned my drive and for the first time in 2 years or so I have a 20gig partition for Ubuntu instead of wrestling with VMs. It has taken some time to get it all up and running :).

I created an aac file with the most recent neroAacEnc and this played with no errors on the current vlc-git. Perhaps you used an older neroAacEnc at the time? Love to see a sample....

It was from files created with an older nero from a couple of years ago - just tried again with the latest 1.3 & now they're fine. Just one of those little bumps in the road..

(I wonder if 1.2 is actually going to release or not?

---

### Post by andrew.46 on 2012-01-15
> **mc4man said:**
> (I wonder if 1.2 is actually going to release or not?

No big rush by the look of it :).

---

### Post by undercash on 2012-01-21
what happens if I already have a system ffmpeg built (using fakeoutmandoor theads)? will I erase it if I follow this tutorial to have a working ffmpeg for vlc?

---

### Post by andrew.46 on 2012-01-21
> **undercash said:**
> what happens if I already have a system ffmpeg built (using fakeoutmandoor theads)? will I erase it if I follow this tutorial to have a working ffmpeg for vlc?

If you have installed FFmpeg according to FakeOutdoorsman's excellent guide you can safely omit the FFmpeg section of this guide and allow vlc to find the system copy.

Bear in mind that there is a subtle difference between the git FFmpeg and the git vlc. The 'development' version of FFmpeg is intended for immediate use by end users while the 'development' version of vlc is *not*. vlc-git is intended to be used by developers and anyone interested in assisting with development at the bleeding edge, and by those curious enough to follow this bleeding edge :).

---

### Post by undercash on 2012-01-21
thanks for your reply

i have ffmpeg installed as I said but when I use  venc=ffmpeg (instead of x264 I assume) i get this error message


```
[0x8990080] avcodec encoder error: cannot find encoder H264 - MPEG-4 AVC (part 10)
*** Your FFMPEG installation is crippled.   ***
*** Please check with your FFMPEG packager. ***
*** This is NOT a VLC media player issue.   ***
[0x8990080] main encoder error: La diffusionÂ*/Â*le transcodage a Ã©chouÃ©
[0x8990080] main encoder error: Il semble que votre installation de FFMPEG (libavcodec) ne comprenne pas l'encodeur suivant :
H264 - MPEG-4 AVC (part 10).
Si vous ne savez pas comment corriger ceci, demandez du support Ã* votre distribution.
```


```
ffmpeg version N-31404-ga8c2ff2, Copyright (c) 2000-2011 the FFmpeg developers
  built on Jul 11 2011 11:13:09 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-la --enable-libvorbis --enable-libmp3lame --enable-libx264 --enable-libxvid --enable-x11grab --enable-shared
  libavutil    51. 11. 0 / 51. 11. 0
  libavcodec   53.  7. 0 / 53.  7. 0
  libavformat  53.  5. 0 / 53.  5. 0
  libavdevice  53.  2. 0 / 53.  2. 0
  libavfilter   2. 24. 4 /  2. 24. 4
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  51.  2. 0 / 51.  2. 0

```

note that I am not using vlc beta 1.2 but vlc 1.1.13 and I was thinking I had to compile the beta version to support ffmpeg

---

### Post by mc4man on 2012-01-22
> **undercash said:**
> thanks for your reply

i have ffmpeg installed as I said but when I use  venc=ffmpeg (instead of x264 I assume) i get this error message


note that I am not using vlc beta 1.2 but vlc 1.1.13 and I was thinking I had to compile the beta version to support ffmpeg

Unless you happened to alter FO's guide to build FFmpeg as "shared" then your 1.1.13 version of vlc is using your 'real' system ffmpeg shared libs, libavcodecXX, libavformatXX, libswscaleX, ect. 

So try opening synaptic & upgrading the ffmpeg shared libs, (search libav), to the extra versions which will have libx264 support

Just mark the extra ones for install, the current one will be auto removed when you do so. - screen, mark all the extra ones you see, probably 6 or 7 total

---

### Post by undercash on 2012-01-23
ok assuming the --enable-shared could be the problem I upgraded ffmpeg but I get the same error from vlc, my ffmpeg is crippled.. what can I do? Also, do you know how to make vlc use all my cpu core while transcoding? this is a bit the reason why I am trying to get ffmpeg venc working instead of x264, to see if it makes any differences.

thanks


```
ffmpeg version N-37057-gb9db728 Copyright (c) 2000-2012 the FFmpeg developers
  built on Jan 23 2012 12:19:58 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libmp3lame --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil      51. 34.101 / 51. 34.101
  libavcodec     53. 57.105 / 53. 57.105
  libavformat    53. 30.100 / 53. 30.100
  libavdevice    53.  4.100 / 53.  4.100
  libavfilter     2. 59.101 /  2. 59.101
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0.  6.100 /  0.  6.100
  libpostproc    52.  0.100 / 52.  0.100
Hyper fast Audio and Video encoder
```


```
ffmpeg -codecs |grep MPEG
 D A D  als             MPEG-4 Audio Lossless Coding (ALS)
 D V D  h264            H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
  EA    libmp3lame      libmp3lame MP3 (MPEG audio layer 3)
  EV    libx264         libx264 H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
  EV    libx264rgb      libx264 H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 RGB
  EV    libxvid         libxvidcore MPEG-4 part 2
 D A D  mp1             MP1 (MPEG audio layer 1)
 D A D  mp1float        MP1 (MPEG audio layer 1)
 DEA D  mp2             MP2 (MPEG audio layer 2)
 D A D  mp2float        MP2 (MPEG audio layer 2)
 D A D  mp3             MP3 (MPEG audio layer 3)
 D A D  mp3adu          ADU (Application Data Unit) MP3 (MPEG audio layer 3)
 D A D  mp3adufloat     ADU (Application Data Unit) MP3 (MPEG audio layer 3)
 D A D  mp3float        MP3 (MPEG audio layer 3)
 DEVSDT mpeg1video      MPEG-1 video
 DEVSDT mpeg2video      MPEG-2 video
 DEVSDT mpeg4           MPEG-4 part 2
 D VSDT mpegvideo       MPEG-1 video
 DEVSD  msmpeg4         MPEG-4 part 2 Microsoft variant version 3
 D VSD  msmpeg4v1       MPEG-4 part 2 Microsoft variant version 1
 DEVSD  msmpeg4v2       MPEG-4 part 2 Microsoft variant version 2
```

---

### Post by andrew.46 on 2012-01-23
The method in this guide for building FFmpeg uses a local copy that should not interfere with any system copies, perhaps try this instead of the Gordian knot of your existing FFmpeg installation :).

---

### Post by undercash on 2012-01-23
hello, 

I followed your advice and installed a local ffmpeg and x264 for vlc 

I don't see any difference :
[http://pastebin.com/s9jT4CDP](http://pastebin.com/s9jT4CDP)

---

### Post by andrew.46 on 2012-01-24
OIC, you are trying to force x264 encoding through FFmpeg using vlc? I am not certain that this will work and certainly the local copy of FFmpeg built with this guide does not have this capability. I cannot experiment with this at the moment as not only am I between Ubuntu installations but I don't actually have vlc installed either for the time being :(.

---

### Post by undercash on 2012-01-24
thank you for your answer. 

Honestly I wouldn't mind using x264 as venc, I am just trying to get vlc to use several core of the cpu as I think it could resolve some of my issue, with a stream let's say, choppy.. when it actually does works..

here is the command I use, more or less: 

```
cvlc "/home/file.avi" -vvv input_stream --file-caching=5000 --sout='#transcode{venc=ffmpeg{keyint=64},vcodec=x264,vb=150,acodec=aac,deinterlace,ab=96,channels=2,samplerate=44100,threads=4}:rtp{dst=127.0.0.1,port=1234,mux=ts,caching=5000,sdp=file:///home/vlc.sdp}'
```

and I apologize since this is a bit offtopic

---

### Post by undercash on 2012-01-26
I would like to know please how to remove this local version of ffmpeg.. now when I encode using my php script I get 2 ffmpeg (16threads on a quad core HT) encoding and the resulting video is corrupted even though only partially

---

### Post by andrew.46 on 2012-01-26
The local copy should not interfere as FFmpeg itself is not built in this guide, only the libraries. Check this:

```

**[COLOR="Red"]sudo find /usr -type f -iname ffmpeg[/COLOR]**
/usr/bin/ffmpeg

```

to see if you have more than one copy of FFmpeg installed (I suspect a copy in /usr as well as one in /usr/bin).

---

### Post by andrew.46 on 2012-02-19
Exciting times as vlc 2.0.0 is released :). Should be easy enough to build using this guide...

---

### Post by kevdog on 2012-02-19
Nice desktop andrew, is that openbox?

---

### Post by FakeOutdoorsman on 2012-02-19
My guess is Fluxbox, but I may be wrong. I use Openbox with tint2. Pretty boring looking though with an all black background.

---

### Post by yetiman64 on 2012-02-19
Hi all, I've been trying out this guide today but keep running into an error, wants me to use an option fPIC  while compiling ?

```
/usr/bin/ld: /usr/local/lib/libvpx.a(vpx_codec.c.o): relocation R_X86_64_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libvpx.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
libtool: install: error: relink `libavcodec_plugin.la' with the above command before installing it
make[7]: *** [install-libvlcLTLIBRARIES] Error 1
make[7]: Leaving directory `/home/yetiman/vlc_build/vlc/modules/codec/avcodec'
make[6]: *** [install-am] Error 2
make[6]: Leaving directory `/home/yetiman/vlc_build/vlc/modules/codec/avcodec'
make[5]: *** [install] Error 2
make[5]: Leaving directory `/home/yetiman/vlc_build/vlc/modules/codec/avcodec'
make[4]: *** [install-recursive] Error 1
make[4]: Leaving directory `/home/yetiman/vlc_build/vlc/modules/codec'
make[3]: *** [install] Error 2
make[3]: Leaving directory `/home/yetiman/vlc_build/vlc/modules/codec'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/yetiman/vlc_build/vlc/modules'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/yetiman/vlc_build/vlc'
make: *** [install] Error 2

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```Does that mean I need to add a different switch for use with "./configure" for -fPIC ? Or is there something worse at play here ?

Edit: I get the error at the very end, the section for building vlc itself. Everything else goes through without error.

---

### Post by andrew.46 on 2012-02-20
> **kevdog said:**
> Nice desktop andrew, is that openbox?

Fakeoutdoorsman has hit the mark, it is Fluxbox :).

---

### Post by qyot27 on 2012-02-20
> **yetiman64 said:**
> Hi all, I've been trying out this guide today but keep running into an error, wants me to use an option fPIC  while compiling ?

```
/usr/bin/ld: /usr/local/lib/libvpx.a(vpx_codec.c.o): relocation R_X86_64_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libvpx.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
libtool: install: error: relink `libavcodec_plugin.la' with the above command before installing it
make[7]: *** [install-libvlcLTLIBRARIES] Error 1
make[7]: Leaving directory `/home/yetiman/vlc_build/vlc/modules/codec/avcodec'
make[6]: *** [install-am] Error 2
make[6]: Leaving directory `/home/yetiman/vlc_build/vlc/modules/codec/avcodec'
make[5]: *** [install] Error 2
make[5]: Leaving directory `/home/yetiman/vlc_build/vlc/modules/codec/avcodec'
make[4]: *** [install-recursive] Error 1
make[4]: Leaving directory `/home/yetiman/vlc_build/vlc/modules/codec'
make[3]: *** [install] Error 2
make[3]: Leaving directory `/home/yetiman/vlc_build/vlc/modules/codec'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/yetiman/vlc_build/vlc/modules'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/yetiman/vlc_build/vlc'
make: *** [install] Error 2

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```Does that mean I need to add a different switch for use with "./configure" for -fPIC ? Or is there something worse at play here ?

Edit: I get the error at the very end, the section for building vlc itself. Everything else goes through without error.
Yes, it does require another option.  Usually, position-independent code (aka PIC) is turned on through the '--enable-pic' option.  **This is very often - if not always - required for building the program as 64-bit**, which is likely the reason why it's complaining.

From the specific error, it looks as though you want to link libvpx into VLC, but the problem is that libvpx wasn't compiled as position-independent.  You'd need to recompile libvpx with --enable-pic, and then try again.  Maybe it's on VLC's side too, I dunno.

---

### Post by andrew.46 on 2012-02-20
> **yetiman64 said:**
> Hi all, I've been trying out this guide today but keep running into an error, wants me to use an option fPIC  while compiling ?
```
/usr/bin/ld: /usr/local/lib/libvpx.a(vpx_codec.c.o): relocation R_X86_64_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC

```


I have to admit that not only am I between Ubuntu installations but at the moment I only have the vlc release version 2.0.0 installed :(. However looks like you have a version of libvpx installed in /usr/local which is causing trouble? As a short-term measure perhaps you could remove the option:

```
--enable-libvpx \
```

from the FFmpeg section and recompile FFmpeg and then vlc? With any luck this will get a copy of vlc-git going, but without webm transcoding ability for the moment.

I will hopefully be building a computer soon that will finally rid me of the shackles of this underpowered laptop and I will then be able to run this guide and others on dedicated Ubuntu installations! Hopefully within the next 4 weeks or so which would be well and truly in time for the release of Precise Pangolin....

---

### Post by yetiman64 on 2012-02-20
Thanks Andrew.46, 

I removed the option "--enable-libvpx" and tried again, it works now :).

I must have installed libvpx (the optional section) from fakeoutdoorsman's ffmpeg guide. Seems the only likely place I would have picked it up.

I'm happy enough to lose out on the transcoding for the time being, just testing out the latest vlc out of interest. Will think about removing libvpx later and rebuilding from this guide down the track a bit. Thank you, yetiman64.

---

### Post by andrew.46 on 2012-02-20
> **yetiman64 said:**
> I removed the option "--enable-libvpx" and tried again, it works now :).

I must have installed libvpx (the optional section) from fakeoutdoorsman's ffmpeg guide. Seems the only likely place I would have picked it up.

Good to hear compilation succeeded :). Perhaps you could recompile libvpx according to Fakeoutdoorsman's guide and add in:

```

--enable-pic

```

as a *./configure* option with libvpx, recompile FFmpeg according to my vlc guide (restoring the libvpx option), and then recompile vlc-git. This may be enough to get everything going completely :).

This is all part of the fun of building vlc....

---

### Post by yetiman64 on 2012-02-20
> **andrew.46 said:**
> .... Perhaps you could recompile libvpx according to Fakeoutdoorsman's guide and add in:

```

--enable-pic

```as a *./configure* option with libvpx, recompile FFmpeg according to my vlc guide (restoring the libvpx option), and then recompile vlc-git. This may be enough to get everything going completely :).

This is all part of the fun of building vlc....
Yes did this, it compiled without a hitch, thanks again Andrew.46.

Yes it certainly has been fun, not just compiling vlc, but vlc, mplayer and ffmpeg are compiled from the forum guides here, it has been fun getting them to co-operate.  Cheers Andrew, and have a good day. :smile:

---

### Post by andrew.46 on 2012-02-20
> **yetiman64 said:**
>  Cheers Andrew, and have a good day. :smile:

And you too :).

---

### Post by FlipeGarcia on 2012-03-08
Hi,

Thank you for this guide that I am planning to use for the installation of VLC. My question is however related to a pre-installation decision. I am planning to switch to 64 bits, but you say in your tutorial that MPlayer binary codecs are of no use to 64bit users. I am worried I might miss many encoding/decoding capabilities if I change to 64 bits, and this is important to me, since I transcode frequently, although almost always to H.264 and HE-AAC. Actually, my frequent transcoding is an important reason to switch, as I have heard that the increase in speed is noticeable for this kind of process.

Can you please tell me what is lost by switching to 64 bits and maybe your opinion whether it is worth switching? I don't really know what the Mplayer binary codecs offer.

Thanks in advance!

---

### Post by FakeOutdoorsman on 2012-03-08
See this thread ['codecs' confusion](https://bbs.archlinux.org/viewtopic.php?pid=1058156#p1058156).

---

### Post by FlipeGarcia on 2012-03-08
Thanks for the clarification! So it seems there is no reason to worry about switching to a 64 OS unless I run across an extremely unusual codec. I will then take the risk :)

---

### Post by andrew.46 on 2012-03-08
For vlc there is little problem in switching to a 64bit version, in part because as far as I am aware all ubuntu vlc packages do not even use the option *--enable-loader* and thus do not access the codecs assembled by the MPlayer developers at all. The vlc developers are not keen to further develop this little corner of vlc either. As FakeOutdoorsman link describes routine video and audio transcoding are not affected by lack of access to these codecs which address access to more unusual and proprietary media.

A bigger issue is the use of this guide for the installation of vlc. The development version is not intended for mainstream use and will frequently break or have entire sections of playback or transcoding that will not work. The guide is thus intended for those who like tinkering with vlc and are capable of troubleshooting errors and are keen to live on the bleeding edge. If that is what you want go for it :).
[B]
OffTopic: [/B]I have a new flash AMD FX-8150 computer now with decent 3D graphics so I can finally appreciate vlc + ProjectM! Screenshot attached..... Dare I say it, this is a worthy successor to goom which may very well vanish completely from this guide.

---

### Post by kevdog on 2012-03-08
Is anyone able to compile the latest from git.  I keep getting an error in a c file.  Yes I know that not posting the error doesn't help -- I'll have to get to that.

---

### Post by mc4man on 2012-03-09
Probably should soon consider adjusting package version to 2.1.0<whatever you like> to reflect actual & keep ahead of current release (2.0) & possible in 12.04 (2.0.1

(--enable-real isn't used anymore

---

### Post by FlipeGarcia on 2012-03-09
> **andrew.46 said:**
> For vlc there is little problem in switching to a 64bit version, in part because as far as I am aware all ubuntu vlc packages do not even use the option *--enable-loader* and thus do not access the codecs assembled by the MPlayer developers at all. The vlc developers are not keen to further develop this little corner of vlc either. As FakeOutdoorsman link describes routine video and audio transcoding are not affected by lack of access to these codecs which address access to more unusual and proprietary media.

Thanks for the clarification! I think it is probably worth then switching, hoping I have a quicker transcoding, as the computer starts to be rather old for this kind of use (about 6 years old).

> **andrew.46 said:**
> A bigger issue is the use of this guide for the installation of vlc. The development version is not intended for mainstream use and will frequently break or have entire sections of playback or transcoding that will not work. The guide is thus intended for those who like tinkering with vlc and are capable of troubleshooting errors and are keen to live on the bleeding edge. If that is what you want go for it :).

I will then try and in case I run into too many problems that I can't handle (I am newbie), switch back to a stable version. Thanks again!

---

### Post by andrew.46 on 2012-03-10
> **kevdog said:**
> Is anyone able to compile the latest from git.  I keep getting an error in a c file. 

Broken here as well :(.

---

### Post by andrew.46 on 2012-03-10
> **mc4man said:**
> Probably should soon consider adjusting package version to 2.1.0<whatever you like> to reflect actual & keep ahead of current release (2.0) & possible in 12.04 (2.0.1

(--enable-real isn't used anymore

Thanks mc4man. Rewrite is coming up soon when this new computer is settled in *and* after I return from a 2 week retreat. Ashram has no phone, radio, tv etc :).

---

### Post by mc4man on 2012-03-10
> **andrew.46 said:**
> Broken here as well :(.
Didn't see any issue, yesterday or today (curious to see something so rebuilt a few times (git pull is up to date

> $ vlc -vv
VLC media player 2.1.0-git Rincewind (revision 797ca65)


(only real diff would be I don't build in live 555 more than occasionally

Last used - 
```
cd $HOME/vlc_build/vlc && \
if [ ! "$(uname -m)" = "x86_64" ]; then
 ARCHOPTS="--enable-loader"
else
  ARCHOPTS=""
fi && \
./bootstrap && \
CPPFLAGS="-I$HOME/vlc_build/vlcdeps/usr/include " \
CFLAGS="-I$HOME/vlc_build/vlcdeps/usr/include"  \
CXXFLAGS="-I$HOME/vlc_build/vlcdeps/usr/include" \
LDFLAGS="-L$HOME/vlc_build/vlcdeps/usr/lib" \
PKG_CONFIG_PATH="$HOME/vlc_build/vlcdeps/usr/lib/pkgconfig" \
./configure $ARCHOPTS \
            --prefix=/usr/local \
            --enable-realrtsp \
            --enable-aa \
            --enable-merge-ffmpeg \
            --enable-vcdx \
            --enable-ncurses \
            --with-tuning=native && \
make && \
sudo checkinstall --pakdir "$HOME/vlc_build" --backup=no --deldoc=yes --pkgname vlc \
                  --pkgversion "2.1.0-git-$(date +%Y%m%d)-$(git show --abbrev-commit \
                  | grep '^commit' | cut -f2 -d " ")" --fstrans=no \
                  --deldesc=yes --delspec=yes --default && \
make distclean && sudo ldconfig 
```

Anyway, have a good 2 weeks ..

---

### Post by andrew.46 on 2012-03-10
Thanks mc4man :). The trip to the ashram is in 2 weeks time and I look forward to it immensely. I will be spending time up until then outfitting this new computer with its 'pure' 64bit distro and adjusting all my build scripts to suit. I made 3 stupid mistakes when reqriting my vlc-git script and I have now produced a slightly barebones copy which compiles successfully:

```

andrew@skamandros~$ **[COLOR="Red"]cvlc --version | head -n 3[/COLOR]**
VLC media player 2.1.0-git Rincewind (revision 797ca65)
VLC version 2.1.0-git Rincewind (797ca65)
Compiled by root on skamandros.andrews-corner.org (Mar 10 2012 22:32:31)
Compiler: gcc version 4.6.2 (GCC)

```

which I will expand a little over the next week or so. Nice being able to run *make -j 12 *on this 8 core machine btw :). When I come back from my break it will be close to Precise Pangolin's release so perhaps this will be a good time to rewrite. Changes needed now:

[LIST=1]
[*]Fix up the elaborate live555 syntax, no patching should be required for later versions.
[*]Upgrade FFmpeg to 0.10
[*]Switch to a snapshot for x264 local copy.
[/LIST]

---

### Post by kevdog on 2012-03-10
Thanks andrew -- I'll enjoy reading your new guide when its complete.

---

### Post by mc4man on 2012-03-10
Doesn't appear to be any need to patch live555 anymore, the patch check has been removed from configure.ac as have the contrib patches

---

### Post by andrew.46 on 2012-03-15
Those who own bluray drives may be interested to see this:

[http://vlc-bluray.whoknowsmy.name/](http://vlc-bluray.whoknowsmy.name/)

Not sure of the legal status of this in *your* country so don't break any laws...

---

### Post by mc4man on 2012-03-15
I noticed that vlc git added wmal thru avcodec but due to a bug it can cause a crash (bug doesn't affect ffplay
Anyway a post on, I gather at some point it should be working, ect.

[http://forum.videolan.org/viewtopic.php?f=13&t=99084](http://forum.videolan.org/viewtopic.php?f=13&t=99084)

---

### Post by andrew.46 on 2012-03-15
Hmmmm..... is bat999 our Ron999?

---

### Post by mc4man on 2012-03-15
> **andrew.46 said:**
> Hmmmm..... is bat999 our Ron999?

Could be - the locale & other posts seem appropriate to Ron

---

### Post by andrew.46 on 2012-03-18
Added in compilation instructions for libbluray and libaacs. Those with bluray drives might be interested to try? I have chosen the version numbers to enable a seamless move to Precise in the next month or so. 

Please no questions about bluray keys in this thread as sharing such information on these Forums would break Forum rules and doubtless the laws in some countries as well.

---

### Post by mc4man on 2012-03-19
For those interested in such things the previous browser plugin is now - npapi-vlc, (browser-plugin-vlc in 12.04

git clone git://git.videolan.org/npapi-vlc.git

[http://git.videolan.org/?p=npapi-vlc.git;a=shortlog](http://git.videolan.org/?p=npapi-vlc.git;a=shortlog)

---

### Post by mc4man on 2012-03-22
Same deal as mplayer - wmal support now works ok in vlc-git
> [0x876cfe0] avcodec decoder debug: libavcodec initialized (interface 0x360c64)
[0x876cfe0] avcodec decoder debug: ffmpeg codec (Windows Media Audio Lossless) started


Didn't test with the ffmpeg release though, substituted a 
git clone --depth 1 git://source.ffmpeg.org/ffmpeg
instead of the wget, ect.

---

### Post by andrew.46 on 2012-03-27
> **mc4man said:**
> Same deal as mplayer - wmal support now works ok in vlc-git.

This is excellent news and in part justifies my own move to a 64bit installation for my primary distro. I might wait for a release version of FFmpeg that incorporates this change for this guide, there is a enough complexity in place as it is without adding in the git FFmpeg :).

BTW: This single login to the Ubuntu Forums comes from a computer in the ashram I am staying at... believe it or not this computer is running *Karmic* Koala :) A happy om to all.......

---

### Post by mc4man on 2012-03-28
> **andrew.46 said:**
>  I might wait for a release version of FFmpeg that incorporates this change for this guide, there is a enough complexity in place as it is without adding in the git FFmpeg :).


I somewhat tried the 10.2 release though not on vlc. 
In this case it was with audacious where only a recent FFmpeg git would work. 
(using the 3.3 aud git. Other aud sources would likely need a small patch to use with current FFmpeg, just got the current aud dev to adjust for this.

---

### Post by andrew.46 on 2012-03-28
> **mc4man said:**
>  Other aud sources would likely need a small patch to use with current FFmpeg, just got the current aud dev to adjust for this.

I presume [this is the patch]("https://github.com/audacious-media-player/audacious-plugins/commit/2236fb3d8e0a121bfef80382abef03c342be1e6a")? I shall patch my own copy of audacious when I get home :).

---

### Post by mc4man on 2012-03-29
> **andrew.46 said:**
> I presume [this is the patch]("https://github.com/audacious-media-player/audacious-plugins/commit/2236fb3d8e0a121bfef80382abef03c342be1e6a")? I shall patch my own copy of audacious when I get home :).

That would be it
(On 12.04 ran into 4 other issues, 2 where resolved by configure option, the other 2 I just built around. * using the 3.3 git aud source

```
./configure  LDFLAGS='[COLOR="Blue"]-lgmodule-2.0[/COLOR] -lpthread'
```
The blue for ladspa, tried directly in it's Makefile but didn't work in a straight up build, a Makefile edit does work in a debian built??

The other for the 'alarm' plugin - the Makefile does include "${PTHREAD_LIBS}" but still needed it on configure

Jack & alsa also showed some 'undefined', rather than explore just configured out, not needed here, main point was to test audacious & FFmpeg, & resolve the _fmt change.

(notice FFmpeg, aud bases off of that, not Libav, *at least for now

Edit
If any jack issues the jack dev libs need to be installed for ffaudio, that's why a configure out it not fixable

---

### Post by andrew.46 on 2012-04-01
Temporarily added in:

```
 --disable-v4l2
```

while some work is done with this [at vlc-git]("http://git.videolan.org/?p=vlc.git&a=search&h=HEAD&st=commit&s=v4l2"). Breaks compilation at the moment....

---

### Post by andrew.46 on 2012-04-01
> **mc4man said:**
> (using the 3.3 aud git. Other aud sources would likely need a small patch to use with current FFmpeg, just got the current aud dev to adjust for this.

Good news is that the ffaudio change has been absorbed into the new 3.2.2 release, so looks like the long history of problematic wma lossless playback is well and truly finished :).

---

### Post by mc4man on 2012-04-01
> **andrew.46 said:**
> Good news is that the ffaudio change has been absorbed into the new 3.2.2 release, so looks like the long history of problematic wma lossless playback is well and truly finished :).
All does seem well on the self-built front, Debian/Ubuntu package  users will have to wait a bit. 
Hopefully the next time D/U upgrades Audacious they won't take 6+ months to get their act together as far as the ffaudo plugin

---

### Post by mc4man on 2012-04-03
Ot - 
Went ahead & did a new aud build with the 3.2 release & as you mentioned alls well with a current FFmpeg & that source

If you came across some time - 
For the current gtk there are quite alot of warnings that could be cleaned up - not critical, but still..

To do by hand would be time consuming, figure there is one of your nice commands that could search thru the affected files & fix.

Some of the more common ones that are widespread in both aud & the plugin source - if you had a command or two then could definitely put 2 & 2 together, ect.

Ex.

>  &#8216;gtk_vbox_new&#8217; is deprecated : Use 'gtk_box_new' 

 &#8216;gtk_hbox_new&#8217; is deprecated : Use 'gtk_box_new' 

&#8216;gtk_hseparator_new&#8217; is deprecated : Use 'gtk_separator_new'

 &#8216;gtk_hscale_new&#8217; is deprecated : Use 'gtk_scale_new' 

---

### Post by andrew.46 on 2012-04-03
> **mc4man said:**
> 
If you came across some time - 
For the current gtk there are quite alot of warnings that could be cleaned up - not critical, but still..

To do by hand would be time consuming, figure there is one of your nice commands that could search thru the affected files & fix.


I will admit that I have not tested this thoroughly but permutations of the following should do the trick, from the root directory of the source:

```

grep -rl 'gtk_vbox_new' src/ | xargs sed -i_bak 's/gtk_vbox_new/gtk_box_new/'

```

Of course once you have full confidence in the syntax you would drop the *_bak* and then no backup would be saved... Don't you love Linux!!!

---

### Post by andrew.46 on 2012-04-06
Hmmmmmmm........ interesting times ahead:

Pending Changes to Tutorials and Tips
[http://ubuntuforums.org/showthread.php?t=1949027](http://ubuntuforums.org/showthread.php?t=1949027)

---

### Post by mc4man on 2012-04-08
The web page looks pretty good - 
While I don't use the v4l in 12.04 it seems ok, at least the plugin built

---

### Post by andrew.46 on 2012-04-08
> **mc4man said:**
> The web page looks pretty good - 

Actually I like the background image trick that I filched from the Ubuntu Community Wiki so much I may very well use it for the rest of my site :).


> While I don't use the v4l in 12.04 it seems ok, at least the plugin built

Next major look at the guide will be 12.04....

---

### Post by andrew.46 on 2012-04-08
Website version bumped for Precise Pangolin.......

---

### Post by andrew.46 on 2012-05-05
Version bump for libbluray and libaacs for keen owners of bluray drives :). This version bump puts this guide ahead of repository offerings of both already!

---

### Post by nothingspecial on 2012-05-17
Closed at the request of the OP.

---

