---
title: "DVD-Video to MPEG-2"
date: 2009-08-26
forum: Ubuntu Studio
---

### Post by narcisgarcia on 2009-08-26
The video tracks in a DVD-Video are encoded in MPEG-2, and all rip utilities I find make a conversion to MPEG-4, OGM and others.

Can somebody recommend me an utility to extract an audio and video track from DVD to a common video file, without decoding and recompressing data?

Thanks

---

### Post by psycho on 2009-08-26
If you're wanting to copy video from a DVD without changing it in any way, you can simply copy the VOB files using cp and play them directly with a media player like mplayer. If by "extract" you mean take a specific chapter out of the VOB, dvd::rip can do this (and dvd::rip is a good DVD ripper if you do want to re-encode the video, too). To rip the chapter without re-encoding it, just select the chapter you want, rip it as a VOB, and then exit dvd::rip rather than going on through the other tabs.

---

### Post by narcisgarcia on 2009-08-26
.VOB and .MPG are not the same container format. VOB is video-multitrack, subtitle-multitrack, audio-multitrack (a real container); but .MPG files (what I want) have only a single video track and a single audio track.

Do you mean that with dvdrip I can extract a video track + audio track from a DVD (not only 1 chapter) and obtain a .MPG file without a re-encoded video, or I will obtain a part .VOB?

---

### Post by partake06 on 2009-09-14
> **narcisgarcia said:**
> The video tracks in a DVD-Video are encoded in MPEG-2, and all rip utilities I find make a conversion to MPEG-4, OGM and others.
 
Can somebody recommend me an utility to extract an audio and video track from DVD to a common video file, without decoding and recompressing data?
 
Thanks
 
 
try **Moyea DVD Ripper**, it has **built-in codecs** so that you can easily and fastly rip DVDs to any other popular formats without decoding and recompressing data...
 
Moreover it has **advnaced audio and video sync technology** and **good after-sale service.**

---

### Post by narcisgarcia on 2009-09-14
Can somebody moderate partake06's spam message? The product that partake06 sells is not related with Ubuntu nor free software.

Now I've tried the "DeVeDe" from the repositories, but is since version 3.14.0 that works for me:
[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

---

