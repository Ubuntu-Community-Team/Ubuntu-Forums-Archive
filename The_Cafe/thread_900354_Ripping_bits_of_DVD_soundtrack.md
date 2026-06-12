---
title: "Ripping bits of DVD soundtrack?"
date: 2008-08-25
forum: The Cafe
---

### Post by whitefort on 2008-08-25
Hi...

Just for fun, I'm toying with the idea of using one-liners from some of my favorite movies as various computer event sounds.

In the past, I've used bits and pieces of Windows software for this, but I'm trying to put all that stuff behind me!

I was just wondering if anyone can recommend anything from the repositories for ripping little bits of DVD soundtrack?

Thanks!

---

### Post by Dr Small on 2008-08-25
ffmpeg. I use it to rip sound from a DVD.
Mount the DVD, cd to it's TS_VIDEO directory, and then you'll have to play around until you finally guess the correct track that has the video on it (they make DVDs confusing).

Then, in the end, I run:
```
ffmpeg -i input_video -vn -f wav /path/to/output.wav
```

From there, you can edit the wav audio file with audacity, cut out whatever you want, and then save it how you want to (like an ogg vorbis).

Dr Small

---

### Post by whitefort on 2008-08-25
Many thanks - that sounds like *exactly* what I need.

Thanks again!

---

