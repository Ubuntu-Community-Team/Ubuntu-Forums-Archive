---
title: "Delta44 and Peavey PV6 and having some trouble."
date: 2010-11-15
forum: Ubuntu Studio
---

### Post by Wolzly on 2010-11-15
I'm a novice linux user, firstly.

I *seem* to  be able to record tracks in Ardour, using either my bass-guitar or electric guitar.
I can't seem to be able to play the tracks back through my stereo to hear/test them.

I say that they are being recorded  because there are waveforms appearing in the track... so...

I have onboard audio connected to my stereo using spdif connection and I know that is working because system sounds play through the stereo fine, just the playback doesn't work.

I've been looking at the Envy24 levels and during playback there are meters jumping in the PCM Out 1 and PCM Out 2 channels...

I must be able to route the audio going there towards my spdif output on the motherboard I just dont know where to go about that.

...

Thanks in advance! :guitar:


Not sure if I should just make a new thread or if I should go read something somwhere else, but I will ask my question anyways.

I've gotten the Jack Audio Connection Kit working and am looking at "jamin" now with a nice waveform of my guitar on it... 

Not really sure what to do now and with what in order to lay down a track...

---

### Post by RaumTrug on 2010-11-16
hi!

have you tried to set in envy24control, in "patchbay/router"-tab, s/pdif outs to "digital mix", and then leveling/unmuting the right channels in "monitor pcms/input" (try pcm-out 1 left way up, right zero, pcm out 2 right way up, left zero and unmute the turned up sliders with the button below)?

I think with delta cards, when patchbay is set to "s/pdif out" you can direct-feed the s/pdif port, bypassing the mixer, with jack output channels 9&10 instead of 1&2. but the monitor mixer has the advantage of allowing to get the inputs into the mix  without latency.

hope that helps!

---

