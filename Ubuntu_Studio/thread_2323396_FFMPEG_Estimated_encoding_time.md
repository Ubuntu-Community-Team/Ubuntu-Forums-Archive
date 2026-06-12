---
title: "FFMPEG: Estimated encoding time"
date: 2016-05-04
forum: Ubuntu Studio
---

### Post by alfirdaous on 2016-05-04
Hello everyone,

Is there any way to get the estimated encoding time of a video using FFMPEG?

i.e:

```

ffmpeg -i INPUT -strict experimental -vf "drawtext=fontfile='/usr/share/fonts/truetype/freefont/FreeSansBold.ttf':text='www.site.com':x=5:y=30:fontsize=20:fontcolor=white" -vcodec libx264 -preset medium -crf 24 -acodec copy OUTPUT

```

Thanks in advance

---

### Post by FakeOutdoorsman on 2016-05-05
No. However, you could attempt to parse the stats in the console output and do something with that.

If you're asking "how long did this encoding take", then just use time:
```
$ time ffmpeg -i input output
...
real    0m3.026s

```

---

### Post by alfirdaous on 2016-05-05
So there is noway to know before starting the encoding!!

---

