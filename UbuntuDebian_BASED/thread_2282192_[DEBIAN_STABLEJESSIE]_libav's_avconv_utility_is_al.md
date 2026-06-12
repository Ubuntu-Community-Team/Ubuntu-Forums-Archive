---
title: "[DEBIAN STABLE/JESSIE] libav's avconv utility is always producing low-quality output"
date: 2015-06-12
forum: Ubuntu/Debian BASED
---

### Post by s3a on 2015-06-12
Hello, everyone!

I'm using Debian stable/jessie, and after doing some research on how to convert an ogv file to an avi file using avconv, I ended up with the following command.:
```
avconv -i input.ogv output.avi -global_quality 100
```

All I want is to convert the ogv file to an avi without losing any quality whatsoever (in practice - I suppose in theory avi is a lossy format, which I believe means every conversion to avi will lose some unnoticeable amount of quality).

What am I doing wrong?

Any input would be greatly appreciated!

---

### Post by slickymaster on 2015-06-12
Have you tried [mencoder]("https://help.ubuntu.com/community/MEncoder")?
```
mencoder input.ogv -ovc lavc -oac mp3lame -o output.avi
```The **-ovc lavc** switch is to encode with the libavcodec codec  and the **-oac mp3lame** switch to encode with the lamp mp3 audio codec.

---

### Post by s3a on 2015-06-12
Thanks for the response, but mencoder is no longer supported in newer versions of Debian (and Ubuntu) (and neither is ffmpeg), so I was hoping I could use something in the repositories that is well-maintained.

---

### Post by mc4man on 2015-06-12
That -global_quality 100 likely does nothing plus it's trailing the output, options should be before.
You need to raise the video bitrate considerably, probably to at least 2500k or more.
You could try using q, 0 would produce best but a large file, wouldn't go over 6 for vid or 2 for audio
ex.
```
avconv -i input.ogv  -q:v 2 -q:a 2  output.avi
```

---

