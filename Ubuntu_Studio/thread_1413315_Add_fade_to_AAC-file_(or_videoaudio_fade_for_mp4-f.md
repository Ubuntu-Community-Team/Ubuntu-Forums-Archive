---
title: "Add fade to AAC-file? (or video/audio fade for mp4-file)"
date: 2010-02-22
forum: Ubuntu Studio
---

### Post by rylleman on 2010-02-22
Basically I need to add fade to the end of mp4-clips.

I could do this in some NLE but do not want to re-encode the material.

Now I've created the mp4's in avidemux, from avi, where I've added video fade, but it can't do audio fades (!).
So I split audio and video tracks to separate streams using FFMpeg, intending to add audio fade then mux a/v together again.

But I cant' find a way of adding fade to the end of the AAC-audio. Neither Audacity nor SoX can open AAC-files.

Am I complicating stuff? Should I just start over, importing the avi into an NLE, add fades and re-export the clips?
Or are there a simple way of fading AACs?

---

### Post by FakeOutdoorsman on 2010-02-22
I don't think you can add a fade to AAC without re-encoding, but I would like to be proved wrong.  Can export to WAV from Avidemux?  Then you could use SoX to add the fade and then re-encode to AAC using FFmpeg, neroAacEnc, or any other AAC encoder.  The files can then be re-muxed with MP4Box (part of the **gpac** package):
```
MP4Box -add video.mp4 -add audio.aac output.mp4
```
or FFmpeg:
```
ffmpeg -i video.mp4 -i audio.aac -vcodec copy -acodec copy output.mp4
```
If you only have the AAC audio available, you could use FFmpeg or MPlayer to decode the AAC to WAV, pipe it to SoX to fade, and then pipe it to FFmpeg to re-encode:
```
ffmpeg -i input.aac -f wav - | sox -t wav - -t wav - fade t 0 32 3 | ffmpeg -f wav -i - -acodec libfaac -ab 128k -ac 2 output.aac
```
[B]
Update:[/B] You may need to enable *libfaac* in FFmpeg:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by rylleman on 2010-02-23
I guessed there wasn't an easy way. Strange really. I mean, it shouldn't be such an uncommon task to do I'd imagine.

Thanks!

---

