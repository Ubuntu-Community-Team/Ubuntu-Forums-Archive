---
title: "[SOLVED] Converting mts or mt2s to usable format"
date: 2008-10-25
forum: Ubuntu Studio
---

### Post by HIGHLIFE on 2008-10-25
Could someone help me find an up to date guide on how to convert mts or m2ts into a usable format in Ubuntu?

---

### Post by HIGHLIFE on 2008-10-26
I've searching ubuntu forums and their seems to be no up to date easy answer.  Is anyone doing this right now?  It would be nice if I could have an avi without losing quality.

---

### Post by FakeOutdoorsman on 2008-10-26
What do you want to convert to?  Maybe a better question is: what will the converted video be used for?  I've converted mts (h264 video, ac3 audio) from the Panasonic HMC-150 using ffmpeg with no problems.

---

### Post by cotcot on 2008-10-26
[[COLOR="Blue"]Here[/COLOR]]("http://wesleybailey.com/articles/m2tstoavi-avchd") is a way to convert.
Another way is to compile the latest version of kdenlive (beta 0.7). 

This is the way I ended after trying the above link :
```
xporthdmv -nh 00161.MTS 1 1 1
ldecod -i bits0001.mpv -o /tmp/samplevideo.yuv
mv bits0001.mpa /tmp/samplevideo.ac3
ffmpeg -r 25 -s 1440x1080 -i 00161.MTS -acodec ac3 -ab 256k -ac 2 -vcodec mpeg4 -sameq -aspect 16:9 -b 15000k -deinterlace -copyts 00161.avi
```

My camera is a Canon HF100.

---

### Post by HIGHLIFE on 2008-10-27
I've tried that link but my video always comes out looking like the picture I have attached.  I can somewhat see the video I've taken so I can tell it's doing something right, but it still looks horrible.  Is there a way to fix this?  By the way my camera is a Canon Vixea HF10.  

cotcot when I try your commands I get:

Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec (id=86020) for input stream #0.1

---

### Post by HIGHLIFE on 2008-10-28
bump.

---

### Post by HIGHLIFE on 2008-11-04
I'm sorry guys but I'd really like to have the ability to use the video from this camera. Does anyone know what I'm doing wrong?

---

### Post by FakeOutdoorsman on 2008-11-04
Paste the complete output of:
```
ffmpeg -i input.mts
```

---

### Post by HIGHLIFE on 2008-11-04
```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
[h264 @ 0xb7ecb6e8]PAFF interlacing is not implemented
[h264 @ 0xb7ecb6e8]concealing 4080 DC, 4080 AC, 4080 MV errors
Input #0, mpegts, from '00000.MTS':
  Duration: 00:00:07.3, start: 0.800300, bitrate: 16041 kb/s
  Stream #0.0[0x1011]: Video: h264, yuv420p, 1920x1080, 29.97 fps(r)
  Stream #0.1[0x1100]: Audio: 0x0000, 48000 Hz, stereo, 256 kb/s
Must supply at least one output file

```

---

### Post by FakeOutdoorsman on 2008-11-04
I'm going to assume your video contains ac3 audio.  Your version of ffmpeg doesn't seem to support ac3 audio.  You can see if decoding or encoding is available with your ffmpeg version with:
```
ffmpeg -formats | grep ac3
```
Mine gives:
```
DEA    ac3             ATSC A/52A (AC-3)
```
D = decoding available
E = encoding available
A = audio codec

You can either use an older, third-party precompiled version of ffmpeg from Medibuntu or compile the most recent ffmpeg yourself.  I'm unsure if Medibuntu's version of ffmpeg can handle ac3, but if you compile it yourself ac3 support is built in.

[HOWTO: Compile the latest ffmpeg and x264]("http://ubuntuforums.org/showthread.php?t=786095")

---

### Post by nowardev on 2008-11-05
medibuntu for ibex has not ffmpeg yet

---

### Post by HIGHLIFE on 2008-11-10
Thanks Fakeoutdoorsman, after compiling a new version of ffmpeg everything is working.

---

### Post by jtappin on 2008-12-01
> **FakeOutdoorsman said:**
> I'm going to assume your video contains ac3 audio.  Your version of ffmpeg doesn't seem to support ac3 audio.  

SNIP

  I'm unsure if Medibuntu's version of ffmpeg can handle ac3, but if you compile it yourself ac3 support is built in.

