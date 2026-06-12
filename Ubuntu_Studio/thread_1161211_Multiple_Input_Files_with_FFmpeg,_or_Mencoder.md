---
title: "Multiple Input Files with FFmpeg, or Mencoder"
date: 2009-05-16
forum: Ubuntu Studio
---

### Post by unoodles on 2009-05-16
Hi all.
I have 5 or so .vob files that I am trying to combine together. As far as I can tell, neither ffmpeg nor mencoder can accept multiple input files.
Is there a tool to quickly stitch a couple of .vob files together (preferably command-line)?
Thanks in advance!

---

### Post by FakeOutdoorsman on 2009-05-16
Some containers (MPEG-1, MPEG-2 PS, DV, VOB) allow you to concatenate them:
```
cat input1.vob input2.vob input3.vob > all.vob
```

---

### Post by unoodles on 2009-05-16
Thank You!
The resulting vob file had issues, displaying the total length of the video, but I am now able to run the entire resulting file through ffmpeg.

---

### Post by FakeOutdoorsman on 2009-05-16
You might be able to fix the timing issues and skip any re-encoding with:
```
ffmpeg -i all.vob -acodec copy -vcodec copy output.vob
```

---

