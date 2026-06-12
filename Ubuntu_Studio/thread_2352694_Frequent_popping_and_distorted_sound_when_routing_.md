---
title: "Frequent popping and distorted sound when routing guitar through jack"
date: 2017-02-14
forum: Ubuntu Studio
---

### Post by bile-kjeld on 2017-02-14
Hi, 

I'm trying to get Ubuntu studio 16.04 going for my home recording setup, but run in to two different problems. I use a Line6 POD UX1 studio audio interface to route my guitar signal into my computer. This works fine, I use alsamixer to select the correct input channel and mute the monitor(Otherwise the signal sounds extremely distorted, not sure if this is related). I fire up qjackctl to start up the jack audio server. When I connect the system captures with the system playbacks, I am able to hear my guitar over my speakers. The default settings I use are:
- Interface selected my POD UX1 studio
- Realtime on
- Samplerate 44100

The two problems I am facing:

1. When I try out more low latency settings, which I need for direct playback, the normal sound of my guitar is alternated by a very distorted sound, like I would hear when keeping the monitoring on in alsamixer. The lowest setting I tried and faced the issue where:
- 128 Frames per period
- 3 Periods per buffer

2. When I try out higher latency settings, there is a frequent popping through my signal. I get this at each setting I tried. The lowest setting which were kind of acceptable latency wise were 
- 256 frames per perios
- 3 frames per buffer

A couple of thoughts come to mind:
- Is my hardware outdated? I'm not running cutting edge hardware, my computer is clicked together at home 4 years ago, but I think it should be acceptable for home recording, especially since it worked on Windows. I use an Intel(R) Core(TM) i5-3330 CPU @ 3.00GHz with 8GB of RAM on a MSI Z77A-G43 motherboard. Surely the soundcard shouldn't be the problem, it is designed for home recording.
- I see a lot of threads getting the realtime kernel, but as I installed Ubuntu studio, which is specifically designed for this purpose, I imagined this is part of the distribution. Am I wrong there?

Is there anyone who experienced similar problems and can help me find a solution?

EDIT: I feel quite stupid I didn't try this sooner. Switching my Line6 Pod from a normal usb port to a USB3.0 port  solved the issue. I am able now to run JACK with quite good settings. 64 Frames per period with 4 periods per buffer gives me a latency of only 6ms. I am looking forward to discovering the world of audio recording on linux further now!

---

### Post by hombrearbol on 2017-02-28
> **bile-kjeld said:**
> EDIT: I feel quite stupid I didn't try this sooner. Switching my Line6 Pod from a normal usb port to a USB3.0 port  solved the issue. I am able now to run JACK with quite good settings. 64 Frames per period with 4 periods per buffer gives me a latency of only 6ms. I am looking forward to discovering the world of audio recording on linux further now!

:biggrin::biggrin::biggrin:Sometimes the solution is right in front of our eyes. I'm glad that everything works fine! Now, go to make music!

---