[HOWTO: Compile the latest ffmpeg and x264]("http://ubuntuforums.org/showthread.php?t=786095")

Strange thing is, it did work a couple of months ago, but now even manually reinstalling the medibuntu version of ffmpeg (on hardy) doesn't seem to work.

---

### Post by FakeOutdoorsman on 2008-12-01
> **jtappin said:**
> Strange thing is, it did work a couple of months ago, but now even manually reinstalling the medibuntu version of ffmpeg (on hardy) doesn't seem to work.

What is your ffmpeg command and the full ffmpeg output?

---

### Post by jtappin on 2008-12-02
> **FakeOutdoorsman said:**
> What is your ffmpeg command and the full ffmpeg output?

I'm using a somewhat modified version of the m2tstoavi.fifo script.

The ffmpeg call is:
```

			ffmpeg -r 29.97 -s ${xsz}x1080 -vcodec mpeg4 \
			    -sameq -i $videofifo -aspect ${aspect} \
			    -acodec pcm_s16le -i $audiofile -b 15000k \
			    $outputfile || exit 1 


```
Where $xsz can be either 1920 or 1440, and $aspect is "4:3" or "16:9". The only option for -acodec that I've tried which doesn't cause an error is "copy"


The output from ffmpeg is:
```

Input #0, rawvideo, from '/tmp/00006.yuv':
  Duration: N/A, bitrate: N/A
  Stream #0.0: Video: rawvideo, yuv420p, 1920x1080, 29.97 fps(r)
Input #1, ac3, from '/tmp/00006.ac3':
  Duration: 00:00:11.9, start: 0.000000, bitrate: 256 kb/s
  Stream #1.0: Audio: 0x0000, 48000 Hz, stereo, 256 kb/s
Output #0, avi, to '00006.avi':
  Stream #0.0: Video: mpeg4, yuv420p, 1920x1080, q=2-31, 15000 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: pcm_s16le, 48000 Hz, stereo, 1536 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #1.0 -> #0.1
Unsupported codec (id=86020) for input stream #1.0
exit 1

```

I have tried installing the source package, and rebuilding with:
```

confflags += --enable-decoder=ac3 --enable-demuxer=ac3 --enable-parser=ac3

```
added to [FONT="Courier New"]debian/rules[/FONT] but to no avail.

(I have tried using the svn source build from the m2ts install script, but than I get loads of mpeg4 header errors (I don't have a copy of those handy)).

---

### Post by nowardev on 2008-12-03
use mencoder then if you can 
 
just to write an example.... i don't know if it works but ffmpeg it's evil everytime it changes everysingle software ffmpeg based is fuc*ed

mencoder  -forceidx  -ofps 25  -oac mp3lame   -lameopts abr:br=128  -srate 48000  -vf scale= ${xsz}:1080,harddup -ovc xvid -xvidencopts bitrate=1500 $videofifo || exit 1 

or 

mencoder  -forceidx  -aspect 16:9  -ofps 25  -oac faac  -faacopts br=128  -srate 48000  -vf scale=720:576,harddup -ovc xvid -xvidencopts bitrate=1500

---

### Post by jtappin on 2008-12-04
> **nowardev said:**
> use mencoder then if you can 
 

mencoder also has essentially the same problem -- it produces an error that it doesn't know how to decode the audio, but then instead of stopping, it goes ahead and makes a video with no audio.

I'm therefore guessing that some library used by both ffmpeg and mencoder has had ac3 support removed, the question is which one?

---

### Post by FakeOutdoorsman on 2008-12-04
> **jtappin said:**
> I'm using a somewhat modified version of the m2tstoavi.fifo script.

...

Where $xsz can be either 1920 or 1440, and $aspect is "4:3" or "16:9". The only option for -acodec that I've tried which doesn't cause an error is "copy"

What version of Ubuntu are you using?  Give the full output of:
```
ffmpeg -version
```

---

### Post by jtappin on 2008-12-04
> **FakeOutdoorsman said:**
> What version of Ubuntu are you using?  Give the full output of:
```
ffmpeg -version
```

I'm running Kubuntu Hardy (I'm not yet ready to go to KDE4 except on my "crash & burn" box).

The version of ffmpeg is installed from the source packages in the repositories, with the following additions to the [FONT="Courier New"]debian/rules[/FONT] file:
```

DEB_BUILD_OPTIONS="risky"
confflags += --enable-decoder=ac3 --enable-demuxer=ac3 --enable-parser=ac3

```

```

james@xena:/data/software$ ffmpeg -version
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-decoder=ac3 --enable-demuxer=ac3 --enable-parser=ac3 --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Dec  2 2008 19:49:10, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
ffmpeg      SVN-rUNKNOWN
libavutil   3212032
libavcodec  3352064
libavformat 3344896
james@xena:/data/software$ ffmpeg -formats | grep ac3
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-decoder=ac3 --enable-demuxer=ac3 --enable-parser=ac3 --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Dec  2 2008 19:49:10, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
 DE ac3             raw ac3
  EA    ac3

```

The first ac3 line in the formats list only appeared in my source-builds, the second is unchanged from the standard release

---

### Post by Erlander on 2008-12-05
I'm useless with the command line so when in another thread Handbrake was suggested I tried it straight away. [http://ubuntuforums.org/showthread.php?t=898235&highlight=Handbrake]("http://ubuntuforums.org/showthread.php?t=898235&highlight=Handbrake")

I have converted 1920 x1080 MTS files and 1440 x 1080 files from my Sony Hard Disc HD camera with good results.

Handbrake is in the repositories and now does more than rip DVD's.

Rob

---

### Post by FakeOutdoorsman on 2008-12-05
> **jtappin said:**
> I'm running Kubuntu Hardy (I'm not yet ready to go to KDE4 except on my "crash & burn" box).

