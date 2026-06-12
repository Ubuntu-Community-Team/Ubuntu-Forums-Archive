---
title: "ffmpeg and flv files"
date: 2009-04-01
forum: Ubuntu Studio
---

### Post by Ursidae on 2009-04-01
I'm trying to create a .jpg file using ffmpeg and a .flv file as my input.
Here's what I have:

ffmpeg  -i  myvideo.flv -vcodec mjpeg -an -f rawvideo -s 400x320 test.jpg

No matter what I always receive this error:
I/O error occured
Usually that means that input file is truncated and/or corrupted.

I've tried using a .mp4 file in place of the .flv file and everything works just fine. Is there a codec library I could be missing, or does my command look incorrect?

---

### Post by FakeOutdoorsman on 2009-04-02
> **Ursidae said:**
> I/O error occured
Usually that means that input file is truncated and/or corrupted.
I've only seen this error if the input file is actually corrupted.  Try re-downloading it.

---

### Post by Ursidae on 2009-04-02
Putting apostrophes around the file names solved my problem.

---

