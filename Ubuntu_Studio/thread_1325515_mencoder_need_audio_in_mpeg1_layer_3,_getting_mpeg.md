---
title: "mencoder need audio in mpeg1 layer 3, getting mpeg2 layer 3"
date: 2009-11-13
forum: Ubuntu Studio
---

### Post by sdowney717 on 2009-11-13
> mencoder 1313921.divx -o 122boutputmpeg.divx -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1100:mbd=2:vpass=1:vqmin=2:vqmax=31:keyint=30 -ffourcc DIVX -oac lavc -lavcopts acodec=libmp3lame  


[http://www9.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-libavcodec.html#menc-feat-enc-libavcodec-audio-codecs](http://www9.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-libavcodec.html#menc-feat-enc-libavcodec-audio-codecs)

according to this, libmp3lame is supposed to produce mpeg1 audio

transcode the mp4 file gives mpeg 1 audio
but the other file gives mpeg2 audio

found out if you set audio to pcm it will play in the DSM 320
I still dont know how to encode mpeg1 audio!

keyint=250 best for mp4 videos
mencoder 1313921.divx -o 122dcboutputmpeg.divx  -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1100:mbd=2:vpass=1:vqmin=2:vqmax=31:keyint=250 -ffourcc DIVX -oac pcm

---

