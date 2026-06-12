---
title: "Minimal packages needed to play H.264 video"
date: 2014-03-11
forum: Ubuntu Development Version
---

### Post by alan-pater on 2014-03-11
I am trying to see if I can get video playing without installing a bunch of extra packages. That leaves out the restricted extras packages.

Supposedly, recent Firefox builds have much more built in capacity for playing HTML5/H.264 video, but I don't have it working.
I read that I need the gstreamer1.0-plugins-good and gstreamer1.0-libav packages, but that is not enough for the following sites:

[http://www.youtube.com/html5](http://www.youtube.com/html5)
[http://vimeo.com/86155755](http://vimeo.com/86155755)

As well, the Totem Video player cannot find H.264 codecs.

---

### Post by raja.genupula on 2014-03-11
open synaptic package manager there you can choose what ever you want. Then it will integrate with any system installed player and you can watch.

---

### Post by alan-pater on 2014-03-11
1) Synaptic is not installed in Ubuntu 14.04 by default. I am using "apt-cache search" and "apt-get install".
2) What do I want? What package in Ubuntu 14.04 will allow H.264 video?

---

### Post by alan-pater on 2014-03-11
Just got through reading the earlier post of this: [http://ubuntuforums.org/showthread.php?t=2208040](http://ubuntuforums.org/showthread.php?t=2208040)

Looks like I need to wait for a build of Firefox that can use gstreamer 1.0.

---

### Post by alan-pater on 2014-03-11
Videos (aka Totem) is not playing the video from .flv files. It does play the audio. 

mp4 videos, on the other hand, play both the video and the audio.

Both FLV and MP4 files contain h.264 video.

---

### Post by mc4man on 2014-03-11
Each player is different, you've asked about totem (Videos

gstreamer1.0-libav will give you h.264 in common containers with aac, ect.
gstreamer1.0-plugins-bad will take care of remaining (inc. .flv
If need be also install  gstreamer1.0-plugins-ugly

Players like vlc, mplayer, mpv do not use gstreamer so simply installing them takes care of any needed external libs

---

### Post by alan-pater on 2014-03-11
> **mc4man said:**
> gstreamer1.0-plugins-bad will take care of remaining (inc. .flvInteresting bunch of packages and libraries in the gstreamer1.0-plugins-bad metapackage, but it's not clear which will help play H.264 video in an FLV container. > libdc1394-22 - high level programming interface for IEEE1394 digital camera
libass4 - library for SSA/ASS subtitles rendering
libchromaprint0 - audio fingerprint library
libdca0 - decoding library for DTS Coherent Acoustics streams
libdvdnav4 - DVD navigation library
libdvdread4 - library for reading DVDs
libenca0 - Extremely Naive Charset Analyser
libfaad2 - freeware Advanced Audio Decoder
libfftw3-double3 - Library for computing Fast Fourier Transforms 
libflite1 - Small run-time speech synthesis engine
libfluidsynth1 - Real-time MIDI software synthesizer
libgles2-mesa - free implementation of the OpenGL|ES 2.x API
libgme0 - Playback library for video game music files
libgtkglext1 - OpenGL Extension to GTK+
libilmbase6 - several utility libraries from ILM used by OpenEXR
libkate1 - Kate is a codec for karaoke and text encapsulation
libmimic0 - A video codec for Mimic V2.x content
libmms0 - MMS stream protocol library
libmodplug1 - shared libraries for mod music based on ModPlug
libmpg123-0 - MPEG layer 1/2/3 audio decoder
libofa0-dev - Library for acoustic fingerprinting
libopenal1 - Software implementation of the OpenAL API
libopencv-* - computer vision libraries
libopenexr6 - runtime files for the OpenEXR image library
libsoundtouch0 - Sound stretching library
libspandsp2 - Telephony signal processing library
libsrtp0 - Secure RTP (SRTP) and UST Reference Implementations
libswscale2 - Libav video scaling library
libtbb2 - parallelism library for C++ - runtime files
libvo-aacenc0 - VisualOn AAC encoder library
libvo-amrwbenc0 - VisualOn AMR-WB encoder library
libwildmidi1 - software MIDI player library
libzbar0 - bar code scanner and decoder
freepats - Free patch set for MIDI audio synthesis

---

### Post by alan-pater on 2014-03-11
Aha, narrowed it down!> gstreamer1.0-plugins-bad-videoparsersSo now Videos can play FLV files

---

### Post by mc4man on 2014-03-11
> **alan-pater said:**
> Aha, narrowed it down!So now Videos can play FLV files

It appears that in  14.04 they split up 'bad' into 3 packages

---

### Post by alan-pater on 2014-03-11
Ok. The next video file I am testing is with a .DIVX extension. System reports MP3 audio, DivX MPEG-4 video, and subpicture/x-xsub as unknown.

Audio did not play, taken care of with a: **sudo apt-get install gstreamer1.0-fluendo-mp3**

But no subtitles.

Another video with subtitles that will not play, this time with a .MKV extension. Audio and video both play. audio: MPEG-4 AAC   video: H.264

    subtitles: DVD subpicture

So I have a couple of movies that Movies cannot show the subtitles for ....

---

### Post by QDR06VV9 on 2014-03-11
As mc4man pointed out for one of the few options,
```
Players like vlc, mplayer, mpv do not use gstreamer so simply installing them takes care of any needed external libs
```
I know your mainly interested in totem, but vlc is a great little player.
I can't recall anything it wouldn,t play, and lots of toys and adjustments under the hood.
Regards:)

---

### Post by mc4man on 2014-03-11
No idea about sub support in gstreamer, in regards to divx - see here (on going for 4 yrs., what current status is ???
[https://bugzilla.gnome.org/show_bug.cgi?id=628429](https://bugzilla.gnome.org/show_bug.cgi?id=628429)

---

### Post by SeijiSensei on 2014-03-12
I strongly recommend [SMPlayer]("http://smplayer.sourceforge.net/") if you want a single application that will handle all types of media with good support for subtitles.  It uses mplayer2 as the engine.  Just run "sudo apt-get install smplayer", and you'll be all set.

I long ago gave up trying to navigate the gstreamer world.

---

### Post by QDR06VV9 on 2014-03-12
> **SeijiSensei said:**
> I strongly recommend [SMPlayer]("http://smplayer.sourceforge.net/") if you want a single application that will handle all types of media with good support for subtitles.  It uses mplayer2 as the engine.  Just run "sudo apt-get install smplayer", and you'll be all set.

I long ago gave up trying to navigate the gstreamer world.
Thank You I had forgotten about SMplayer victim of habit>:D
I also have given up on navigating gstreamer.LOL

---

### Post by alan-pater on 2014-03-12
Thanks guys, I am well aware of the other options and use them all the time. 

But the point of this thread was to explore the current state of the art using a minimal default install, not to install a bunch of other apps and a ton of libraries that do a bunch of unrelated things.

---

### Post by andrew.46 on 2014-03-13
> **alan-pater said:**
> I am trying to see if I can get video playing without installing a bunch of extra packages. That leaves out the restricted extras packages.

Fresh install Trusty Tahr (no Flash, no extra codecs) with html 5 preferences set in Youtube played the majority of youtube clips that I requested. These were all VP8 video and vorbis sound and I will admit that I did not test *extensively*. Mind you I prefer browsing youtube with smtube but I guess you are after a more minimal approach...

---

### Post by alan-pater on 2014-03-14
> **andrew.46 said:**
> Fresh install Trusty Tahr (no Flash, no extra codecs) with html 5 preferences set in Youtube played the majority of youtube clips that I requested. These were all VP8 video and vorbis sound and I will admit that I did not test *extensively*. Mind you I prefer browsing youtube with smtube but I guess you are after a more minimal approach...Yes, I have Youtube playing everything I throw at it as well. Still missing is [https://vimeo.com/86155755](https://vimeo.com/86155755) which insists on H264 rather then VP8. I haven't been able to identify which, if any, library or plugin is capable of adding H264 support to Firefox 28.

---

### Post by mc4man on 2014-03-14
> **alan-pater said:**
> Yes, I have Youtube playing everything I throw at it as well. Still missing is [https://vimeo.com/86155755](https://vimeo.com/86155755) which insists on H264 rather then VP8. I haven't been able to identify which, if any, library or plugin is capable of adding H264 support to Firefox 28.

That page works fine here, using current default 14.04 FF 
(while  not youtube I'd guess if you got like in screen on the[ youtube html5 test page]("http://www.youtube.com/html5") you'd be ok.

---

### Post by andrew.46 on 2014-03-14
> **alan-pater said:**
> I haven't been able to identify which, if any, library or plugin is capable of adding H264 support to Firefox 28.

I believe that near native h.264 playback in Firefox is being planned 'in the first half of 2014', if you can wait....

---

