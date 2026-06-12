---
title: "Can't record audio in Rosegarden and Ardour"
date: 2010-02-26
forum: Ubuntu Studio
---

### Post by fauzie on 2010-02-26
Hi, I need help to get audio recording to work in Rosegarden and Ardour.

I can get recording to work with Audacity. First channel is perfect. The 2nd channel is extremley choppy, but that's not the issue here. The thing is, the mic is working well.

Jack starts without complaints

I just upgraded my computer (both hardware and software), and move my USB soundcard (Zoom S2t) to the new computer running Karmic. The card worked perfectly in the older older running Hardy.

In the new system, playback is working well, as well as recording with Audacity. Only recording in Rosegarden and Ardour doesn't work.

Please help ...

---

### Post by fauzie on 2010-02-26
Ah, found it.
It is because I'm using more than one soundcard. Jack chose the wrong card. Changing the Input device and the Output device in Jack Setup from <default> to the correct sound card fix the problem.

---

### Post by fauzie on 2010-02-26
By the way, if anybody get a problem of choppy recording with Audacity, try to choose Jack as the host for Audacity.

---

