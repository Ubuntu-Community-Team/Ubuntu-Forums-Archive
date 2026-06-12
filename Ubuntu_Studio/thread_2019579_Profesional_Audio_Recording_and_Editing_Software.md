---
title: "Profesional Audio Recording and Editing Software?"
date: 2012-07-07
forum: Ubuntu Studio
---

### Post by rebelplankton on 2012-07-07
I'm new to Ubuntu, actually I don't use Studio, I use Ubuntu 12.04. I need to know which software do you recommend best for audio recording, editing, etc... for a professional studio?

Thanks in advance!

---

### Post by jejeman on 2012-07-07
What do you mean by recording and editing? One track, multitrack etc.

Anyway check out Audacity and Ardour.

---

### Post by rebelplankton on 2012-07-07
> **jejeman said:**
> What do you mean by recording and editing? One track, multitrack etc.

Anyway check out Audacity and Ardour.

Yes, multitrack. to record voice, guitars, bass, drums. I have Audacity, but i need something more professional.

---

### Post by jejeman on 2012-07-07
As I said try Ardour. Also there is Muse, Traverso, Qtractor.

---

### Post by sgx on 2012-07-07
A main Ardour goal has been to record the best audio signal,
I have seen comparisons in a web article years back, and
they were achieving the goal then, while improving greatly in many
expansions in the interim. The Harrison Mixbus collaboration may be
of interest to you/your studio owners

For quick single tracks, timemachine records 24bit w64 files,
which sound excellent.
Cheers

---

### Post by Alecossy on 2012-07-09
I'm wondering, how does the audio delay work with these programs?

---

### Post by jejeman on 2012-07-09
Do you mean delay as effect, or audio latency?

---

### Post by sgx on 2012-07-10
> **Alecossy said:**
> I'm wondering, how does the audio delay work with these programs?
latency is not an issue when things are set up right.

Fender Mustang modeling amps are great for electric guitar
recording, usb and line input, appear by name in qjackctl

---

### Post by WalmartSniperLX on 2012-07-11
I use Ardour. It offers a ton of flexibility, with jack, to allow you to set up resolutions, patching, and ultimately latency. I did a quick setup and got a lower latency using this (around 1-3ms) than I did  in windows using live guitar effects (which will usually add latency due to required time to process). 

To give you an idea of what I've used in a windows based studio, and what I'm now using at home in Ubuntu:

**Reaper --> Ardour** (reaper is actually a very nice DAW but ardour's editor seems smoother while offering all the same features, if not more)
**Pod Farm 2.5 (for guitar and effects) --> Rakarrack** Pod Farm does offer a more "real" sound. It's more similar to actually plugging into an amp than Rakarrack. However, I have not spent a whole lot of time messing with Rakarrack's settings.
**Zynaddsubfx** I use this in place of several MIDI synths. Still need to learn how or where to find more instruments.
**Superior Drummer 2.0 w/ NY Studios License --> Hydrogen ** This is the one that I'm still 'iffy' on. I need to find new samples for Hydrogen since the current ones are very digital (based on some Roland stock kits on their vdrum lineup). However, the engine itself seems to be very promising as it doesn't lack any important features, while having a somewhat more 'friendly' UI.
**qjackctl** Is needed for patching. It's an excellent GUI for jack audio. It's in here where I tweak the settings to achieve low latencies.

---

