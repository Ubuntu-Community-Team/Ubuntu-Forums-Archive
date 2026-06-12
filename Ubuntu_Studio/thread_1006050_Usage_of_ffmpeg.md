---
title: "Usage of ffmpeg"
date: 2008-12-08
forum: Ubuntu Studio
---

### Post by benoybose on 2008-12-08
I found FFmpeg in the repository of Ubuntu 8.10, Will it be legal for usage in India, for production purpose?

---

### Post by stinger30au on 2008-12-09
everything is legal till u get caught, go for it mate and get it all done

---

### Post by FakeOutdoorsman on 2008-12-09
If this is for personal use you probably shouldn't worry about it, but I am not a lawyer.  You should first read [FFmpeg License and Legal Considerations](http://ffmpeg.mplayerhq.hu/legal.html).  Secondly, you should check if India has implemented software patents.  Also, by default ffmpeg from the Ubuntu repositories has not been configured to use many non-free or restricted formats.  You would have to manually install the "unstripped" ffmpeg libraries to enable encoding and decoding of these additional restricted formats.

---

### Post by nowardev on 2008-12-09
If you** enable restricted formats**

license IS NOT GPL ... so *i think* you can't redistribute 

that's is written when you compile ffmpeg.

---

