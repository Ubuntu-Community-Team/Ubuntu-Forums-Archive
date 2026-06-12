---
title: "Audacity errors"
date: 2009-09-19
forum: Ubuntu Studio
---

### Post by Rog-Mahal on 2009-09-19
I'm running Ubuntu Studio 9.04 64 bit on a Macbook 2,1. In an effort to get pulseaudio and jack to play nicely, I upgraded to pulseaudio 0.9.15, but as a result, I can't seem to get audacity to play reasonably.

I've selected ALSA:pulse as my device for both playback and recording, but every time I try and play a track, the first few seconds are played quickly and sound garbled, making it virtually impossible to sample things correctly.

I've tried to ditch the pulse driver and make audacity use ALSA:default, but every time I try to play something I get the following error followed by audacity crashing:

```
$audacity
Expression 'snd_pcm_start( stream->playback.pcm )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 2072
Expression 'AlsaStart( stream, 0 )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 3271

```

Any thoughts?

---

