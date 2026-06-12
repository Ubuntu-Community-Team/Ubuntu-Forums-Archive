---
title: "Ardour setup help please"
date: 2014-11-11
forum: Ubuntu Studio
---

### Post by John_Kirk on 2014-11-11
Hi...

Im tearing my hair out with Ardour..

Hope someone can stick with me and help me through the config

I have a Envy24 chipset soundcard and am running the latest frest install of Ubuntu Studio.

Basicly, I recorded a Audio track (guitar) in Ardor..
When I try to create vocals on a seperate audio channel Ardour re-records the guitar channel on the new channel along with the vocals.

Im using enclosed headphones.

Where do I start to track down the problem ? ..... Options seem endless. I was told to look at the Alsa mixer confgs but was not told what to look for recently.

thanks...

---

### Post by John_Kirk on 2014-11-11
I open Ardour
Create New Session
Busses master bus = 2 channels
Inputs Auto Connect to Physical
Outputs Auto Connect ... to master bus
Open

Add Audio Track
Mono
Track = normal

In Mixer I have to change from capture_1 to either Capture-11 or Capture_12 to get a signal from my Mic
I record, 
all is well.

Add 2nd Audio Track
Mono
Track = normal

In Mixer I have to change from capture_1 to either Capture-11 or Capture_12 to get a signal from my Mic
I record, 
all is not well. I get a shadow of track one on track 2 as I record to track 2 (not same volume as track 1, lower)

No physical bleed as I record, the issue is internal.

where do I start to fix this issue please ?

---

