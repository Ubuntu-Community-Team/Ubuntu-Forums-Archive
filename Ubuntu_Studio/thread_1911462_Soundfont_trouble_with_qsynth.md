---
title: "Soundfont trouble with qsynth"
date: 2012-01-18
forum: Ubuntu Studio
---

### Post by treacl on 2012-01-18
Hi everyone,

I'm new to qsynth and trying to get a working harpsichord soundfont. [This (synthesized) one]("http://www.realmac.info/hpschd2.htm") works, but [this (sampled) one]("http://sonimusicae.free.fr/blanchet1-en.html") does not work, at least for me.

I used [sfark]("http://www.melodymachine.com/sfark.htm") via Wine to decompress the sf2 file. I then select the sf2 file in the Settings > Soundfonts tab in qSynth, and in qJackCtl connect keyboard to Fluid Synth and Fluid Synth to audio. The green light in the lower lefthand corner of qSynth flashes, but no sound is produced.

Does anyone else have experience with this soundfont? Is there any reason why a sampled soundfont wouldn't work with qSynth, or a sampled soundfont of this size (225 Mb)? Is there any way to check the sf2 file to make sure it isn't corrupted? Anything else I should be checking?

Many thanks,
treacl

---

### Post by Sylos on 2012-01-19
Hello.

This may sound stupid but have you made sure that there is an instrument selected. I nkow form my own experience that some soundfonts load with an instrument already loaded into the channel but some dont and you have to add it for yourself (I forget how now as Im not at my studio PC).

Cheers

---

### Post by treacl on 2012-01-19
Bingo! I didn't even know you had to do that. Thank you.

---

### Post by Sylos on 2012-01-19
No problem.

Please mark the thread as solved.

Cheers

---

