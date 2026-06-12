---
title: "line6linux"
date: 2009-10-06
forum: Ubuntu Studio
---

### Post by JoeHandford on 2009-10-06
I've built the line6linux application using the RT linux headers and installed it. Having rebooted and connected my TonePort UX2 via a USB port I can see that Ubuntu has recognised it by looking at System> Preferences> Sound. However I can't get any sound out of the Toneport. I guess that I'm not configuring something properly. Here's what I did:
In System> Preferences> Sound I have most options set to ALSA - Advanced Linux Sound Architecture. I have the mixer set to HDA Intel (ALSA mixer). I have Sound Capture set to the Tone Port UX2 ALSA option (that now appears following line6linux installation).
I start Jack Control and run the Jack Server and connect the capture inputs of System to the Playback outputs of System. I don't hear anything. I also tried including Rosegarden and recording to an audio track but there was still no sound. Can someone please supply some step by step instructiuons on how to configure Jack, etc now that the TonePort is being recognised?
Thanks, Joe

---

### Post by AutoStatic on 2009-10-20
Hello JoeHandford, what exactly did you build? And what version of Ubuntu? The line6 kernel module from [Markus Grabner]("http://www.tanzband-scream.at/line6/") is included in the Ubuntu kernel since Intrepid Ibex. And the Toneport is supported by that module so it should work OOTB.

---

