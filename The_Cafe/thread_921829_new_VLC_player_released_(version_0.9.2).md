---
title: "new VLC player released (version 0.9.2)"
date: 2008-09-16
forum: The Cafe
---

### Post by imgkg on 2008-09-16
new VLC player 0.9.2 has been released for installations you can check this [http://tombuntu.com/index.php/2008/09/16/install-vlc-media-player-092-in-ubuntu/](http://tombuntu.com/index.php/2008/09/16/install-vlc-media-player-092-in-ubuntu/)

---

### Post by majorhabib on 2008-09-16
:( Still does not support Right-to-Left Arabic subtitles.

---

### Post by Chame_Wizard on 2008-09-16
already have it :P:lolflag:

---

### Post by Lord Xeb on 2008-09-16
Just upgraded :D

---

### Post by Polygon on 2008-09-16
whoa, when did vlc .9 come out....let alone .9.1....

---

### Post by klange on 2008-09-16
@Polygon: They didn't. This is the first release in the 0.9 series.

I finally updated my QGtkStyle just for VLC.

---

### Post by Polygon on 2008-09-16
hmm,why they choose such confusing numbering conventions is beyond me. 

if its a development release, why not just call  it 0.9-svn...why have a 0.9 and a 0.9.1 milestone if no one but the developers ever see it?

and..OMG VLC USES QT I MUST BOYCOTT/FORK THIS PROGRAM NOW QT IS THE EVVVIILLL

---

### Post by uberdonkey5 on 2008-09-16
> **Polygon said:**
> and..OMG VLC USES QT I MUST BOYCOTT/FORK THIS PROGRAM NOW QT IS THE EVVVIILLL

what is QT?

VLC is a great package for me, will update ASAP

---

### Post by Polygon on 2008-09-16
QT is a toolkit, which is used in KDE, while Gnome uses the GTK+ toolkit. Running a QT app means you just gotta install libqt on linux, it doesn't mean you have to install all 50000 kde libraries. QT looks out of place on a gnome desktop, but there is a QT theme that makes it look like your current GTK theme, called QGTKstyle or something.

---

### Post by klange on 2008-09-16
> **Polygon said:**
> QT is a toolkit, which is used in KDE, while Gnome uses the GTK+ toolkit. Running a QT app means you just gotta install libqt on linux, it doesn't mean you have to install all 50000 kde libraries. QT looks out of place on a gnome desktop, but there is a QT theme that makes it look like your current GTK theme, called QGTKstyle or something.
It doesn't look out of place at all.
You need to grab qmake-qt4 and you can then build + install [qgtkstyle](http://labs.trolltech.com/page/Projects/Styles/GtkStyle) quite easily.

I started using it with a minimum number of QT apps back when it was still in testing. Qgtkstyle is now part of QT 4.5 (but even in Intrepid, we'll still have 4.4, so you need to build it manually).

[img]http://random.oasis-games.com/vlc092.png[/img]

^ VLC with ClearGlow GTK theme.

---

### Post by mips on 2008-09-17
> **WindowsSucks said:**
> It doesn't look out of place at all.


Qt apps look good in Gnome, however the opposite is not true unfortunately. Fortunately a QT Firefox should be out soon for those dependant on FF3.

---

### Post by jwaiwit on 2008-09-17
#WindowsSucks
Is that a Naruto ? he he he , I will upgrade soon. a great package.

---

### Post by Rhubarb on 2008-09-17
> **majorhabib said:**
> :( Still does not support Right-to-Left Arabic subtitles.

While I don't have any videos with right-to-left arabic subtitles to test this myself, it might just work.
In VLC, Tools --> Preferences
Subtitles & OSD, Then try changing the default Language encoding to something more suitable.

Otherwise, perhaps SMPlayer (which is based on mplayer) may be better for you.


I must say, VLC 0.9.2 is really impressive.  They've done a really impressive job with it :D

---

### Post by pt123 on 2008-09-17
> **mips said:**
> Qt apps look good in Gnome, .

Not really KTorrent looks crap.

---

### Post by qazwsx on 2008-09-17
Matroska + vorbis  = nosound (=99 %  of my video files) :(

---

### Post by mips on 2008-09-17
> **pt123 said:**
> Not really KTorrent looks crap.

I suspect the new version based on Qt4 (when released) will look better.

---

### Post by billgoldberg on 2008-09-17
> **mips said:**
> I suspect the new version based on Qt4 (when released) will look better.

VLC 0.9.2 looks out of place on gnome.

No question about it.

Unless your gtk theme resembles the qt theme.

I am using a dark theme, and it looks hidious.

Might try out that qgtk thing.

---

### Post by mips on 2008-09-17
> **billgoldberg said:**
> VLC 0.9.2 looks out of place on gnome.

No question about it.

Unless your gtk theme resembles the qt theme.

I am using a dark theme, and it looks hidious.

Might try out that qgtk thing.

I was referring to Ktorrent.

I suspect qgtk thing would resolve your issue.

I don't use gnome so have no gtk.

---

### Post by Scruffynerf on 2008-09-17
It doesn't like subtitles very much.

.mkv, native language japanese, english subtitles:
"[***] **MSGL_V**: event at 9311857, +2260: 263,,Style1,Comment,0000,0000,0000,,there's a good chance that we'll turn up\neven more hidden financial backers."

When running it through the terminal.

Although, it does look and generally behave very nicely. I'll probably use this as the default player for a while.

---

### Post by Nevon on 2008-09-17
Oh this is rich. I installed this new version this morning. It worked fine at first, I was able to play a few movies without a hitch (although I absolutely hate the way you browse files in it). However, now when I tried to start it, it just wouldn't work. So I uninstalled vlc and vlx-nox, and then removed the repository. Then I reinstalled the old version of VLC and do you think it worked...? Nope. Now when I try to start vlc I get this message:
```
vlc: error while loading shared libraries: libvlc.so.0: cannot open shared object file: No such file or directory
```

---

### Post by klange on 2008-09-17
> **billgoldberg said:**
> VLC 0.9.2 looks out of place on gnome.

qgtkstyle works extremely well, take a look at my previous post - it has a screenshot. I guess I'll post some of the other windows as well as some GNOME apps for comparison.

For me, VLC 0.9.2 looks great under GNOME.

---

### Post by Canis familiaris on 2008-09-17
> **billgoldberg said:**
> VLC 0.9.2 looks out of place on gnome.

No question about it.

Unless your gtk theme resembles the qt theme.

I am using a dark theme, and it looks hidious.

Might try out that qgtk thing.

It Integrates well with my system. Do you have "Qt 4 Settings" installed in your Ubuntu installation?

---

### Post by billgoldberg on 2008-09-17
> **mips said:**
> I was referring to Ktorrent.

I suspect qgtk thing would resolve your issue.

I don't use gnome so have no gtk.

Nope, Qgktstyle didn't work for me.

I applied the theme, and the preview looked good. 

Vlc however still looked the same.

--

It looks good on my laptop, because the gtk theme matched the qt theme.

On my desktop, I'll stick to totem.

---

### Post by jensbw on 2008-09-18
I noticed this thread and thought it could be interesting to see how the current KTorrent looks with QGtkStyle so there you go.
edit: I also eventually realized how incredibly off-topic it is... :-/

---

### Post by lzfy on 2008-09-18
> **jensbw said:**
> I noticed this thread and thought it could be interesting to see how the current KTorrent looks with QGtkStyle so there you go.
edit: I also eventually realized how incredibly off-topic it is... :-/

How does the file dialogs look like? Does it use the gtk dialogs or KDE?

One thing I hate about gtk apps in KDE are the GTK file dialogs.

---

### Post by jensbw on 2008-09-18
> **lzfy said:**
> How does the file dialogs look like? Does it use the gtk dialogs or KDE?

One thing I hate about gtk apps in KDE are the GTK file dialogs.

It will use the KDE one for now, but it will appear as if it was written with Gtk+. It might be possible to get the GNOME native one after Qt 4.5 is out though but this has yet to be determined.

---

### Post by Polygon on 2008-09-18
vlc looks fine with qgtklooks

also, this version FINALLY can skip through mkv files w/out crashing. i am happy =)

and the GUI in full screen and the ability to go to 200% volume (rather then just 97%) is very cool as well =P

---

### Post by simtaalo on 2008-09-18
i quite like how the new version looks :)

---

### Post by pt123 on 2008-09-19
> **jensbw said:**
> I noticed this thread and thought it could be interesting to see how the current KTorrent looks with QGtkStyle so there you go.
edit: I also eventually realized how incredibly off-topic it is... :-/
That looks nice.

What version of Ktorrent is that and QGtkStyle?

---

### Post by Jordanwb on 2008-09-19
I think I'll stick to 0.8.6 thank you very much.

---

### Post by Polygon on 2008-09-19
> **Jordanwb said:**
> I think I'll stick to 0.8.6 thank you very much.

your loss. there was a crap load of bugs fixed in this version.

---

### Post by Jordanwb on 2008-09-19
> **Polygon said:**
> your loss. there was a crap load of bugs fixed in this version.

Really? The only one I noticed was that I could never get volume up to 100% on non Windows installs. Also if I fast forwarded too fast, the audio wouldn't work for a few seconds.

---

### Post by andrewabc on 2008-09-19
> **Jordanwb said:**
> Really? The only one I noticed was that I could never get volume up to 100% on non Windows installs. Also if I fast forwarded too fast, the audio wouldn't work for a few seconds.

The changelog is huge. So lots of changes, some of which you won't notice.

```
Note: version 0.9.0 was skipped due to bugs being discovered at the last
minute.

Important notes:
----------------
* This release will need Windows 2000 and Mac OS X 10.4 (Tiger) to work
correctly
* The HTTP interface is now only available on the local machine by default.
If you want to make it available from other machines, you will have to
edit the ".hosts" file.
- On UNIX/Linux, the file is in /usr/share/vlc/http/.hosts
If you're using the old http interface, it's located in
/usr/share/vlc/http/old/.hosts
- On Windows they are in C:\Program Files\VideoLAN\VLC\http\.hosts and
C:\Program Files\VideoLAN\VLC\http\old\.hosts
- On Mac OS X, you can find it in VLC.app/Contents/MacOS/share/http/.hosts
and respectively in VLC.app/Contents/MacOS/share/http/old/.hosts
* This version of VLC contains a new interface for Windows and Linux.
This interface has a fullscreen controller and simplified preferences.
This interface lacks the "Streaming Wizard" that used to be present in VLC
0.8.6, but provides basic profiles.
* The marq, mosaic and logo commands in the rc interface changed. They
now require a target name as their first argument. Example:
vlc --sub-filter "marq@test{marquee=Hello}" -I rc
You can then use commands like: @test marq-marquee Goodbye
If you didn't name the object using @test, its name will default to the
plugin name (hence 'marq') in this example.
These new commands are also available in the telnet interface.
* The "rtp" access output module has been removed.
Please use the RTP stream output instead, e.g.:
Old: '#std{access=rtp,mux=ts,dst=239.255.1.2:5004,sap}'
New: '#rtp{mux=ts,dst=239.255.1.2,port=5004,sap}'
* You now need to append --m3u-extvlcopt to your command line to enable
EXTVLCOPT options parsing in m3u playlists. Note that only a limited set
of options is available to m3u playlists (CVE-2007-6683).
* The old access:url syntax is no longer supported to resolve ambiguities
with some file names. Use access://url instead.
E.g.: vlc:quit -> vlc://quit ;
udp:@239.255.12.12 -> udp://@239.255.12.12
* The ffmpeg module has been removed and replaced by the new avcodec,
avformat, swscale (or imgresample if you use a swscale-less ffmpeg build)
and postproc modules.
* The web plugins ActiveX (IE)/Firefox/Mozilla/Safari now recognize the
following states: IDLE/CLOSE=0, OPENING=1, BUFFERING=2, PLAYING=3, PAUSED=4,
STOPPING=5, FORWARD=6, BACKWARD=7, ENDED=8, ERROR=9. With FORWARD and
BACKWARD being reserved for future implementations and are thus not
functional atm.
* Croping and padding in transcode are now done using the croppadd video
filter. For example:
transcode{vcodec=mp2v,vfilter=croppadd{cropttop=20,cropbottom=30,paddleft=100}}
* Canvas setting in transcode is now done using the canvas video filter.
For example:
transcode{vcodec=mp2v,vfilter=canvas{width=640,height=480}}
* Glide video output module has been removed.

Changes:
--------

Security updates:
* Updated libfreetype on Windows and Mac OS X (CVE-2008-1806, CVE-2008-1806,
CVE-2008-1807)
* TTA Parser improvements (CVE-2008-3732)
* MMS Access Module improvements (CVE-2008-3794 )

Playlist:
* Vastly improved playlist support:
* Media library creation to save all your playlist items
* "Live search"
* Shoutcast TV listings
* Audioscrobbler/Last.FM support
* Album art support
* User definable Lua playlist scripts. See share/lua/playlist/README.txt
(Default scripts open YouTube, DailyMotion, metacafe, Google Video and
lots of other URLs)
* User definable Lua album art fetcher scripts. See share/lua/meta/README.txt

Inputs:
* Video for Linux 2 (V4L2) input support
* UDP-Lite transport for RTP/AVP
* DCCP transport for RTP/AVP
* Proxy support for MMSH stream
* JACK audio input support
* Input run time option (improved live stream recording)
* BDA devices access module for DVB-C/S/T capture cards on Microsoft Windows
* Re-written Screen access module for Mac OS X
using OpenGL instead of QuickDraw
* Screen module now supports partial screen capture and mouse following on X11.
* Experimental EyeTV access module
This requires the user to install a plugin to EyeTV.app
(available as a separate download).
* Simple RTP input (with MPEG A/V, G.711 and PCM support).
* RTMP input support
* QTKit-based Input module for Mac OS X allowing display and streaming of video
taken from all iSight-labelled video cameras (no audio support)
* HTTP access now supports gzip compressed data and Digest Access
Authentication.
* New options to reduce latency between arrival of raw data and display of
frames. (--auto-adjust-pts-delay and --use-stream-immediate)

Demuxers:
* MP4 gpac and Apple chapter support
* Fixed playback of AIFF stereo files
* Fixed audio glitch on seek
* Improved FLAC demuxer (duration / current time / meta data)
* AAC tags support
* APEv1/2 tags support
* Improved ID3v2 tags support
* Improved Ogg/Vorbis tags support
* Raw video support
* Standard MIDI File (types 0 & 1) support
* TiVo Series 2 support
* CD+G karaoke Files support
* MXF files support
* OMA support

Decoders:
* VP60/VP61/VP6F/VP62 support
* Flash Screen Video support
* CamStudio Screen Video support
* DosBox Capture support
* Karl Morton's Video support
* limited atrac3 support
* Fraps support
* Fluidsynth MIDI software synthesis (with external sound fonts)
* New codec FOURCCs to support more specific files:
Avid, FCP, Sony, Samsung, ...
* H.264 PAFF support
* DNxHD / VC-3 support
* NellyMoser ASAO support
* APE (Monkey audio) support
* RealVideo support (with the RealVideo run-time)
* Dirac video support using libschroedinger

Subtitles:
* Closed Caption Decoder (DVD, ReplayTV, TiVo, DVB/ATSC)
* VBI & EBU (Teletext) support (*nix, Mac OS)
* Ogg/Kate subtitles support
* AQTitle subtitles support
* MKV USF subtitles support
* HTML-based subtitles support
* MPSub subtitles support
* JacoSub subtitles basic support
* MPL2 subtitles support
* Rewrite of ***/SSA scripts and subtitles support
* PowerDivx (.psb) Subtitles support
* Realtext subtitle support
* DKS subtitle support
* SubViewer 1.0 (SubRip09) subtitles support
* Correct Right-to-left languages in subtitles support

Encoders:
* Flash Screen Video support
* Improved H.264 encoding speed

Video outputs and filters:
* New CoreAnimation-based output module (VLCKit framework on OS X only)
* Adjust, Invert and Distort (now split into Wave, Ripple, Gradient and
Psychedelic) video filters can now be streamed
* New puzzle video output filter
* Re-written motion detection video filter
* New extract video filter (extract Red, Green and Blue components from a
video)
* New sharpen video filter (increase the contrast of adjacent pixels)
* New erase video filter (removes logos from a video)
* Enhanced subtitles' renderer to support bold, italic and some HTML tags
(Google Summer of Code Student project)
* Support for RGBA and I420 blending.
The latter improves Mosaic CPU usage *a lot*.
* New transparency mask video filter (for use with the mosaic_bridge module).
* New bluescreen video filter (for use with the mosaic_bridge module).
This was previously part of the mosaic module.
* Fixed random characters problem in RSS filter.
* Add rotate-deciangle for more precision on rotate filter
* Support for Intel SSE2 instruction set in chroma converters
* Improved use of Intel MMX instruction set in chroma converters
* New croppadd and canvas video filters.

Audio outputs and filters:
* Replay gain support
* Audio playback when going slower/faster (with pitch correction via
new scaletempo audio filter)
* New spatializer audio filter
* Correct DTS output via S/PDIF

Stream output:
* RTSP for TS-multiplexed broadcast streams
* New RTP payload formats:
* Speex voice audio codec
* ITU T.140 (for text, subtitles) output
* G.711 (both A-law and µ-law) output
* UDP-Lite transport for RTP
* DCCP transport for RTP
* Lots of fixes for RTSP broadcasting
* RTMP output

Interfaces:
* All
* New Simple Preferences dialogs showing the most important settings in an
end-user suitable way.
* Improved user interaction
* Improved mouse gestures
* Vastly improved Update checker
* Full support for meta data editing (ID3v2, Ogg/Vorbis, AAC, APEv1/2)
* Windows/Linux
* Brand new interface for Linux and Windows, based on the Qt toolkit
* Fullscreen controller (transparency on Linux+Composite)
* Mac OS X
* Improved video output features
* Online access to VideoLAN's Help Wiki within VLC
* New setting to disable the "Recent Items" service
* When playing Radio (live) streams, the current track is shown correctly
* Correct appearance on Macs using Aqua's graphite theme
* Simplified Extended Controls panel
* Ncurses:
* Correctly displays wide characters when using an UTF-8 locale,
if libncursesw is available.
* Some nice colors if the terminal supports it (most do)
* Experimental Lua interface modules. See vlc -I lua and
share/lua/playlist/README.txt for more info.
* Unix
* Option to allow only one running instance, using D-Bus interface.
* D-Bus Interface implementing the MPRIS
(Media Player Remote Interfacing specification), a common dbus control
interface for media players that intends to become an xdg standard when
finished: [http://wiki.xmms2.xmms.se/index.php/Media_Player_Interfaces](http://wiki.xmms2.xmms.se/index.php/Media_Player_Interfaces) .
* Motion module using disk accelerometers to keep video horizontal
* Plugin to set Telepathy presence message using MissionControl
* Fixed VLM schedule time on Linux

Linux Port:
* VLC now complies with the XDG Base Directory Specification version 0.6
[http://standards.freedesktop.org/basedir-spec/basedir-spec-0.6.html](http://standards.freedesktop.org/basedir-spec/basedir-spec-0.6.html)
(which means that VLC doesn't use the $HOME/.vlc directory anymore)

Mac OS X Port:
* Mac OS X Framework "VLCKit" that can be used to embed VLC in third party
applications (Google Summer of Code Student project, Mac OS X 10.5 only)
* New text renderer based on Quartz replacing the existing Freetype solution
* Complete compatibility with Mac OS X 10.5 Leopard
* It is now required to compile a fully featured build
* The support of Mac OS X 10.3.9 and QuickTime 6.x was discontinued.

LibVLC:
* Event management and various improvements in libvlc
(Part of a Google Summer of Code Student project)

New Localizations:
* Finnish
* Persian
* Polish
* Punjabi
* Bulgarian

Developers:
* LibVLC now supports externally built plugins properly.
A "vlc-plugin" pkg-config package is provided.
* Java bindings are now built from a separate source.
```

You may not like it at the moment, but eventually you'll be using 0.9.x (if 0.8 works fine for you, then no need to manually upgrade).

I hope it is included in Intrepid. But so far it is not.
[http://packages.ubuntu.com/intrepid/vlc](http://packages.ubuntu.com/intrepid/vlc)
[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/270404](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/270404)

---

### Post by LookTJ on 2008-09-19
Did they really improve FLAC? Or does it still skip?

---

### Post by Polygon on 2008-09-20
i just played a flac file and it works fine with vlc 0.9.2

---

### Post by LookTJ on 2008-09-20
> **Polygon said:**
> i just played a flac file and it works fine with vlc 0.9.2Thanks, I was just wondering because the .8 series kinda screwed up FLAC

---

### Post by Polygon on 2008-09-20
it also seems that the new version is going to be in intrepid after all. there is talk on the bug report page about testing the 0.9.2 package.

---

### Post by doorknob60 on 2008-09-20
Woot a QT4 interface, that just made my day :)

---

### Post by mips on 2008-09-20
> **doorknob60 said:**
> Woot a QT4 interface, that just made my day :)

Made my day a while back ;) Keep an eye out for Firefox3 QT version.

---

### Post by kwilliam on 2008-09-25
Shucks!
```
main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Cannot mix incompatible Qt libraries
Aborted
```

---

### Post by mister_pink on 2008-09-26
Does this finally handle forced dvd subtitles properly yet? I'm yet to find any player that will easily let me watch Bourne dvds with the subtitles on the foreign bits only!

---

### Post by Artemis3 on 2008-09-27
To clarify, there are qt libs, gtk libs, kde libs and gnome libs. You can have programs using gtk libs and no gnome libs, and qt programs using qt libs and no kde libs. Software using qt does not mean kde, same for software using gtk and gnome.

VLC 9 is using qt4, so the open file dialog reflects qt style file browsing.

---

### Post by darco on 2008-09-27
sweet.....just d/l it on my Linux Mint...

darco

---

### Post by zombrax on 2008-09-27
since I manually installed VLC in the first place, as I was having dilema's connecting properly to the proxy server about 6 months ago; how can i rm the VLC from my system and then use the CLI to install a fresh/new version so that I can automatically upgrade through the package manager or CLI?

many thanks for this.. and sorry if this is a little off topic.

zombrax@ub-lap:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree        
Reading state information... Done
vlc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
zombrax@ub-lap:~$ 

but in VLC, help, about; I get

VLC media player 0.8.6 (wxWidgets interface)

(c) 1996-2006 - the VideoLAN Team

---

### Post by Martje_001 on 2008-09-27
You will only get critical updates. If you want to use 0.9 you have to compile it yourself, get a deb package somewhere or upgrade top intrepid.

---

### Post by Elfy on 2008-09-27
You can get it from here [http://tombuntu.com/index.php/2008/09/16/install-vlc-media-player-092-in-ubuntu/](http://tombuntu.com/index.php/2008/09/16/install-vlc-media-player-092-in-ubuntu/)

---

### Post by binbash on 2008-09-27
this release fixed my all subtitle bugs : ) I am happy with it.It is time to uninstall smplayer

---

### Post by zombrax on 2008-09-28
> **forestpixie said:**
> You can get it from here [http://tombuntu.com/index.php/2008/09/16/install-vlc-media-player-092-in-ubuntu/](http://tombuntu.com/index.php/2008/09/16/install-vlc-media-player-092-in-ubuntu/)

yup did it according to that page and i still end up installing the same version..

is this tutorial for the new versions only? i run 7.04

---

### Post by Elfy on 2008-09-28
yea - I guess you'd need to do it from sources for feisty.

Did you know that Feisty will soon be out of support - [http://ubuntuforums.org/showthread.php?t=932075](http://ubuntuforums.org/showthread.php?t=932075)

---

### Post by cariboo on 2008-09-28
Version 0.9.2 showed up in the Intrepid repositories on friday night so it will be in the next release.

Jim

---

### Post by zombrax on 2008-09-28
> **forestpixie said:**
> yea - I guess you'd need to do it from sources for feisty.

Did you know that Feisty will soon be out of support - [http://ubuntuforums.org/showthread.php?t=932075](http://ubuntuforums.org/showthread.php?t=932075)


yeah man; I'm aware of the cycle but my poor lappy with 256MB RAM runs pretty slow as it is with 7.04. I don't think I'll be installing anything else on this apart from putting it in the Hall of Fame :lolflag:

---

### Post by binbash on 2008-09-28
Version 0.9.3 is up

---

### Post by Elfy on 2008-09-28
That was quick :)

---

### Post by www.rzr.online.fr on 2008-12-29
> **billgoldberg said:**
> Nope, Qgktstyle didn't work for me.

I applied the theme, and the preview looked good. 

Vlc however still looked the same.

--

It looks good on my laptop, because the gtk theme matched the qt theme.

On my desktop, I'll stick to totem.


I suspect it's a bug to report on vlc or your theme , what theme are you using ? :

-- 
[http://rzr.online.fr/q/dark](http://rzr.online.fr/q/dark)

---

### Post by mamamia88 on 2008-12-29
are you sure thats new?  i did vlc --version in the terminal and it says 0.9.4 so does that mean i have the latest version installed already?

---

### Post by misGnomer on 2008-12-30
There's another thread about installing VLC 0.9.8 (for Hardy and Intrepid).

[http://ubuntuforums.org/showthread.php?p=6435444](http://ubuntuforums.org/showthread.php?p=6435444)

---

### Post by ksraj on 2009-04-02
> **imgkg said:**
> new VLC player 0.9.2 has been released for installations you can check this [http://tombuntu.com/index.php/2008/09/16/install-vlc-media-player-092-in-ubuntu/](http://tombuntu.com/index.php/2008/09/16/install-vlc-media-player-092-in-ubuntu/)


Can anyone please he help me in getting started in MPEG4,I need to understand where closed caption information is getting into MPEG4 Frame. 

if you have any document about closed caption in MPEG4

Thanks,
Raj

---

### Post by JackieChan on 2009-04-02
> **klange said:**
> It doesn't look out of place at all.
You need to grab qmake-qt4 and you can then build + install [qgtkstyle](http://labs.trolltech.com/page/Projects/Styles/GtkStyle) quite easily.

I started using it with a minimum number of QT apps back when it was still in testing. Qgtkstyle is now part of QT 4.5 (but even in Intrepid, we'll still have 4.4, so you need to build it manually).

[img]http://random.oasis-games.com/vlc092.png[/img]

^ VLC with ClearGlow GTK theme.
I hate Naruto. But at least your not a fanboy, so I at least have some respect for you. ;)

---

### Post by toejamfootball on 2009-04-02
Awesome :guitar:

---

### Post by Rocket2DMn on 2009-04-02
This thread is outdated, please start a new one for your problems in the proper support forum.
Thank you.

---

