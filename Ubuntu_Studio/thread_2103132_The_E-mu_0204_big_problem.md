---
title: "The E-mu 0204 big problem"
date: 2013-01-09
forum: Ubuntu Studio
---

### Post by ABOBA on 2013-01-09
Hi!):P
I bought e-mu 0204 usb soundcard and now I have serios problem. When I'm turning off this card the system crashes. And one way to save the situation is reloading (manualy, with On/Off button).
Also I have e-mu 0404 usb (but not here, it in the another place) and all fine with 0404, but 0204 makes problems(
System: Ubuntu Studio 12.04 64-bit, kernel 3.2.0-35-lowlatency, ALSA 1.0.25, PulseAudio 1.1.0
Thanks in advance
New information: When I kill pulseaudio all fine! :) The jack didn't want to work with PA and I killed PA. Jack started succsesfully! But now I'm without PA(((
Also I have some messages from logs
```

[alsa-sink] alsa-sink.c: ALSA woke us up to  write new data to the device, but there was actually nothing to write!
[alsa-sink] alsa-sink.c: Most  likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report  this issue to the ALSA developers.
[alsa-sink] alsa-sink.c: We  were woken up with POLLOUT set -- however a subsequent snd_pcm_avail()  returned 0 or another value < min_avail.

```

---

