---
title: "Sound problems"
date: 2009-12-24
forum: Wine
---

### Post by Enk on 2009-12-24
Hi

I have recently got some sound issues in Wine. 

I've used programs like spotify for months without problems, but now suddenly nothing works (no sound in games, strange sound in spotify).

I am running Ubuntu 9.10 x64 and Wine 1.1.35. 

When I run winecfg I get some error-messages saying that mmap() couldn't allocate memory, followed by: 
> ALSA lib pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave

When I go to the audio-tab in winecfg, and press test sound, I can hear the sound but winecfg locks, giving me this error-message:

> err:wave:wodPlayer_WriteMaxFrags Error in writing wavehdr. Reason: Resource temporarily unavailable
ALSA lib pcm.c:7234:(snd_pcm_recover) underrun occured


I have tried OSS without luck, and I know I've used ALSA without problems for months. 

I have not updated wine before I got the problem.

---

### Post by Enk on 2009-12-25
bump :(

---

### Post by ron999 on 2009-12-27
Hi
I used to be able to use Spotify with Wine no problems.
But I've just upgraded to Karmic and the sound was distorted.
So I did the winecfg thing and changed the Audio driver to OSS instead of ALSA.
But it wouldn't work until I installed **oss-compat** using Synaptic.
That cured the prolem.
Spotify's working fine now.
:D

---

