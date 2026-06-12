---
title: "Totem fails with some video files"
date: 2012-03-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by x-shaney-x on 2012-03-11
If I try to play some .AVI files, totem refuses to play them and throws up a box with this error: ```
An error ocurred

Internal data stream error.
```

The output in the terminal gives this: ```
** Message: Error: Internal data stream error.
gstavidemux.c(5212): gst_avi_demux_loop (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20/GstAviDemux:avidemux0:
streaming stopped, reason not-negotiated
```

If I try to play a .MPG files then totem doesn't react at all.  No errors in the window or terminal, totem just remains blank and doesn't appear to register anything has happened.


.3GP .MP4 and SOME .AVI files do play fine.

All the normal codec stuff is installed and ALL the videos in question play normally in 11.10.

---

