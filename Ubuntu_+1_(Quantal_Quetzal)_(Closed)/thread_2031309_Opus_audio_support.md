---
title: "Opus audio support"
date: 2012-07-21
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by jfernyhough on 2012-07-21
Following on from the announcement that Firefox 15 supports Opus [1] I thought I'd have a play. There is a package in the repos (opus-tools) that allows me to encode audio but nothing appears to want to play them, despite them being identified as valid audio files (though this may be down to the Vorbis container).

According to Wikipedia: "The integration of Opus support in GStreamer is largely complete. For FFmpeg, there are patches, but these are still somewhat lacking." [2]

Does anyone know if/when Opus support will make it into Quantal?

--edit
Just noticed the gstreamer1.0-* packages waiting in synaptic. Could well be in there somewhere. :)


[1] [https://hacks.mozilla.org/2012/07/firefox-beta-15-supports-the-new-opus-audio-format/](https://hacks.mozilla.org/2012/07/firefox-beta-15-supports-the-new-opus-audio-format/)
[2] [https://en.wikipedia.org/wiki/Opus_%28codec%29]("https://en.wikipedia.org/wiki/Opus_%28codec%29")

---

### Post by mc4man on 2012-07-21
As far as gstreamer, maybe awhile (1.0?

Support is currently in FFmpeg, haven't checked Libav which is what Debian/Ubuntu/Gstreamer are currently using

By & large libav will lag behind FFmpeg is these area's, even when avplay can decode that doesn't assure Libav's libavcodec will do so. (wmal decoding is an example there or at least was last I checked.

So for example created a test.opus from a .wav (didn't look at the opusenc options too much yet..
Currently I have an audacious build that uses a shared FFmpeg build in /opt. So  I quickly rebuilt FFmpeg with --enable-libopus & aud plays the test encode just fine, see screen

edit: see you mentioned gstreamer1.0 - those packages have been there quite some time & ATM nothing is using them except GS deps on the 1.10 libstreamer package
I'd think all the elements are in place but don't know if there are plans to do so this cycle
(totem would need a new clutter-gst that uses gst 1.0, which is possible, RB,Banshee, ect would need rebuilds at the very least...

---

### Post by mc4man on 2012-07-24
As a bit of further - 
It's likely that 12.10 will stick with the current gstreamer 10 branch, if so maybe they can be prodded into using a more current bad plugin.

support for opus is currently in the 1.0 & is available for the .10 though it hasn't been enabled in Debian(Sid)/Ubuntu
(not surprising in Ubuntu as it's bad plugin is quite old

As I rebuild the bad plugin here to fix a longstanding issue I simply enabled it & opus (decoding), is working thru gstreamer/gstreamer players just fine, though again the current bad plugin (git) has had several fixes for opus

FF should play any online opus as of today's update & local files as well (open with firefox

---

### Post by ads52 on 2012-08-10
> **jfernyhough said:**
> Following on from the announcement that Firefox 15 supports Opus [1] I thought I'd have a play. There is a package in the repos (opus-tools) that allows me to encode audio but nothing appears to want to play them, despite them being identified as valid audio files (though this may be down to the Vorbis container).

It is more than a little bare-bones but you will find that opus-tools also ships with *opusinfo* and *opusdec*. *opusdec* will play back your file easily enough, [an example]("http://www.andrews-corner.org/samples/luckynight.opus") on my own system:

```

$ [COLOR=Red]**opusdec luckynight.opus**[/COLOR]
Decoding to 48000 Hz (2 channels)
Encoded with libopus 1.0.1-rc
ENCODER=opusenc from opus-tools 0.1.4
artist=Jody Marie Gnant
title=Lucky Night
album=Treasure Quest Soundtrack
genre=Soundtrack
track=9
Decoding complete. 

```With a little bit of work, as mc4man has suggested, you may only have to visit *opusdec* this once :).

---

### Post by jfernyhough on 2012-08-13
I've just found out that Debian have added support for Opus in their gstreamer0.10-plugins-bad package.

So I downloaded it to see if it worked. ;)

$ cd ~/temp
$ wget [http://ftp.us.debian.org/debian/pool/main/g/gst-plugins-bad0.10/gstreamer0.10-plugins-bad_0.10.23-7_amd64.deb](http://ftp.us.debian.org/debian/pool/main/g/gst-plugins-bad0.10/gstreamer0.10-plugins-bad_0.10.23-7_amd64.deb)
$ wget [http://ftp.us.debian.org/debian/pool/main/g/gst-plugins-bad0.10/libgstreamer-plugins-bad0.10-0_0.10.23-7_amd64.deb](http://ftp.us.debian.org/debian/pool/main/g/gst-plugins-bad0.10/libgstreamer-plugins-bad0.10-0_0.10.23-7_amd64.deb)
$ sudo dpkg -i --force-overwrite *.deb

Load an .opus file into Totem - and it works!

Unfortunately anything that doesn't use gstreamer won't see the codec e.g. VLC. Also, programs that don't know about .opus don't want to load it, e.g. Clementine.

Note those links are for amd64. For other architectures look here: 
[http://packages.debian.org/sid/gstreamer0.10-plugins-bad](http://packages.debian.org/sid/gstreamer0.10-plugins-bad)
and here: 
[http://packages.debian.org/sid/libgstreamer-plugins-bad0.10-0](http://packages.debian.org/sid/libgstreamer-plugins-bad0.10-0)

---

### Post by mc4man on 2012-08-13
Vlc just added some support to the git source - 
[http://trac.videolan.org/vlc/ticket/7185](http://trac.videolan.org/vlc/ticket/7185)
But no decoder thru avcodec yet

If 12.10 doesn't upgrade to gstreamer1.0* then hopefully they'll provide a more recent bad plugin than the current old, semi-broken one

---

### Post by ads52 on 2012-08-13
> **jfernyhough said:**
> Unfortunately anything that doesn't use gstreamer won't see the codec e.g. VLC.

This wiki page will probably work for Quantal, although I admit I have not tested it with the prerelease:

[https://help.ubuntu.com/community/Compiling%20MPlayer](https://help.ubuntu.com/community/Compiling%20MPlayer)

and should give opus playback from the MPlayer commandline and from the gui SMPlayer. You could probably omit the section where libopus is compiled and simply download* libopus-dev* with the other -dev files. (Although I note that the repository is already carrying an *older* version of libopus...).

Exciting times indeed :).

---

### Post by pravinbravi on 2012-08-14
foobar2000 1.1.14 beta3 (via wine) plays opus. great!!!

---

### Post by FakeOutdoorsman on 2012-08-14
> **pravinbravi said:**
> foobar2000 1.1.14 beta3 (via wine) plays opus. great!!!

I avoid using wine.

As of 2012-06-24 [FFmpeg has an Opus decoder](http://git.videolan.org/?p=ffmpeg.git;a=commit;h=a6cf296bd90ae4a8097f1681f86bfa42b32fe074) via [libopus](http://www.opus-codec.org/). You can compile this library:

```
sudo apt-get install build-essential checkinstall
wget http://downloads.xiph.org/releases/opus/opus-1.0.1-rc.tar.gz
tar xzvf opus-1.0.1-rc.tar.gz
cd opus-1.0.1-rc
./configure
make
sudo checkinstall --pkgname=opus --pkgversion="1.0.1-rc" --backup=no \
  --deldoc=yes --fstrans=no --default
```

or install **libopus-dev** as of Ubuntu Quantal 12.10.

...and then see [How To Compile FFmpeg and x264 on Ubuntu](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide). During the FFmpeg *./configure* step add *--enable-libopus*. You should then be able to play the Opus files with ffplay or re-encode them to whatever you want with ffmpeg (I haven't actually tested these instructions or tried to decode Opus with ffmpeg on 12.10).

Another earlier commit shows a [Xiph CELT/Opus decoder using libcelt](http://git.videolan.org/?p=ffmpeg.git;a=commit;h=89451dd6e4da40ed73b8bbee2d48d8d8be1d5b0c).

---

### Post by jfernyhough on 2012-08-14
> **pravinbravi said:**
> foobar2000 1.1.14 beta3 (via wine) plays opus. great!!!Oh, that reminded me of the noise sharpening plugin. Works great in Foobar, just wish I could get decatf's delta plugin working in KDE...

[https://decatf.wordpress.com/2010/11/04/gstreamer-delta-audio-sharpening-plugin/](https://decatf.wordpress.com/2010/11/04/gstreamer-delta-audio-sharpening-plugin/)

---

### Post by jfernyhough on 2012-10-17
I *think* Opus is now supported by default in Quantal by Gstreamer... at least, it works in Totem. :)

Just waiting for other players like DeaDBeeF and Clementine to catch up...

---

### Post by mc4man on 2012-10-17
> **jfernyhough said:**
> I *think* Opus is now supported by default in Quantal by Gstreamer... at least, it works in Totem. :)

Just waiting for other players like DeaDBeeF and Clementine to catch up...
opus was enabled in the bad plugin upgrade to  0.10.23-7ubuntuX, overall most complete bad plugin for 12.10/12.04 currently is here

[https://launchpad.net/~diwic/+archive/gstreamer-h264-testing](https://launchpad.net/~diwic/+archive/gstreamer-h264-testing)

Vlc just added opus in 12.10 in 2.0.4-0ubuntu1

---

