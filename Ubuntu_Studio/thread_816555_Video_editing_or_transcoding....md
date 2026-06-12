---
title: "Video editing or transcoding..."
date: 2008-06-02
forum: Ubuntu Studio
---

### Post by PsycoGeek on 2008-06-02
Is there any way to edit or transcode .ASF files in Linux?

---

### Post by eye208 on 2008-06-03
It depends on the format of the stream inside. ASF is a container format like AVI. It is most commonly used for WMV and WMA streams.

If MPlayer can play the file, MEncoder can transcode it.

---

### Post by PsycoGeek on 2008-06-03
Well, I think the format may be Divx because the recordings were made on a Cowon iAudio A2, which touts Divx in it's specifications.  Thank you for the info eye208!  We'll see how it goes when I finally get a system up and running on Ubuntu.

---

### Post by PsycoGeek on 2008-06-08
> **eye208 said:**
> It depends on the format of the stream inside. ASF is a container format like AVI. It is most commonly used for WMV and WMA streams.

If MPlayer can play the file, MEncoder can transcode it.

I tried Mplayer and the files won't play.  Any other ideas on how to transcode or edit the files directly? How do I tell what format the stream is inside?

What sux here is Windows Movie Maker can edit the files just fine, but I want to put using any Microcrap stuff well behind me.

---

### Post by eye208 on 2008-06-09
The Cowon iAudio A2 records MPEG4 video and MP3 audio, but it probably uses non-standard FourCCs to mark the streams in the ASF container. You can configure MPlayer to recognize non-standard FourCCs by adding these to the ~/.mplayer/codecs.conf file.

If MPlayer doesn't recognize a stream, it will report its FourCC in the terminal window. Try to play one of those ASF files, then post all of MPlayer's output here.

---

### Post by netyire on 2008-06-09
Try kdenlive from the repository, its the best video editor that Ubuntu has right now and its very much similar to Windows Movie Maker (a lot better though).

If it won't open the .asf file you can try converting it with ffmpeg, mencoder or transcode. If all else fails you can always use an online service to convert the file (for free!) - check out [http://www.zamzar.com](http://www.zamzar.com)

If you choose mencoder:
mencoder -ovc lavc -oac lavc -lavcopts acodec=mp3:abitrate=192:vcodec=mpeg4:vbitrate=1500 <inputfile> -o <outputfile>

If you pick ffmpeg: (depending on whether its aspect ratio is 4/3 or 16/9)
ffmpeg -i <inputfile> -target ntsc-dvd <outputname>.mpg
ffmpeg -i <inputfile> -target pal-dvd <outputname>.mpg

---

### Post by eye208 on 2008-06-09
> **netyire said:**
> If it won't open the .asf file you can try converting it with ffmpeg, mencoder or transcode. If all else fails you can always use an online service to convert the file (for free!) - check out [http://www.zamzar.com](http://www.zamzar.com)

If you choose mencoder:
mencoder -ovc lavc -oac lavc -lavcopts acodec=mp3:abitrate=192:vcodec=mpeg4:vbitrate=1500 <inputfile> -o <outputfile>

If you pick ffmpeg: (depending on whether its aspect ratio is 4/3 or 16/9)
ffmpeg -i <inputfile> -target ntsc-dvd <outputname>.mpg
ffmpeg -i <inputfile> -target pal-dvd <outputname>.mpg
What exactly is the point of transcoding the file? Why would you want to transcode from MPEG4 to MPEG2?

---

### Post by FakeOutdoorsman on 2008-06-09
> **PsycoGeek said:**
> ... How do I tell what format the stream is inside? ...

You can use ffmpeg to tell you about the contents of a file:
```
[frink@hedron encode]$ ffmpeg -i pasteeater.avi
Input #0, avi, from 'pasteeater.avi':
  Duration: 00:00:35.66, start: 0.000000, bitrate: 30314 kb/s
    Stream #0.0: Video: dvvideo, yuv411p, 720x480, 29.97 tb(r)
    Stream #0.1: Audio: pcm_s16le, 48000 Hz, stereo, 1536 kb/s
```
Unfortunately, ffmpeg in the repo has not been compiled to support restricted formats so it may not be able to give you information on any media encoded in those formats.  You can use the ffmpeg version from the Medibuntu repo which has been compiled to support many restriced formats.

The "file" command often works too, but is not as detailed:
```
[frink@hedron encode]$ file pasteeater.avi
pasteeater.avi: RIFF (little-endian) data, AVI, 720 x 480, ~30 fps, video: uncompressed, audio: uncompressed PCM (stereo, 48000 Hz)
```

---

