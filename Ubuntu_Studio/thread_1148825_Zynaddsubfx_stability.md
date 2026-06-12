---
title: "Zynaddsubfx stability"
date: 2009-05-04
forum: Ubuntu Studio
---

### Post by raboofje on 2009-05-04
Just wanted to let you know: I had rather bad stability problems with zynaddsubfx on jaunty: switching to the drum bank would reliably disconnect zynaddsubfx from jack, after which both needed to be restarted.

I just compiled zynaddsubfx myself from CVS, and the stability of the home-compiled version is *much* better.

I haven't checked whether this is caused by settings or simply by improvements since the release based on which the package was made.

---

### Post by barisurum on 2009-05-05
Zynaddsubfx uses the OSS sound system, and JACK connects to it via alsa-oss wrapper driver which is not a good idea because Zynadd uses very high resources of DSP which I think causes problems in a non-native wrapper.
I have the very same problem and have had it for a long time. Fortunately there is a project which ports zynaddsubfx as a LV2 plugin: [http://home.gna.org/zyn/](http://home.gna.org/zyn/) 
Maybe you should give it a try.

PS: You may try increasing the timeout setting in JACK setup if a client disconnects from the server unexpectedly. If this is set to low then JACK will wait for a short time to hear from the client and if it doesn't answer will kick it out. Make it 2000 or higher.

---

### Post by raboofje on 2009-05-05
> **barisurum said:**
> Zynaddsubfx uses the OSS sound system, and JACK connects to it via alsa-oss wrapper driver which is not a good idea because Zynadd uses very high resources of DSP which I think causes problems in a non-native wrapper.

Oh, I configured it to use Jack directly (LINUX_AUDIOOUT=JACK in src/Makefile.inc).

> PS: You may try increasing the timeout setting in JACK setup if a client disconnects from the server unexpectedly. If this is set to low then JACK will wait for a short time to hear from the client and if it doesn't answer will kick it out. Make it 2000 or higher.

I want to play in real time, so i like low latencies :).

---

### Post by Stochastic on 2009-05-05
> **raboofje said:**
> I want to play in real time, so i like low latencies :).

The timeout setting value does not affect the latency.  It affects how long it takes before Jack thinks another software program has become non-responsive to the server.  Latency settings are ones that affect the delay from hardware to software such as frames/period, samplerate, and periods/buffer.

---

### Post by carlotheman on 2009-05-06
I can confirm this problem and I assume that it is a problem that goes all the way down to the code itself.

That is why I have discontinued use of ZynAddSubFX and I now attempt to recreate its sound quality using a sound scripting language: SuperCollider.

So far, SuperCollider and Pure Data are the only Linux synths I have tried with acceptable stability for professional live use. (my use case includes pitch and amplitude detection). Systems I have tested include CSound, Pure Data, Om, Ingen, AlsaModularSynth, and ZynAddSubFX. 

There is also an unfinished project aimed at refactoring Zyn while keeping the algorithms: ZynJackU. It is much better at stability, but takes a strong performance hit. Also, there are no presets, and it only reproduces AddSynth.

Carlo

---

### Post by Stochastic on 2009-05-06
> **carlotheman said:**
> So far, SuperCollider and Pure Data are the only Linux synths I have tried with acceptable stability for professional live use. (my use case includes pitch and amplitude detection). Systems I have tested include CSound, Pure Data, Om, Ingen, AlsaModularSynth, and ZynAddSubFX.

How is CSound not stable!?!?

---

### Post by tru infini on 2010-11-12
I was running zynadd all by it's lonesome just fine on 10.04 but when i switched to Centos then back to Uubntu (10.10) I can't get any sound to come out of my zynadd. it shows that sound is coming out and i can record and playback the sound but I can't hear the initial keystroke. it's as if something else is blocking my soundcard.

---

