---
title: "rework audio DTS to AC3 mkv file &gt;12Gb"
date: 2009-04-11
forum: Ubuntu Studio
---

### Post by ctw on 2009-04-11
Hi Everybody,

I've tried to convert the DTS audio to AC3 in one mkv file 12Gb longer.

The problem is i've did the compilation, it automatically cuts the file to 9,2 Gb. I lost the rest of the mkv file.

It's a problem with the Ext3? or there is another better way to do it without to lost of the full file.

I use ubuntu 8.10 64x and I've did the work using this doc:

[http://www.networkedmediatank.com/wiki/index.php/Convert_DTS_to_AC3](http://www.networkedmediatank.com/wiki/index.php/Convert_DTS_to_AC3)

Thanks in advance

---

### Post by theluddite on 2009-04-23
Thanks for that link.  I've been looking everywhere for a good way to convert DTS to AC3 since I'm having a similar problem on my D-Link DSM-750 media player.  I'll give it a try and let you know how it works.

---

### Post by FakeOutdoorsman on 2009-04-23
Maybe you can try FFmpeg?

1. Convert the audio:
```
ffmpeg -i input.mkv -ab 448k audiooutput.ac3
```

2. Combine video and audio:
```
ffmpeg -i input.mkv -i audiooutput.ac3 -map 0:0 -map 1:0 -vcodec copy -acodec copy output.mkv
```

---

### Post by theluddite on 2009-04-23
> **FakeOutdoorsman said:**
> Maybe you can try FFmpeg?

1. Convert the audio:
```
ffmpeg -i input.mkv -ab 448k audiooutput.ac3
```

2. Combine video and audio:
```
ffmpeg -i input.mkv -i audiooutput.ac3 -map 0:0 -map 1:0 -vcodec copy -acodec copy output.mkv
```

I would prefer to use ffmpeg since I'd be able to integrate it into the config file for the media server I'm using a lot better and encode on the fly.  Unfortunately I haven't been able to get it to work.  I've searched the web and I can't seem to get a good answer on how to use the "-map" switch.  When I enter what you've suggested I get the same answer I got last night:

> Input #1, ac3, from 'audiooutput.ac3':
  Duration: 01:52:50.8, bitrate: 448 kb/s
    Stream #1.0: Audio: liba52, 48000 Hz, 5:1, 448 kb/s
Number of stream maps must match number of output streams


The mkvdts2ac3 script however, seems to be working famously.  The only thing I can suggest to the OP is that maybe his /tmp partition is too small so the script runs out of room to store the transitional mkv files?

---

### Post by FakeOutdoorsman on 2009-04-24
Post your FFmpeg command and the complete FFmpeg output.

---

### Post by theluddite on 2009-04-26
> **FakeOutdoorsman said:**
> Post your FFmpeg command and the complete FFmpeg output.

Here's the whole thing:

> 
theluddite@big-machine:~/Desktop$ ffmpeg -i input_file.mkv -ab 448k audiooutput.ac3
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:52:45, gcc: 4.3.2
[matroska @ 0x7f7e8ad26040]Ignoring seekhead entry for ID=0x1549a966
[matroska @ 0x7f7e8ad26040]Ignoring seekhead entry for ID=0x1654ae6b
[matroska @ 0x7f7e8ad26040]Ignoring seekhead entry for ID=0x114d9b74
[matroska @ 0x7f7e8ad26040]Unknown entry 0x73a4 in info header
[matroska @ 0x7f7e8ad26040]Unknown track header entry 0x55aa - ignoring
[matroska @ 0x7f7e8ad26040]Unknown track header entry 0x23314f - ignoring
[matroska @ 0x7f7e8ad26040]Unknown track header entry 0x55ee - ignoring
[matroska @ 0x7f7e8ad26040]Unknown track header entry 0xaa - ignoring
[matroska @ 0x7f7e8ad26040]Unknown track header entry 0x55aa - ignoring
[matroska @ 0x7f7e8ad26040]Unknown track header entry 0x23314f - ignoring
[matroska @ 0x7f7e8ad26040]Unknown track header entry 0x55ee - ignoring
[matroska @ 0x7f7e8ad26040]Unknown track header entry 0xaa - ignoring
[matroska @ 0x7f7e8ad26040]Unknown track header entry 0x55aa - ignoring
[matroska @ 0x7f7e8ad26040]Unknown track header entry 0x23314f - ignoring
[matroska @ 0x7f7e8ad26040]Unknown track header entry 0x55ee - ignoring
[matroska @ 0x7f7e8ad26040]Unknown track header entry 0xaa - ignoring
[matroska @ 0x7f7e8ad26040]Unknown track header entry 0x55aa - ignoring
[matroska @ 0x7f7e8ad26040]Unknown track header entry 0x23314f - ignoring
[matroska @ 0x7f7e8ad26040]Unknown track header entry 0x55ee - ignoring
[matroska @ 0x7f7e8ad26040]Unknown track header entry 0xaa - ignoring
Input #0, matroska, from 'input_file.mkv':
  Duration: 01:43:35.8, start: 0.000000, bitrate: N/A
    Stream #0.0(eng): Video: h264, yuv420p, 1280x544 [PAR 1:1 DAR 40:17], 23.98 tb(r)
    Stream #0.1(eng): Subtitle: 0x0000
    Stream #0.2(dut): Subtitle: 0x0000
    Stream #0.3(eng): Audio: liba52, 48000 Hz, 5:1
Output #0, ac3, to 'audiooutput.ac3':
    Stream #0.0(eng): Audio: ac3, 48000 Hz, 5:1, 448 kb/s
Stream mapping:
  Stream #0.3 -> #0.0
Press [q] to stop encoding
size=  339927kB time=6215.8 bitrate= 448.0kbits/s    
video:0kB audio:339927kB global headers:0kB muxing overhead 0.000000%
theluddite@big-machine:~/Desktop$ ffmpeg -i input_file.mkv -i audiooutput.ac3 -map 0:0 -map 1:0 -vcodec copy -acodec copy output.mkv
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:52:45, gcc: 4.3.2
[matroska @ 0x7fa27f812040]Ignoring seekhead entry for ID=0x1549a966
[matroska @ 0x7fa27f812040]Ignoring seekhead entry for ID=0x1654ae6b
[matroska @ 0x7fa27f812040]Ignoring seekhead entry for ID=0x114d9b74
[matroska @ 0x7fa27f812040]Unknown entry 0x73a4 in info header
[matroska @ 0x7fa27f812040]Unknown track header entry 0x55aa - ignoring
[matroska @ 0x7fa27f812040]Unknown track header entry 0x23314f - ignoring
[matroska @ 0x7fa27f812040]Unknown track header entry 0x55ee - ignoring
[matroska @ 0x7fa27f812040]Unknown track header entry 0xaa - ignoring
[matroska @ 0x7fa27f812040]Unknown track header entry 0x55aa - ignoring
[matroska @ 0x7fa27f812040]Unknown track header entry 0x23314f - ignoring
[matroska @ 0x7fa27f812040]Unknown track header entry 0x55ee - ignoring
[matroska @ 0x7fa27f812040]Unknown track header entry 0xaa - ignoring
[matroska @ 0x7fa27f812040]Unknown track header entry 0x55aa - ignoring
[matroska @ 0x7fa27f812040]Unknown track header entry 0x23314f - ignoring
[matroska @ 0x7fa27f812040]Unknown track header entry 0x55ee - ignoring
[matroska @ 0x7fa27f812040]Unknown track header entry 0xaa - ignoring
[matroska @ 0x7fa27f812040]Unknown track header entry 0x55aa - ignoring
[matroska @ 0x7fa27f812040]Unknown track header entry 0x23314f - ignoring
[matroska @ 0x7fa27f812040]Unknown track header entry 0x55ee - ignoring
[matroska @ 0x7fa27f812040]Unknown track header entry 0xaa - ignoring
Input #0, matroska, from 'input_file.mkv':
  Duration: 01:43:35.8, start: 0.000000, bitrate: N/A
    Stream #0.0(eng): Video: h264, yuv420p, 1280x544 [PAR 1:1 DAR 40:17], 23.98 tb(r)
    Stream #0.1(eng): Subtitle: 0x0000
    Stream #0.2(dut): Subtitle: 0x0000
    Stream #0.3(eng): Audio: liba52, 48000 Hz, 5:1
Input #1, ac3, from 'audiooutput.ac3':
  Duration: 01:43:35.8, bitrate: 448 kb/s
    Stream #1.0: Audio: liba52, 48000 Hz, 5:1, 448 kb/s
Number of stream maps must match number of output streams
theluddite@big-machine:~/Desktop$ 


I tried inserting the switch to copy subtitles too.  No dice.

---

### Post by vinan on 2009-10-31
[COLOR=DarkOliveGreen]I used Avidemux,
open file, just leave video mode to copy, and change audio to AC3, and format to MVK. 
and save the file.

good luck:D


Regards
Siva[/COLOR]

---

### Post by MarceloCulotta on 2011-09-01
For converting MKV DTS to MKV ac3, I use two applications: 
WinFF and MKVmerge (it shows as MKV files creator in the Applications menu)


[LIST=1]
[*]WinFF:For creating the AC3 audio track, I open WinFF, then I Add the MKV file that contains the DTS track. In Output details,  I select
[/LIST]
           
           Convet to           **Audio**
            Device Preset      **Ac3 - 384kbps Stereo **
           Output Folder      **Any folder you like** (I use the one containing the MKV file)
           
           This will create an audio file with the same name as the MKV file, but with the   ac3 extension

            2. MKV files creator (mkvmerge)
    
    Input Files: **add the MKV** file for which you created the ac3 audio track.
    In the Tracks, chapters and tags, **UNSELECT the DTS audio file**
    Input files again: **add the ac3** file that you created with WinFF
    **Start muxing**

This creates a file with the same name as the MKV file, except it has a (1) added to it that will have the ac3 audio track for playing as 2 channel stereo.
   
I hope this helps!

---

### Post by Zulu (Be) on 2011-09-25
WinFF only supports AC3 - STEREO, no dolby surround ! If you want more read on ...

FFmpeg can convert to dolby but has one very annoying problem: center speaker sound is not correctly mapped.

best solution is to use the **[mkvdts2ac3]("https://github.com/JakeWharton/mkvdts2ac3/tree/8131e77772ef20250d2b304ba6f12a3813cd6664")** script**. **

[https://github.com/JakeWharton/mkvdt...f12a3813cd6664]("https://github.com/JakeWharton/mkvdts2ac3/tree/8131e77772ef20250d2b304ba6f12a3813cd6664")

Very user friendly, even for a ubuntu dummy like me :wink:.

However, if you have to convert larger dts files it becomes tricky: 

since dcadec is used, you need to install package [libdca]("http://videolan.org/developers/libdca.html%5D"). I recommend following site (step 1)
[http://juliensimon.blogspot.com/2009...audio-dts.html]("http://juliensimon.blogspot.com/2009/01/howto-processing-multichannel-audio-dts.html")

However Package libdca-0.0.5  has a bug when converting large files. You need to adapt 
in previous link following step: 

ubuntu% ./configure --prefix=/usr/localshould become 

ubuntu% ./configure --prefix=/usr/local **CFLAGS="-D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE"**

(see also [http://forums.gentoo.org/viewtopic-t...9-start-0.html]("http://forums.gentoo.org/viewtopic-t-836439-start-0.html") )

I hope this will save you a lot of time I had to spent finding a real solution to convert DTS to AC3 - dolby surround :grin:

---

