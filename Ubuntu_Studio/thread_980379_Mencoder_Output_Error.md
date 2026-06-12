---
title: "Mencoder Output Error"
date: 2008-11-12
forum: Ubuntu Studio
---

### Post by xchecker on 2008-11-12
I am trying to make a stop motion video from jpegs.  I have tried the Stop Motion software but couldn't get the export function to work.  Found a thread recommending just using Mencoder to do it, so I tried that too.  Here is the error I get:

```
crichmond@brichmond-desktop:/home/brichmond/Photos/2008/09/13$ mencoder mf://*.jpg -mf w=800:h=600:fps=25:type=jpg -ovc lavc \
>     -lavcopts vcodec=mpeg4:mbd=2:trell -oac copy -o output.avi
MEncoder 2:1.0~rc2-0ubuntu13+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) Dual  CPU  E2200  @ 2.20GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 16  data: 0x0 - 0x0
MF file format detected.
[mf] search expr: *.jpg
[mf] number of files: 106 (424)
VIDEO:  [IJPG]  800x600  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:16  fourcc:0x47504A49  size:800x600  fps:25.00  ftime:=0.0400
File not found: 'output.avi'
Failed to open output.avi.
Cannot open output file 'output.avi'.

```

I took the commands directly from the Mplayer documentation for converting a folder of jpegs to an Mpeg4 video.  Why does this fail at output and how do I fix it please?  I am running 8.04 Thanks.

---

