---
title: "convert flv files with nellymoser audio with ffmpeg"
date: 2009-02-06
forum: Ubuntu Studio
---

### Post by etechship on 2009-02-06
I saw that in October of '07 they released something with ffmpeg where we can now do now work with nellymoser audio. I can currently get my video, but no audio. My FLV files have both audio and video. Something else might work, so here are my goals.

Goals:
- I would like to be able to convert video and audio from a flv file and burn it to a DVD
- I would like to be able to convert just the audio from a flv file and burn it to a CD.

Please note that these files are created with red5 (a open source version of FMS). 

Here is a link to one of my files, so that you can test what-ever you think may work before you post it here:
[http://216.6.239.42/~ucsteami/streamVids.php?position=0&file=662](http://216.6.239.42/~ucsteami/streamVids.php?position=0&file=662)

(the extension for the file is .flv)

Thanks
dave

---

### Post by FakeOutdoorsman on 2009-02-06
> **etechship said:**
> I saw that in October of '07 they released something with ffmpeg where we can now do now work with nellymoser audio. I can currently get my video, but no audio. My FLV files have both audio and video. Something else might work, so here are my goals.

What is your FFmpeg command and full output?  FFmpeg from the repository should support decoding of Nellymoser Asao Codec:
```
ffmpeg -formats | grep moser
D A    nellymoser
```
The D indicates that the codec can be decoded and the A indicates that it is an audio codec.  If you compile FFmpeg yourself, you will be able to encode Nellymoser Asao as well: [HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)
> - I would like to be able to convert video and audio from a flv file and burn it to a DVD
FFmpeg can convert the video to a DVD friendly format. You will need to install the **libavcodec-unstripped-51** package to enable encoding with restricted formats in FFmpeg such as mpeg2video, otherwise I think it will default to mpeg1video:
```
ffmpeg -i abi_ec47de928180faa81a0317814eb6e992.flv -target ntsc-dvd output.mpg
```
> - I would like to be able to convert just the audio from a flv file and burn it to a CD.
```
ffmpeg -i abi_ec47de928180faa81a0317814eb6e992.flv output.wav
```

---

### Post by etechship on 2009-02-06
awesome. I just redid my server and started from scrach. I used the ffmpeg from the respo. and I was able to get the audio out fine. Now It seems to have little blaches on the video (you can see the people and background, it just has colored sqaures).

I'm sure I could search on google, but since I have you here, how do I put that .wav file onto a music CD?

so:
- video has colored sqaures: fix?
- put .wav onto a music CD

thanks
dave

---

### Post by FakeOutdoorsman on 2009-02-06
I converted the same video and I don't see any colored squares.  Did you try a different player?  I played the video in mplayer and ffplay and it looks ok.  I'm sure there are several GUI tools in Ubuntu that can burn WAV to CD.  Did you try Brasero?  There are also command-line tools such as cdrecord.

---

