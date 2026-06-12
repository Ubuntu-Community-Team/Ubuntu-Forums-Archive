---
title: "no sound in mplayer ans controls are not responding"
date: 2006-01-12
forum: The Cafe
---

### Post by paxjapan on 2006-01-12
welcome to my night mare
i have no sound when i log in a movie on my tv/
here is what i have in my ubutu shell konsole=

Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
ALSA lib pcm_dmix.c:802:(snd_pcm_dmix_open) unable to open slave
alsa-init: playback open error: Device or resource busy
Could not open/initialize audio device -> no sound.
Audio: no sound
Starting playback...
VDec: vo config request - 640 x 272 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.35:1 - prescaling to correct movie aspect.
VO: [dfbmga] 640x272 => 640x272 Planar YV12  [fs]
vo_dfbmga: Video surface 640x272 YV12
vo_dfbmga: Field parity set to: Don't care
vo_dfbmga: CRTC2 using triple buffering
vo_dfbmga: CRTC2 surface 720x480 YV12
vo_dfbmga: Sub-picture layer using triple buffering
vo_dfbmga: Sub-picture surface 720x480 ALUT44 (Sub-picture layer)
Linux RTC read error: Interrupted system call
 (!!!)  *** ONCE [accessing video memory during suspend] *** [../../../src/core/surfaces.c:801 in dfb_surface_software_lock()]
(!) [ 8532:    0.000] --> Caught signal 11 (at 0x45, invalid address) <--

i have no clue what to do can some one help me?thank-you

---

