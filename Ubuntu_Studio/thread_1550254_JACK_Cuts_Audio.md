---
title: "JACK Cuts Audio"
date: 2010-08-10
forum: Ubuntu Studio
---

### Post by Ethan G. on 2010-08-10
Hi- I just upgraded to Ubuntu Studio 10.04 just to give it a try. I have found that when I start JACK, my audio output cuts out completely and for the life of me I can't figure out why. I've attached screenshots of all the setup tabs and the messages window from JACK. Maybe one of you guys can help me figure it out? Thanks in advance.
-Ethan

---

### Post by AutoStatic on 2010-08-11
Congrats Ethan G., JACK works!

A normal desktop session uses PulseAudio to output sound. As soon as you start QjackCtl PulseAudio gets suspended, hence your 'sound issue'. Now if you check the Connections window in QjackCtl you can make new connections there with any JACK aware program like Hydrogen (drum editor), ZynAddSubFX (softsynth) or Aqualung (mediaplayer). And no, Firefox, desktop sounds and all that kind of stuff are not JACK aware.

---

