---
title: "Multiple Soundcards, RME Multifaces, job offer"
date: 2010-12-02
forum: Ubuntu Studio
---

### Post by sonicolonic on 2010-12-02
Simple question here:

Has anyone ever run, seen, or heard of a Linux recording computer with 2 synced RME Multifaces? no resampling with alsa_in/alsa_out audioadapter either, no point really if there's loss in audio quality. 

If so, I might actually pay for a working solution at this point. 

~b

---

### Post by cchhrriiss121212 on 2010-12-02
I can't say for sure, but if you have two identical cards both set to the same sample/bit rates then I don't think alsa_in/alsa_out will resample. And if it did I don't see how it would result in loss of quality. 

Without that you would need to create your own custom asoundrc, maybe looking at this one would help get you started:
[http://www.jrigg.co.uk/linuxaudio/ice1712multi.html](http://www.jrigg.co.uk/linuxaudio/ice1712multi.html)

---

### Post by sonicolonic on 2010-12-02
Been there, done that, no such luck. Even tried it when I was trying to sync my ice1712 and hdsp cards earlier this year with no luck. Ended up using alsa_in/alsa_out but with sooo much added cpu load, made it not really feasible. Also, been having trouble trying to ./configure make jack from scratch to add alsa_in/alsa_out to ubuntustudio, which is frustrating that it isn't there to begin with in the first place. 

If I can actually make the alsa_in/alsa_out tools on my machine I'll give them another try. Actually, I kinda already did. I installed dreamstudio, which conveniently already has alsa_in/alsa_out, and it still didn't work, so noodle that one for a while.

My next attempt is going to be just routing digital outs from one into the other, treat it as a "standalone"  converter that actually leans on the pc as it were, but even then I lose 4 channels @ 96khz. 

...

~b

---

### Post by sonicolonic on 2011-01-03
Setting things up in my new studio. I was able to use HDSPmixer to route the digital outs from one soundcard into the adat lightpipe of the other, syncing via spdif.coax. Only tested this with one recording, seems to be working fine. I lose the 4 channels @ 96khz, but at least I'm using the second soundcard.

---

### Post by AutoStatic on 2011-01-05
Hello, try the [LAU mailinglist]("http://lists.linuxaudio.org/listinfo/linux-audio-user"). Paul Davis or Florian Faber will most likely be able to help you out.

Best,

Jeremy

---

### Post by sonicolonic on 2011-01-07
Hey Jeremy, Thanks, I'll give that a try. Giving it a second thought, I don't have any other gear that uses lightpipe right now, so the only drawback is losing 4 channels @ 96khz. I *could* use HDSPmixer to mix the 8 channels into 4 I believe, but that has it's own drawbacks too. So, I can live with this solution if nothing else works, but it's obviously frustrating. Thanks again man. Hey, check out my studio pix on LM!

~b

---

