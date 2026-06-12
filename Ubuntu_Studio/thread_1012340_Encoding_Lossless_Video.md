---
title: "Encoding Lossless Video"
date: 2008-12-15
forum: Ubuntu Studio
---

### Post by Yonderknight on 2008-12-15
Hi,

I've been trying to create a time-lapse video from a sequence of jpeg's I have. So far I've been using ffmpeg to do it and this works just fine for lossy videos. However, I was wondering what should I do if I want to keep a lossless copy (maybe one day I will want to edit it)? I've been trying to mess around with the settings in ffmpeg to get the equivalent of an uncompressed AVI in windows but I can't really find such a thing.

What formats are best for lossless video encoding?

Thanks

---

### Post by eye208 on 2008-12-16
HuffYUV is probably the most popular lossless codec, also widely used on Windows. It's available in FFmpeg too.

FFV1 is FFmpeg's own lossless codec. It yields smaller files than HuffYUV but is still fast enough for realtime video capturing.

x264 will produce lossless H.264 streams if you set a constant quantizer of 0 (zero). This will compress even better than the previous ones, but it will also be slower. It's probably best for archiving.

---

