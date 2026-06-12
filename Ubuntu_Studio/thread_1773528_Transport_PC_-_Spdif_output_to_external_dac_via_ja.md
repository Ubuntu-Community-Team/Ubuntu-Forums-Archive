---
title: "Transport PC - Spdif output to external dac via jack?"
date: 2011-06-02
forum: Ubuntu Studio
---

### Post by Uriaheep on 2011-06-02
Hello,

I have problems with jack configuration (as well as audio).

I have onboard alc888 chip with coaxial digital out and external dac&stereo amplifier. I'm trying to use jack to playback my flac archive with this setup. External DAC shows there is signal in with 16bit 48khz. But i cant hear any sound from my system. When i shutdown jack and reopen audacious (with alsa output) sound came back. I checked jack configuration, as well as default device in setup. Everything seems fine and there is no error or warning in message window.

My question is; is it possible to bypass digital audio with coaxial connection to external dac with jack? Or am i missing something?

Please help!

Thanks.

---

### Post by cchhrriiss121212 on 2011-06-02
If you just want to play back some FLAC files with audacious, then you don't need jack at all. Unless you would like to use some other jack based software at the same time?

---

### Post by Uriaheep on 2011-06-03
Yes, i know that it can play without jack at all. But jack gives me direct connection to sound chip without modifying any source , with low latency? Is it correct?

---

### Post by Pablo_F on 2011-06-03
I guess few of us US users who frequent this forum use or even know something about jack with spdif output. It could be that someone chime in here but I suggest you also ask in the IRC #jack channel at freenode.net (for example via webchat.freenode.net) or in the linux audio users mailing list.

Cheers, Pablo

---

### Post by Uriaheep on 2011-06-03
Thanks Pablo, i'll check.

---

### Post by cchhrriiss121212 on 2011-06-03
> **Uriaheep said:**
> Yes, i know that it can play without jack at all. But jack gives me direct connection to sound chip without modifying any source , with low latency? Is it correct?
Not really. Jack uses ALSA to talk to the sound card, so you are actually adding an extra piece of software in your audio chain.
Jack does have low latency capability, but latency is not ever going to be noticeable for audio playback.

My advice would be for you to use audacious with pure ALSA, remove pulse audio if you haven't done so already. Pulse does use resampling by default, and you can't change it without messing with config files. Don't ask me why anyone thought that would be a good idea, it is just another reason to avoid pulse.

---

### Post by Uriaheep on 2011-06-04
> **cchhrriiss121212 said:**
> use audacious with pure ALSA, remove pulse audio if you haven't done so already.


That's it! I removed pulseaudio completely. Point out alsa digital output to Audacious. Now i have sweet digital sound to my external dac! Difference is amazing. Thanks Chris!

---

