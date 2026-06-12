---
title: "Multi-card Jack setup (Firebox &amp; Audigy)"
date: 2009-02-02
forum: Ubuntu Studio
---

### Post by Mynock51 on 2009-02-02
I hate to keep beating a dead horse here, but I have tried everything I can find to get my firebox working in Ubuntu to no avail.  There is a good chance I'm just doing something stupid however.

I can successfully get jackd running in real time with freebob, and I get the blue light on my firebox to come on.  However when I go to hook up the audio inputs and outputs using Patchage (or through the Jack patchbay), the only audio I/O ports I see are system ones:

[IMG]http://img403.imageshack.us/img403/7893/screenshotpatchage1fr0.png[/IMG]

([http://img403.imageshack.us/img403/7893/screenshotpatchage1fr0.png](http://img403.imageshack.us/img403/7893/screenshotpatchage1fr0.png))

My understanding is that the Firebox should show up here in some form.  Right now all I'm looking to do is get audio to play through my speakers in real time.

Thoughts?  Advice?

I should point out that I am running the Firebox through the firewire port on my Audigy ZS soundcard.  I have a pci firewire card, but when I plug the firebox into that it isn't even recognized by gscanbus.  Any help on this issue would be appreciated as well.

---

### Post by Stochastic on 2009-02-02
System is the name of your firebox card.  Try connecting them, it should work.

The number of ins/outs should match your card (if you include spdif and all line outs, etc...).

---

### Post by Mynock51 on 2009-02-02
> **Stochastic said:**
> System is the name of your firebox card.  Try connecting them, it should work.

The number of ins/outs should match your card (if you include spdif and all line outs, etc...).

Thanks for the quick response.  Your reply makes sense, but then where are the audio out ports for my sound card?  I tried connecting all the system in/outs with no luck (I don't have headphones so I can't check the firebox out).

Also I'm still curious why the firebox wouldn't be recognized when going through my other firewire PCI card.  I double checked and the card is correctly using the ohci driver.

---

### Post by Stochastic on 2009-02-03
> **Mynock51 said:**
> ...but then where are the audio out ports for my sound card?  I tried connecting all the system in/outs with no luck...

Do you mean your Audigy2 Soundcard?  Or your Firebox soundcard?  Or do you have some other soundcard that you don't see listed in the Patchage listings?  (the Emu10k1 output is an ALSA driver for Audigy cards)

I can't help you with your firewire card issue as I'm not familiar.

---

### Post by Mynock51 on 2009-02-03
> **Stochastic said:**
> Do you mean your Audigy2 Soundcard?  Or your Firebox soundcard?  Or do you have some other soundcard that you don't see listed in the Patchage listings?  (the Emu10k1 output is an ALSA driver for Audigy cards)

Ah yeah, sorry, I mean my Audigy card.  The Firebox is external.  The Audigy card shows up, but only as a MIDI device and this is where I'm confused.  Maybe this is a stupid question and in the wrong forum, but how do I just patch the audio input from the firebox through to my speakers which are plugged into my sound card?

---

### Post by Stochastic on 2009-02-04
I moved (mine and) your posts to their own thread as they're very different from the firewire setup thread they were under originally.  If you disagree with this move, please speak now.

Could you refer to both of your soundcards by their model name, Audigy or Firebox, this will help all sentences be a little less ambiguous.

I've only ever set jack up to use one driver at a time (alsa, freebob, or ffado).  It's easy to setup a multi-soundcard jack with the same driver, just choose the input and output devices from the qjackctl settings dialog.  Audigy uses the alsa drier, Firebox uses the freebob(or ffado) driver.

Sending sound from the ins of one card to the outs of another could also be done by netjack (I think), but that setup process is not for a beginner to tackle.  Other setups may be possible, but they're probably all quite difficult for beginners.  In the end, the best bet is probably to plug your speakers into the outputs of your firebox; it would take less time than it took me to write this post.

Maybe there is a simple way that I'm not familiar with, so if anyone else knows, please chime in.

---

### Post by thorgal on 2009-02-04
start jackd with freebob for your firewire card.
Use alsa_in and alsa_out for the other card since its driver is ALSA based. alsa_in and alsa_out are tools that are part of netjack. They can resample the audio to sync stuff with the jack master server (that drives your firewire card). All you will get is more physical inputs and outputs in the same jack graph. I hope that's what you want :)

---

