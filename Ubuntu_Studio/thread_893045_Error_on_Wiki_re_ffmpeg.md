---
title: "Error on Wiki re ffmpeg?"
date: 2008-08-17
forum: Ubuntu Studio
---

### Post by Maverick88 on 2008-08-17
I just read the wiki page on ffmpeg.  It explains how to compile ffmpeg from source and enable some functions (like extra codecs etc).

But I was very surprised that the ./configure line for Hardy Heron does not include "--enable-libmp3lame".  The ./configure line for later versions of Hardy Heron is ALSO missing "--enable-libdts".  (These options are shown for Gutsy etc).

I was able to successfully compile ffmpeg on Hardy Heron 8.04.1 with BOTH "--enable-libmp3lame --enable-libdts". 

Am I missing something?  Does the wiki for ffmpeg contain an error (with respect to the ./configure lines for Hardy Heron and later versions of Hardy Heron")?

---