The version of ffmpeg is installed from the source packages in the repositories, with the following additions to the [FONT="Courier New"]debian/rules[/FONT] file.

The first ac3 line in the formats list only appeared in my source-builds, the second is unchanged from the standard release

I recommend removing your compiled ffmpeg and undoing whatever changes you made to debian/rules:
```
sudo apt-get purge ffmpeg
```
Then recompile using the latest version of ffmpeg from the official ffmpeg svn.  The Ubuntu repository source is old and if you're going to compile ffmpeg yourself then I don't know of any reason not to use the latest ffmpeg source.  FFmpeg is actively developed and recent revisions natively support ac3:

[HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095")

Also, it is much easier to troubleshoot recent ffmpeg revisions.

---

### Post by HighInBC on 2009-11-28
I can watch this type without converting it by using VLC player.

---

### Post by tetrafuran on 2009-12-24
This was labeled solved. I wonder how did you solve it. I faced the same problem U know.

---

### Post by tetrafuran on 2009-12-26
Now I have fought with this long enough. It's time to ask.
1) during the installation it displays a video without sound. How do I fix the sound?
2) I've copied m2tstoavi.fifo script to /usr/local/bin/ folder, but attempting to convert a file results in "xporthdmv: Command not found". Apparenlty the guide forgot to mention I need more scripts and I need to put them somewhere too. great... OK. so what do I need and where should it be put?

---

### Post by cotcot on 2009-12-27
> **tetrafuran said:**
> Now I have fought with this long enough. It's time to ask.
1) during the installation it displays a video without sound. How do I fix the sound?
2) I've copied m2tstoavi.fifo script to /usr/local/bin/ folder, but attempting to convert a file results in "xporthdmv: Command not found". Apparenlty the guide forgot to mention I need more scripts and I need to put them somewhere too. great... OK. so what do I need and where should it be put?
This thread is already old because development in AVCHD is going fast nowadays. Ffmeg and mplayer support .mts fairly good. 
If you are in  karmic I suggest to use [[COLOR="Red"]Handbrake[/COLOR]]("http://handbrake.fr/downloads.php").
For command line I use this after having installed mplayer :
```
mencoder -oac copy -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=1920:1080,harddup -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=8000:keyint=15:aspect=16/9:threads=4 whatever.MTS -ofps 25 -fps 50 -o whatever.mpg
```

Or if you want it deinterlaced :
```
mencoder -oac copy -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=1920:1080,harddup -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=8000:keyint=15:aspect=16/9:threads=4 whatever.MTS -vf lavcdeint -ofps 25 -fps 50 -o whatever.mpg
```

---

### Post by tetrafuran on 2009-12-28
cool.
Thanks. This will be worth my time. U know the problem with the advice "use the search before posting" is that lots of threads don't seem to answer the question and even if they do, they are already obsolete.

OMG. That conversion will take a while... I didn't think it was that CPU-labor-intensive.

---

