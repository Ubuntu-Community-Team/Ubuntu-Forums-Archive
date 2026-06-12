---
title: "AviDemux to compress AVI ?"
date: 2009-09-28
forum: Ubuntu Studio
---

### Post by oygle on 2009-09-28
I have a large AVI file, about 68 Mb, and would like to compress it, so that the file size reduces significantly, without loss in quality, if possible.

I tried saving the AVI a MPEG in AviDemux, after seeing a thread on using this app to compress AVI files. But, the resulting MPEG is larger.  :(

Any clues please ?

Oygle

---

### Post by FakeOutdoorsman on 2009-09-28
You're always going to lose quality when encoding to a lossy format, but with the proper settings the resulting video can be nearly visually lossless.  You didn't mention what format you want or what the final destination of this video is, so I'll give you an example using FFmpeg to encode H.264 video in a MP4 container because it is what I prefer for general desktop use.

If you're using Ubuntu Intrepid or higher you will need to install FFmpeg and enable the restricted encoders.  That's easy to do:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

Now for the FFmpeg command:
```
ffmpeg -i input.avi -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre hq -crf 24 -threads 0 output.mp4
```

Adjust the quality/file size with the *crf* option.  Sane values are 18-28 and a lower number means higher quality.  To learn more about this command see the [FFmpeg x264 encoding guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/).

---

### Post by VertexPusher on 2009-10-01
> **oygle said:**
> I have a large AVI file, about 68 Mb, and would like to compress it, so that the file size reduces significantly, without loss in quality, if possible.

I tried saving the AVI a MPEG in AviDemux, after seeing a thread on using this app to compress AVI files. But, the resulting MPEG is larger.  :(
No matter how large your AVI is, if it has already been compressed there may be no way to reduce its size even more without significant quality loss.

Furthermore you have to understand that there are multiple generations of MPEG video compression. MPEG-1 is the oldest and least efficient. MPEG-2 is better but still requires high bitrates to look good. MPEG-4 ASP and MPEG-4 H.264 are frequently used today, with H.264 being the most efficient so far. As FakeOutdoorsman pointed out, it really depends on where you want to use the resulting file.

You can encode H.264 with Avidemux as well as with ffmpeg or MEncoder. All three use the same codec. In Avidemux, choose AAC for the audio part and either MKV or MP4 as container.

---

### Post by ajaustin on 2009-10-26
> **FakeOutdoorsman said:**
> 

Now for the FFmpeg command:
```
ffmpeg -i input.avi -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre hq -crf 24 -threads 0 output.mp4
```

Adjust the quality/file size with the *crf* option.  Sane values are 18-28 and a lower number means higher quality.  To learn more about this command see the [FFmpeg x264 encoding guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/).

Many thanks for this insight.  I have Hardy Heron installed along with ffmpeg from the Medibuntu package.

When I try to run the command I get:-
```
tony@ubuntu:~/video/sept2009/edit-them$ ffmpeg -i tony-sept2009.avi -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre hq -crf 24 -threads 0 output.mp4
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 17 2009 21:37:49, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
Input #0, avi, from 'tony-sept2009.avi':
  Duration: 00:02:52.4, start: 0.000000, bitrate: 30375 kb/s
  Stream #0.0: Video: dvvideo, yuv420p, 720x576, 25.00 fps(r)
  Stream #0.1: Audio: pcm_s16le, 48000 Hz, stereo, 1536 kb/s
Unknown codec 'libfaac'

```
 
I have libfaac0 installed but not libfaac-dev.

Any ideas on what I need to do?

Tony

---

### Post by FakeOutdoorsman on 2009-10-26
> **ajaustin said:**
> Many thanks for this insight.  I have Hardy Heron installed along with ffmpeg from the Medibuntu package.

When I try to run the command I get:-
```
tony@ubuntu:~/video/sept2009/edit-them$ ffmpeg -i tony-sept2009.avi -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre hq -crf 24 -threads 0 output.mp4
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 17 2009 21:37:49, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
Input #0, avi, from 'tony-sept2009.avi':
  Duration: 00:02:52.4, start: 0.000000, bitrate: 30375 kb/s
  Stream #0.0: Video: dvvideo, yuv420p, 720x576, 25.00 fps(r)
  Stream #0.1: Audio: pcm_s16le, 48000 Hz, stereo, 1536 kb/s
Unknown codec 'libfaac'

```
 
I have libfaac0 installed but not libfaac-dev.

Any ideas on what I need to do?

Tony

FFmpeg from Medibuntu is too old for that command.  It is using the libx264 presets and this isn't supported by your FFmpeg.  I recommend compiling FFmpeg and x264 if you would like to use this command.  It's not very hard to do:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by ajaustin on 2009-10-26
Thanks FakeOutdoorsman.  I think I may be able to do what I want with Kino.  It has an Export facility that gives a good range of formats and bitrates.  If this doesn't work out for me I will take a look at the re-compilation options.

Tony

---

### Post by ajaustin on 2009-10-27
Hello again FakeOutdoorsman.  I address you personally because you seem to be the most on the ball on this topic and many thanks for that.

I have achieved what I wanted, which was to reduce the overall size of a video clip for posting to YouTube, with Kino and think it would be useful to add this info to the thread.

Kino has an Export function and within this there is a general Other tab for exporting to various formats (H264, Flash, MPEG3, MPEG4, 3GPP, AVI, VCD, XVID) at various qualities using FFMPEG.  I don't pretend to know what all these things are but it seems to me that Kino is providing a more friendly user interface to FFMPEG which could be very useful to the less-initiated like myself.

Would you care to take a look at Kino yourself and offer a more informed opinion of what I am saying, for the benefit of others who may follow this thread.

Thanks, Tony

---

### Post by VertexPusher on 2009-10-27
When it comes to video conversion, Avidemux is your best option.

For example, FFMPEG can't encode SSA subtitles into the video. Only Avidemux can do that.

Beginning with Karmic, FAAC support will be removed from FFMPEG. However, Karmic's version of Avidemux remains unaffected because it talks to libfaac directly, not through the crippled libavcodec.

---

### Post by ajaustin on 2009-10-27
> **VertexPusher said:**
> When it comes to video conversion, Avidemux is your best option.

For example, FFMPEG can't encode SSA subtitles into the video. Only Avidemux can do that.

Beginning with Karmic, FAAC support will be removed from FFMPEG. However, Karmic's version of Avidemux remains unaffected because it talks to libfaac directly, not through the crippled libavcodec.

Thanks for your suggestion VertexPusher.  I have looked at Avidemux _again_ and still can't make head nor tail of it.  Is there a Getting Started guide somewhere? I looked at the web site and that is dense with technicalities too.  Neither the Wiki nor the Forum seems to have anything that is remotely suitable for someone like me with 35 years in IT but no knowledge whatsoever of processing video files.

The program itself has no built-in Help.  I don't wish to sound as if I'm carping because I'm sure it's technically very good but it doesn't seem to ready for Jo Public to get started with.

Tony

---

### Post by FakeOutdoorsman on 2009-10-27
> **ajaustin said:**
> Hello again FakeOutdoorsman.  I address you personally because you seem to be the most on the ball on this topic and many thanks for that.

I have achieved what I wanted, which was to reduce the overall size of a video clip for posting to YouTube, with Kino and think it would be useful to add this info to the thread.

Kino has an Export function and within this there is a general Other tab for exporting to various formats (H264, Flash, MPEG3, MPEG4, 3GPP, AVI, VCD, XVID) at various qualities using FFMPEG.  I don't pretend to know what all these things are but it seems to me that Kino is providing a more friendly user interface to FFMPEG which could be very useful to the less-initiated like myself.

Would you care to take a look at Kino yourself and offer a more informed opinion of what I am saying, for the benefit of others who may follow this thread.

Thanks, Tony

Usually I would recommend using the H.264 option, but I looked at Kino's export settings and it is using some terrible options for H.264 so the other options may actually look better, so you're just going to have to do some experimenting.  Choose a section of your video to act as a test clip.  A good test clip would include a cut to another scene.  Now export in Kino.  Try H.264 MP4 Single Pass, H.264 MP4 Dual Pass, MPEG-4 MP4 Single Pass, H.264 MP4 Dual Pass, and the XviD option. Choose a profile that has the word "progressive" in it, like most of the "Best Quality" profiles, otherwise the YouTube video may show interlacing artifacts.  Now watch each clip and choose the one that looks best.

The Kino export settings probably wouldn't work with a recent FFmpeg.  YouTube is going to re-encode whatever you give it, so I recommend giving it high-bitrate videos.

If you compiled FFmpeg, just export as DV File, and then use this FFmpeg command:
```
ffmpeg -i filefromkino.dv -acodec libfaac -ac 2 -ab 192k -vcodec libx264 -vpre hq -crf 18 -threads 0 output.mp4
```
If the audio and video are not synched in YouTube after uploading, then try:
```
ffmpeg -i filefromkino.dv -acodec libfaac -ac 2 -ab 192k -vcodec libx264 -vpre hq -vpre main -crf 18 -threads 0 output.mp4
```
If your input footage is interlaced you can try the *-deinterlace* option.

---

### Post by VertexPusher on 2009-10-28
> **ajaustin said:**
> I have looked at Avidemux _again_ and still can't make head nor tail of it.  Is there a Getting Started guide somewhere? I looked at the web site and that is dense with technicalities too.
Avidemux is very similar to VirtualDub on Windows. Basic operation is to load a video file, optionally cut out some parts, then choose
[list][*]a video codec[*]an audio codec[*]a container format[/list]
and click the Save button. If you select the "Copy" codec, the video or audio stream from the input file will be copied to the output file without modification. This is useful if all you want to do is change the container format.

Optionally you can apply filters to the video or audio before it gets processed by the codec. The most frequently used video filters are
[list][*]Crop (to remove black bars)[*]Resize (to change resolution)[/list]
Audio filters allow e.g. mixdown from 5.1 surround to 2.0 stereo.

Most codecs have reasonable default settings, but you can tweak them towards smaller files or higher quality. Of course, this is where things get technical. If you deal with DVD video, you will need to know
[list][*]how to convert between [interlaced](http://en.wikipedia.org/wiki/Interlace) and [progressive](http://en.wikipedia.org/wiki/Progressive_scan) video[*]how to apply or remove [telecine](http://en.wikipedia.org/wiki/Telecine)[*]how to handle [aspect ratio](http://en.wikipedia.org/wiki/Pixel_aspect_ratio) in anamorphic video[/list]
The most frequently used combinations of codecs and containers are
[list][*]Xvid + MP3 + AVI (aka. "DivX")[*]x264 + AAC + MP4 (Quicktime, iPod, PS3, Xbox 360)[*]x264 + AAC + MKV (aka. "DivX Plus")[/list]

---

### Post by ajaustin on 2009-10-31
> **VertexPusher said:**
> Avidemux is very similar to VirtualDub on Windows. Basic operation is to load a video file, optionally cut out some parts, then choose
[list][*]a video codec[*]an audio codec[*]a container format[/list]
and click the Save button. If you select the "Copy" codec, the video or audio stream from the input file will be copied to the output file without modification. This is useful if all you want to do is change the container format.

Thanks, VertexPusher.  You may not think it, but this is a huge step forward for me.  I had my suspicions about what codecs were but had no idea about containers.

Encouraged by this new enlightenment I am now able to take my first steps in trying to use Avidemux to do something useful.

BTW. I've never heard of Virtual Dub, that's how new to video editing I am, but then I only use Windows in an emergency.

Tony

---

### Post by rykel on 2009-11-01
Hi all,

I am also interested in reducing the filesize of an .avi video made using my camera so that I can upload it quickly to Youtube, and I liked the interface of Kino.

However, despite being user-friendly already, I am also confused by the many options Kino offers, and wonder if anyone knows which is the Export output that gives the best video quality with the smallest filesize?

Thanks for your advice!

---

### Post by ajaustin on 2009-11-01
> **rykel said:**
> Hi all,

I am also interested in reducing the filesize of an .avi video made using my camera so that I can upload it quickly to Youtube, and I liked the interface of Kino.

However, despite being user-friendly already, I am also confused by the many options Kino offers, and wonder if anyone knows which is the Export output that gives the best video quality with the smallest filesize?

Thanks for your advice!

Rykel, with the help of good people in this thread I am now able to reduce the size of videos easily using Avidemux; they all seemed to think that this is a better option than Kino.

Here's what I do:-

Open the .avi file with Avidemux.

Edit it by playing through and setting the A and B markers to the bits I want to cut out and deleting them or saving clips of the content between the A and B markers as new files.

Set the Video option to the first item which is "MPEG-4 ASP (Xvid4)" and the Audio option to "MP3 LAME", leave the Format option as "AVI".

Click on the Video/Configure option and stay on the Main tab.  Change the Encoding Type to Two Pass - Video Size and set the Target Video Size to the number of MB that you would like your file to be.  OK the option window.

Click on Save and give your file a name.  It will be saved with the reduced file size.

I am specifying a file size of 20MB for clips of about 1 minute and they are coming out at between 10MB and 20MB.

Once I got the basics of Avidemux by doing these simple things I found that the rest of it started to make a bit more sense too. I hope this helps you.  "Teach a man to fish and he'll feed himself for the rest of his life."

Tony

---

### Post by JBAlaska on 2009-11-01
ajaustin, After reading through this thread I just have to say that I admired the way you approached your task, Even though you had positive results with kino, you TRIED Avidemux (even though you found it somewhat challenging at first) and you succeeded in accomplishing what you wanted. Bravo M8, for not being afraid to try something new! This to me makes for the perfect Linux user!

---

