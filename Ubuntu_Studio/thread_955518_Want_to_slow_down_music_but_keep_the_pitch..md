---
title: "Want to slow down music but keep the pitch."
date: 2008-10-22
forum: Ubuntu Studio
---

### Post by gusst250 on 2008-10-22
Hello. One of my favourites is playing the guitar. I want an application that slows music down but keeps the pitch at the same level.

I think it can be done in audacity but when I open a file in audacity nothing can be done to it, all filters, tools and stuff are deactivated, I can just play it and nothing more.

Any solutions are welcome!

---

### Post by ajgreeny on 2008-10-22
You will need the ladspa plugins, and I think you may even need to compile audacity yourself to get the speed change plugin to work; I believe it is a broken plugin in the ubuntu .deb.  It was possible in a previous version of audacity on ubuntu, I know because I used it several times, so it my be worth trying an earlier version of audacity if you can get one.

For the plugins look for **tap-plugins** and **swh-plugins** in synaptic.

---

### Post by 6v6 on 2008-10-22
Hi all.

I'm trying to do the same but with video (guitar tuition DVD's and solos!)

You can do audio in Audacity - works fine for me with Intrepid :

- Open Audacity & load a sound file
- select all or part of the file (drag over the waveform with your mouse)
- click "Effect->ChangeTempo"

This works for me, the "Effect" controls are only greyed out when the sound is playing

HTH!

---

### Post by thorgal on 2008-10-23
google Rubberband by Chris Cannam, it is the library that ardour is using for time stretching/shrinking without pitch change.
rubberband can do quite some useful stuff and is keeping improving.

---

### Post by pirattrev on 2008-10-23
wait, it's possible to slow down music but keep the pitch? That's awesome! I always though that it'd be almost impossible to keep the consistency of the music and change the pitch (since most pitch changers literally lengthen the wave for the note, making it lower).

---

### Post by thorgal on 2008-10-24
you can also look into an app called freecycle. It works like Recycle, you can see a video here :

[http://www.propellerheads.se/products/recycle/index.cfm?fuseaction=get_article&article=what_is_it](http://www.propellerheads.se/products/recycle/index.cfm?fuseaction=get_article&article=what_is_it)

---

### Post by skullmunky on 2008-10-31
Yeah, in Audacity, Change Tempo will let you slow down without changing pitch, and Change Pitch will let you change pitch without changing the speed.  Change Speed does the more traditional resampling method, where higher pitched sounds are faster and vice versa.

If you can't apply any effects, you may have to select something first.  Drag over the waveform or do Ctrl-A to select all, then try doing effects.  That stopped me from using Audacity for like half a year ... 

@pirattrev - crazy, right?  :guitar:   it's timestretching and interpolating but on a whole lot of tiny windows instead of over the whole sample.  with too much change you do get artifacts.  which in turn gives you the signature sound of drum n bass.

---

### Post by raboofje on 2008-11-22
Rubberband and audacity are good options already mentioned.

Drawback of those is that you can't manipulate the speed 'live'/'realtime' afaik. 

I seem to remember the free [Sonic Visualiser]("http://www.sonicvisualiser.org/") does that, as well as the commercial (but cool and cheap) [Transcribe!]("http://www.seventhstring.com/xscribe/overview.html")

---

### Post by Ethel the Frog on 2008-11-24
not perhaps the answer you are looking for but the Roland Boss micro BR will do it.

Awsome bit of kit in my view and sooo sexy to look at.  the designer deserves a pat on the back!

---

### Post by luctor on 2008-11-24
+1 for Sonic Visualizer. It uses rubberband as time stretcher.
Had to build it from source (both rubberband and sonic-visualiser) because there´s no amd64 package :-)
Also the beat/tempo detection is pretty good, you'll need the qm plugins for that.

