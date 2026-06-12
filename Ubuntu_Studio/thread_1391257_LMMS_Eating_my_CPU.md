---
title: "LMMS Eating my CPU"
date: 2010-01-26
forum: Ubuntu Studio
---

### Post by nf119 on 2010-01-26
I am running Ubuntu 9.10 64-bit. I had the same problem back in 9.04 32-bit and I thought the problem would be wiped by the upgrade but no. As soon as it starts up, LMMS eats up one of my cores. Good thing I have two or else the system would be completely unresponsive. LMMS does work pretty good though. But I can't afford to turn my laptop into a hot plate every time I feel like making some beats. How can I diagnose the problem?

---

### Post by AutoStatic on 2010-01-27
Hello nf119, which audio driver are you using in LMMS? And how did you find out it eats up one of your cores?

---

### Post by nf119 on 2010-01-27
Hey Static, reading your post reminded me of gstreamer-properties. I messed around with the Output Plugin selection and the Audio Interface selection in LMMS. Seems like selecting OSS on both lets LMMS run smoothly. Thanks for your help!

---

### Post by AutoStatic on 2010-01-27
Ok, great!

---

