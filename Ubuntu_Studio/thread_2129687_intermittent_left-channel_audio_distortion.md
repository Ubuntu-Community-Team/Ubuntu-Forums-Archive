---
title: "intermittent left-channel audio distortion"
date: 2013-03-27
forum: Ubuntu Studio
---

### Post by potiphera on 2013-03-27
A few months ago, I installed Xubuntu 12.04 and upgraded it to Ubuntu Studio. Since I installed, I've been having an intermittent problem with distortion in the left audio channel. Most of the time my audio is absolutely fine, but occasionally I'll get kind of a crackly sound on that side. The issue is hard to replicate, but it will very occasionally start while playing a Flash video in Firefox, and it also happens sometimes when I'm using Audacity, I think usually after opening a file that isn't at a 44.1 kHz sampling rate. Entering ```
rm -r ~/.pulse ~/.asound* ~/.pulse-cookie
``` in the terminal is usually the only way to fix the problem after it starts (although then I have to restart some open applications to get them to play audio again).

I can also replicate the issue while using JACK if I open Audacity, whether the audio output in Audacity is ALSA or JACK. At that point, all audio playing through JACK will manifest the left-channel distortion. I don't know a terminal command to fix the sound inside JACK, so I have to reboot if I want to get it back to normal. Everything is fine if I stop QjackCtl though.

How do I diagnose the problem and fix this? Thanks!

---

### Post by zequence on 2013-04-04
I would make a bug report about this.

I'm still a little bit unclear about if this only happens when jack is running or not.

If it happens with pulseaudio only, and you are sure jack has not been started at all, then please report a bug for pulseaudio. You'll need to create a launchpad account, if you did not have one. do that first at [https://login.launchpad.net/+new_account](https://login.launchpad.net/+new_account)

Then, in a terminal: ```
ubuntu-bug pulseaudio
```

If this only happens while jack is running, and pulse is connected to jack, that would be interesting to know.

---

### Post by potiphera on 2013-04-12
Thanks for the response! Yeah, the problem occurs even without JACK running.

Do I need to wait for the problem to reoccur before using ubuntu-bug to collect information, or can I do that at any time?

---

### Post by zequence on 2013-04-12
Well, it might help if you wait until it occurs. I'm not sure what will be collected for the bug report, but there may be something useful.

---

