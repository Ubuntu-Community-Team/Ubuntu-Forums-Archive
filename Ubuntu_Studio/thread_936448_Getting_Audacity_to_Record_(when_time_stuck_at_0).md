---
title: "Getting Audacity to Record (when time stuck at 0)"
date: 2008-10-02
forum: Ubuntu Studio
---

### Post by tibasic on 2008-10-02
I've been fiddling around with Audacity for a couple hours and either nobody had the same problem as me or nobody knew the answer.

Description of Problem: I downloaded Audacity and clicking record would make my time indicator just sit there and flash at 0.0 (a.k.a it wouldn't record.) I found that if I had "play other tracks while recording new one" checked under Edit>Preferences>Playthrough and another track was in there it would record, but if there was no other track I had the same problem.

On Windows someone had the same problem and the answer was to mute digital capture.

How to solve: I solved my problem by opening my "Volume Control" and Checking everything under preferences. Under the "Recording" tab I muted the microphone on "digital" and unmuted the microphone on "capture"... Ta da! It works!

---

### Post by fredbird67 on 2009-07-01
Tibasic (or T.I. Basic or whatever it is you go by), THANKS A MILLION!  I have been having the very same problem with Audacity on Linux Mint 7 (aka "Gloria"), which I installed just this past weekend.  I was THIS CLOSE to wiping and re-installing Mint, but you've just spared me that grueling process.  In my case, under the device name "VIA 8237 (Alsa mixer)", I enabled the "Recording" tab, clicked on the "Recording" tab, and found that my "capture" setting was indeed un-muted, so I muted it, and now Audacity acts like it's gonna record for me once more, and I couldn't be happier! :p

T.I. Basic, you ROCK, dude! :guitar:  Many, MANY thanx for providing the solution, and I mean that!

Fred in St. Louis

---

