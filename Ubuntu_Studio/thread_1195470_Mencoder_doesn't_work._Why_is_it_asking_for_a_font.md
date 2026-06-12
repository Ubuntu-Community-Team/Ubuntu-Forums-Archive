---
title: "Mencoder doesn't work. Why is it asking for a font file?"
date: 2009-06-23
forum: Ubuntu Studio
---

### Post by Endolith on 2009-06-23
```
[swscaler @ 0x883e410]SwScaler: 3264x2448 -> 3264x2448
videocodec: libavcodec (3264x2448 fourcc=47504a4d [MJPG])
New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.
fish: Job 1, &#8220;mencoder "mf://*.jpg" -mf fps=4 -o output -ovc lavc -lavcopts vcodec=mjpeg&#8221; terminated by signal SIGSEGV (Address boundary error)


```

There are no fonts used in this command.  It's just converting a string of JPEGs into a MJPEG.  Is the font error causing it to crash or is it just crashing for no legitimate reason?

---

### Post by andrew.46 on 2009-06-23
Hi Endolith,

> **Endolith said:**
> ```
Please supply the text font file (~/.mplayer/subfont.ttf).
```

Lack of this font would not normally make the whole program crash, but you can place the font anyway and at least rid yourself of the error message:

```

$ mkdir -v $HOME/.mplayer
$ ln -sv /usr/share/fonts/truetype/ttf-bitstream-vera/Vera.ttf ~/.mplayer/subfont.ttf

```

or another font of your choice.

Andrew

---

### Post by Endolith on 2009-06-23
It works if I use smaller JPEGs.  I guess that's a bug?

---

### Post by andrew.46 on 2009-06-24
Hi Endolith,

> **Endolith said:**
> It works if I use smaller JPEGs.  I guess that's a bug?

Sounds a little as if it might be. Mind you it depends a little on which version of MEncoder you are using. The repository version for every Ubuntu version except the alphas of Karmic Koala carry rc2 which in MPlayer terms is quite ancient and a bug report would not be accepted by the MPlayer devs. It would of course be a different story if you were running the current svn?

I tested the syntax taken directly from the man pages with the current svn MEncoder, simply changing the fps and it worked perfectly:

```

andrew@skamandros~/images$ **[COLOR="Purple"]mencoder "mf://*.jpg" -mf fps=2 -o output.avi -ovc lavc -lavcopts vcodec=mpeg4[/COLOR]**
**[COLOR="Purple"]MEncoder SVN-r29374-4.2.4 (C) 2000-2009 MPlayer Team[/COLOR]**
success: format: 16  data: 0x0 - 0x0
MF file format detected.
[mf] search expr: *.jpg
[mf] number of files: 10 (40)
[demux_mf] file type was not set! trying 'type=jpg'...
VIDEO:  [IJPG]  0x0  24bpp  2.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:16  fourcc:0x47504A49  size:0x0  fps:2.000  ftime:=0.5000
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Unsupported PixelFormat -1
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG)
==========================================================================
VDec: vo config request - 1024 x 768 (preferred colorspace: Planar 444P)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar 444P as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
[swscaler @ 0x8e8e200]BICUBIC scaler, from yuv444p to yuv420p using MMX2
videocodec: libavcodec (1024x768 fourcc=34504d46 [FMP4])
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
VDec: vo config request - 1280 x 856 (preferred colorspace: Planar YV12)]
VDec: using Planar YV12 as output csp (no 3)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VDec: vo config request - 1024 x 768 (preferred colorspace: Planar 444P)]
VDec: using Planar 444P as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VDec: vo config request - 3056 x 2292 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 3)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VDec: vo config request - 1142 x 761 (preferred colorspace: Planar 444P)]
VDec: using Planar 444P as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VDec: vo config request - 1024 x 768 (preferred colorspace: Planar 444P)0]
VDec: using Planar 444P as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
Pos:   5.0s     10f (100%)  0.00fps Trem:   0min   1mb  A-V:0.000 [2316:0]
Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream: 2316.006 kbit/s  (289500 B/s)  size: 1447504 bytes  5.000 secs  10 frames

```

and these images were a huge range of large and small.

Andrew

---

