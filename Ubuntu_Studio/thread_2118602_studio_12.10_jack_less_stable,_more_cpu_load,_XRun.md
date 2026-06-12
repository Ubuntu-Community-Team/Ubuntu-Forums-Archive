---
title: "studio 12.10 jack less stable, more cpu load, XRuns-QSync silent,  better window mgr"
date: 2013-02-21
forum: Ubuntu Studio
---

### Post by iwl on 2013-02-21
Hi group,

I have just tryed ubuntu studio 12.10 32 - may be the border / resize problem is solved and really is the windows look a little different and the sensitive area for resize is bigger.

Unfortunately the sound-system / jack is much less stable, jack consumes 7 % load when idle and there are a lot more xruns, I played a little with the buffer size I need at least <= 256 BufSize with 2 buffers which is 10ms latency to not hear the latency between my hardwaresynth and QSynth.

With QSynth on the load is 30% playing ore not, I have an xrun every couple of minutes an then I can't hear QSynth anymore until I change Buflen in Patchage and Back.

It is not playable that way while 12.04 was. There I had to do this may be once an hour.

It also seems flash playback is a little slower. On 12.04 I had the feel gotten a little better after installing the X bin ati driver not worked and deinstalled again.

---

### Post by iwl on 2013-02-22
I have just to figure out it is nearly the same with studio 12.04

Buflen 256, 3x QSynth connected to midi keyboard XRun after couple of minutes Qsynth is silent and realy hard to recover, sometimes QSynth restart helps, sometimes jack restart helps sometimes nothing, changing Buflen in Patchage allways but silence again when I close patchage...

The RT load is less with 12.04 ~ 15%.

---

