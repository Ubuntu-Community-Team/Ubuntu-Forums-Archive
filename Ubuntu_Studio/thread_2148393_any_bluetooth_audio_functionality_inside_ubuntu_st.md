---
title: "any bluetooth audio functionality inside ubuntu studio (13.04)?"
date: 2013-05-25
forum: Ubuntu Studio
---

### Post by jeff jordan on 2013-05-25
hi folks,

for nearly two months i'm trying to use bluetooth audio equipment like headset, handsfree set or external speaker with ubuntu studio.
unfortuneately it always fails. the bluedio H9 headset seems to connect properly but is non functional and the dual BT100 speaker connects for about 2 seconds but looses connection then.
the only device that works thru bluetooth here is my logilink mouse.
just tried it at different computers, with different bluetooth hw. i even bought a new bluetooth 4.0 EDR compliant dongle, but ubuntu studio behaves always in the same way.

meanwhile i'm still wondering whether ubuntu studio supports bluetooth audio devices, or not.

anybody out there who managed to use some bluetooth audio equipement inside ubuntu studio ?
or somebody who shares my expericence ?

---

### Post by metalf8801 on 2013-05-31
I just got a bluetooth speaker working with my laptop running Ubuntu Studio 12.04 I think what finally did it for me was installing pulseaudio-module-bluetooth and restarting my computer

---

### Post by jeff jordan on 2013-06-02
Thank you for your reply. Didn't knew that it's nescessary to install a special bluetooth module for pulseaudio.

The Dual BT100 speaker now shows up as BTP100 in the pulseaudio configuration, recognized as "High Fidelity Playback (A2DP)" and could be used as expected.
But with the H9 headset, now recognized as "Telephony Duplex (HSP/HFP)", i'm still messing around. 
Seems that the teamspeak client, that i'm trying to configure, still won't use it.
Anyhow, a big **thank you** for your hint.

---

### Post by jeff jordan on 2013-06-04
> **jeff jordan said:**
> ... recognized as "High Fidelity Playback (A2DP)" and could be used as expected.


Ok, meanwhile i discovered that bluetooth audio doesn't really match the low latency approach of ubuntu studio ](*,).
When i use the BTP100 Speaker, a severe delay could be noticed, so this way is not useable when you try to record life music (while the drummer is provided by hydrogen) or want to make some dubbing.
It's ok when you want to play an mp3 in the background, but even when you try to play back some video streams, you may notice the loss of lipsync.

So after all: sudo apt-get remove pulseaudio-module-bluetooth is the result of trying out the bluetooth way [-(.

---

