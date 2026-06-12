---
title: "can't use the built in mic - gazp3"
date: 2007-10-18
forum: System76 Support
---

### Post by tedrampart on 2007-10-18
okay, I awhile ago, I tried to get the built in mic (beside webcam) to work, but eventually gave up.

so I tried since gutsy's working nicely on my gazelle p3, but still am not having any luck.

I've read all the old posts about how to get it working, but my screens don't come close to the ones shown, and I've tried every combination of mic, mic capture, mic boost, different programs etc..

I can get sound recorded from the regular mic input if I plug a mic into it.. the built in one doesn't even record static.

so far I've tried alsa and oss, in both sound recorder and GNUsound .. GNUsound crashed and dropped me back into GDM..

Idealy I would like it to work in a program I can use along with the webcam for video conferencing.

PLEASE PLEASE PLEASE can someone help me.. its getting frustrating..

---

### Post by thomasaaron on 2007-10-19
Hi, tedrampart.

I've been lucking out a lot lately with mic problems! So, let's get this one worked out before my luck runs out!

1. What is the model number on the bottom of your computer?
2. Post output of cat /proc/asound/version
3. Double-click on your speaker. In the resulting window, go to edit > preferences and make sure every box is checked.
4. Tell me what options you have under each tab.

---

### Post by tedrampart on 2007-10-19
model #: Z62JM
output: Advanced Linux Sound Architecture Driver Version 1.0.14 (Thu May 31 09:03:25 2007 UTC).
every box is checked, and has the following under each tab:

playback: master, pcm, microphone, mic boost, internal mic
recording: capture, digital
switches: microphone capture, mix, external amplifier, internal mic capture

---

### Post by thomasaaron on 2007-10-22
OK. I'll do some testing.

Try setting the "Digital" slider to about 50% and the "Capture" slider to about 75%. Play with those a little bit.

---

### Post by tedrampart on 2007-10-22
okay, I'll fool around with them tonight, I'm betting on 4 hours downtime at work..

---

