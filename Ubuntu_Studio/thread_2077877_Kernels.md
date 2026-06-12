---
title: "Kernels?"
date: 2012-10-29
forum: Ubuntu Studio
---

### Post by maciekpruski on 2012-10-29
Hi, I have a question about choosing the right Kernel:

I've read that the newer generic Kernels for ubuntu 12.04 and 12.10 perform well enough for audio edition, but using a lowlatency or realtime kernel is still recommended in some threads.

If so, what are the main differences?

If I understand correctly realtime kernels are not only about latency but also about strict deadlines so that timing is right on.
In what areas is it most percievable? Is it when playing an instrument over pre-recorded material? or perhaps the timing of MIDI events? Also, does hardware monitoring make the issue less relevant?

The next question would be about the best choice- rt, lowlatency, lowlatency-pae (what does pae stand for anyway?) or realtime? Also, if you can achieve acceptable latency on a generic kernel , should you switch to  realtime anyway (with higher risk or xruns and different performance issues)

There are probably answers somewhere but I thought it would be good to have a comprehensive one here. Sorry if it has been covered before

P.S. I also have another slightly related question- when I run qjackctl and cadence with the same settings they show a different latency:confused: which one should I trust?

---

### Post by jejeman on 2012-10-30
Don't ask me how and why lowlatency kernel performs better than generic regarding audio production. Which means less xruns.
Simply put: PAE is extension that allowes 32bit kernel to adress more than 3GiB RAM.

Trust your calculator
(frames/sample rate)*period
e.g.
(128/48000)*2=0.005333333=5.3333ms latency

---

