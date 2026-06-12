---
title: "AVi converter to jpeg"
date: 2010-12-22
forum: Ubuntu Studio
---

### Post by icequeen419got1 on 2010-12-22
I am trying to find a video converter so I can convert it to jpeg or jpeg. I have tried many but all have errors after downloading. I am trying to get this done for Xmas. Please help me!:guitar:

---

### Post by Jose Catre-Vandis on 2010-12-22
ffmpeg is your tool, finding the frame you want to export can be fun, though.

```
#Grab a still frame from an avi (video) file
# -ss x.xx is number of seconds into the video for the grab

ffmpeg -i input.avi -vframes 1 -ss x.xx still.jpg
```

---

