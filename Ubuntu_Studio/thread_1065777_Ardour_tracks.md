---
title: "Ardour tracks"
date: 2009-02-10
forum: Ubuntu Studio
---

### Post by mikeymo1741 on 2009-02-10
I run Ardour with Ubuntu Studio 8.10 on a Acer Aspire 3000 notebook.  The soundcard is a SiS7012 with a AC'97 codec. Everything runs fine except one thing: 

I use the mic in to record each track. When I begin to record the second track, it records whatever is on the first track.  Is there a way I can set up my connections so that I can monitor the first track and record on the second track without having it bleed over? 

I have tried track 1 outputs to 1+2 and to Master In - same deal.  If I mute PCM in the soundcard mixer I get no sound at all.

---

### Post by Stochastic on 2009-02-10
You should adjust the inputs to the second track and make sure they're only attached to your microphone.  Hopefully you're listening with headphones, or you might be experiencing acoustic bleed-over.

What are the inputs set to?

---

### Post by mikeymo1741 on 2009-02-11
They are set to system_capture 1 and 2.  

Under the volume control I have the mic selected and line muted.  The only thing that stops it is muting PCM, but then I get no sound on anything.

---

