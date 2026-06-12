---
title: "Convert .avi to .ogg"
date: 2009-02-15
forum: Ubuntu Studio
---

### Post by Kidfork on 2009-02-15
Ok so i have a .avi i took form my computer, but i want to put it on Youtube. The file is 208MB and will take forever to upload, But if i convert to .ogg the file probaly wont be so large, so how would i go about converting .avi to .ogg?

---

### Post by FakeOutdoorsman on 2009-02-15
You can use FFmpeg:
```
ffmpeg -i input.avi -acodec libvorbis -ac 1 -b 768k output.ogg
```

---

