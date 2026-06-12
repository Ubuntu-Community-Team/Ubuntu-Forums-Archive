---
title: "Jack Clients disappearing (9.10 x64)"
date: 2009-11-04
forum: Ubuntu Studio
---

### Post by jeebustrain on 2009-11-04
I've been slowly getting my x64 Karmic setup running over the last few days. I've installed wine and the x64 wineasio and jack (seems) to be configured properly. I've got an M-Audio Delta1010 audio card along with an onboard sound card. I'm only using Jack through the Delta (hw:2) and I'm able to route both midi and audio to/from both wine instruments (FM8, NI B4II, etc...)and native linux apps (zynaddsubfx) to both my audio outputs and midi controllers without issue. Everything seems to play except for that every once in a while things just stop working. I realized that the Audio client (the soft synth) disappears from the Jack Connections window. I have to either close/reopen the synth and redraw the map or (in the case of the VSTs through wine) go into the audio settings and flip from Directx back to ASIO in order to reinitialize the driver. 

I don't ever recall having this issue with 32bit Jack on either Jaunty or OpenSUSE 11.1 (what my desktop was before I rebuilt it). 

I'm having a hard time finding anything useful on the web about this. Has anyone run into this issue before?

---

### Post by AutoStatic on 2009-11-04
With ZynAddSubFX yes, it doesn't like buffer sizes below 128 on my system (Jaunty with 2.6.31-9-rt) with certain instruments.

---

### Post by jeebustrain on 2009-11-04
hmm, I'll try that tonight to see if that makes a diff. What sort of audio card are you using?

---

### Post by AutoStatic on 2009-11-04
Edirol UA-25.

---

