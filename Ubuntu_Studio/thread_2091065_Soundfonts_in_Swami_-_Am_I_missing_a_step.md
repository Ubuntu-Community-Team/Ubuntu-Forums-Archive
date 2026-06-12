---
title: "Soundfonts in Swami - Am I missing a step?"
date: 2012-12-04
forum: Ubuntu Studio
---

### Post by vidwarren on 2012-12-04
Hi,

I'm aiming to create soundfonts in Swami. The ultimate goal is to use my keyboards and electronic drum kit to trigger my own MIDI sounds in real-time.

I think I'm most of the way towards having a basic soundfont to test. I've loaded four samples into the samples tree, moved them into the instrument tree, assigned them to their own velocity ranges, and have tried moving the instrument to the 'percussion presets' tree. I've saved the soundfont to .sf2 and loaded it into qsynth.

I still can't get my keyboard to trigger the sounds from my soundfont. It works fine with other soundfonts, so it must be my soundfont that is the problem.

Am using QJackCtrl and RoseGarden.

Any steps that I'm missing? Thanks in advance,

Vid

---

### Post by Sylos on 2012-12-04
Stupid sounding question, but, have you remembered to select the soundfont channel in Qsynth (I found that some already are selected by default but others you to selet manually).

Cheers

---

### Post by vidwarren on 2012-12-04
I got it working!

I think you were right. I think the  Qsynth channels that I needed were set to default channels for **melodic** sounds.

Cheers,

Vid

---

