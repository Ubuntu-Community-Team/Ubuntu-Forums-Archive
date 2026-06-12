---
title: "Best way to combine three 7GB mkv files"
date: 2009-02-02
forum: Ubuntu Studio
---

### Post by jbrown96 on 2009-02-02
I have a movie split into three mkv video files. They all use the same codec, resolutions, etc. I am just looking for a way to combine all three. Suggestions on program?

---

### Post by FakeOutdoorsman on 2009-02-03
You could try MP4Box which is part of the **gpac** package:
```
MP4Box -cat file1.mp4 -cat file2.mp4 -cat file3.mp4 output.mp4
```
No quality loss because there is no re-encoding.

---

### Post by FakeOutdoorsman on 2009-02-03
I assumed MP4Box would work with h264/aac mkv files, but it didn't work for me.  Might have better luck with mkvmerge from the **mkvtoolnix** package (mkvtoolnix-gui for GUI), but I have no experience with it:
```
mkvmerge -o output.mkv file1.mkv file2.mkv file3.mkv
```

---

