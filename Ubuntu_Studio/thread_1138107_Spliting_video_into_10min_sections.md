---
title: "Spliting video into 10min sections?"
date: 2009-04-26
forum: Ubuntu Studio
---

### Post by Fatguyinspandex on 2009-04-26
I have a almost 3 hour video I need to put into 10min sections for upload to youtube. is there a faster way than with kino. each video is taking 20min to export. is there anyway i can just make it split the main video into a new video every 10min?

---

### Post by bobince on 2009-04-26
It depends&#8201;—&#8201;what format's the video?

For general video processing you could use mencoder (command line) or avidemux (GUI). For some formats you can use direct stream copying (‘-ovc copy -oac copy’ in mencoder, ‘Video->Copy/Audio->Copy’ in avidemux) to avoid re-encoding the streams (which is what takes you 20 minutes, and loses quality). Select an input region using the ‘-ss’ and ‘-endpos’ options to mencoder, or use the ‘A’ and ‘B’ buttons in avidemux.

Then if you want to automate it you can just make a shell script containing the right mencoder parameters for each 10-minute block, or in avidemux save a project file and edit it to include multiple uses of app.markerA/markerB and app.save().

There may also be more direct tools for specific formats, eg. mpgtx for MPEG splitting.

---

### Post by FakeOutdoorsman on 2009-04-27
FFmpeg can do this without the need to re-encode:
```
ffmpeg -ss 00:10:00:00 -t 00:10:00:00 input.mp4 -acodec copy -vcodec copy output.mp4
```
The *-ss* option tells FFmpeg to ignore the first 10 minutes (hours:minutes:seconds:frames) of the input video.  The *-t* option is the duration.  In this example, FFmpeg will start 10 minutes into the input video and then "record" 10 minutes to the output file.  FFmpeg is just copying the audio and video, so it should be quick because you are not transcoding anything.

---

### Post by Tuvok41 on 2009-08-13
> **FakeOutdoorsman said:**
> FFmpeg can do this without the need to re-encode:
```
ffmpeg -ss 00:10:00:00 -t 00:10:00:00 input.mp4 -acodec copy -vcodec copy output.mp4
```
The *-ss* option tells FFmpeg to ignore the first 10 minutes (hours:minutes:seconds:frames) of the input video.  The *-t* option is the duration.  In this example, FFmpeg will start 10 minutes into the input video and then "record" 10 minutes to the output file.  FFmpeg is just copying the audio and video, so it should be quick because you are not transcoding anything.
So if I wanted to not skip the first 10 mins and have that first 10 mins saved to a new file, I just dont add : -ss 00:10:00:00 is that right? Then I would add it for the second part and the next ones would need to be added another 10 mins to -ss 00:10:00:00 to look like -ss 00:20:00:00, is that how it should be perform?
And thnx for this command, I think it will come in handy for me. Just want to make sure if I understood it right.

---

### Post by FakeOutdoorsman on 2009-08-13
> **Tuvok41 said:**
> So if I wanted to not skip the first 10 mins and have that first 10 mins saved to a new file, I just dont add : -ss 00:10:00:00 is that right? Then I would add it for the second part and the next ones would need to be added another 10 mins to -ss 00:10:00:00 to look like -ss 00:20:00:00, is that how it should be perform?
And thnx for this command, I think it will come in handy for me. Just want to make sure if I understood it right.

Yes, you can omit *-ss* for the first 10 minute section.  You also need *-t 10:00* to copy only 10 minutes.  The *-t* option will stay the same for all of them except maybe the last section, if it is under 10 minutes, it can be omitted.

---

### Post by Tuvok41 on 2009-08-13
> **FakeOutdoorsman said:**
> Yes, you can omit *-ss* for the first 10 minute section.  You also need *-t 10:00* to copy only 10 minutes.  The *-t* option will stay the same for all of them except maybe the last section, if it is under 10 minutes, it can be omitted.
Thank you very much for the precision, it is well appreciated.
I forgot to mention in the previous post does it work with an avi file as well? replacing .mp4 by .avi ?

Just tried it and here is what happens :

```
ffmpeg -t 00:08:00:00 The.xxxxx.xxxxx.avi -acodec copy -vcodec copy /temp/The.xxxxx.xxxxx.Part.1of3.avi

```

And here is the output, it is trying to overwrite my original file!
```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 16 2009 21:16:26, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
File 'The.xxxxx.xxxxx.avi' already exists. Overwrite ? [y/N] N

```
What is wrong with the command did I miss something?

---

### Post by Tuvok41 on 2009-09-05
Here is what I entered in terminal to successfully split the file:
```

ffmpeg -i 00:10:00:00 input.mpg -acodec copy -vcodec copy output.mpg

ffmpeg -i 00:10:00:00 input.mpg -ss 00:10:00:00 -acodec copy -vcodec copy output.mpg

ffmpeg -i 00:10:00:00 input.mpg -ss 00:20:00:00 -acodec copy -vcodec copy output.mpg

```

---

### Post by COKEDUDE on 2012-04-16
Avidemux can also easily do this.

---

