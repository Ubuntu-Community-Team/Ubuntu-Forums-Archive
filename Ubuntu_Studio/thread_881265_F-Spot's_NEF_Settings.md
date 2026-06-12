---
title: "F-Spot's NEF Settings"
date: 2008-08-05
forum: Ubuntu Studio
---

### Post by punong_bisyonaryo on 2008-08-05
Yesterday, lebeyak messaged me asking if I had found the solution to my problem: what settings does F-Spot use with RAW files. It had already slipped my mind. And since the original post is now in the archives, I am posting a new thread in response. The original thread is [here]("http://ubuntuforums.org/showthread.php?t=726159")

As I remembered, I couldn't find this information by searching the web, so I went straight to the source. Source code that is. I downloaded it, and browsed through the directories and found under the src/Imaging folder the DCRawFile class, containing the RawPixbufStream method with a nice, convenient String as below:
```
string [] args = new string [] { dcraw_command, "-h", "-w", "-c", "-t", "0", path };
```

And looking up the dcraw manual, it basically means:
-h Output a half-size color image
-w Use the color balance specified by the camera. If this can’t be found, print a warning and revert to the default,
-c Write decoded images or thumbnails to standard output.
-t 0 disables all flipping

I'm hoping to be able to test this out some time this week, but if anyone could provide any input or insight, it would be much appreciated!

:)

---

