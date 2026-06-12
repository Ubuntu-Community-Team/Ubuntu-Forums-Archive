---
title: "Recovering MP4 video"
date: 2015-02-23
forum: The Cafe
---

### Post by cguy on 2015-02-23
Is it possible to recover at least some fragments from a lost MP4 file ?

It was filmed on an Android phone & was lost because of cutting instead of copying while the filesystem was mounted in the wrong mode.

I have dd-ed the whole internal memory and ran file-recovery tools, including photorec/testdisk. None was able to recover it.

Is there a program which can recognize individual frames and put together a video ?

---

### Post by tgalati4 on 2015-02-23
Are you sure the file was stored in internal flash memory?  Perhaps it was stored on the SD card, which is usually where recorded videos are stored.

Otherwise, you would go through sector by sector, following a chain of sectors until you have a group of sectors that you suspect is part of the video.  Then see if there are MP4 keyframes:

```
ffprobe -show_frames video_fragment_that_I_recoverd_after_several_hours.mp4 > possible_keyframes.txt
```

If you get an output that makes sense, then put that fragment in a video editor and see if you can decode and view it.

*photorec* should have found the file if it was a simple delete.  If you are on the wrong disk or wrong partition, then it won't find it.

---

