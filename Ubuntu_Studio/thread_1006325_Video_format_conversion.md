---
title: "Video format conversion"
date: 2008-12-09
forum: Ubuntu Studio
---

### Post by benoybose on 2008-12-09
Can any one please help me on converting MPEG video to FLV format, probably by using FFmpeg.

---

### Post by unutbu on 2008-12-09
```
ffmpeg -sameq -i input.mpg output.flv
```
The -sameq flag means the output will have the same quality as the input.

---

### Post by andr100 on 2008-12-09
Many tools can help you! Search in goole please!

---

### Post by Erlander on 2008-12-11
Try Handbrake.

[http://handbrake.fr/]("http://handbrake.fr/")

Rob

---

