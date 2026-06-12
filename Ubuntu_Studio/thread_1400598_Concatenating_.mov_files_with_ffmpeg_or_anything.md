---
title: "Concatenating .mov files with ffmpeg or anything?"
date: 2010-02-07
forum: Ubuntu Studio
---

### Post by davemar on 2010-02-07
I've got some .mov files orignally from a HD camera which are in 1440x1080 format (non-square pixels) and is in yuv422p format. I would like to concatenate these files into one big one, but can't find out how. Simply doing a "cat f1.mov f2.mov > fall.mov" does not work. I've tried piping this to ffmpeg with -vcodec to to "copy", but that doesn't work either. So is there a way to do it with either ffmpeg or something else?

I used ffmpeg to cut the original monster .mov files down to smaller ones, so I assume concatenation would be within it's ability.

I know that the .mov don't play (in vlc at least) unless they are complete as they appears to be some vital information at the end of file which is required before it can play. So I assume it's how you deal with the header and footer of the file is the issue.

Ta, Dave.

---

### Post by LuridCinema on 2010-02-07
Im reading that AVISynth can do it ..
[http://www.videohelp.com/tools/Avisynth](http://www.videohelp.com/tools/Avisynth)

---

### Post by davemar on 2010-02-07
It appears to be a Windows only application, so out of the question for me unfortunately.

---

### Post by FakeOutdoorsman on 2010-02-07
Can you provide some details about the video files?
```
ffmpeg -i input.mov
```
You may be able to use MP4Box or mkvmerge depending on the format.

---

### Post by LuridCinema on 2010-02-07
Wouldnt it be easier to just drop them into an NLE and just render ? take bout the same time as command line and less if tyou count searching for an answer

---

### Post by FakeOutdoorsman on 2010-02-07
> **LuridCinema said:**
> Wouldnt it be easier to just drop them into an NLE and just render ? take bout the same time as command line and less if tyou count searching for an answer

Sometimes you do have to end up taking that route, but what if davemar is using command-line only system or wants to create an automated script?

Installing a NLE that works and re-encoding long, high resolution videos could take much more time, and end up being lower quality (unless a lossless format is used), than simply appending one stream to another without the need to re-encode.

---

### Post by davemar on 2010-02-08
> **FakeOutdoorsman said:**
> Can you provide some details about the video files?
```
ffmpeg -i input.mov
```
You may be able to use MP4Box or mkvmerge depending on the format.

Here's the output:
```

FFmpeg version SVN-r21637, Copyright (c) 2000-2010 Fabrice Bellard, et al.
  built on Feb  4 2010 23:44:09 with gcc 4.4.1
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50. 8. 0 / 50. 8. 0
  libavcodec    52.52. 0 / 52.52. 0
  libavformat   52.50. 0 / 52.50. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 9. 0 /  0. 9. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'cam0_0.mov':
  Metadata:
    major_brand     : qt  
    minor_version   : 512
    compatible_brands: qt  
    encoder         : Lavf52.50.0
    encoder-eng     : Lavf52.50.0
  Duration: 00:00:21.00, start: 0.000000, bitrate: 115975 kb/s
    Stream #0.0(eng): Video: dvvideo, yuv422p, 1440x1080, 115200 kb/s, PAR 4:3 DAR 16:9, 25 fps, 25 tbr, 25 tbn, 25 tbc
    Stream #0.1(eng): Audio: pcm_s16be, 48000 Hz, 1 channels, s16, 768 kb/s
At least one output file must be specified

```

I'm not fussed about the audio, that can go if needed.

I've got lots of files to concatenate, so doing it all from the command line and scripts it what I'm after.

---

### Post by Grenage on 2010-02-08
I've used mencoder in the past, works a treat.

```
mencoder -oac copy -ovc copy -idx -o output.avi video1.avi video2.avi video3.avi
```

---

### Post by FakeOutdoorsman on 2010-02-08
> **davemar said:**
> Here's the output:
```

FFmpeg version SVN-r21637, Copyright (c) 2000-2010 Fabrice Bellard, et al.
  built on Feb  4 2010 23:44:09 with gcc 4.4.1
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50. 8. 0 / 50. 8. 0
  libavcodec    52.52. 0 / 52.52. 0
  libavformat   52.50. 0 / 52.50. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 9. 0 /  0. 9. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'cam0_0.mov':
  Metadata:
    major_brand     : qt  
    minor_version   : 512
    compatible_brands: qt  
    encoder         : Lavf52.50.0
    encoder-eng     : Lavf52.50.0
  Duration: 00:00:21.00, start: 0.000000, bitrate: 115975 kb/s
    Stream #0.0(eng): Video: dvvideo, yuv422p, 1440x1080, 115200 kb/s, PAR 4:3 DAR 16:9, 25 fps, 25 tbr, 25 tbn, 25 tbc
    Stream #0.1(eng): Audio: pcm_s16be, 48000 Hz, 1 channels, s16, 768 kb/s
At least one output file must be specified

```

I'm not fussed about the audio, that can go if needed.

I've got lots of files to concatenate, so doing it all from the command line and scripts it what I'm after.
Looks like DVCPRO HD.  I was able to concatenate / join / merge / append two DVCPRO HD videos with similar specs to yours with mkvmerge (part of the mkvtoolnix package).  It doesn't like the mov container (it would be worth taking a look at the mkvmerge options) so this would have been a perfect case to use a named pipe, but mkvmerge doesn't read y4m files, so instead I had to use temporary files:
```
ffmpeg -i input.mov -vcodec copy -acodec copy temp.mkv
ffmpeg -i input2.mov -vcodec copy -acodec copy temp2.mkv
mkvmerge -o output.mkv temp.mkv + temp2.mkv
```
My computer was too old and slow to decode this properly, but I think it worked.

I didn't try Grenage's example, but it might be more effective and easier.

---

### Post by davemar on 2010-02-09
> **Grenage said:**
> I've used mencoder in the past, works a treat.

```
mencoder -oac copy -ovc copy -idx -o output.avi video1.avi video2.avi video3.avi
```

That did the trick. I had to use -nosound as it was confused over the audio I had, but I'm not needing the audio anyway.

I haven't tried FakeOutdoorsman's method yet, but will try do so if I've time.

Thanks for the efforts.

---

### Post by Grenage on 2010-02-09
Glad it did the job.  I think that there is also a mencoder command for checking and correcting audio that's out of synch.  I used to use it after 'catting' videos together; unfortunately I can't remember what it was!

---

### Post by speedrcj on 2010-09-09
and what do you do if they're different codecs?  For example... I'm trying to add a single black frame onto the beginning of an m2v file.  It's mpeg2, and I have a .png.

---

### Post by FakeOutdoorsman on 2010-09-09
Can you show some more information about your m2v file?
```
ffmpeg -i input.m2v
```
You want only 1 black frame at the beginning?

---

### Post by speedrcj on 2010-09-09
Input #0, mpegvideo, from part2A.m2v: Duration: 00:03:05.79, bitrate: 48999 kb/s Stream #0.0: Video: mpeg2video, yuv420p, 1408x1056 [PAR 1:1 DAR 4:3], 49000 kb/s, 30 tbr, 1200k tbn, 60 tbc


Yeah 1 frame at the beginning.  It's a weird request I know, thanks for helping though!

---

### Post by speedrcj on 2010-09-09
I should mention I made a 1 frame clip from a black frame and attempted.. Was really kinda hoping that would work. =)

```

cat blackFrame.m2v video.m2v > output.m2v
ffmpeg -i output.m2v -vcodec mpeg2video finalVideo.m2v

```

---

### Post by FakeOutdoorsman on 2010-09-09
How about something like this?  These commands are straight from my *history* (GNU History Library), so you'll need to change a few parameters like *-size* and *-r*.

1. Create black frame.  You could use the GIMP, but I'll use convert from the imagemagick package because I like command-line tools:
```
convert -size 1280x720 xc:black black.png
```
2. Make video from image:
```
ffmpeg -r 24 -i black.png -vcodec mpeg2video -qscale 2 -vframes 1 frame.m2v
```
3. Combine videos:
```
cat frame.m2v video.m2v > combined.m2v
```
or (depending on file names):
```
cat *.m2v | ffmpeg -i - -vcodec copy combined.m2v
```
or if you're using a recent FFmpeg:
```
ffmpeg -i concat:'frame.m2v|video.m2v' -vcodec copy poop.m2v
```

---