[http://www.sonicvisualiser.org/](http://www.sonicvisualiser.org/)
[http://vamp-plugins.org/](http://vamp-plugins.org/)

Transcribe!7 has a good realtime eq and also besides tempo change can do realtime pitch shifting. It's an amazing program.

---

### Post by pranayama on 2008-12-04
I have done this for speeches that I had to transcribe. Use Synaptic or apt-get to install sox and libsox-fmt-all. Then at the command line type:

```
sox originalfile slowerfile tempo 0.6 rabbit -c0
```

This would create a new file called slowerfile at the same pitch but 60% of the speed/tempo of originalfile.

---

### Post by kaligus on 2008-12-29
> **luctor said:**
> +1 for Sonic Visualizer. It uses rubberband as time stretcher.
Had to build it from source (both rubberband and sonic-visualiser) because there´s no amd64 package :-)
Also the beat/tempo detection is pretty good, you'll need the qm plugins for that.


Info:
Ubuntu 8.04-64 on an amd64 with 4gb of ram, several hundred GB of hard drive space, could care less about audio output though I do have the default pulse stuff.

question:
What silly little step, memo, note, or other doodad did I miss in compiling sonic visualizer.

I have used SV for a long time before I left the MS fold for Ubuntu and havent had need since until now and when I try compiling 'rubber band' from source I get the following (quoted far below).

Vamp seems to compile ok and the rubber band configure doesnt seem to throw errors or other junk.

Synaptic spews lots of things when searching for ladspa though nothing which looks like a solution to me.

> # make
g++ -DHAVE_FFTW3 -DFFTW_DOUBLE_ONLY -DNO_THREAD_CHECKS -g -O2 -fPIC -Wall       -I/usr/local/include   -Irubberband -Isrc    -c -o src/AudioCurve.o src/AudioCurve.cpp
g++ -DHAVE_FFTW3 -DFFTW_DOUBLE_ONLY -DNO_THREAD_CHECKS -g -O2 -fPIC -Wall       -I/usr/local/include   -Irubberband -Isrc    -c -o src/ConstantAudioCurve.o src/ConstantAudioCurve.cpp
g++ -DHAVE_FFTW3 -DFFTW_DOUBLE_ONLY -DNO_THREAD_CHECKS -g -O2 -fPIC -Wall       -I/usr/local/include   -Irubberband -Isrc    -c -o src/FFT.o src/FFT.cpp
g++ -DHAVE_FFTW3 -DFFTW_DOUBLE_ONLY -DNO_THREAD_CHECKS -g -O2 -fPIC -Wall       -I/usr/local/include   -Irubberband -Isrc    -c -o src/HighFrequencyAudioCurve.o src/HighFrequencyAudioCurve.cpp
g++ -DHAVE_FFTW3 -DFFTW_DOUBLE_ONLY -DNO_THREAD_CHECKS -g -O2 -fPIC -Wall       -I/usr/local/include   -Irubberband -Isrc    -c -o src/PercussiveAudioCurve.o src/PercussiveAudioCurve.cpp
g++ -DHAVE_FFTW3 -DFFTW_DOUBLE_ONLY -DNO_THREAD_CHECKS -g -O2 -fPIC -Wall       -I/usr/local/include   -Irubberband -Isrc    -c -o src/Profiler.o src/Profiler.cpp
g++ -DHAVE_FFTW3 -DFFTW_DOUBLE_ONLY -DNO_THREAD_CHECKS -g -O2 -fPIC -Wall       -I/usr/local/include   -Irubberband -Isrc    -c -o src/Resampler.o src/Resampler.cpp
g++ -DHAVE_FFTW3 -DFFTW_DOUBLE_ONLY -DNO_THREAD_CHECKS -g -O2 -fPIC -Wall       -I/usr/local/include   -Irubberband -Isrc    -c -o src/rubberband-c.o src/rubberband-c.cpp
g++ -DHAVE_FFTW3 -DFFTW_DOUBLE_ONLY -DNO_THREAD_CHECKS -g -O2 -fPIC -Wall       -I/usr/local/include   -Irubberband -Isrc    -c -o src/RubberBandStretcher.o src/RubberBandStretcher.cpp
g++ -DHAVE_FFTW3 -DFFTW_DOUBLE_ONLY -DNO_THREAD_CHECKS -g -O2 -fPIC -Wall       -I/usr/local/include   -Irubberband -Isrc    -c -o src/SilentAudioCurve.o src/SilentAudioCurve.cpp
g++ -DHAVE_FFTW3 -DFFTW_DOUBLE_ONLY -DNO_THREAD_CHECKS -g -O2 -fPIC -Wall       -I/usr/local/include   -Irubberband -Isrc    -c -o src/SpectralDifferenceAudioCurve.o src/SpectralDifferenceAudioCurve.cpp
g++ -DHAVE_FFTW3 -DFFTW_DOUBLE_ONLY -DNO_THREAD_CHECKS -g -O2 -fPIC -Wall       -I/usr/local/include   -Irubberband -Isrc    -c -o src/StretchCalculator.o src/StretchCalculator.cpp
g++ -DHAVE_FFTW3 -DFFTW_DOUBLE_ONLY -DNO_THREAD_CHECKS -g -O2 -fPIC -Wall       -I/usr/local/include   -Irubberband -Isrc    -c -o src/StretcherImpl.o src/StretcherImpl.cpp
g++ -DHAVE_FFTW3 -DFFTW_DOUBLE_ONLY -DNO_THREAD_CHECKS -g -O2 -fPIC -Wall       -I/usr/local/include   -Irubberband -Isrc    -c -o src/StretcherProcess.o src/StretcherProcess.cpp
g++ -DHAVE_FFTW3 -DFFTW_DOUBLE_ONLY -DNO_THREAD_CHECKS -g -O2 -fPIC -Wall       -I/usr/local/include   -Irubberband -Isrc    -c -o src/StretcherChannelData.o src/StretcherChannelData.cpp
g++ -DHAVE_FFTW3 -DFFTW_DOUBLE_ONLY -DNO_THREAD_CHECKS -g -O2 -fPIC -Wall       -I/usr/local/include   -Irubberband -Isrc    -c -o src/Thread.o src/Thread.cpp
g++ -DHAVE_FFTW3 -DFFTW_DOUBLE_ONLY -DNO_THREAD_CHECKS -g -O2 -fPIC -Wall       -I/usr/local/include   -Irubberband -Isrc    -c -o src/Window.o src/Window.cpp
g++ -DHAVE_FFTW3 -DFFTW_DOUBLE_ONLY -DNO_THREAD_CHECKS -g -O2 -fPIC -Wall       -I/usr/local/include   -Irubberband -Isrc    -c -o src/sysutils.o src/sysutils.cpp
g++ -DHAVE_FFTW3 -DFFTW_DOUBLE_ONLY -DNO_THREAD_CHECKS -g -O2 -fPIC -Wall       -I/usr/local/include   -Irubberband -Isrc    -c -o src/main.o src/main.cpp
g++ -o bin/rubberband src/AudioCurve.o src/ConstantAudioCurve.o src/FFT.o src/HighFrequencyAudioCurve.o src/PercussiveAudioCurve.o src/Profiler.o src/Resampler.o src/rubberband-c.o src/RubberBandStretcher.o src/SilentAudioCurve.o src/SpectralDifferenceAudioCurve.o src/StretchCalculator.o src/StretcherImpl.o src/StretcherProcess.o src/StretcherChannelData.o src/Thread.o src/Window.o src/sysutils.o src/main.o -lsndfile   -lsamplerate   -lfftw3 -lm    -lpthread
ar rsc lib/librubberband.a src/AudioCurve.o src/ConstantAudioCurve.o src/FFT.o src/HighFrequencyAudioCurve.o src/PercussiveAudioCurve.o src/Profiler.o src/Resampler.o src/rubberband-c.o src/RubberBandStretcher.o src/SilentAudioCurve.o src/SpectralDifferenceAudioCurve.o src/StretchCalculator.o src/StretcherImpl.o src/StretcherProcess.o src/StretcherChannelData.o src/Thread.o src/Window.o src/sysutils.o
g++ -shared -Wl,-Bsymbolic -Wl,-soname=librubberband.so.2 src/AudioCurve.o src/ConstantAudioCurve.o src/FFT.o src/HighFrequencyAudioCurve.o src/PercussiveAudioCurve.o src/Profiler.o src/Resampler.o src/rubberband-c.o src/RubberBandStretcher.o src/SilentAudioCurve.o src/SpectralDifferenceAudioCurve.o src/StretchCalculator.o src/StretcherImpl.o src/StretcherProcess.o src/StretcherChannelData.o src/Thread.o src/Window.o src/sysutils.o -o lib/librubberband.so -lsamplerate   -lfftw3 -lm    -lpthread
g++ -DHAVE_FFTW3 -DFFTW_DOUBLE_ONLY -DNO_THREAD_CHECKS -g -O2 -fPIC -Wall       -I/usr/local/include   -Irubberband -Isrc    -c -o src/vamp/RubberBandVampPlugin.o src/vamp/RubberBandVampPlugin.cpp
g++ -DHAVE_FFTW3 -DFFTW_DOUBLE_ONLY -DNO_THREAD_CHECKS -g -O2 -fPIC -Wall       -I/usr/local/include   -Irubberband -Isrc    -c -o src/vamp/libmain.o src/vamp/libmain.cpp
g++ -shared -Wl,-Bsymbolic -Wl,--version-script=src/vamp/vamp-plugin.map -o lib/vamp-rubberband.so src/AudioCurve.o src/ConstantAudioCurve.o src/FFT.o src/HighFrequencyAudioCurve.o src/PercussiveAudioCurve.o src/Profiler.o src/Resampler.o src/rubberband-c.o src/RubberBandStretcher.o src/SilentAudioCurve.o src/SpectralDifferenceAudioCurve.o src/StretchCalculator.o src/StretcherImpl.o src/StretcherProcess.o src/StretcherChannelData.o src/Thread.o src/Window.o src/sysutils.o src/vamp/RubberBandVampPlugin.o src/vamp/libmain.o -L/usr/local/lib -lvamp-sdk   -lsamplerate   -lfftw3 -lm    -lpthread
g++ -DHAVE_FFTW3 -DFFTW_DOUBLE_ONLY -DNO_THREAD_CHECKS -g -O2 -fPIC -Wall       -I/usr/local/include   -Irubberband -Isrc    -c -o src/ladspa/RubberBandPitchShifter.o src/ladspa/RubberBandPitchShifter.cpp
In file included from src/ladspa/RubberBandPitchShifter.cpp:15:
src/ladspa/RubberBandPitchShifter.h:18:20: error: ladspa.h: No such file or directory
In file included from src/ladspa/RubberBandPitchShifter.cpp:15:
src/ladspa/RubberBandPitchShifter.h:29: error: ISO C++ forbids declaration of ‘LADSPA_Descriptor’ with no type
src/ladspa/RubberBandPitchShifter.h:29: error: expected ‘;’ before ‘*’ token
src/ladspa/RubberBandPitchShifter.h:52: error: ‘LADSPA_PortDescriptor’ does not name a type
src/ladspa/RubberBandPitchShifter.h:53: error: ‘LADSPA_PortRangeHint’ does not name a type
src/ladspa/RubberBandPitchShifter.h:56: error: ‘LADSPA_PortDescriptor’ does not name a type
src/ladspa/RubberBandPitchShifter.h:57: error: ‘LADSPA_PortRangeHint’ does not name a type
src/ladspa/RubberBandPitchShifter.h:59: error: ‘LADSPA_Properties’ does not name a type
src/ladspa/RubberBandPitchShifter.h:61: error: ‘LADSPA_Descriptor’ does not name a type
src/ladspa/RubberBandPitchShifter.h:62: error: ‘LADSPA_Descriptor’ does not name a type
src/ladspa/RubberBandPitchShifter.h:64: error: ‘LADSPA_Handle’ does not name a type
src/ladspa/RubberBandPitchShifter.h:65: error: ‘LADSPA_Handle’ has not been declared
src/ladspa/RubberBandPitchShifter.h:65: error: ‘LADSPA_Data’ has not been declared
src/ladspa/RubberBandPitchShifter.h:66: error: ‘LADSPA_Handle’ has not been declared
src/ladspa/RubberBandPitchShifter.h:67: error: ‘LADSPA_Handle’ has not been declared
src/ladspa/RubberBandPitchShifter.h:68: error: ‘LADSPA_Handle’ has not been declared
src/ladspa/RubberBandPitchShifter.h:69: error: ‘LADSPA_Handle’ has not been declared
src/ladspa/RubberBandPitchShifter.cpp:59: error: ‘LADSPA_PortDescriptor’ does not name a type
src/ladspa/RubberBandPitchShifter.cpp:73: error: ‘LADSPA_PortDescriptor’ does not name a type
src/ladspa/RubberBandPitchShifter.cpp:89: error: ‘LADSPA_PortRangeHint’ does not name a type
src/ladspa/RubberBandPitchShifter.cpp:126: error: ‘LADSPA_PortRangeHint’ does not name a type
src/ladspa/RubberBandPitchShifter.cpp:165: error: ‘LADSPA_Properties’ does not name a type
src/ladspa/RubberBandPitchShifter.cpp:168: error: ‘LADSPA_Descriptor’ does not name a type
src/ladspa/RubberBandPitchShifter.cpp:192: error: ‘LADSPA_Descriptor’ does not name a type
src/ladspa/RubberBandPitchShifter.cpp:216: error: expected initializer before ‘*’ token
src/ladspa/RubberBandPitchShifter.cpp:272: error: ‘LADSPA_Handle’ does not name a type
src/ladspa/RubberBandPitchShifter.cpp:284: error: variable or field ‘connectPort’ declared void
src/ladspa/RubberBandPitchShifter.cpp:284: error: ‘LADSPA_Handle’ was not declared in this scope
src/ladspa/RubberBandPitchShifter.cpp:285: error: expected primary-expression before ‘unsigned’
src/ladspa/RubberBandPitchShifter.cpp:285: error: ‘LADSPA_Data’ was not declared in this scope
src/ladspa/RubberBandPitchShifter.cpp:285: error: ‘location’ was not declared in this scope
make: *** [src/ladspa/RubberBandPitchShifter.o] Error 1


---

### Post by thorgal on 2008-12-29
from this error message:

```

src/ladspa/RubberBandPitchShifter.h:18:20: error: ladspa.h: No such file or directory

```

it looks like you are missing the LADSPA SDK (one header file, basically). Install it :

```

sudo apt-get install ladspa-sdk

```

---

### Post by Ndlovu on 2009-07-30
Here's another way to do it with mplayer:
[http://ubuntuforums.org/showthread.php?t=1226982](http://ubuntuforums.org/showthread.php?t=1226982)

Has the advantage that you don't need to change any files, it all happens on the fly (useful for me working with long transcripts in mp3 format).

---

### Post by andrew.46 on 2009-07-30
Hi Ndlovu,

> **Ndlovu said:**
> Here's another way to do it with mplayer:
[http://ubuntuforums.org/showthread.php?t=1226982](http://ubuntuforums.org/showthread.php?t=1226982)

And yet another if you look at Tip 1: Using 'scaletempo'... :

Top 10 Tricks and Tips for the svn MPlayer
[http://ubuntuforums.org/showthread.php?t=1154431](http://ubuntuforums.org/showthread.php?t=1154431)

All the best,

Andrew

---

### Post by Ndlovu on 2009-07-31
Hi Andrew,

> **andrew.46 said:**
> 
And yet another if you look at Tip 1: Using 'scaletempo'... :

Top 10 Tricks and Tips for the svn MPlayer
[http://ubuntuforums.org/showthread.php?t=1154431](http://ubuntuforums.org/showthread.php?t=1154431)


Scaletempo looks great, especially being able to adjust the tempo on the fly. I'm just not brave enough to compile the svn version yet!

Thanks for your guides, it's great documentation if I ever need the advanced functionality.

---

### Post by andrew.46 on 2009-07-31
Hi Ndlovu,

> **Ndlovu said:**
> Scaletempo looks great, especially being able to adjust the tempo on the fly. I'm just not brave enough to compile the svn version yet!

No need to compile the svn MPlayer if you can wait for the release of Karmic Koala which will have a version of MPlayer that will be able to use the scaletempo filter.

All the best,

Andrew

---

### Post by fracturedmorals on 2009-08-03
If you REALLY want to go crazy with timestretching, there's a program called paulstretch 2.0

[http://hypermammut.sourceforge.net/paulstretch/](http://hypermammut.sourceforge.net/paulstretch/)

This program is completely insane and impractical...and I absolutely love it.

You can stretch a bassdrum out for several years if you so desire (Although, for obvious reasons, I wouldn't recommend that)

Anyways, if you want a precompiled binary you can PM me....

---

