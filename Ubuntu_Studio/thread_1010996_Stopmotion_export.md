---
title: "Stopmotion export"
date: 2008-12-14
forum: Ubuntu Studio
---

### Post by Nate0402 on 2008-12-14
First off I am a newbie and this is my first post. So I am trying to make a simple stop motion video created from a series of images. My issue is that when I try to export the file two boxes come up, one simply says "failed" and the other says the following:

> MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4800+ (Family: 15, Model: 107, Stepping: 2)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 16  data: 0x0 - 0x0
MF file format detected.
[mf] search expr: /home/nate/.stopmotion/packer/tree_first/images/*.jpg

Exiting...
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.


Does anyone know what I should do? Would like to find the fix for this program but would also use another program if there are any suggestions. Thanks.

---

### Post by Katilyst666 on 2009-01-08
I'm having the same problem anybody know why?

---

### Post by schmindy on 2009-01-10
That's three of us:-(

---

### Post by pallian on 2009-01-16
Check out the stop motion video I made using a Nikon D90: [http://www.vimeo.com/2845917]("http://www.vimeo.com/2845917")
i've also written a blog post on how I made the video... hopefully that will help.

The blog can be found here: [http://www.pallian.com/2009/01/15/the-making-of-christmas-jingle/]("http://www.pallian.com/2009/01/15/the-making-of-christmas-jingle/")

---

### Post by 24601oxy on 2009-03-02
I'm also having the same problem. 

```
MEncoder 2:1.0~rc2-0ubuntu17+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 16  data: 0x0 - 0x0
MF file format detected.
[mf] search expr: /home/oxy/.stopmotion/packer/raw/images/*.jpg

Exiting...
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

```

I've been saving the file as "stopcard.avi". 

The post above does not seem to be relevant, as the poster did not use stopmotion, or even ubuntu, from the sound of it.

---

### Post by Peter76 on 2009-03-03
May I suggest:

```
sudo aptitude install stopmotion
```

Never used it myself, but came across it a little while ago...

---

### Post by andrelage on 2009-10-29
hi,

I had the same problem and I solved it be resizing the jpg files [1]: I just chose a smaller dimension. For exporting the video, it worked with memcoder (mpeg4) configuration.

Cheers,

André Lage.

[1] I used this script: [http://gitorious.org/maux-scripts/maux-scripts/blobs/master/imagemagick/resize.sh](http://gitorious.org/maux-scripts/maux-scripts/blobs/master/imagemagick/resize.sh)

---

