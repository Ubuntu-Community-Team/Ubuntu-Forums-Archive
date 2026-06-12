---
title: "jackd not working with creative x-fi sound card"
date: 2009-09-01
forum: Ubuntu Studio
---

### Post by rjawad on 2009-09-01
Hi, 
I just got a new computer a few months ago and have been having a lot of trouble getting ubuntu studio 8.04 to work with my sound card, which is a creative x-fi.  I got the new driver snd-ctxfi and got it working with modprobe.  So the sound works, but jackd, when i click play, still gives the error:

ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa

and then it stops right away. 

I'm wondering if anyone knows hows to get jack working with my sound card.  
OR
I'm wondering if someone can recommend a soundcard for ubuntu studio 8.04 that works with jack.

Thanks in advance.
Ryan

---

### Post by rjawad on 2009-09-01
I don't know whether this would help, but I ran lspci and it shows 2 audio devices.  

01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]
02:00.0 Audio device: Creative Labs SB X-Fi

the ati, i thought, isn't an audio device, but a video card.  but, i'm not so sure now.

anyway, i thought that because there are two, maybe jackd doesn't know which to choose or is confused somehow

---

