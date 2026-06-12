---
title: "No master control found on HDA ATI HDMI"
date: 2011-02-24
forum: Wine
---

### Post by Omegaham on 2011-02-24
Hello everyone,

I've been trying to figure out how to get my sound working in Wine for a while; it doesn't seem to be working.

Whenever I open Winecfg in the terminal and go to Audio, I get the following:

```
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
```

The same thing happens every time I try to start up a game. Graphics are working fine; it's just the sound that's not working.

I'm using ALSA sound. Every time I test the audio, I get the same error message in the terminal. However, I DO get the "boop" sound, but it doesn't work in-game.

Thanks in advance!

---

### Post by cogadh on 2011-02-25
Pretty much everyone gets that message, it just means that your audio hardware device does not have a master volume control as defined by ALSA, nothing more. Most audio hardware that is not "professional" or "gamer" grade doesn't have that kind of control. It isn't what is preventing your audio from working, what's doing that is (most likely) PulseAudio, the sound system Ubuntu uses but Wine doesn't fully support. Since Pulse is a drop-in replacement for OSS, you can try switching Wine to OSS instead of ALSA, it may make it work.

---

### Post by Omegaham on 2011-02-25
> **cogadh said:**
> Pretty much everyone gets that message, it just means that your audio hardware device does not have a master volume control as defined by ALSA, nothing more. Most audio hardware that is not "professional" or "gamer" grade doesn't have that kind of control. It isn't what is preventing your audio from working, what's doing that is (most likely) PulseAudio, the sound system Ubuntu uses but Wine doesn't fully support. Since Pulse is a drop-in replacement for OSS, you can try switching Wine to OSS instead of ALSA, it may make it work.

Thank you very much. Killed Pulseaudio, (typed killall pulseaudo into the terminal) and it magically started working. You are awesome.

---

