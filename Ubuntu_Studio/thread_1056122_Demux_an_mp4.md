---
title: "Demux an mp4"
date: 2009-01-31
forum: Ubuntu Studio
---

### Post by azangru on 2009-01-31
Okay, so here is an mp4 file that contains a video stream in H264 format and an audio stream in AAC format. Is there an easy linux way to extract these two streams and reencode them individualy into something less exotic? Like get an .m2v video file and a .wav audio file?

---

### Post by sleepingdragon on 2009-02-01
Avidemux allows you to separate audio and video and convert them into different formats. To do the audio, select your audio type from the drop-down list on the left, configure to your exact needs and then use the Audio -> Save menu item. 

The video can be done by changing the main audio track to "none" then selecting the appropriate video codec for your needs - then you save it. You'll then have the two separate streams you asked for.

---

### Post by FakeOutdoorsman on 2009-02-01
FFmpeg can do this as well.  For the audio:
```
ffmpeg -i input.mp4 output.wav
```
And now the video:
```
ffmpeg -i input.mp4 -sameq output.m2v
```
You will need the **libavcodec-unstripped-51** package in addition to ffmpeg to activate restricted encoders such as mpeg2video, libfaac, libmp3lame, mpeg4, etc.

---

### Post by azangru on 2009-02-02
Thank you very much for the advice! The ffmpeg way turned out to be even easier than avidemux, because I got all confused choosing the right video codec in the left-hand panel.

The weird thing with ffmpeg, though, is that the frame size of the saved video track became a bit smaller than the original, so the peripheral part of the image was cut off. Is there any way I could tune the frame size?

---

### Post by FakeOutdoorsman on 2009-02-02
> **azangru said:**
> The weird thing with ffmpeg, though, is that the frame size of the saved video track became a bit smaller than the original, so the peripheral part of the image was cut off. Is there any way I could tune the frame size?
That's odd because it shouldn't change the frame size unless you tell it to.  Paste your FFmpeg command and the full output.  You can specify frame size with the **-s** option: **-s 640x480** for example.

---

### Post by azangru on 2009-02-02
Ok, I re-checked and it turned out I was wrong. The frame size in the m2v output is correct; the cutting of the frame occurs when I import the m2v file in Adobe Premiere on another computer.

---

### Post by FakeOutdoorsman on 2009-02-02
> **azangru said:**
> Ok, I re-checked and it turned out I was wrong. The frame size in the m2v output is correct; the cutting of the frame occurs when I import the m2v file in Adobe Premiere on another computer.
Perhaps Premiere is choosing the incorrect aspect ratio.  In Premiere, right click on a video file, choose Interpret Footage -> Conform to: and choose your aspect ratio.

---

### Post by azangru on 2009-02-03
I imported another version of the video file in Premiere, and now the frame size remained normal. The difference from the previous version was that this time it was not high-definition. Perhaps, Premiere was having problems with high def. :-? That's all right, though; I didn't really need high definition.

Thank you very much for the help!

---

### Post by sramanujam on 2013-03-21
Worked like a magic!!! Thanks.

> **FakeOutdoorsman said:**
> FFmpeg can do this as well.  For the audio:
```
ffmpeg -i input.mp4 output.wav
```
And now the video:
```
ffmpeg -i input.mp4 -sameq output.m2v
```
You will need the **libavcodec-unstripped-51** package in addition to ffmpeg to activate restricted encoders such as mpeg2video, libfaac, libmp3lame, mpeg4, etc.

---

### Post by FakeOutdoorsman on 2013-03-21
> **FakeOutdoorsman said:**
> And now the video:
```
ffmpeg -i input.mp4 -sameq output.m2v
```
You will need the **libavcodec-unstripped-51** package in addition to ffmpeg to activate restricted encoders such as mpeg2video, libfaac, libmp3lame, mpeg4, etc.

Unfortunately, this is incorrect.[-sameq does not mean "same quality"](http://superuser.com/a/478550/110524), and anyway this option has been removed upstream. Instead:
```
ffmpeg -i input -qscale:v 2 output.mpg
```

This is an ancient thread, and old information is often outdated, and I can't edit the old post and fix it (a major annoyance about these forums).

---

### Post by sramanujam on 2013-03-21
> **FakeOutdoorsman said:**
> Unfortunately, this is incorrect.[-sameq does not mean "same quality"](http://superuser.com/a/478550/110524), and anyway this option has been removed upstream. Instead:
```
ffmpeg -i input -qscale:v 2 output.mpg
```

This is an ancient thread, and old information is often outdated, and I can't edit the old post and fix it (a major annoyance about these forums).

Ubuntu did give me a warning when I ran that code saying ffmpeg is deprecated and will be removed in future release. It suggested me to use avconv instead. But still, the command you mentioned worked when I know nothing about these packages! I would try newer ones in future.

Thanks again!

---

### Post by FakeOutdoorsman on 2013-03-21
> **sramanujam said:**
> Ubuntu did give me a warning when I ran that code saying ffmpeg is deprecated and will be removed in future release. It suggested me to use avconv instead.

This is a misleading statement. See:

[list]
[*][Who can tell me the difference and relation between ffmpeg, libav, and avconv?](http://stackoverflow.com/a/9477756/1109017)
[*][The FFmpeg/Libav situation](http://blog.pkh.me/p/13-the-ffmpeg-libav-situation.html)
[/list]

---

### Post by wildmanne39 on 2013-03-28
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

