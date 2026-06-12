---
title: "Ardour / Rosegarden Advice"
date: 2010-01-27
forum: Ubuntu Studio
---

### Post by Entropy_Sam on 2010-01-27
I'm looking into the options available in setting up a hobbyist music production setup on Ubuntu. I've previously had experience of using Ableton on Windows, so I'm accustomed to a powerful midi/audio sequencer with control over a number of audio plugins etc.
 
Having done some research, it looks like the two most interesting apps are Rosegarden and Ardour. Ardour apparently has some VST support (I still have a decent selection of VSTs) but it apparently doesn't yet have MIDI support (and I found 2 year old posts saying people had been waiting for 3 years for that support, so I'm not going to just sit tight and hold my breath there). Is that to say, then, that Ardour only supports live VST play, recording that as sound rather than as a MIDI track?
 
I'm not sure I fully understand the ins and outs of JACK, so can anyone advise me as to what, would be the benefits, if any, of routing the output of Rosegarden into Ardour (or vice-versa).
 
Thanks for your advice...
 
Entropy_Sam

---

### Post by robeast on 2010-01-27
I'm going to give a high level explanation of what I think are some aspects of Ardour and Rosegarden that you will find useful. We can get into the nitty gritty later, and there are many others here who will know much more than me.

The "ins and outs" of JACK are what make it so great; all applications that can use JACK as their sound server can communicate with each other. So you can have some music sequenced in Rosegarden sending that MIDI data to a plugin or VST with MIDI ins that you are using in Ardour (I think that technically uses ALSA, but you can set up the connections through the JACK connections window). JACK applications can use the JACK transport so when you hit play, pause or seek around they are all synced up. It makes for some very interesting possibilities but a lot of patch bay time :) This hasn't been the best example, because Rosegarden can host it's own synths to playback the sequences you write there. I usually do that and then pipe the audio into Ardour to record it.

Don't expect functionality like you have in Ableton, get a simple setup going and experiment. Ardour and Rosegarden have a lot to offer on their own so figure out how they work apart before you put them together. There a lots of other cool audio applications out there too.

---

### Post by prokoudine on 2010-01-28
> **Entropy_Sam said:**
> Having done some research, it looks like the two most interesting apps are Rosegarden and Ardour. Ardour apparently has some VST support
So does Rosegarden, via DSSI-VST ;)

> **Entropy_Sam said:**
> I'm not sure I fully understand the ins and outs of JACK, so can anyone advise me as to what, would be the benefits, if any, of routing the output of Rosegarden into Ardour (or vice-versa).
Well, it depends on how much you usually do with audio tracks. I'd say that 

Rosegarden > MIDI > Synth/Sampler > Ardour

is what most users seem to do.

---

