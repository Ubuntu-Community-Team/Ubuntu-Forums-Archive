---
title: "No audio when ffmpeg converts to flv"
date: 2009-04-13
forum: Ubuntu Studio
---

### Post by Austin17 on 2009-04-13
I was using ffmpeg and it was working fine except that it didn't have the xvid codec and wouldn't convert anything that needed it. So I followed [this]("https://wiki.ubuntu.com/ffmpeg") guide to compile it myself from the repositories with the proper codecs. It seemed to compile fine and it now started converting the videos with xvid, except now for some reason anything I convert to flv has no audio. The video works fine, but even for files I converted to flv before I recompiled it have no audio when I try to reconvert them. What have I done wrong? Did I miss an audio codec or something when I recompiled it? Thanks for the help in advance.

---

### Post by andrew.46 on 2009-04-14
Hi Austin17,

Could you attempt to convert a file to flv exactly as you have described here and post the *full* commandline and *full* terminal results? This will give some info as to the version of FFmpeg that you have and also why the audio is failing.

All the best,

Andrew

---

### Post by Austin17 on 2009-04-14
Thanks for the reply; this is what I get:

```
austin@MEUbuntu:~$ ffmpeg -i Test.wmv Test.flv
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-liba52 --disable-debug --enable-libfaad --enable-libfaac --enable-gpl --enable-x264 --enable-xvid --enable-pthreads --enable-libvorbis --enable-pp --enable-libtheora --enable-libogg --enable-libgsm --enable-swscaler --disable-debug --enable-shared --prefix=/usr
  libavutil version: 49.3.0
  libavcodec version: 51.38.0
  libavformat version: 51.10.0
  built on Apr 12 2009 17:16:37, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
[wmv3 @ 0xb7ed4188]Extra data: 8 bits left, value: 0

Seems stream 1 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, asf, from 'Test.wmv':
  Duration: 00:00:29.8, start: 20.000000, bitrate: 986 kb/s
  Stream #0.0: Audio: wmav2, 44100 Hz, stereo, 64 kb/s
  Stream #0.1: Video: wmv3, yuv420p, 640x480, 25.00 fps(r)
Output #0, flv, to 'Test.flv':
  Stream #0.0: Video: flv, yuv420p, 640x480, q=2-31, 200 kb/s, 25.00 fps(c)
Stream mapping:
  Stream #0.1 -> #0.0
[wmv3 @ 0xb7ed4188]Extra data: 8 bits left, value: 0
Press [q] to stop encoding
frame=  745 q=24.8 Lsize=    1305kB time=29.8 bitrate= 358.9kbits/s    
video:1294kB audio:0kB global headers:0kB muxing overhead 0.913982%
```

---

### Post by FakeOutdoorsman on 2009-04-14
What version of Ubuntu are you using?  My guess is that you will have to tell FFmpeg what the output audio should be.  For some reason it isn't doing it automatically, either it can't decode wmav2 or it doesn't know (or can't encode) what audio format should go into flv.  It's hard to guess since there are so many revisions of FFmpeg floating around.  Show the output of:
```
ffmpeg -formats | egrep "wmav|mp3"
```
Although compiling FFmpeg is usually the best way to enable restricted encoders, the guide you followed uses old source code.  I keep meaning to update that FFmpeg wiki page.  A more up to date guide:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by Austin17 on 2009-04-14
I'm running 8.04 server edition. Here is the output of that command:
```
austin@MEUbuntu:~$ ffmpeg -formats | egrep "wmav|mp3"
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-liba52 --disable-debug --enable-libfaad --enable-libfaac --enable-gpl --enable-x264 --enable-xvid --enable-pthreads --enable-libvorbis --enable-pp --enable-libtheora --enable-libogg --enable-libgsm --enable-swscaler --disable-debug --enable-shared --prefix=/usr
  libavutil version: 49.3.0
  libavcodec version: 51.38.0
  libavformat version: 51.10.0
  built on Apr 12 2009 17:16:37, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
 DE mp3             MPEG audio layer 3
 D A    mp3
 D A    mp3adu
 D A    mp3on4
 DEA    wmav1
 DEA    wmav2
```

