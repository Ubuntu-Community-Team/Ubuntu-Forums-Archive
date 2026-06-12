---
title: "Joining Two Video Files Quickly &amp; Easily"
date: 2009-01-23
forum: Ubuntu Studio
---

### Post by HalNineThousand on 2009-01-23
I have to join two videos, in different versions, one in .mpg for DVDs and one in .mp4.  What's the best program that can do this without glitches or a high learning curve on Intrepid?  No editing, no dissolves, just stick one after the other.

Thanks!

---

### Post by cotcot on 2009-01-24
You will need to convert one of the clips to the format of the other.
Joining can than be done in terminal : ```
cat file1.mpg fileconverted.mpg > file.mpg
```.
You can do this also with Avidemux in 2 steps. First step is opening the mp4 clip and convert it to dvd (use the DVD entry under the tab "auto"). Do the same with the mpg video (might be not necessary but it doesn't harm). Then open a new avidemux session. Open the first clip you want. Then append the second (see Append under the "file" tab) and save the result again as DVD.

---

### Post by HalNineThousand on 2009-01-24
Avidemux did it fine.  The only ones I wanted to join were already in dvd format, so it went quick and easy.

Thanks!

---

