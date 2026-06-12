---
title: "HOWTO: Convert .ts to .mkv"
date: 2008-09-15
forum: Tutorials
---

### Post by falstaff on 2008-09-15
Hello,

I searched several hours to do this conversation, thats why im sharing this here. [MPEG transport stream]("http://en.wikipedia.org/wiki/MPEG_transport_stream"), which is usullay a .ts files, is often used in TV broadcasting. So with this guide you can convert recorded TV-streams (HDTV and SDTV) into mkv files. Note: There is no reencoding/compression of video or sound streams! When it is MPEG-2 before, its MPEG-2 after too!

**Motivation**
Why would I want to convert a .ts file to .mkv? There are two main reasons for me: First, Matroska (mkv) is an open Video Container with broad support. Second, Matroska files are smaller then .ts files (around 3%, without additional compression, just less overhead!). Additional, you can define more Metainformation for the streams (e.x. audio language)

**Demuxing .ts file**
I did this with TsRemux from dmz01 over at doom9.org. There is no native Linux version! It's written in .NET, so we can use Mono to run it under Linux (tested with 0.21.2).

First we need to install additional Mono libraries.
```

  $ sudo aptitude install libmono-winforms2.0-cil

```

Then you have to download TsRemux from [this thread]("http://forum.doom9.org/showthread.php?t=125447") in the doom9.org Forum.

To start this TsRemux use this command:
```

  $ mono TsRemux.exe

```

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=85322&stc=1&d=1221497061[/IMG]

At the main window you can open your .ts-file. Once opened, you should see a stream list in the left box. **Right click** an a stream and select "**Demux ... to elementary stream**". A filename you can use anything you want, its probably a good idea to name it after the content, for example out.mpeg or out.avc.

Once demuxed, you can get over and remux it to a mkv-file.

**Muxing to a .mkv file**

This is done using mkvmerge from the mkvtoolnix program suite. We also need mplayer do determine the fps of the .ts stream. There may be an easier method... It doesnt matter from where you now the fps of your .ts stream, the number is all that counts :-)! It is all contained in the repository, so we use a little aptitude magic again:
```

  $ sudo aptitude install mkvtoolnix mkvtoolnix-gui mplayer

```

You can run the GUI using this command:
```

  $ mmg

```

Now you can add the streams demuxed before with the add button. 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=85323&stc=1&d=1221497061[/IMG]

You may get a warning that the number of frames per seconds could not be determined. We can do this using mplayer from the console on the original .ts file:

```

  $ mplayer input.ts

```

You get an output like this:
```

MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3200+ (Family: 15, Model: 31, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Desktop/arte.hd.ts.
TS file format detected.
VIDEO H264(pid=120) AUDIO MPA(pid=131) NO SUBS (yet)!  PROGRAM N. 3585
[COLOR="Red"]**FPS seems to be: 25.000000**[/COLOR]
xscreensaver_disable: Could not find XScreenSaver window.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] Failed to connect to server: Connection refused
[AO_ALSA] alsa-lib: pcm_hw.c:1099:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: Device or resource busy
[AO_ALSA] alsa-lib: pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
[AO_ALSA] Playback open error: Device or resource busy
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Device or resource busy
[AO_ALSA] alsa-lib: pcm_hw.c:1099:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: Device or resource busy
[AO_ALSA] alsa-lib: pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
[AO_ALSA] Playback open error: Device or resource busy
[AO ARTS] loading the aRts backend "/usr/lib/libartscbackend.la" failed
[AO ESD] latency: [server: 0.24s, net: 0.00s] (adjust 0.24s)
AO: [esd] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...

```

You have to set this frame rate in the "Format specific options" Tab of the Video stream under "FPS".

Once all streams are added, you can define an output filename and start muxing! You're done! 

If audio is not sync with video, you may have taken a wrong FPS-rate....

---

### Post by swMan on 2008-09-27
Thank you falstaff. It is very useful to know the TsRemux.exe program can run in linux.

---

### Post by EzInKy on 2008-10-22
This...

```

ffmpeg -i input.ts -vcodec copy -sameq -acodec copy -f matroska output.mkv

```

...works as well, and doesn't require installing mono.

---

### Post by jimmah6786 on 2009-01-05
> **EzInKy said:**
> This...

```

ffmpeg -i input.ts -vcodec copy -sameq -acodec copy -f matroska output.mkv

```

...works as well, and doesn't require installing mono.

When i try that i get the response of

```
 Unable for find a suitable output format for 'output.mkv' 
```

Did you have to compile your version of FFMpeg a certain way?

---

### Post by bebox on 2009-04-01
it doesnt work for me with ffmpeg...can you help me.?

---

### Post by FakeOutdoorsman on 2009-04-01
> **bebox said:**
> it doesnt work for me with ffmpeg...can you help me.?
Show the complete FFmpeg output.

---

### Post by jimmah6786 on 2009-04-30
> **jimmah6786 said:**
> When i try that i get the response of

```
 Unable for find a suitable output format for 'output.mkv' 
```

Did you have to compile your version of FFMpeg a certain way?

**GOT IT!!**
Have to compile ffmpeg from source. Follow this link [http://ubuntuforums.org/showthread.php?t=786095&highlight=ffmpeg+m2ts]("http://ubuntuforums.org/showthread.php?t=786095&highlight=ffmpeg+m2ts")

---

### Post by tsx2424 on 2012-01-22
It works.Thank you for tips.

---

### Post by adalle on 2013-05-04
You don't have to demux TS input sources for mkvmerge GUI (/usr/bin/mmg).  You can give it the TS as the input source, and it will see the A/V sources therein, and you can remux it without the intermediary step.

Running 12.04LTS, which includes mkvmerge 5.1.0.

---

### Post by meekey on 2013-10-27
[QUOTE=EzInKy;6013396]This...

```

ffmpeg -i input.ts -vcodec copy -sameq -acodec copy -f matroska output.mkv

```

 Change the code to this, It worked for me :) 

```

ffmpeg -i input.ts -sn -vcodec copy -sameq -acodec copy -f matroska output.mkv

```

---

### Post by FakeOutdoorsman on 2013-10-27
[sameq does not mean "same quality"](http://superuser.com/a/478550/110524): it is being ignored in your command since you can't re-encode and use "-vcodec copy" at the same time, and it has been removed upstream anyway. The "-f matroska" is superfluous.

---

