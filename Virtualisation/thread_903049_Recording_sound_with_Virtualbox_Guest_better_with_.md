---
title: "Recording sound with Virtualbox Guest better with ALSA than Pulse..."
date: 2008-08-27
forum: Virtualisation
---

### Post by diablo75 on 2008-08-27
I've just done a little experimenting with Virtualbox to see if I could record sound into it with my microphone.  ALSA (which I tested second) proved to be the most successful.  Pulse Audio...

Well, I'm using Audacity Sound Editor for Windows within the guest machine.  When you record something with it while Virtualbox is using the PulseAudio device, the sound records seemingly half (or other ever other) sampled audio.  When you play it back, it's twice as fast and sounds choppy, but the pitch is kept the same. When you repeat the experiment with ALSA, no problems.

Not sure what to make out of this, but I guess I'll have to use ALSA for the time being.

---

### Post by geograf on 2008-10-17
I confirm this: When I record sound with my microphone, and the VirtualBox Audio Host Driver is Pulse Audio, the Playback is twice as fast and sounds choppy.

The Difference by me is: There is NO Record/Sound with ALSA, with OSS-Driver there is only Playback!

Ubuntu Hardy,  Virtualbox 2.02

---

### Post by reed1 on 2011-01-15
> **geograf said:**
> NO Record/Sound with ALSA, with OSS-Driver there is only Playback!

The same goes for me , fortunately I got OSS recording working with tricks here

```
http://forums.virtualbox.org/viewtopic.php?f=11&t=15068&p=170842
```

---

