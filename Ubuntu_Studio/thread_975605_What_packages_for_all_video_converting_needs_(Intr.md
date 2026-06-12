---
title: "What packages for all video converting needs (Intrepid, ffmpeg...)"
date: 2008-11-08
forum: Ubuntu Studio
---

### Post by zackiv31 on 2008-11-08
My ultimate goal is to have a fully function ffmpeg (or mencoder) tool that I can use to convert to/from any video formats.  I mostly have a bunch of TS, AVI, MKV HD files that I want to convert to a format readable by my PS3/XBOX 360... ffmpeg seems to be the key, but I keep getting issues related to codecs not available.

1. Where should I install ffmpeg and other packages from?
2. Are there additional packages I need ?
3. What commands should I use for lossless converting of my files?

---

### Post by nowardev on 2008-11-09
read this 

[http://www.nowardev.netsons.org/?q=node/12](http://www.nowardev.netsons.org/?q=node/12)

---

### Post by FakeOutdoorsman on 2008-11-09
> **zackiv31 said:**
> My ultimate goal is to have a fully function ffmpeg (or mencoder) tool that I can use to convert to/from any video formats.  I mostly have a bunch of TS, AVI, MKV HD files that I want to convert to a format readable by my PS3/XBOX 360... ffmpeg seems to be the key, but I keep getting issues related to codecs not available.

1. Where should I install ffmpeg and other packages from?
I prefer to compile my own ffmpeg:

[HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095")

You can get similar (although dated) functionality by installing the packages nowardev mentions on the very bottom of his web site that he linked to in his post.
> 3. What commands should I use for lossless converting of my files?
This depends on how you intend to use the converted files.  Are they for archiving, editing, etc?  Explain a little more.

---

### Post by zackiv31 on 2008-11-10
I want them in a format playable by my PS3... I'm pretty sure they're all H264, which means I should be able to repackage them without changing the video at all?  I do not want to re-encode unless absolutely necessary... and if I have to I want to do it at basically the same filesize and quality as the original.

---

