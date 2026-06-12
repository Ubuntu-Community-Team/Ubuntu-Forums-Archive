---
title: "HandBrakeCLI Problem"
date: 2008-09-14
forum: Ubuntu Studio
---

### Post by Metallinut on 2008-09-14
Hey all, I hope some guru out there will know exactly what the problem is, and how I can fix it.

I have HandBrakeCLI installed, and can encode movies fine into divx no problem.  But if I try encoding MPEG-4 (-e ffmpeg) I get the following error at the start of the 2nd pass:
```
No accelerated IMDCT transform found
Segmentation fault
```

Here is the encoder command I use:
```
HandBrakeCLI -i /dev/scd0 -o test.mpg -e ffmpeg -E ac3 -2 -m
```

I found some info online about IMDCT being related to AC3, but the same error happens if I use -E mp3 too...

Any ideas?

---

### Post by binbash on 2008-09-19
I am not a guru at least not a media one but i can say : 

IMDCT transform is just a debug msg, you can fix it by compiling a52dec with --enable-djbfft support.BUT IT is just a debug msg.PPl will probably need a trace for the seg fault.

---

