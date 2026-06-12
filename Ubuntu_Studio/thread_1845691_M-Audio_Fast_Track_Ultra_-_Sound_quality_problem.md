---
title: "M-Audio Fast Track Ultra - Sound quality problem"
date: 2011-09-17
forum: Ubuntu Studio
---

### Post by zefiro2 on 2011-09-17
Hi all,

I read some threads which state that **M-Audio Fast Track Ultra** (FTU) USB 2.0 interface works properly on Ubuntu, but I still wonder why it's not so good for me...

I'm currently trying it on Ubuntu 10.10, HP/Compaq nc8430 (T7200 Core Duo @ 2GHz, 4GB RAM); I successfully tested the capture of an electric bass through FTU via Ardour/JACK, correcting the gain to avoid distortion/clipping, but *the sound quality is painfully poor* (the sound appears awfully opaque and numb), while at the same time its analog capture through hardware monitor (plugging headphones through the FTU direct monitor, before its digitization) appears MUCH more detailed and brilliant!

Despite sample rate is currently set to 96000 Hz (see attached JACK settings screenshot), it seems like there's a dramatic loss of information. I'm running an ordinary kernel (neither low-latency nor realtime), but I don't think this may be the cause of such a disgusting result (analog capture through my humble onboard soundcard sounds MUCH better, that's a real shame!).

As I'm a newbie in music recording, I'd really appreciate suggestions from experienced users, especially someone who succeeded in getting a pretty decent sound quality out of FTU. Thank you!

---

### Post by sgx on 2011-09-17
Hi, periods buffer should be 3, not two, for linux usb devices.
Then lower the 1024 to 512, 256, 128 etc to lower latency.

Then instead of Capture, choose duplex, so you hear the ouput of the card.
In the settings page

Input device >
Output device >

click the > for a dropdown list of your detected audio devices, and choose
the mAudio for both. It may be designated with some ice_1712 or similar,
used for the typical envy24 sounchips.

A special mixer for maudio cards called envy24control is good, it may be in the alsa-tools package in synaptic, if not shown separately.

make sure ardour is using the same sample rates as qjackctl.

Cheers

---

### Post by zefiro2 on 2011-09-20
Hi sgx,

thank you for your help; I tweaked the buffering settings as suggested, optimizing the latency, but I discovered that the **real problem** (shame on me!) was *software monitoring option set within Ardour* (menu 'Options/Monitoring/Ardour does monitoring') -- now it's set to 'Options/Monitoring/Audio Hardware does monitoring' and sounds much better. Hope this may help someone else too :D

PS: envy24 apparently did not apply to FTU.

---