---

### Post by FakeOutdoorsman on 2009-04-14
Most FLV use mp3 audio, but your FFmpeg can't encode mp3.  You have several choices:

[size=4]1.[/size] Recompile FFmpeg from recent source as explained in my link above and then use this command:
```
ffmpeg -i input.wmv -acodec libmp3lame -ar 44100 -b 512k output.flv
```

*or*

[size=4]2.[/size] Use FFmpeg from the Medibuntu repository as explained here,  [HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283), and use this command:
```
ffmpeg -i input.wmv -ar 44100 -b 512k output.flv
```

You can change the *-b* option to whatever bitrate you prefer, otherwise FFmpeg will default to 200 kb/s which may be too low for you.

**Edit:** If you're going to use this FLV with a Flash movie player such as JW Player or FlowPlayer, you will need to run it through FLVtool2 to correct the metadata so it will play correctly:
```
flvtool2 -UP output.flv
```

---

### Post by Austin17 on 2009-04-14
Thanks for the help. Now it is working like it originally did, the wmv is converting to flv with audio and all, but avi videos with xvid are failing to convert. Any ideas on what I should try?

Here is what is happening now:
```
austin@MEUbuntu:~$ ffmpeg -i input.avi output.flv
FFmpeg version SVN-r18518, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.25. 0 / 52.25. 0
  libavformat   52.32. 0 / 52.32. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on Apr 14 2009 21:36:36, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
Input #0, avi, from 'input.avi':
  Duration: 04:02:14.48, start: 0.000000, bitrate: 953 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 544x320 [PAR 1:1 DAR 17:10], 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, 5.1, s16, 192 kb/s
Output #0, flv, to 'output.flv':
    Stream #0.0: Video: flv, yuv420p, 544x320 [PAR 1:1 DAR 17:10], q=2-31, 200 kb/s, 90k tbn, 25 tbc
    Stream #0.1: Audio: libmp3lame, 48000 Hz, 5.1, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height
```

---

### Post by FakeOutdoorsman on 2009-04-14
FLV can only handle an audio sampling rate of 44100 Hz or below, so you need to add **-ar 44100** to your output options.

---

### Post by Austin17 on 2009-04-14
Hmm, still doesn't seem to work, this is what I'm getting:

```
austin@MEUbuntu:~$ ffmpeg -i input.avi -ar 44100 output.flv
FFmpeg version SVN-r18518, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.25. 0 / 52.25. 0
  libavformat   52.32. 0 / 52.32. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on Apr 14 2009 21:36:36, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
Input #0, avi, from 'input.avi':
  Duration: 04:02:14.48, start: 0.000000, bitrate: 953 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 544x320 [PAR 1:1 DAR 17:10], 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, 5.1, s16, 192 kb/s
Output #0, flv, to 'output.flv':
    Stream #0.0: Video: flv, yuv420p, 544x320 [PAR 1:1 DAR 17:10], q=2-31, 200 kb/s, 90k tbn, 25 tbc
    Stream #0.1: Audio: libmp3lame, 44100 Hz, 5.1, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height
```

---

### Post by FakeOutdoorsman on 2009-04-15
I failed to realize that your input audio has 5.1 channel surround sound.  The output needs to be downmixed to stereo or mono for FLV:
```
ffmpeg -i input.avi -ar 44100 -ac 2 output.flv
```
This may not give you the best results since downmixing can lead to distortion, but for a FLV video it should work fine.

---

### Post by andrew.46 on 2009-04-15
Hi Austin17,

Try adding in:

```
-ac 2
```

Andrew

**Edit:** Beaten :-).

---

### Post by Austin17 on 2009-04-15
Woohoo! Thanks guys, its seems to be working now! I didn't finish let it finish it's encoding job, but started it and it seemed to be working fine. I'll leave it encoding overnight for now. Thanks for the help!

---

### Post by Austin17 on 2009-04-15
Sorry for the double post, just wanted to say that it converted fine, only thing is ffmpeg seems to run slower than it did before for some reason. Thanks again for the help!

---

