---
title: "Signal routing, ALSA/JACK/SBLive"
date: 2008-05-27
forum: Ubuntu Studio
---

### Post by darsu on 2008-05-27
I have an issue with sound signal paths with ALSA/JACK that I've never been able to solve satisfactorily.

When I start Linux, there's always a signal playback path active. This is to say that if I plug something into my soundcard's input, the system plays it back through the output even if I have no software running.

What is this "default" signal path? What process or daemon controls it? How can I disable it?

The specific nuisance here is that if I start JACK and set up a signal chain in order to eg. play an instrument through it, the signal I get through the sound card output is a mix of two independent signal paths: the processed one that went through my JACK setup and the omnipresent unprocessed mystery signal.

I've been scrutinizing this with mixer programs (Aumix, ALSAmixer). Besides the master volume, none of the volume or panning settings offered by Aumix seems to affect the "default" signal - only the JACK signal. This leads me to the possibility that the uncontrollable signal never even exits my soundcard (SB Live), being routed directly from the input to the output in hardware. Is this possible or likely? Circumventable?

Edit: During the system shutdown process, this signal dies simultaneously with the message of ALSA being shutoff. It would have to be under ALSA control, then...

This isn't a rare soundcard, and I can't be the only one who's wondered about it. I appreciate any insight.

---

### Post by SynthesizersFTW on 2008-05-28
I haven't had an SBLive for a long time, but thinking about what you describe gives me the intuition that real-time monitoring is the "unprocessed mystery signal".  You don't really need it if your host app sends the track's processed output back through the main outs (posiibly along with any other tracks being played back).  Disabling that can be done in QjackCtl if my memory serves...give it a try.  Good luck!

P.S.- I made a lot of really great recordings with that card!  I kind of miss it...

---

### Post by darsu on 2008-05-29
Alas, hardware monitoring and similar options are all off in the JACK config (and as I said, nothing on the JACK level seems to have impact on the signal), but thanks for the hint - I'll look into whether there are similar features hidden in the ALSA layer somewhere.

---

### Post by Higgaion on 2009-11-20
Not sure if you still care, but what you are hearing is the sound card passing it's input directly to it's output. if you run

```
alsamixer -V all
```

You should see a channel for AC97, that will be the pass through of the ADC to the output.
You should see a different channel for AC97 Capture, that is the level of ADC to route into software, like jack.

So zero out the channel for AC97 pass through, and your omnipresent mystery should be solved.

---

### Post by darsu on 2009-12-13
I need to try that. Thanks!

---

