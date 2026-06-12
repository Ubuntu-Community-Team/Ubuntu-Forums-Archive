---
title: "Rift"
date: 2011-07-01
forum: Wine
---

### Post by Sunfist on 2011-07-01
Has anybody gotten Rift to run properly under wine, if so what did you have to do to get it installed and running. I can install it but the frame rate it terrible and it is almost unplayable.

---

### Post by brian70809 on 2011-07-03
See this post..

[http://ubuntuforums.org/showthread.php?t=1742883&highlight=rift](http://ubuntuforums.org/showthread.php?t=1742883&highlight=rift)

search function is your friend.

---

### Post by k3yb0ardn1nja on 2011-08-20
This is a very late reply, but I recently switched to Ubuntu 10.04 from Windows 7 and was having a similar issue with very low frame rates when running rift with wine.

I was able to fix my issue by enabling "Legacy Fullscreen Support" under the "Workarounds" tab in the "Utility" section of the CompizConfig Settings Manager.

I was originally getting 3-4 fps. After enabling that setting I am at 18-35 fps consistently.

**Note:** I had to run Single or Separate X Screen to get this working. Otherwise, the game would default to the resolution of both of my monitors combined, while only displaying on the primary. This made everything squished.

---

