---
title: "Stream VLC JACK audio from broken file"
date: 2008-07-07
forum: Ubuntu Studio
---

### Post by JohnLM_the_Ghost on 2008-07-07
Well, I've got a broken MPEG-something (TS probably) file
It has **H264** video and **AC3** audio streams.
I want to extract streams and make a new correct file (an MKV, AVI or OGG)

The streams seem to be intact, but headers I believe are messed up or incorrect!

I tried these software to do something with it:
**Avidemux** - fails to open it! (says it cannot determine aspect ratio)

**mkvtoolnix** - finds H264 elementary stream... no audio!

**VLC** - seems to open the file, but any transcoding (I've tried) results file with no audio.

So before anything else I want to extract audio!
I think I could use **VLC's JACK Audio output** to transfer audio to other audio software... **Ardour** perhaps.

Problem is... I have no idea how to use **JACK**!
Any suggestions?

---

